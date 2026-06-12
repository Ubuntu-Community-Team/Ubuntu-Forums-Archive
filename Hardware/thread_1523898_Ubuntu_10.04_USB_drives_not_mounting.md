---
title: "Ubuntu 10.04 USB drives not mounting"
date: 2010-07-04
forum: Hardware
---

### Post by atulkakrana on 2010-07-04
Hello,

I have been using Ubuntu quite a time but this problem has really stumped me.

I can't mount Pendrives or USB storage devices anymore. They used to work on fresh install. The problem came after some updates. 

But if I logout and login, pen drive mounts automatically, But this is quite annoying to close all your work and relogin to mount USB drives.

Please suggest me a solution or at least whats wrong.

---

### Post by dino99 on 2010-07-04
into a console:

sudo update-usbids && sudo update-pciids

mountmanager is an easy tool to deal with partitions and devices, install it with synaptic, then set your prefs with it

---

### Post by atulkakrana on 2010-07-05
Thanks Dino for quick reply.

I tried
**sudo update-usbids && sudo update-pciids**

It downloaded the new IDs but didn't resolved the problem

I have installed the **mount-manager** also

But I have few doubts

1. Do I have to mount every pen drive manually by setting the mount point. In that case it will be very difficult to use

2. As my pendrive mounts fine after I logout and login, I believe that my machine detects pendrive fine but there is some other problem

3. I use my machine for bioinformatics and want to run least processes possible to improve productivity.

"lsusb" shows my pendrive but doesnt mounts the drive


setu@BloodhoundX:~$ lsusb
Bus 002 Device 004: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6407 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
setu@BloodhoundX:~$

---

### Post by atulkakrana on 2010-07-05
I have also tried other fixes like

**sudo modprobe usb-storage**

AND

setu@BloodhoundX:~$ **sudo rmmod -f floppy**
[sudo] password for setu: 
ERROR: Removing 'floppy': No such file or directory

AND

**Disabling Floppy in BIOS**, there is no floppy drive or such option

---

### Post by atulkakrana on 2010-07-05
Ok I tried mounting through mount-manager as suggested

**mount point used : /media/disk1**

Pen drive mounts successfully and I can transfer data too

BUT, no safely remove option

The name of drive is not recognized

AND above all

Cannot unmount

[B]Error: Unable to unmount disk1
umount: /media/disk1 is not in the fstab (and you are not root)[/B]

---

### Post by SonicMetalMan on 2010-07-11
I too have had maddening issues with the 10.04 Ubuntu release across the board regarding automounting of USB drives. Ubuntu, Xubuntu, Lubuntu, and Linux Mint 9 all share the same flaw even with current updates. This is obviously something major broken in the distro and none of the workarounds suggested have a prayer of succeeding. I am really tired of wasting my time trying to get USB drives to mount without rebooting.

Can anybody answer if this is fixed in Ubuntu 10.10? I am about ready to ditch this junk and go back to Fedora or PCLinuxOS. I haven't had this much trouble with Ubuntu since the 8.xx release branch broke the Atmel wireless drivers.

---

### Post by atulkakrana on 2010-07-13
Ubuntu is going down now. They are busy releasing new edition every six months rather then fixing bugs. I have used Ubuntu for 4 years and now I believe that its worth going back to Windows or Fedora. 

I spend a lot of time fixing bugs and if I fix one. two more follows. 

Anyway, the problem got fixed after latest updates and now USB drives are working fine.

But I still have late boot, no brightness control and random wi-fi disconnect problems

---

### Post by jkoval on 2011-11-25
I cannot mount some USB drives and my camera in 10.04,
although the same drives and camera can be accessed on another almost identical 
machine running 10.10.
I don't know if  I have messed up the OS or the hardware is at fault.

---

### Post by James D. Moore on 2012-12-25
I am with you on this I started using ubuntu Warty Warthog and have used Ubuntu and recommended it to everyone but since 12.00 series people call me to fix problems that I my self have trouble fixing used to be it just worked now it needs help and i think that the powers that be have lost contact with the people that they orginally sought to 
serve now its a fanboy/linux nut type situation Unity S#@%s started using PCBSD hope to 
get a more stable system and not go with the FADS just my 2cents worth Dave

---

### Post by overdrank on 2012-12-25
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

