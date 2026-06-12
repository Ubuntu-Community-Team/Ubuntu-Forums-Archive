---
title: "2 Problems - Lock Screen &amp; Ati Radeon 9250 Drivers"
date: 2008-08-07
forum: General Help
---

### Post by modchamp on 2008-08-07
Ok well I'm loving Ubuntu so far, but I'm currently having 2 problems and looking to get some help.

1. I use the lock screen feature quite a bit and usually during the day, even if it sits a couple hours I'll come back and login just fine, but sometimes when I leave it locked overnight I'll get back in the morning and when I move the mouse or hit a button on the keyboard the screen just goes black for a second then goes back to the screensaver. The password box doesn't come up so I can't unlock the screen and am forced to restart.

2. I've downloaded the linux drivers for the Ati Radeon 9250 and I'm trying to get it installed so that I can use it as opposed to my integrated graphics. Anyways I use sudo su to have root admin access or w/e then when I try and use the command sh ati-driver-installer-8.28.8.run I get the error X Server: Unable to detect then it removes the temp directory and cancels the installation.

All help is greatly appreciated, thanks.

-modchamp

---

### Post by modchamp on 2008-08-08
Bump. Wow dropped to page 20 in 1 day ^_^

---

### Post by modchamp on 2008-08-10
Another bump. Anyone got any ideas?

---

### Post by modchamp on 2008-08-10
More info:

When I run the installer package it gives this:

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install

---

### Post by Ryadt on 2008-08-10
For your graphic card try installing envy 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
or you can try installing the binaries
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by modchamp on 2008-08-10
I've got envyng installed (since I'm using ubuntu 8.04) but when I try to install my graphics card driver I get this:

> EnvyNG - Version 1.1.1
Ubuntu Hardy 32bit
Your graphic card has been detected as a ATI Radeon 9250
Your graphic card is supported by the legacy Driver
EnvyNG ERROR: ATI's legacy driver does not support your operating system

Also just tried installing from the binary and I get the following:

> michael@michael-desktop:~$ sudo dpkg-reconfigure -phigh linux-restricted-modules-'uname -r'
Package `linux-restricted-modules-uname' is not installed and no info is available.
Package `-r' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-restricted-modules-uname -r is not installed

---

### Post by modchamp on 2008-08-12
Any suggestions?

---

### Post by itkeepsrepeating on 2008-08-15
I am having the same exact problems with the ati driver installation as original poster, right down to word-for-word errors. I am trying this on an ati radeon 9600XT card. Also, during the process of trying to install both ways, i've borked my xorg.conf, and only run in safe-graphics mode. Any suggestions as to get it back to original, so i may start over? Thanks in advance...

---

### Post by modchamp on 2008-08-17
Try dpkg-reconfigure xserver-xorg

Anyone else able to help us out with this stuff?

---

### Post by modchamp on 2008-08-20
Bump

---

### Post by freackout on 2009-09-03
> **modchamp said:**
> More info:

When I run the installer package it gives this:

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install

Mint 6 picks up this card no problem compiz works out of the box (abslolutly no configuring at all) its also compatible with ubuntu though i did have some issues with mint 7 its new and stuff is not final so its expected, thanks guys enjoy.

---

