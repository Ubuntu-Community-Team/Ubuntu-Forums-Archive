---
title: "Nvidia driver update problem"
date: 2019-04-24
forum: Hardware
---

### Post by laserburn2 on 2019-04-24
Hi, I use phoronix video driver repo and I've encountered several times an issue like this where I just can't install the Nvidia driver.

[HTML] sudo apt install nvidia-driver-418
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-driver-418 : Depends: xserver-xorg-video-nvidia-418 (= 418.56-0ubuntu0~gpu18.04.1) but it is not going to be installed
                     Depends: libnvidia-cfg1-418 (= 418.56-0ubuntu0~gpu18.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.[/HTML]

I wanted to update the driver from 410 to 418 to get some of that new Vulkan goodies, but then I was visited by this ghost from the past that I forgot how I beat before. The problem was not in the package manager, it was something about installing some kernel headers or something like that. Does anyone have a clue?

---

### Post by #&amp;thj^% on 2019-04-24
> **laserburn2 said:**
> Hi, I use phoronix video driver repo and I've encountered several times an issue like this where I just can't install the Nvidia driver.

[HTML] sudo apt install nvidia-driver-418
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-driver-418 : Depends: xserver-xorg-video-nvidia-418 (= 418.56-0ubuntu0~gpu18.04.1) but it is not going to be installed
                     Depends: libnvidia-cfg1-418 (= 418.56-0ubuntu0~gpu18.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.[/HTML]

I wanted to update the driver from 410 to 418 to get some of that new Vulkan goodies, but then I was visited by this ghost from the past that I forgot how I beat before. The problem was not in the package manager, it was something about installing some kernel headers or something like that. Does anyone have a clue?

Those could be clues you need:
```
apt policy xserver-xorg-video-nvidia-418
apt policy libnvidia-cfg1-418
```
I have No Nvidia card on this machine but they show as availible:
```
me@me-ThinkPad-T430:~$ apt policy xserver-xorg-video-nvidia-418
xserver-xorg-video-nvidia-418:
  Installed: (none)
  Candidate: 418.56-0ubuntu1
  Version table:
     418.56-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu disco/restricted amd64 Packages
me@me-ThinkPad-T430:~$ apt policy libnvidia-cfg1-418
libnvidia-cfg1-418:
  Installed: (none)
  Candidate: 418.56-0ubuntu1
  Version table:
     418.56-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu disco/restricted amd64 Packages
```
I would first see if those are installed first.

---

### Post by laserburn2 on 2019-04-24
[HTML]
apt policy xserver-xorg-video-nvidia-418
xserver-xorg-video-nvidia-418:
  Installed: (none)
  Candidate: 418.56-0ubuntu0~gpu18.04.1
  Version table:
     418.56-0ubuntu0~gpu18.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic/main amd64 Packages

apt policy libnvidia-cfg1-418
libnvidia-cfg1-418:
  Installed: (none)
  Candidate: 418.56-0ubuntu0~gpu18.04.1
  Version table:
     418.56-0ubuntu0~gpu18.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic/main amd64 Packages
[/HTML]

But why would I need to install these two first? Shouldn't the nvidia-driver-418 meta package install them automatically together with the rest? And if I had to specify all the packages for installation, which are they for 418 driver?

---

### Post by #&amp;thj^% on 2019-04-24
> **laserburn2 said:**
> 
But why would I need to install these two first? Shouldn't the nvidia-driver-418 meta package install them automatically together with the rest? And if I had to specify all the packages for installation, which are they for 418 driver?
For some reason they aren't automaticity pulled in with your install, and I don't know why, but try installing them first, and then proceed with the 418 driver.

---

### Post by laserburn2 on 2019-04-25
And then I find an advice on a blog of some Chinese guy. 

> For unmet dependency issue, try removing old NVIDIA proprietary drivers first. 

And sure enough, after I removed the old 410 driver, 418 agreed to install. Now, to test some Proton games.

---

### Post by #&amp;thj^% on 2019-04-25
Good Job, and yes before any new or reinstall the old one must be removed first.
```
sudo apt remove --purge nvidia*
``` 
Enjoy :)

---

