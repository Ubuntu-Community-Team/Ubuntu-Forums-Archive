---
title: "lubuntu14.04 on HP dc7800 SFF kernel issues"
date: 2014-05-03
forum: Hardware
---

### Post by stulluk2 on 2014-05-03
Hi, I have two problems with my HP dc7800 SFF. I feel it is about the kernel, but I have been aware of this when I update to 14.04

here is my dmesg : [http://sprunge.us/OMZA](http://sprunge.us/OMZA)

0.000000] ------------[ cut here ]------------
[    0.000000] WARNING: CPU: 0 PID: 0 at /build/buildd/linux-3.13.0/drivers/iommu/dmar.c:488 warn_invalid_dmar+0x7e/0x90()
[    0.000000] Your BIOS is broken; DMAR reported at address fed90000 returns all ones!
[    0.000000] BIOS vendor: Hewlett-Packard; Ver: 786F1 v01.32; Product Version:  

And this:


[   13.426028] ------------[ cut here ]------------
[   13.426070] WARNING: CPU: 1 PID: 319 at /build/buildd/linux-3.13.0/drivers/gpu/drm/i915/intel_opregion.c:266 swsci+0x2ec/0x300 [i915]()
[   13.426074] excessive driver sleep timeout (DSPL) 4294967295

And here is my lspci: [http://sprunge.us/iYXg](http://sprunge.us/iYXg)

Is there any way to get rid of these? 

Notes: 
1) I just updated my BIOS to newest firmware ( 1.32 )
2) I have these issues on both IDE and RAID ( AHCI ) modes.
3) IIRC, I also had these issues on previous Kubuntu(12.04) and Lubuntu(13.10)

---

### Post by stulluk2 on 2014-05-04
Bump...

---

### Post by mathsguy on 2014-06-15
Hi,
I am seeing similar messages on a System76 Gazelle running Ubuntu 14.04
This system keeps crashing randomly. I wanted to ask, what are the symptoms on your computer that prompted you to write this post?

thanks,
a.


kernel: [    0.000000] WARNING: CPU: 0 PID: 0 at /build/buildd/linux-3.13.0/drivers/iommu/dmar.c:488 warn_in
valid_dmar+0x7e/0x90()
kernel: [    0.000000] Your BIOS is broken; DMAR reported at address 0!
kernel: [    0.000000] BIOS vendor: American Megatrends Inc.; Ver: 1.03.03RS76; Product Version: gazp9      
                     
kernel: [    0.000000] Modules linked in:
kernel: [    0.000000] CPU: 0 PID: 0 Comm: swapper Not tainted 3.13.0-27-generic #50-Ubuntu
kernel: [    0.000000] Hardware name: System76, Inc.                   Gazelle Professional            /Gaze
lle Professional           , BIOS 1.03.03RS76 01/15/2014
kernel: [    0.000000]  000000000000000b ffffffff81c01de8 ffffffff817199c4 ffffffff81c01e30
kernel: [    0.000000]  ffffffff81c01e20 ffffffff810676bd ffffffff81fdd01c ffffffff81fdd07c
kernel: [    0.000000]  0000000000000000 ffffffff81de12c0 ffffffff81c01fb0 ffffffff81c01e80

---

