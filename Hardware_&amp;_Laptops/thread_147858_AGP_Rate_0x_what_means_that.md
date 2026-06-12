---
title: "AGP Rate 0x: what means that?"
date: 2006-03-21
forum: Hardware &amp; Laptops
---

### Post by pinguin on 2006-03-21
I've installed on my PC (PIII 600 5 years old) a Nvidia RIVA TNT2 Model 64/Model 64 Pro graphics card.
O.S. is Linux Ubuntu Breezy 5.10 Kernel 2.6.12-10-686.
I've installed nvidia "legacy" drivers corresponding at 1.0-7174 nvidia driver.
The command
cat /proc/driver/nvidia/agp/status
reports this:
Status:          Enabled
Driver:          AGPGART
AGP Rate:        0x
Fast Writes:     Disabled
SBA:             Disabled

What means AGP Rate: 0x?
My motherboard and BIOS support AGP up to 2x.
Is there something wrong on my system?
Must I configure some settings to have AGP rate work at 2x?
Thank you.
Here is the  attach file with report of nvidia-bug-report.sh.

---

### Post by akiro.yamamoto on 2006-03-21
When I installed my new card, I had to go into my BIOS and set my AGP to 8x 
instead of the previous 4x setting I was using before..... 
Maybe you have to do the same ;)

---

### Post by pinguin on 2006-03-21
[QUOTE=akiro.yamamoto]When I installed my new card, I had to go into my BIOS and set my AGP to 8x 
instead of the previous 4x setting I was using before..... 
Maybe you have to do the same ;)[/QUOTE]

I installed the graphic card first and then ubuntu

---

