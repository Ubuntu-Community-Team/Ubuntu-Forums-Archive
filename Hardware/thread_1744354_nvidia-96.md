---
title: "nvidia-96"
date: 2011-04-30
forum: Hardware
---

### Post by cane on 2011-04-30
I've installed 11.04, after login it says I don't have the required hardware to run unity so it reverted back to gnome. Ok, I don't even care. But when I tried to install nvidia drivers I've got the following surprise:

> 
sudo apt-get install nvidia-96

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-96 : Depends: xorg-video-abi-8.0 but it is not installable
             Depends: xserver-xorg-core (>= 2:1.8.99.905-1ubuntu3) but it is not going to be installed
E: Broken packages


What the hell is that?

---

### Post by eugenie98 on 2011-05-01
I'm encountering the same problem in 11.04 on a fresh install on my Dell Inspiron 2650 (Geforce 2 Go)

olddell@ubuntu:~$ sudo apt-get install nvidia-96
[sudo] password for olddell: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-96 : Depends: xorg-video-abi-8.0 but it is not installable
             Depends: xserver-xorg-core (>= 2:1.8.99.905-1ubuntu3) but it is not going to be installed
E: Broken packages

---

### Post by eugenie98 on 2011-05-01
Looks like it's a known issue with the 96 drivers

[http://askubuntu.com/questions/33204/why-am-i-unable-to-install-the-nvidia-96-driver](http://askubuntu.com/questions/33204/why-am-i-unable-to-install-the-nvidia-96-driver)

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/741930](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/741930)

I don't see any workarounds or fixes yet.

---

### Post by cane on 2011-05-02
Yes, thanks, those problems seems to be related to nvidia-96 drivers compatibility issues with xorg server 1.10. As a sidenote, also nvidia-173 drivers seem to be subject to the same issues. I guess the only way to solve the problem is to wait for nvidia to release updated drivers.

---

### Post by balor123 on 2011-05-09
Do we have an ETA on when Nvidia is planning on updating these drivers? It's a problem for me as well. I'm using the Nouveau drivers in the mean time however due to bugs I can't use two monitors with them.

---

### Post by cane on 2011-05-10
The problem has been raised on nvnews:

[http://www.nvnews.net/vbulletin/showthread.php?t=162140](http://www.nvnews.net/vbulletin/showthread.php?t=162140)

but still no news.

---

### Post by rolnics on 2011-05-10
> **cane said:**
> also nvidia-173 drivers seem to be subject to the same issues. I guess the only way to solve the problem is to wait for nvidia to release updated drivers.

Thought it was my usual problem, now I know its the drivers and I'm not going to get around it for a while!

I don't particularly hold out hope of this being a quick fix.

---

