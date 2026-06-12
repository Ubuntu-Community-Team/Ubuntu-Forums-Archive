---
title: "Nvidia card to bypass built-in ATI chip - will it work?"
date: 2014-03-05
forum: Hardware
---

### Post by egeezer on 2014-03-05
I'm running 12.04.4 on a stock HP desktop with an AMD Athlon II quad-core processor, but the integrated ATI Radeon HD 4200 graphics are pretty limited in their performance.  I know if I install a new PCI-e card it will bypass the integrated graphics, but do I have to stick with the Radeon series or can I use an Nvidia equally well?  I'd prefer the Nvidia, because I have encountered a lot more grief trying to get fglrx to work than choosing the latest Ubuntu-blessed Nvidia driver.

Suggestions, comments, and links are all welcome.  Nothing urgent about it, but I'd like to learn from other folks who have tried.

Thanks in advance

---

### Post by papibe on 2014-03-05
Hi egeezer.

I can't say for sure. Is the integrated graphics con the processor ship itself, or in the motherboard?

As far as I my experience, you can set the BIOS to use integrated graphics or a discrete cards. If that's the case, it won't matter if it is an Nvidia card.

However, if your system has a hybrid system (the equivalent of 'Nvidia Optimus'), I wouldn't now how would that work.

Regards.

---

### Post by bcschmerker on 2014-03-05
I'd recommend staying with Advanced Micro Devices® GPU's due to a long history of hardware and driver conflicts between ATi® and nVIDIA® even in Microsoft® Windows® 5.x and 6.x.  From my experience with the Radeon® HD™ Series, I'd recommend the HD™ 5850 for your rig - I had to abort a test run of Ubuntu® 13.12a1 on an Asus® CM1630-06 with EAH6850 DirectCU® video and XONAR® audio in January, primarily due to a panicky Kernel 3.13.0-4-generic on my particular hardware set-up, rather than anything inherently wrong in either the X.org xserver-video-radeon or ALSA snd-virtuoso module.  There should be a means to set PCI-Express as the primary display in your Hardware Set-up menu, a common feature of all later BIOS's.

---

### Post by Mark Phelps on 2014-03-05
>  I know if I install a new PCI-e card it will bypass the integrated graphics

Not necessarily ... I have an integrated AMD HD 4290 chip and had to go into the BIOS and disable it before I could use my replacement AMD HD 8850 PCIe card.

---

### Post by egeezer on 2014-03-06
Thanks for the quick replies!  You're right, I'll have to set up the hardware to do the bypass - I just meant that the built-in will simply not be used.

I do have one (home-built) with an AMD FX-8120 processor and an Nvidia card that seem happy together, but that one never shared its chip architecture with graphics.

Well, still thinking.  And you've given me more to think about - again, thanks much!

---

### Post by kurt18947 on 2014-03-06
I have an AMD 785 chipset based MoBo w/integrated graphics.  BIOS settings will disable onboard AMD graphics and look first to the PCIe slot when booting.  The previous Nvidia GS8400 board and current Geforce 210 board both seem happy using Nvidia's current drivers.  I have found suspend/resume issues using the Nouveau video drivers, the proprietary driver seems better on this machine.

---

### Post by mastablasta on 2014-03-06
4xxx series support was dropped, however many features of proprietary driver will be in new kernel (in opensource) available in 14.04. while still not as good as proprietary driver the opensource one has improved a lot and as i understand AMD is working with community to make them even better.

---

### Post by Yellow Pasque on 2014-03-06
You can use Nvidia cards with an AMD chipset (and vice versa back in the days when Nvidia made chipsets). I have seen some complaints such as bcschmerker refers to, but they're the exception to the rule.

---

### Post by bcschmerker on 2014-03-07
> **kurt18947 said:**
> I have an AMD 785 chipset based MoBo w/integrated graphics.  BIOS settings will disable onboard AMD graphics and look first to the PCIe slot when booting.  The previous Nvidia GS8400 board and current Geforce 210 board both seem happy using Nvidia's current drivers.  I have found suspend/resume issues using the Nouveau video drivers, the proprietary driver seems better on this machine.
Which is consistent with my experience with an eMachines®/Acer® EL1210-09 (Advanced Micro Devices® Athlon 64® LE-1620, nVIDIA® MCP78S chipset with integrated 64-bit GeForce® graphics) with substantial upgrades:  A Shuttle® PC6300001 power supply with three +12VDC rails, retrofitted against unknowns in upgrade-GPU power demand; and an EVGA® GeForce® 8400 GS&#8482; low-profile PCIe x1 video display adapter (replaces an Asus® EN210/D1/512MD3(LP) whichhad connector issues in the EL1210's slimline case due to insufficient pigtail length on its DE15; both, ironically, use the nVIDIA® GT218 GPU).  Only I had some problems with both the nVIDIA® driver and some base problems stalling the boot process in Ubuntu® 14.01a2; will see if a fresh install of Ubuntu® 14.02b1 fixes things....

**Update:**  Fresh install helped, once I solved the display-assignment problem - apparently the nVIDIA® GT218 likes to use an analog hook-up as primary, favoring the DVI-I (in DVI-A mode) over the DE15 VGA/XGA port for the purpose.

---

