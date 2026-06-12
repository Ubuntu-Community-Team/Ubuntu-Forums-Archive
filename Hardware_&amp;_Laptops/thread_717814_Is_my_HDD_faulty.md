---
title: "Is my HDD faulty?"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by Carl H on 2008-03-07
I have a little used Hitachi Deskstar hard drive, part number HDS722580VLAT20 A320A60A

It has previously had Debian Etch and Ubuntu Studio 7.10 installed on it no problem. I have tried to install Ubuntu Hardy A5 on it, but it won't boot up afterwards, it just hangs with "GRUB" at the bottom of the screen. 

I have just tried to install FreeBSD 6.3 onto it, and during the hardware detection phase I noticed a lot of DMA Timeout errors on ad0 (the hdd). The FreeBSD installer then informed me that the geometry of the drive was unlikely to be correct. I proceeded anyway; the installation failed with a "cant' write to drive" error. 

I have also booted the PC with a PCLOS live CD - on bootup this also mentions DMA Timeout, and also something about "Host Protected Area". 

I have just tried reinstalling Debian, and this reports a "dma_timer_expiry 0x61", a "failed opcode: unknown", and "dma_timer_expiry 0x58 {DriveReady SeekComplete DataRequest}", amongst other ominous sounding things. 

At the risk of asking a daft question - is the drive broken? 

BTW, I have already replaced the IDE cable.

---

### Post by wolfen69 on 2008-03-07
if you used Etch  and Studio before without problems, then yes, i would say it's shot.

---

