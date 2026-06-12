---
title: "Can any body say, how to install ubuntu on an extern harddisk via mac osx???"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by PLZ_HELP_ME on 2005-07-22
HI

i have an ibook g3 with mac osx and an ipod mini as an extern harddisk. i want to install unbuntu on the ipod, because i havent any free space on my intern hareddisk.

it connects via fire wire and has the full 4 GB space free. i have the ubuntu 5.04 install disk and just want to install it. but it doesnt work. if i installed ubuntu, i cant boot from the ipod.(yaboot cant be installed, always mistake).

can any body help me???

---

### Post by interrupt on 2005-08-01
Hi,

it is possible to have an external firewire drive booting Ubuntu (or other Linux). I posted instructions

[here](http://www.ubuntuforums.org/showthread.php?t=29837) 

then the thread died and reappeared again

[here](http://ubuntuforums.org/showthread.php?t=40536) 

Unfortunately, because of limitations in the ability of the kernel to access firewire at boot-time, you have to boot via a RAM disk. And although this is quite straightforward (see my post), it is neccessary to have a working linux system in order to make the modifications required. I got round this by temporarily installing onto my iBook internal drive (having cloned the OSX stuff to a safe place! :) ), installing Ubuntu onto the internal drive, getting the firewire drive bootable, then putting OSX back onto the internal drive.

Another thing you should maybe consider is whether an iPod drive is designed to be used in this way. I don't know, it may be fine, but heavy use as the boot disk of an OS is probably going to be requiring it to do disk activity that it would not have been designed for.

---

