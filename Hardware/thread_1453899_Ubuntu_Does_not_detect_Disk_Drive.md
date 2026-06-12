---
title: "Ubuntu Does not detect Disk Drive"
date: 2010-04-13
forum: Hardware
---

### Post by razbataz on 2010-04-13
Ok so I'm fairly new to this linux stuff. I have learned a little in school so far and have happen to grow fond of it, but I can't seem to get it to load on my system at home. I get the install process where it detects your disk drives and says I need drivers. Ive been on google for the last 2 1/2 days but no luck. 

OS trying to install Ubuntu 9 Server

My system specs:
Phenom 9500
4GB OCZ 800mhz 
motherboard - nforce mi-a78s-8209 (has GeForce 8200 video chipset)
HDD 2X 1TB Hitachi Deskstar 7k1000

My bios does recognize the hard disks so I'm really lost right now. If anyone has any input it would be much appreciated and thank you in advance.

---

### Post by utnubuuser on 2010-04-13
Those disks are probably a raid array?

There's were some release notes about raid setups with Ubuntu 9
I'll try to find the link for you.

The link> [http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

There is a boot option "nodmraid" that might help you get around your problem.

Alternately, you could try disconnecting one of the drives for the install, then adding the second afterwards.

And I've also read that there are settings in BIOS for drive preferences.  Might be worth having a look at.

---

### Post by razbataz on 2010-04-14
Well I have tried uninstalling one of the drives and still no luck. I have gone into the bios and checked out my sata options and tried those. I finally gave up and installed an old 80GB IDE drive which ubuntu took to right away. This is only a temporary fix hopefully considering I bought both of those Hitachi drives for this build. I'm wondering if ubuntu doesnt recognize the other drives because they are sata or if its because they are there are no drivers for those drives yet.

---

### Post by razbataz on 2010-04-14
yeah still no luck. I'm really getting frustrated. I really want to use this OS, but I dont see the point if I cant run it.  if anyone could please at least point me in the right direction it would be much appreciated.

---

