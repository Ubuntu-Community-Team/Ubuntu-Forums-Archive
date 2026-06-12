---
title: "Enableing motherboard graphics"
date: 2009-04-07
forum: Hardware
---

### Post by linuxuser21 on 2009-04-07
I have a ATi X1300 card (PCI).  I have a [KM400a]("http://www.via.com.tw/en/products/chipsets/k7-series/km400a/") motherboard.  Naturally, the BIOS put the X1300 as the main display and disabled the motherboard graphics.
Is it possible to re-enable the motherboard graphics to add another screen?  The BIOS doesn't have the option to run both of them.

---

### Post by Sam Lars on 2009-04-09
I don't think you could use both... the BIOS may allow you to force it to use onboard video, but some BIOSes can only use the card you have installed.

---

### Post by askreet on 2009-04-09
Sam Lars is right, most motherboards do not support using both an on-board and expansion video card.

---

### Post by bcschmerker on 2009-04-09
Thanks for a confirmation on something that I already suspected to be the case.  My Everex' new Elitegroup 'board is set up to run only one SVGA/XGA display off its planar [nVIDIA GeForce6100](http://www.nvidia.com/); but several vendors purchase nVIDIA GPU's compatible with my existing drivers in quantity for both 4x/8x AGP and PCI-Express x8/x16 expansion boards.  I'm currently researching dual-out PCI-E x8 boards using GeForce GPU's and 128 to 512 MB onboard DDR2 or DDR3 video RAM, as I see a need for one HDMI or DVI and one SVGA/XGA or S-Video outputs in the near future.  At present, I'm back to the open-source VESA 2D driver, as I discovered what I consider a critical bug in nVIDIA's 3D driver in the NVIDIA_GLX_new Debian package:  Uncommanded system shutdowns on certain Web pages withot even unmounting my ext3 hard drive volumes.:p

Addendum:  Uncommanded-shutdown problem eventually fixed with a main-memory derate from DDR2-800 (per manufacturer) to DDR2-667 to stay within limits discovered during offline burn-in.  Runs OK with nVIDIA Envy driver.

---

### Post by askreet on 2009-04-09
If you have a need for HDMI, DVI and VGA you could buy a "Dual DVI" card that has DVI->VGA and DVI->HDMI adapters.  They're pretty common.

---

### Post by linuxuser21 on 2009-04-09
> **Sam Lars said:**
> I don't think you could use both... the BIOS may allow you to force it to use onboard video, but some BIOSes can only use the card you have installed.
> **bcschmerker said:**
> Thanks for a confirmation on something that I already suspected to be the case.  My Everex' new Elitegroup 'board is set up to run only one SVGA/XGA display off its planar [nVIDIA GeForce6100](http://www.nvidia.com/); but several vendors purchase nVIDIA GPU's compatible with my existing drivers in quantity for both 4x/8x AGP and PCI-Express x8/x16 expansion boards.  I'm currently researching dual-out PCI-E x8 boards using GeForce GPU's and 128 to 512 MB onboard DDR2 or DDR3 video RAM, as I see a need for one HDMI or DVI and one SVGA/XGA or S-Video outputs in the near future.  At present, I'm back to the open-source VESA 2D driver, as I discovered what I consider a critical bug in nVIDIA's 3D driver in the NVIDIA_GLX_new Debian package:  Uncommanded system shutdowns on certain Web pages withot even unmounting my ext3 hard drive volumes.:p
I kind of have to laugh at this because it's quite a coincidence.  The whole thing that got me wondering if I could do this is *my* 6100 motherboard and my 6600 card on my other computer.  I had it set up to run the onboard and both the heads on the 6600 with the BIOS.  I had three screens going.  So, actually, bcschmerker, I'm pretty sure you can do it too.  With that setup in mind, that is what I want to do with this computer.

---

### Post by linuxuser21 on 2009-04-09
> **askreet said:**
> If you have a need for HDMI, DVI and VGA you could buy a "Dual DVI" card that has DVI->VGA and DVI->HDMI adapters.  They're pretty common.

Actually, that's what I am currently doing.  I have the VGA hooked up to one of my monitors and a DVI>VGA adapter and monitor hooked up to that one as well.

---

### Post by Sam Lars on 2009-04-09
I think that's something unique to Nvidia... they have something called SLI that allows two different cards to work together.

---

### Post by linuxuser21 on 2009-04-09
> **Sam Lars said:**
> I think that's something unique to Nvidia... they have something called SLI that allows two different cards to work together.

That's between more than one of the same card though.  It's not between motherboard and GPU.  They have to be SLI enabled and they are connected by a bridge between them.  ATi's version is Crossfire.  I know that I can't do it through the BIOS; however, I think that's just to select the main card (the one that shows up for the BIOS screen and the one you're desktop will use unless you change it).

---

### Post by bcschmerker on 2009-04-09
> **askreet said:**
> If you have a need for HDMI, DVI and VGA you could buy a "Dual DVI" card that has DVI->VGA and DVI->HDMI adapters.  They're pretty common.Thanks for the tip; in case I relocate the Everex to the front room, I've a Samsung flat-screen multimedia display unit ready to take the DVI feed via HDMI Input 2, so a Dual-DVI or DVI + HDMI setup is also an option.

---

### Post by markbuntu on 2009-04-11
You can do it. You need to hand edit xorg.conf for each driver and screen instance. Lots of people run their on-board and plug in cards together. Some on board gpus will not show up in bios or lspci unless there is an active monitor plugged into them.

---

### Post by linuxuser21 on 2009-04-11
> **markbuntu said:**
> You can do it. You need to hand edit xorg.conf for each driver and screen instance. Lots of people run their on-board and plug in cards together. Some on board gpus will not show up in bios or lspci unless there is an active monitor plugged into them.

Okay, I'm willing to do that.  Okay, I've messed with the xorg file before; however, I, by no means am an expert with it.  How do I do it? I do have a screen hooked up to it.

---

### Post by bcschmerker on 2009-06-01
> **bcschmerker said:**
> ...My Everex' new Elitegroup 'board is set up to run only one SVGA/XGA display off its planar [nVIDIA GeForce6100](http://www.nvidia.com/); but several vendors purchase nVIDIA GPU's compatible with my existing drivers in quantity for both 4x/8x AGP and PCI-Express x8/x16 expansion boards....At present, I'm back to the open-source VESA 2D driver, as I discovered what I consider a critical bug in nVIDIA's 3D driver in the NVIDIA_GLX_new Debian package:  Uncommanded system shutdowns on certain Web pages withot even unmounting my ext3 hard drive volumes....As I found out the hard way, the nVIDIA nForce405 chipset has a propensity for uncommanded shutdowns.  I have since replaced the Elitegroup with a [Gigabyte MA78GM-S2HP](http://www.gigabyte.com.tw/), and the uncommanded shutdowns are history, at least for now.  The new 'board has planar DVI and HDMI in addition to VGA/XGA, so the need for a second GPU is not so imminent; I do have one PCI-Express x16 slot to take another GPU if necessary.

---

### Post by bcschmerker on 2011-06-21
**Postscript:**  The exclusion case against nVIDIA® is on appeal, as other Users had problems with [Elitegroup® system boards with other chipsets](http://www.ecsusa.com/).  Tests on a rebuilt eMachines®/Acer® EL1210-09 ([Advance Micro Devices® Athlon 64® LE-1620](http://www.amd.com/) (Socket AM2, 45*max*W), [nVIDIA® MCP78S chipset and GeForce® 8200 GPU](http://www.nvidia.com/)) running Ubuntu® 10.04.2-LTS, AMD64 Edition, have completed in short order, as of June 2011.

---

