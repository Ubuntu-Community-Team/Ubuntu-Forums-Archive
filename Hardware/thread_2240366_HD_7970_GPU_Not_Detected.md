---
title: "HD 7970 GPU Not Detected"
date: 2014-08-19
forum: Hardware
---

### Post by GreenRaccoon on 2014-08-19
I'm having trouble getting my computer to recognize my ATI Radeon HD 7970 Sapphire GPU. I'm guessing it's a hardware problem, but I really have no idea. This GPU works in another computer, so I know the GPU is fine. I connected the card to my computer and then did a completely fresh install of Linux Mint 17 XFCE. But Linux doesn't "see" the GPU. The GPU fans are running, so I'm pretty sure the hardware connections are right.

When I power on the computer, the screen is blank for 10 seconds or so and then the BIOS screen shows up. I know that can't be good haha. Also, when I connect my monitor to the GPU card, nothing shows on the screen, not even when I connect to the monitor BEFORE powering on. I couldn't find anything in the BIOS settings that seemed relevant to my problem (like if there was an option checked to disable new hardware detection).

I double checked that the motherboard supported the GPU. My motherboard is a Gigabyte M61PME-S2P. The GPU's compatible with this motherboard according to this site:
[http://www.pc-specs.com/gpu/AMD/HD_7000_Series/Radeon_HD_7970_OC_Sapphire_Edition/946/Compatible_Motherboards](http://www.pc-specs.com/gpu/AMD/HD_7000_Series/Radeon_HD_7970_OC_Sapphire_Edition/946/Compatible_Motherboards)

I tried installing an AMD driver that I know works for this GPU, but I couldn't complete the installation because Linux wasn't detecting the GPU.

I'm out of ideas. Anyone else have any?

---

### Post by grahammechanical on 2014-08-19
Is this the desktop described in your signature? The one with the AMD A10-7850K APU and now an ATI Radeon HD 7970? If so then you are in the realm of Hybrid graphics and there may well be a setting in the BIOS/UEFI to activate that discreet graphic card.

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Regards.

---

### Post by GreenRaccoon on 2014-08-20
> **grahammechanical said:**
> Is this the desktop described in your signature? The one with the AMD A10-7850K APU and now an ATI Radeon HD 7970? If so then you are in the realm of Hybrid graphics and there may well be a setting in the BIOS/UEFI to activate that discreet graphic card.

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Regards.

Thanks for replying!

No, the desktop in my signature is a different computer. This is an older desktop I'm trying to put the video card in (long story haha).

---

### Post by QIII on 2014-08-20
Hello!

Does the motherboard have an integrated graphics adapter?  Are you using a CPU with integrated graphics?  Does your BIOS have a setting to choose a dedicated PCIe card over the on board one?

Edit:  looked up your board.  You need to find the BIOS setting that tells it to use the dedicated PCIe GPU rather than the on board NVIDIA one.

With a board that old, I hope you have a newer power supply.  That adapter will demand a pretty substantial one and a 350 watter will die an ugly death -- and maybe take all the rest with it.

---

### Post by GreenRaccoon on 2015-01-02
This thread is a bit old, but I'll make a last update to it. I never could figure out how to get the HD 7970 GPU to work on this desktop, but I could get a 280x GPU to work, even though the 280x is even newer. :confused:

---

