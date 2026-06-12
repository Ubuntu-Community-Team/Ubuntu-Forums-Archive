---
title: "ATI Radeon 4350 Installation"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by Steve R. on 2009-11-11
I recently bought a new Samsung monitor and the ATI Radeon 4350 video card.  We also just upgraded to Ubuntu 9.10. 

The on-board video driver is by NVIDIA. We also have an AMD64 Motherboard.

My initial attempt at installing the ATI 4350  was an abysmal failure. Before trying this again I wanted to review the following approach to see if it is correct.

Issue #1, I assume that I have to remove the NVIDIA video drivers before installing the ATI video drivers.

Issue #2, The ATI video drivers can be installed by using the Synaptic package manager.(X.Org X server -- AMD/ATI r5xx, r6xx display driver ver 1.2.4-1 Correct Version???)

Issue #3. After installing the ATI Driver Shutdown the computer and install the card. When booting, immediately enter BIOS and set the video driver to the PCI Express slot so that it will use the ATI card.  When Ubuntu next boots, it will recognize the card?

# I also see that there is a program ENVYNG in Synaptic that will install the ATI video drivers.  Is this a good option?

---

### Post by darkod on 2009-11-11
I can recommend EnvyNG, it helped me a lot. The driver within ubuntu was rebooting my pc with integrated Radeon HD3200, the driver from EnvyNG took care of that.

For the rest I can not really give you any advice because I'm ubuntu newbie myself. If it is anything like windows (which it isn't :) ) it wouldn't mind having both sets of drivers present. Then in BIOS you just select the card.

Besides, the logic in the BIOS option should be that once you enable your video card the integrated one is automatically disabled by motherboard. Linux nor Windows shouldn't be able to see it at all, right?

---

### Post by JBAlaska on 2009-11-11
You switched from Nvidia to ATI to run Linux?..Yikes.

Remove the Nvidia driver, rename xorg.conf xorg.conf.old restart x.

Now I'm a bit dated, when I last ran a ATI, the official ATI drivers were the best option.

---

### Post by Steve R. on 2009-11-11
> **JBAlaska said:**
> You switched from Nvidia to ATI to run Linux?..Yikes.

Remove the Nvidia driver, rename xorg.conf xorg.conf.old restart x.

Now I'm a bit dated, when I last ran a ATI, the official ATI drivers were the best option.

Excellent Point. Using an Nvidia card would have eliminated one potential issue with upgrading.  Trying to make three "upgrades" at once was a bit much.  Best to do as small increments.

---

### Post by markbuntu on 2009-11-11
Do not use envy with ati cards.
The driver you need is in Hardware drivers in your Administration menu. Make sure you have all updates and that the nvidia driver is completely removed and that the bios is set for the ati card before enabling it. 

If you have successfully removed the nvidia driver ubuntu will revert to the generic VESA driver which works with all gpus. Set the bios to the ati card, boot into the recovery kernel from the gub menu and choose the fix x option. resume the boot, when you get to the desktop run update manager. reboot. Then go to System/Adminsitration/Hardware Drivers and enable the fglrx driver. reboot. If it does not work reboot into recovery and type

aticonfig --initial -f 

and reboot again.

---

### Post by Steve R. on 2009-11-12
It worked! :p:p

Obviously I have not had time to fully test, but everything looks correct.  I was especially impressed by the fact that UBUNTU recognized my monitor.  With the Nvidia on-board video card, the monitor was not recognized.

Thanks very much.

---

