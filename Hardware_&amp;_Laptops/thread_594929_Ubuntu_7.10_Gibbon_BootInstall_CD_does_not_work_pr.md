---
title: "Ubuntu 7.10 Gibbon Boot/Install CD does not work properly with HP Laptop NC8430"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by ufun on 2007-10-28
On this hardware, HP  NC8430 laptop, Gutsy Gibbon does not work.


System Hardware description :

Laptop HP (Compaq) NC 8430

Memory 	: 2 GB RAM
CPU 	: Intel Core2 Duo T5600 @ 1.83 MHz
HDD 	: Western Digital 160 GB SATA WDC WD1600BEVS-60RST0
SATA CRTRL : Intel 82801GBM SATA AHCI 
LCD	: 1680x1050 Pixel
GRAPHICS:  ATI  Mobility Radeon X1600
First partition : Windows XP SP2 

Ubuntu 7.10 Gutsy Gibbon CD.
ISO MD5 Checked ok...
CD Checked ok...
CD can boot on a more (beige box) standard PC.

CD boot to the point where we see the initial splash screen/install menu.

The menu option "Check CD for defect" run properly.
So does the MemTest option. (No errors in my RAM...)
And the "Boot from Hard disk" do bring me to Windows XP SP2 which reside on the first disk's partition.

But otherwise, all the other menu options bring the laptop to a a dark screen :
========================================================
BusyBox v.1.1.3 (Debian 1:1.1.3-5ubuntu7)Built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) [time] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[time ] ata5.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 data 96 in
[time ] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[time ] ata5.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x5a data 128 in
[time ] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[time ] ata5.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x5a data 128 in
[time ] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[time ] ata5.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x5a data 128 in
========================================================

What I wish to do : 

- Run the Ubuntu 7.10 Boot CD
- Run the Gnome disk partition  resizer to shrink the Windows XP SP2 partition 
- Install in the rest of the freed disk space a dual boot Windows / Linux.

Though things are not working as smoothly as I would hope, 
I still want to thanks the many programmers who worked on this project.
Without your efforts, we would not be here. Thanks.

To put things in perspective, our office's stardard Corporate Windows CD did not produced a workable/bootable laptop either. XP SP2 was necessary to recognise the SATA Controller...

By the way, just to do some more test, a Knoppix 5.1 Boot DVD worked fine on this hardware.



Added 2007/10/29 22:45H...

I used GParted ( http: / / partedmagic.com ) and this enabled me to re-size my partition. GParted was able to see the SATA controler properly on its first try.
The Windows partition is still fine, no data lost.

As for the linux install, I choosed CentOS 5 (http: / / www. centos.org) instead. Centos recognised the controller / disk with no problems.

I know this is a Ubuntu  Forum... Still I wished these few comments to be usefull for who might need it.

---

