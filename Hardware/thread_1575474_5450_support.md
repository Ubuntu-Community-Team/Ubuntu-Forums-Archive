---
title: "5450 support?"
date: 2010-09-15
forum: Hardware
---

### Post by dangerfar on 2010-09-15
So I installed my 5450 and tried to install Ubuntu to some problems. Initially I was using HDMI, but realized to install I had to switch to VGA. No biggie, I installed w/ VGA figuring I would simply need to get a proprietary driver once booting into Ubuntu. Problem is I can't see anything, even with VGA. The computer is working fine, keyboard is active, no freezing or anything, there simply is no display. Am I just out of luck here or is there some sort of magic to be worked?

---

### Post by jpr0 on 2010-09-16
> **dangerfar said:**
> So I installed my 5450 and tried to install Ubuntu to some problems. Initially I was using HDMI, but realized to install I had to switch to VGA. No biggie, I installed w/ VGA figuring I would simply need to get a proprietary driver once booting into Ubuntu. Problem is I can't see anything, even with VGA. The computer is working fine, keyboard is active, no freezing or anything, there simply is no display. Am I just out of luck here or is there some sort of magic to be worked?

What do you mean there is no display? Do you see POST messages during the bootup process? At what point do you stop seeing output on the screen?

Edit: 

The reason why I'm asking is because if you don't see *anything* during the boot up process, then it probably just means that you have to disable your onboard graphics and tell your motherboard to use your 5450 card as the primary display. On my Asus board, there is an option to set the primary video controller as either GFX0, GPP, IGFX and PCI. GFX0 = controller on PCIex16 slot, GPP=PCIex1 slot, IGFX=onboard graphics,  PCI=PCI slot.

---

