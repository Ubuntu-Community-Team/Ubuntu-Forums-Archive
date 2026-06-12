---
title: "Unable to Download and Install of NVIDIA accelerated graphics driver (version 96)"
date: 2009-11-14
forum: Hardware
---

### Post by rebulljr on 2009-11-14
Could use some guidance. 

Installed Ubuntu 9.10 for the first time last night, with the assistance of a friend, on an HP Pavilion zv5000. We ran into problems being able to get my Linksys WPC54G (ver2) wireless card to work. After a couple of hours of trying to follow directions listed in several posts which offer different options using ndiswrapper, my friend gave up in disgust.

Anyway, today I hooked up a usb NIC and was able to connect wireless with no trouble at all.

Being new to linux and ubuntu, I spent some time exploring the system, and at one point was advised to download and install the NVIDIA accelerated graphics driver (version 96) drivers. I have tried numerous times to do exactly that, however, I get to what appears to be between 20%-25% then everything completely stops and does not seem to be progressing at all. Can anyone offer any direction on how to get these drivers to complete their download and install?

---

### Post by Jose Catre-Vandis on 2009-11-14
Do you cancel the process window or does it just pack up by itself. On recent installs I have found that the driver install progress dialog just looks like it has hung, and then just completes by itself? Its one of those "go make a cup of coffee / go for a walk" moments :)

---

### Post by rebulljr on 2009-11-14
> **Jose Catre-Vandis said:**
> Do you cancel the process window or does it just pack up by itself. On recent installs I have found that the driver install progress dialog just looks like it has hung, and then just completes by itself? Its one of those "go make a cup of coffee / go for a walk" moments :)

I have actually had to reboot in order to cancel the download. The last time I tried to do the download I let it run for almost two hours with no progress before I rebooted.

---

### Post by rebulljr on 2009-11-15
Just wanted to give a quick update... I tried to download once more and let it run overnight... still no further progress than I ave gotten thus far.

Any ideas?

---

### Post by aldeby on 2009-11-15
You can simply install this package and say yes to its dependencies
```
sudo apt-get install nvidia-glx-96 
```
This simple step would install the nvidia 3D accelerated drivers.

You could have a look at the Hardware Drivers applet after rebooting and you should see the green light near the 96 drivers.

If you don't try clicking on it and then on "activate".

If still have problems look at file 
```
sudo gedit /etc/X11/xorg.conf
```

and copy/paste this content
```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
EndSection

```

---

### Post by rebulljr on 2009-11-22
I am only able to try working on this on the weekends right now, so please forgive my delays in responding to all your suggestions.

I tried the steps recommended by aldeby. I think (thought I am not 100% certain) that I have the drivers downloaded,[IMG]file:///tmp/moz-screenshot-1.png[/IMG][IMG]file:///tmp/moz-screenshot.png[/IMG] but am still unable to figure out how to install the drivers. Selecting the Activate button, is what I describing in my earlier posts as only getting to about 25% or so. I have attached a screen shot of this.

Following the code below only brings me into a blank file.
sudo gedit /etc/X11/xorg.conf

I am assuming that this means the file does not exist at all and as a result that the driver is not installed.

Still looking for guidance.
rebulljr

---

### Post by doixanh on 2009-11-22
why don't you install & use envyng? it's really great for nvidia cards. I haven't had any trouble using it with 3 different cards (in various systems)

```
sudo apt-get install envyng
```

---

### Post by leg3nddk on 2009-11-26
i had the same problem. but after i did try installing it with terminal. i realized i had put a mark in the repositories on the CD-ROM, by removing that i had no problem with installing it.

---

### Post by WeAreTheSiNs on 2010-01-06
> **leg3nddk said:**
> i had the same problem. but after i did try installing it with terminal. i realized i had put a mark in the repositories on the CD-ROM, by removing that i had no problem with installing it.

That worked for me :) Thanks! :guitar:

---

