---
title: "Install - black screen at start"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by SeanOB on 2008-12-20
Hi,

I'm trying to install 8.10 (32bit) on a new machine.

I get a black screen with a flashing cursor when I:
- try to check cd for defects
- try to boot to the live-cd

I do get the snazzy start cd boot screen that lets me choose these options. Oh - and I can run the memory check.

Oh - and I tried another (AMD64) CD and I get the same result.  CD boot screen is fine - but black screen with cursor when I try to do the cd check.

On my other machine a CD check with this same CD runs fine and returns "no errors found" -- so there's nothing wrong with the CD!

Any ideas? Looks like it doesn't like something on my new machine.

My build:
ASUS P5N7A-VM LGA 775 NVIDIA GeForce 9300/nForce 730i HDMI Micro ATX Intel Motherboard
ASUS Black SATA DVD-ROM Drive Model DVD-E818A3T BULK
Western Digital 500GB GreenPower3.5" SATA Bulk/OEM Hard Drive WD5000AACS
Intel Core 2 Duo E8400 3.0 GHz 6M L2 Cache 1333MHz FSB LGA775 Dual-Core Processor
CORSAIR 450w VX Series 12v ATX 80 Plus Certified Power Supply
CORSAIR XMS2 4GB ( 2 X 2GB ) PC2-6400 800MHz 240-pin DDR2 CL5 Dual Channel Desktop Memory Kit - TWIN2X4096-6400C5

I've never had a problem with an ubuntu install before. And I'm at a loss.

Thanks,

Sean

---

### Post by SeanOB on 2008-12-21
A little more information:
When I exit the first ubuntu CD boot menu and then run the CD Defect check I get this error:
PCI: BIOS BUG #0[00000031] found

And then the system hangs.
Any ideas of what that means?

Thanks,

Sean

---

### Post by Sour Mash on 2008-12-22
I know it's of no use to you but I have a very similar issue with my old Toshiba laptop install, it's not gone well :-( I've been at it for days now and, well it's getting no better. I've had a few dodgy CDs that failed the CD check but even now with a good one I get the balck screen of bewilderment with the chirpy blinking cursor and a useless system!

---

### Post by SeanOB on 2008-12-22
I got the regular install to work when I removed my KVM from the keyboard / mouse path and connected them directly. Apparently having the keyboard / mouse plugged in anywhere other than the usb port under the ps2 connector makes the ubuntu installer angry.

Crazy!  At least I'm up and running now.

-Sean

---

