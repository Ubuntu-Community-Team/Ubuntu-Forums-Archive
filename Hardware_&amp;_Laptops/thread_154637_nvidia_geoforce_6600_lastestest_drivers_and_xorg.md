---
title: "nvidia geoforce 6600 lastestest drivers and xorg"
date: 2006-04-03
forum: Hardware &amp; Laptops
---

### Post by madubuntuer on 2006-04-03
My x server has a module that appears to be ad river for my graphics card but it doesn't provided hardware rendering. Is it safe to just install the nvidia drivers? Also it seems xorg and the driver module are sticking thogether as the module cant be removed with out removing xorg.

root@ubuntu:/home/s# apt-get remove xserver-xorg-driver-nv
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  xserver-xorg xserver-xorg-driver-nv
0 upgraded, 0 newly installed, 2 to remove and 31 not upgraded.
Need to get 0B of archives.
After unpacking 1090kB disk space will be freed.
Do you want to continue [Y/n]? n

---

### Post by Sutekh on 2006-04-04
Yes just install the NVIDIA drivers, either the ones from Ubunut's repository (v7667) or an official one from NVIDIA's website (any version you like, but v8178 is latest)

[Ubuntu Forums -  HOWTO Latest NVIDIA Drivers](http://www.ubuntuforums.org/showthread.php?t=75074)

 - Method 1 is dead easy, will take as long as it takes to download the packages, you can install Ubuntu's NVIDIA drivers this way.

 - Method 2 is a little more involved but not that hard, you can install the official NVIDIA drivers this way.

---

