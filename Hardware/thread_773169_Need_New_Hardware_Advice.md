---
title: "Need New Hardware Advice"
date: 2008-04-28
forum: Hardware
---

### Post by TheKid7 on 2008-04-28
I need to replace the motherboard in the PC that I use in learning Linux.  I have had some positive Linux User feed back on this motherboard:

GIGABYTE GA-G31M-S2L
North Bridge: Intel G31
South Bridge: Intel ICH7
Onboard Video Chipset: Intel GMA 3100
Audio Chipset: Realtek ALC662
Realtek 8111/8169 LAN Driver

For the above Motherboard I will probably match these to it:
CPU: Core 2 Duo E4500
Memory:  Corsair XMS2 DDR2 800 C4
Hard Drive:  Seagate SATA

Does anyone have any feedback on this motherboard or maybe other motherboards with these chipsets?  I want to purchase the motherboard with a high level of confidence that it will work with Ubuntu 8.04 and maybe later Kubuntu 8.04.

The only negative comment that I have found on this motherboard was related to the LAN driver:

"Needed to download the driver from RealTek and blacklist the one with the kernel (not a huge deal)"

I am a Linux Newbie.  How do you "blacklist" the one with the kernel?

Thank you.

---

### Post by Philk on 2008-05-04
Kid7,

I can give you a little help, *perhaps*.  I have a different Gigabyte motherboard (GA-P35-DS4) that came with on-board Realtek 8111B LAN card. I used the drivers Gigabyte provided and have had no problems with LAN until today.  I still have no problems with the 64-bit Hardy.

I tri-boot with 32-bit & 64-bit Hardy and WinXP.  This morning I let WinXP "update" my Realtek LAN driver.  Since then, even after "rolling back" the driver, my card permits no connection in WinXP or 32-bit Hardy.

My advice, if you're going 32-bit, is that the Gigabyte-provided drivers worked for me (with Gutsy and Hardy).  If you're a Windows user, and the Realtek drivers work there, they will probably work fine.

Hope that helps some.

Phil

---

