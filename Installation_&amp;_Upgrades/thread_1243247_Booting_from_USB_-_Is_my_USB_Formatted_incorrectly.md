---
title: "Booting from USB - Is my USB Formatted incorrectly?"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by rhardie on 2009-08-18
I've attempted to create a bootable USB drive using two common techniques that appear to work for others, but not for me.  I'm thinking the commond denominator between the two failed methodologies is my USB drive and I've read that not all USB drives are easily bootable.

My results are that an error message comes up saying my USB drive is not a valid bootable drive.

I reformatted my USB drive (Kingston 4 GB) to FAT32 using either Gparted or USB Startup Disk Creator.

I've tried:
UNetbootin
USB Startup Disk Creator (Ubuntu 9.04)

I've read this wikki [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) with all the command line stuff.

There is mention of setting up the USB drive into two partions with certain names, etc. and there is mention somewhere else of having cylanders too large or small, etc. on certain USB drives.

It seems to me that if there are applications with a GUI that work for others, those applications should work for me too.

Do I just have "Reverse Midas Touch" (Everything I touch turns to S*** instead of gold) or something?

Any suggestions on how I am using the two applications?

---

### Post by stinger30au on 2009-08-18
i installed 9.04 to a 4 gig usb thumb drive a few months ago

from memeory all i had to do was have the thumb drive plugged in and then i just ran usb startdisc creator, find it in system, administration

then point it to the .iso file u want it to put on the thumb drive and let it rip

worked a treat

---

### Post by Mighty_Joe on 2009-08-18
> **rhardie said:**
> 
My results are that an error message comes up saying my USB drive is not a valid bootable drive.

I ran into a similar problem  USB Creator worked on one USB drive, but not on another.  I *think *the problem was [this bug]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/277865") and using GParted to create a new partition, format the drive and write a partition table fixed it.  It's been a few months tho.

> **rhardie said:**
> 
It seems to me that if there are applications with a GUI that work for others, those applications should work for me too.


Not if you are introducing variables like different hardware or using different settings in the GUI. Also, there's no shortage of bugs in the USB Creator.  I ran into three biggies in a day or two of experimenting:
[Persistent partition size limitation]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544")
[Doesn't work unless a partition table exists]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/277865")
[Unclean unmount of persistent partition]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/125702")

---

### Post by dandnsmith on 2009-08-18
There is a page on pendrivelinux.com devoted to whether you will be able to boot from a USB stick - [it's here](http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/)

I used that to check why I had problems with one system

---

### Post by C.S.Cameron on 2009-08-18
Back in the early days of usb-creator, (8.10), I first had to install to my 4G Kingston Traveler using unibootin then erase everything and reinstall using u-c. I think this had something to do with the partition table.
Have you tried your stick on a different computer? some older computer BIOS will not boot from usb and other BIOS can be tricky.

---

### Post by rhardie on 2009-08-19
Thanks for the replies.  I'll try the ideas you have all given and report back.  May take some time due to my lack of time.  :)

---

