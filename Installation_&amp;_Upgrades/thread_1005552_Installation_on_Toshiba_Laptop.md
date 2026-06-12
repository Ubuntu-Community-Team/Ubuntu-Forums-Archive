---
title: "Installation on Toshiba Laptop"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by mwfischer on 2008-12-08
Hi, I'd appreciate if someone could give some suggestions or send a link to a solution.  

This is my second installation of Ubuntu. The first went flawless. I say this only to confirm that my installation disk is most likely good.

I am trying to install on a Toshiba laptop. Satellite 1805-S253.
800mHz Pentium 3 processor, 1GB RAM and 80GB HD.

Installation starts as planned but then after what seems like a complete installation, I get to a black screen. 

I've read on other threads about "safe graphics mode" installation and have tried that and have had the same result.

Any help would be greatly appreciated.

---

### Post by oilchangeguy on 2008-12-08
> **mwfischer said:**
> Hi, I'd appreciate if someone could give some suggestions or send a link to a solution.  

This is my second installation of Ubuntu. The first went flawless. I say this only to confirm that my installation disk is most likely good.

I am trying to install on a Toshiba laptop. Satellite 1805-S253.
800mHz Pentium 3 processor, 1GB RAM and 80GB HD.

Installation starts as planned but then after what seems like a complete installation, I get to a black screen. 

I've read on other threads about "safe graphics mode" installation and have tried that and have had the same result.

Any help would be greatly appreciated.

i don't think your ram is correct. i owned a 1805-s177 with an 800mhz. celeron and 512mb (256x2) of ram (max) and a 40gb hard drive. you might want to check your ram again. i don't think the computer will support 1gb of ram (512x2).

---

### Post by mwfischer on 2008-12-08
> **oilchangeguy said:**
> i don't think your ram is correct. i owned a 1805-s177 with an 800mhz. celeron and 512mb (256x2) of ram (max) and a 40gb hard drive. you might want to check your ram again. i don't think the computer will support 1gb of ram (512x2).

You are correct.  I should have double checked the exact stats before post. Here are the corrected stats:
Intel Pentium III
851 MHz
504 MB RAM

Even with this change, I'm still above the recommended minimum of 700 MHz and 384 MB RAM.

Any thoughts how to get past the freeze.

Thanks!

---

### Post by mwfischer on 2008-12-10
[bump]  Any help???

---

### Post by ProteinPappa on 2008-12-10
Do you get the black screen when booting after the install, or before the installation reboots your machine? If it is before, what happens if you do a hard restart? Do you get to grub? If so, you may be able to use the root shell.

Without having used it myself, you might want to try the alternate installer, which I believe uses a low graphics mode similar to earlier Windows installers. 

I had this problem a couple of years ago when first trying Linux distributions. I think I found the problem was that the operating system was trying to use an unsupported resolution.

---

