---
title: "HP dx5150: No partitionable HDD drive detected!"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by haupte on 2005-07-06
How might I get my Ubuntu to support my new **HP desktop dx5150**? I'm using one **serial ATA disk**. 

SuSE 9.3 Professional was able to install hence there must be Linux drivers for that disk. On the other hand SuSE 9.3 could not detect the **correct video hardware** (ATI Radeon 9600 ????) and was using a framebuffer device.

I'm looking forward to get a running Ubuntu system! Has anybody a tip for me?

Greetings! Erich

---

### Post by codejunkie on 2005-07-06
you might try the expert install insted of the default i think it gives you an option for serial ATA disks in there.

---

### Post by Frank-Hamersley on 2006-05-25
Erich,

I am also installing on a HP dx5150 but with 2 SATA II disks in a RAID-1 configuration.  I had to use the following boot string

    "linux noapic nolapic"

to get it to work.  There were no video problems it seems - I am using the integrated chipset out the DVI-D to HDMI Digital TV.

I am however having other problems and will start a new thread in the BB-AMD64 forum today.

Cheers, Frank.

---

