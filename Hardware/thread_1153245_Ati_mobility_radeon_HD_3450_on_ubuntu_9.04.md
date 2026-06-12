---
title: "Ati mobility radeon HD 3450 on ubuntu 9.04"
date: 2009-05-08
forum: Hardware
---

### Post by filoa86 on 2009-05-08
Hi there, i've some problem with the quoted video card. I tried to search on ati.amd.com site the driver but there aren't. On ubuntu if i install the fglrx modules doesn't seem to have any changes and can't enable compiz, so, i think that that driver isn't correct. Same is when i used xorg-driver-radeonhd. Anyone solved the problem ?

TY

---

### Post by DJYoshaBYD on 2009-05-08
no ati support in 9.04 yet.. use 8.10 or 8.04

---

### Post by lsatenstein on 2009-05-12
This is my experience/frustration. 
I have a P5Q mother board and the vendor installed the hd3450 video card.
It worked 100% for what I did with it in Ubuntu 8.04, and 8.10.

With 9.04, only the FOSS driver works. The driver to support 3D does not. It locks up so badly, that I ended up reinstalling 9.04.

So, I am using the standard driver from the DVD, with any updates that appear.  I wont try the propriatory hardware test as there is no "going back" if it fails. 

What I would like to have is a forward port of the fgrlx drivers from 8.10.

I also would like to test the new drivers with a switch-users test. With the Compiz capable driver, the only switch user was to perform a complete logout, and a log-in with the next user.

This video option, when solved will allow me to review my Web CAM as I want to be able to use it with amsn, skype and Ekiga.

Please keep me in the loop for some updates and some solutions that worked for you.

My xorg.conf
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

So if you have ideas for additional entries that might help, please advise.

---

### Post by filoa86 on 2009-06-21
any updates ? :)

---

