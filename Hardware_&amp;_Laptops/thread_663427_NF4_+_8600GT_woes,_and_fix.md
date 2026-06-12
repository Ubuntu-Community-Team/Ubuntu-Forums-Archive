---
title: "NF4 + 8600GT woes, and fix"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by tor528 on 2008-01-10
Short version: My computer would completely lockup upon trying to start GDM with the nvidia drivers.  I fixed it by flashing my motherboard's BIOS with the latest version.


Long version:

I had an old Athlon 64 3000+ collecting dust, so I decided to build a cheap computer around it.  The specs are as follows:

Athlon 64 3000+
Foxconn NF4K8AB-RS motherboard (which came bundled with a Geforce 6200TC, total $27)
Geforce 8600GT
512 MB Corsair ValueSelect
500GB SATA HDD

I decided to use Ubuntu 32 bit, as it seems to have less problems and more support than 64 bit. Everything worked fine when I used the 6200TC.  When I installed the 8600GT, the computer would completely freeze and the monitor would turn off when GDM tried to start (No keyboard lights, no response to ctrl+alt+(backspace | F1 | delete)).  

The 'nv' driver worked fine, but the 'nvidia' driver would cause the freeze at GDM.  However, I bought the 8600GT specifically to render 3D, so 'nv' was not satisfactory.   After a few hours of messing with it (tried Envy, tried manually installing drivers from Nvidia's website, browsed the forums a lot, etc.), I installed Windows XP to see if the card actually works.  Installed Nvidia drivers, benchmarked it, stressed it a bit, worked fine in XP.

While I had XP running, I decided to update the BIOS.  Used Phoenix Award Winflash and the binaries from the Foxconn website to update to the latest version of the BIOS.  Upon switching back to Linux, I found that I was able to use the nvidia driver with 3d acceleration, no freeze at boot.

Now, to get the sound working...

---

### Post by jespdj on 2008-01-10
The problem might not have been caused by a bug in the BIOS itself; maybe it was a wrong setting in the BIOS setup. When you flash your BIOS, the settings usually get lost (and are reset back to safe defaults).

---

### Post by tor528 on 2008-01-10
Could be.  However, since I have only had the motherboard for a few days, I had not done any dabbling with the BIOS settings other than changing the boot order.  So, almost all of the BIOS settings would still have been set at manufacturer defaults.

I will agree that bad CMOS settings could cause these symptoms, and so it is a good idea to try resetting the CMOS before taking the risk of flashing the BIOS.  Plus, the CMOS should be reset to reduce the risk of a failed BIOS flash.

---

