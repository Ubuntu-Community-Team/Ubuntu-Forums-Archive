---
title: "sata HDD and sata DVD drive okay?"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by eeried on 2007-09-20
hello,

I'm planning to build a new computer based on socket 775 and I'd like to know if it'd be okay to have a sata HDD and a sata DVD-R/W-burner and a DVD drive (I'm not sure there are sata DVD-drives).

Someone has told me sata isn't very good with Linux, and he has chosen to go all IDE, so to speak, but then you can only have two IDE drives, and I'd like to have three drives.

Is it okay to mix sata and IDE drives? Does it depend on chipset or mobo, or the bios? (I might choose Intel P35)


Sorry for my ignorance, and there are so many rumours. Actually IDE was quite good and sata doesn't add much performance, though it's nice to be rid of the master and slave business, not to mention the cables.

---

### Post by Maxtorm on 2007-09-20
I can't comment on Linux's sata capabilities, but why are you restricting yourself to two drives with IDE? Two channels x master&slave = 4 drives max with IDE.

---

### Post by logos34 on 2007-09-20
> **Maxtorm said:**
> but why are you restricting yourself to two drives with IDE? Two channels x master&slave = 4 drives max with IDE.

a lot of boards nowadays have only one IDE connector.  But if you could find one with two then obviously this wouldn't be problem

---

### Post by eeried on 2007-09-20
> a lot of boards nowadays have only one IDE connector
Precisely,  and it seems to be a shame to have 4 or 8 sata connectors and not using them...

I don't own any recent IDE devices anyway -- I only have old stuff sitting in a couple of Pii, PIII, and AMDk6 :)

---

### Post by dabl on 2007-09-20
My Intel motherboard only has one IDE connector, so that's only one channel, so only 2 devices. But it has 4 SATA connectors.  Lots of new motherboards are that way.

Mix 'n match IDE and SATA hard drives can be tricky to set up a dual boot system on, depending on which drive you want Windows to be on.  Basically, you can think of an IDE drive as a "Grub magnet" -- you'll have to either FDISK it and leave it unformatted, or disconnect it, if you want to install Ubuntu to boot on a SATA drive, on a system that has an IDE drive installed.  The easy and "natural" way to do it is to install Windows first, on the IDE drive, and then Ubuntu wherever you want it, and let Grub write itself to the MBR on the Windows (IDE) drive.

I have no experience with SATA CD/DVD drives (and hope to stay that way for awhile!).  :lolflag:

---

### Post by MrHippocampus on 2007-09-20
I would personally try to make everything SATA. SATA for hard drives should be fine, the new libata driver which appeared a while back solved most of the problems. CD/DVD SATA drives are a different matter, not all of them are true SATA devices and they don't work with well with linux (i think there are problems with some drives manufactured by plextor).

The best advice (as always) is to do some research online and see who already has a SATA CD/DVD drive that works well and then try and buy that model/brand. (Any SATA hard drive should *just work*)

---

### Post by eeried on 2007-09-20
Many thanks for your answers! 

No dual-boot with windows ever.

> CD/DVD SATA drives are a different matter, not all of them are true SATA devices and they don't work with well with linux
I'll take due note of this MrHippocampus!

---

### Post by logos34 on 2007-09-20
I agree with mrhippo, go all sata.  Seems there are issues mixing ide and sata with p35...Also, avoid any board with JMicron controller if at all possible.

> 
Basically, you can think of an IDE drive as a "Grub magnet" -- you'll have to either FDISK it and leave it unformatted, or disconnect it, if you want to install Ubuntu to boot on a SATA drive, on a system that has an IDE drive installed.

That's my experience...grub will also frequently get the bios boot order wrong

---

### Post by eeried on 2007-09-20
> Also, avoid any board with JMicron controller if at all possible.
According to a Phoronix review JMicron is only a problem if you dual boot with windows. 
I may choose GA-P35C-DS3R though I think GA-P31-DS3L would be sufficient for my needs. Yet my usual online shop doesn't seem to have any memory stick that fits the P31 mobo, and it has the right sticks for the P35. This is rather strange.. but off topics, sorry!

---

