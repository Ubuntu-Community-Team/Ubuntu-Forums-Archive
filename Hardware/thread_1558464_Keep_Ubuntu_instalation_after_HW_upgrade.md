---
title: "Keep Ubuntu instalation after HW upgrade"
date: 2010-08-22
forum: Hardware
---

### Post by mcgeek on 2010-08-22
I have ordered some new hardware. MB, Memory and CPU. These are the only items changing in my case. My question is...Can I keep my current install of Ubuntu or should I start from scratch again. I have my system lean and mean and don't want to go through a reinstall and configuration if I don't need to.

Current HW

AMD Athlon 64 X2 3800+ Manchester 2.0GHz Socket 939 Dual-Core Processor 

ABIT AN8-ULTRA 939 NVIDIA nForce4 Ultra ATX AMD Motherboard

EVGA 256-P2-N517-AX GeForce 7800GT 256MB 256-bit GDDR3 PCI Express x16 SLI

The new HW on order will replace the CPU and MB everything else will stay the same.

MSI 870A-G54 AM3 AMD 870 SATA 6Gb/s USB 3.0 ATX AMD Motherboard

AMD Phenom II X4 955 Black Edition Deneb 3.2GHz 4 x 512KB L2 Cache 6MB L3 Cache Socket AM3 125W Quad-Core Processor

Do you think I will be good to go?

Thanks

---

### Post by Fafler on 2010-08-22
It's not going to cause any problems. Just go for it.

---

### Post by coffeecat on 2010-08-22
Linux probes for hardware on bootup, so this shouldn't be a problem, unlike with Windows. The only significant issues are likely to be:

Dramatic change in video card with proprietary driver installed. I see you have a nvidia card. If you're using the proprietary nvidia driver you may need to reconfigure if the new machine has, say, ATI graphics. I couldn't see the graphics on your new specs.

Sound - different chipset may mean reconfiguring the sound.

And your ethernet card on the new motherboard will be called eth1 (or eth2, etc) instead of eth0. This can be changed if you want.

In fact I was using an Athlon X2 64 machine as my main one and built a new one around a Phenom X4. I cloned my Ubuntu install (to keep the old one going) to the new machine and had only trivial issues to tidy up.

Have fun!

---

### Post by cascade9 on 2010-08-22
> **mcgeek said:**
> ABIT AN8-ULTRA 939 NVIDIA nForce4 Ultra ATX AMD Motherboard

The new HW on order will replace the CPU and MB everything else will stay the same.

MSI 870A-G54 AM3 AMD 870 SATA 6Gb/s USB 3.0 ATX AMD Motherboard

It should work, but you're going to have to buy new RAM as well. The Abit AN8-Ultra uses DDR1, the MSI 870 uses DDR3.

---

### Post by mcgeek on 2010-08-22
> **cascade9 said:**
> It should work, but you're going to have to buy new RAM as well. The Abit AN8-Ultra uses DDR1, the MSI 870 uses DDR3.

I have 4 GB of RAM in the order. I didn't mention it because I figured it wouldn't matter as far as keeping my current install. 

> **coffeecat said:**
> 
Dramatic change in video card with proprietary driver installed. I see you have a nvidia card. If you're using the proprietary nvidia driver you may need to reconfigure if the new machine has, say, ATI graphics. I couldn't see the graphics on your new specs.


I'm going to use the same video card. My biggest concern was the chip set change from nForce 4 to AMD/ATI 870.

Thanks to all for the help.

---

### Post by mcgeek on 2010-08-29
FYI

The upgrade is complete. No real issues. eth1 was easy to fix. Sound wasn't a problem either.

I did have to download k10temp and compile to get lm sensors working (that was kinda cool...never done that before).

Only issue I have right now is temperature. AMD gave me a cooler with the CPU so I though I would give it a try....give you three guesses what is on order now. HOT HOT HOT. I do a fair share of video encoding and and it only took about 5 min for lm sensors to report 60 C. The fan on the stock cooler was so loud I thought the case was going to levitate. Arctic Silver 5 and a after market cooler is going to be a must have for this CPU.

---

