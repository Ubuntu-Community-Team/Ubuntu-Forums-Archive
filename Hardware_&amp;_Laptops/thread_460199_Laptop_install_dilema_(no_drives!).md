---
title: "Laptop install dilema (no drives!)"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by mortalic on 2007-05-31
So I have an older p3-900m lifebook that has no drives.  Worse yet, it will only boot from three things, hard drive, docked floppy, pxe.

I don't have a dock, and there is no OS on the hdd (and the hdd is sandwiched between the keyboard and mobo so taking it out is not going to be fun).  So PXE seems to be my best option.

So I am new to ubuntu but not new to linux, I setup the pxe server and dhcp and I chose the tftp-hal package from apt, it seems to install properly but when I try to start it I get an error "Segmentation Fault Core dumped, Service already started"

It seems to be runnnig, but it doesn't respond to anything.  The laptop boots, get's an IP sees the pxe server and times out on connecting to the tftp server.

Is there something wrong with tftp in 7.04?

---

### Post by Tilo on 2007-05-31
Why doesn't it have a harddrive?   The tablet's specs seem to be:

 	P3-900M, 256MB, 30GB, 10.4" TFT, Ext. 24X CD, 56K, WLAN, 10/100 + 802.11b

which includes a harddrive.. ? 

You could also boot it from a USB attached CDROM.. or attach a harddrive via USB

---

### Post by mortalic on 2007-05-31
no it does have a hdd, I apologize I should have been more specific.  I'm trying to load onto the hdd using pxe over tftp.  It won't boot from USB anything.  No option for it in the bios.  It's kind of old.  Trust me when I say it will only boot from HDD, docked floppy, or PXE.  This to me isn't a problem, but TFTP seems to not work properly in 7.04 or I don't know what I'm doing with tftp (either is a good possibility!)

---

