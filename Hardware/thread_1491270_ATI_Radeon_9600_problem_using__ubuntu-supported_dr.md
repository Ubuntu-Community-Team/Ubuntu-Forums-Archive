---
title: "ATI Radeon 9600 problem using  ubuntu-supported driver"
date: 2010-05-23
forum: Hardware
---

### Post by InterAnt on 2010-05-23
Hello there.
I have a particular problem and would like your help.
 
From time to time, my screen gets fuzzy and the only solution is to reboot the computer.
 
sudo lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
 
I am also using the ubuntu-supported driver.
 
As you can see from the picture, all the screen is fuzzy except the cursor arrow.
 
Any suggestion is welcome.
 
Thank you[IMG]http://dl.dropbox.com/u/707011/Screenshot-part.jpg[/IMG]

---

### Post by dino99 on 2010-05-23
into synaptic, you need to have these packages installed:

xserver-xorg-video-ati
xserver-xorg-video-radeon

after reboot, check system admin hardware driver, to see if the driver is activated

---

### Post by InterAnt on 2010-05-23
> **dino99 said:**
> into synaptic, you need to have these packages installed:
 
xserver-xorg-video-ati
xserver-xorg-video-radeon
 
after reboot, check system admin hardware driver, to see if the driver is activated
 
 
I have both of them installed, but when on the Hardware Drivers window, it says: "No Propertary drivers are in use on this system.".

---

### Post by dino99 on 2010-05-23
are you using lucid genuine repo or third party driver ?

---

### Post by InterAnt on 2010-05-23
> **dino99 said:**
> are you using lucid genuine repo or third party driver ?
 
I have some repos on the "Other software" tab.
 
My source.lst have enabled these repos:
 
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid main restricted
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free

---

### Post by Brendo613 on 2010-07-24
Having the same issues with the Radeon 9600LE.  lspci refers to it as an RV350 AP as well.

I searched the nvidia-glx-173, 177, 180, 185, and 96 for the 9600 LE; while there are mentions of the 9600 series, they all have a different suffix.  Is it possible that the LE is not supported, though all its siblings are?!

---

### Post by Yellow Pasque on 2010-07-24
You don't have an nvidia card and your card is no longer supported by ATI's proprietary drivers...
Maybe using updated xf86-video-ati video driver will help: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by Brendo613 on 2010-07-25
Wow.  Whoops.  Thanks for the pointer :D Why would ATI and Nvidia make models in the same numeric series, though ... that's hella confusing.

I'll give an updated version of xf86-video-ati video a whirl and see how it goes.  Thanks again

---

### Post by Brendo613 on 2010-08-10
Never did get this card working.  I gave up and put the old card back in.  The 9600LE really doesn't seem to be supported under linux.

---

