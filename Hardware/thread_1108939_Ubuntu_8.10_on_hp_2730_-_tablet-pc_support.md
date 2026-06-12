---
title: "Ubuntu 8.10 on hp 2730 - tablet-pc support"
date: 2009-03-28
forum: Hardware
---

### Post by gugus2009 on 2009-03-28
Hello 

I'm quite new on ubuntu. On my tablet-pc hp 2730p runs ubuntu 8.10 (hopefully soon 9.04)
Can anyone tell me how to make tablet-pc features like rotation and stylus available ?

---

### Post by Favux on 2009-03-28
Hi gugus2009,

Welcome to Ubuntu!

I should be able to help you.  I think the inbuilt digitizer is Wacom, do you know?  The 2710 was a serial tablet, is yours?  Or is it a usb Wacom tablet?  Does your stylus have an eraser?  Are there buttons on the stylus?  If so how many?

One of the things we will have to do is edit the xorg.conf.  You have to be careful with it.  If you break it you will not boot into your desktop.  You'll need to boot into low graphics or recovery mode.  It is at /etc/X11/.  So to back it up in a terminal type (or copy and paste):
```
cp /etc/X11/xorg.conf /etc/X11/my_xorg.bak
```
or whatever you want to name the backup.  And to restore it:
```
cp /etc/X11/my_xorg.bak /etc/X11/xorg.conf
```
To edit xorg.conf you need to be root and will probably want to use the gnome editor gedit.  So you would use:
```
gksudo gedit /etc/X11/xorg.conf
```

A good source is Loic2's Wacom wiki:

[https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom")

Also on the wiki are linuxwacom driver and tools deb's, the 0.8.1-6 version, that we will probably want to install later.  The deb's are pre-packaged Debian packages.  You download them (onto your desktop) and dbl-click them.  Then the Debian package installer will install them.  They show up in Ubuntu's Synaptic Package Installer as if it had installed them.

So a good first step is to answer the questions and post a copy of your xorg.conf.  To get a copy without any danger of damaging it don't make yourself root.  Either navigate to it with Nautilus (Places) or use:
```
gedit /etc/X11/xorg.conf
```
and copy and paste it.

I hope this is helpful.

---

