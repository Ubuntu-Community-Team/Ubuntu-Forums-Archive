---
title: "About Kingston RAM modules"
date: 2012-12-11
forum: Hardware
---

### Post by satimis on 2012-12-11
Hi all,

This is a newly built PC with following config:-

AMD 8-core FX-8150 CPU
Motherboard ASUS M5A97R2.0
Video card	ASUS HD6450 Silent 1GB DDR3
Hard Disk	WD 2TB Black Series
RAM	Kingston HyperX KHX1600C10D381K2/16G (2x8G) (Blue Memory)
OS  Ubuntu 12.04 desktop 64bit

Installation w/o problem.  PC is now working.

$ sudo lshw -short -C memory```

H/W path             Device     Class       Description
=======================================================
/0/0                            memory      64KiB BIOS
/0/4/5                          memory      384KiB L1 cache
/0/4/6                          memory      8MiB L2 cache
/0/4/7                          memory      8MiB L3 cache
/0/2c                           memory      16GiB System Memory
/0/2c/0                         memory      DIMM Synchronous [empty]
/0/2c/1                         memory      8GiB DIMM DDR3 Synchronous 1333 MHz 
/0/2c/2                         memory      DIMM Synchronous [empty]
/0/2c/3                         memory      8GiB DIMM DDR3 Synchronous 1333 MHz 

```

Showing the RAM speed is 1333 NOT 1600?

ASUS M5A97 R2.0 Specification
[http://www.asus.com/Motherboards/AMD_AM3Plus/M5A97_R20/#specifications](http://www.asus.com/Motherboards/AMD_AM3Plus/M5A97_R20/#specifications)

Kingston HyperX KHX1600C10D381K2/16G (2x8G) (Blue Memory)
[http://www.kingston.com/us/memory/hyperx/blu](http://www.kingston.com/us/memory/hyperx/blu)

The RAM sticks are inserted on slot-1 and slot-3
(counted from the Power Supple Connectors-socket)

Did I make mistake here?  Pls advise.  TA

B.R.
satimis

---

### Post by Yellow Pasque on 2012-12-11
Did you try to manually set the RAM speed in the BIOS? Often, RAM sticks will be listed at their maximum guaranteed speed, but run with slower default speed/timing for compatibility reasons. The user has to tweak the BIOS/EFI to take advantage of the RAM's potential.
See also: [https://en.wikipedia.org/wiki/Serial_Presence_Detect](https://en.wikipedia.org/wiki/Serial_Presence_Detect)

---

### Post by satimis on 2012-12-11
> **Temüjin said:**
> Did you try to manually set the RAM speed in the BIOS? Often, RAM sticks will be listed at their maximum guaranteed speed, but run with slower default speed/timing for compatibility reasons. The user has to tweak the BIOS/EFI to take advantage of the RAM's potential.
See also: [https://en.wikipedia.org/wiki/Serial_Presence_Detect](https://en.wikipedia.org/wiki/Serial_Presence_Detect)
Hi,

I got it.

On BIOS
Memory Frequency - Auto

change "Auto" -> "DDR3 1600"

Thanks

---

### Post by tgalati4 on 2012-12-11
Don't forget to run memtest for 30 complete cycles to verify that your timing and higher speed will run reliably.

---

### Post by satimis on 2012-12-12
> **tgalati4 said:**
> Don't forget to run memtest for 30 complete cycles to verify that your timing and higher speed will run reliably.

Thanks

Would it be possible running memtest on Live USB, Fedora/Debian? I don't have DVD/CD ROM/Writer on this PC. Otherwise I'll follow;
Linux] HOWTO: Boot Memtest on USB Drive
[http://forum.canardpc.com/threads/28875-Linux-HOWTO-Boot-Memtest-on-USB-Drive](http://forum.canardpc.com/threads/28875-Linux-HOWTO-Boot-Memtest-on-USB-Drive)

creating memtest on USB. Thanks

B.R.
satimis

---

### Post by Grenage on 2012-12-12
Memtest always used to be part of the installed Ubuntu system, so unless something has changed, you should be able to access it from the Grub menu at boot time.

---

### Post by satimis on 2012-12-12
> **Grenage said:**
> Memtest always used to be part of the installed Ubuntu system, so unless something has changed, you should be able to access it from the Grub menu at boot time.
Ah I see.  Thanks.

(I'm now replying on another PC.)

Grub window is not displayed on booting.  Pressing ESC has no effect.  Finally I have to comment out "GRUB_HIDDEN_TIMEOUT=0" on /etc/default/grub and ran "sudo update-grub"

Up to now I have been running memtest86 >30min.  No error warning displayed.

---

### Post by Grenage on 2012-12-12
I should really have mentioned that you can display a hidden grub menu by holding down *shift* during boot.  Glad that you got there anyhow!

---

### Post by satimis on 2012-12-12
> **Grenage said:**
> I should really have mentioned that you can display a hidden grub menu by holding down *shift* during boot.  Glad that you got there anyhow!

Thanks

Memtest completed with pass and no error.  It took more than an hour.

Furthermore if adding another 16G (2x8G), DDR3 1600, do I need sticking to the same brand, Kingston?  OR I can add another pair from other makers?

satimis

---

### Post by Grenage on 2012-12-12
While it's generally regarded as optimal to have the same memory across the board, it's far from a requirement.

---

### Post by satimis on 2012-12-12
> **Grenage said:**
> While it's generally regarded as optimal to have the same memory across the board, it's far from a requirement.
Noted.  Thanks

satimis

---

### Post by tgalati4 on 2012-12-12
Understand that some motherboards require reduced timing when fully populated.  I have an Intel motherboard that allows full speed at 1/2 board population (4 GB) and reduced speed at full population (8 GB).  Also the rated speed and any overclocking of your CPU can affect your maximum speeds that you can run your full RAM at.  Memtest is helpful for clocking speeds with different bus speeds and CAS timings.  Keep tweaking until something breaks, but some motherboards (like Intel) can actually burn up with incorrect timing--so proceed with caution.  

As far as matching--it's a good idea, but if it works and you have a return policy then you should be covered.

---

