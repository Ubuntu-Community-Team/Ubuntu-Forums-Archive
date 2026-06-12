---
title: "Install disk won't run"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by Sifr on 2009-06-15
I'm trying to install the most recent version of Ubuntu on my Macbook using the basic install-via-CD option. This is the second time I've tried; last time the disk was corrupted, this time I just get a black screen with a flashing white underscore when I boot from the disk. What can I do to make the install CD boot correctly?

I'm a complete novice in the ways of OSes, so the simplest explanation possible would be much appreciated.
Thanks.

---

### Post by yeats on 2009-06-15
Hi there,

I'm assuming you did an [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") check of the disk image (.iso) file before burning?  Did you also verify the CD integrity from the main menu of the Ubuntu disk?

---

### Post by Sifr on 2009-06-15
I hadn't run the md5 check, so thanks for cluing me in on that. The hash was normal, though, so that's not the issue. As for the check from the install menu, I can't even get that far.

I set the boot disk to the burned CD, restarted, and got a blank black screen that does nothing and does not respond to the keyboard for commands.

Apparently the burned .iso is completely fine, but my computer refuses to run it from the disk.

---

### Post by yeats on 2009-06-15
> **Sifr said:**
> I hadn't run the md5 check, so thanks for cluing me in on that. The hash was normal, though, so that's not the issue. As for the check from the install menu, I can't even get that far.

I set the boot disk to the burned CD, restarted, and got a blank black screen that does nothing and does not respond to the keyboard for commands.

Apparently the burned .iso is completely fine, but my computer refuses to run it from the disk.

So do you know that this CD drive is in good working order?  You could attempt to boot from USB:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Sifr on 2009-06-18
I've never had an issue with the drive for any other purposes, but I'll give that a shot and post the results. Thanks again.

---

### Post by perceptus on 2009-06-18
I have run into some drives that are built so that they won't boot even when set to. You might google this for better information.

---

### Post by MyR on 2009-06-18
Does your macbook have an intel processor?

---

### Post by msp3k on 2010-01-07
I have run into this problem as well.

I have about 30'ish iMacs, varying in model from iMac7,1 to iMac9,1.  The iMac7,1 and the iMac9,1 both boot the install disk just fine, but the iMac8,1 is the model that I have a problem with, and it is exactly as the original poster explains:

1) Turn off iMac, put CD into boot drive
2) Turn on iMac while holding down the 'c' key (to boot from the CD)
3) Screen goes black, flashing cursor is seen in the top-left of the screen

I have verified that the machine's internal CD drive is functioning normally, as it will boot the OSX install disk just fine, but the Ubuntu installer will not work.  I have tried the following disks:

ubuntu-9.10-desktop-amd64.iso
ubuntu-9.10-server-amd64.iso
ubuntu-9.10-desktop-i686.iso
ubuntu-9.04-server-amd64.iso
ubuntu-9.04-server-i686.iso

My next step was to try an external CD drive plugged up via USB. *** This worked.***

Since the internal drive does in fact work on on the OSX disk, I can't say that there is anything wrong with the internal hardware.  Maybe it is some incompatability between the Ubuntu ISO boot loader and the iMac8,1 hardware.

The CD drive on this particular run of iMac8,1's is a:
Make/Model: Matshita DVD-r UJ-875
Firmware: DB09
Interconnect: ATAPI
Cache: 2048 KB

Oddly enough, this used to work.  We had a copy of 8.10 installed on this thing, but the very same 8.10 install CD no longer works either.

---

