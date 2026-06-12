---
title: "Changing AGP speed"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by anthony4u on 2008-04-19
Hi all,

Is it possible to change AGP speed of the video card (Nvidia 7800 GS AGP) from 8X to 4X.  It seems to be highly unstable using 3D visuals (ie. glxgears).  I am unable to change it in the BIOS of the mohterboard (MSI K8MM3-V K8M800). In windows I have the same problem with stablility using 3D but was able to fix it using Rivatuner and changing the AGP speed to 4X. I'm a new at Ubuntu so am not comfortable with Xorg files...so if it is possible and requires playing with the Xorg file can you please point to direct instructions on how its done. 
Is there a box with Ubuntu or nvidia drivers where I can just check off 4X?? Wishful thinking eh?

Cheers

---

### Post by overdrank on 2008-04-19
> **anthony4u said:**
> Hi all,

Is it possible to change AGP speed of the video card (Nvidia 7800 GS AGP) from 8X to 4X.  It seems to be highly unstable using 3D visuals (ie. glxgears).  I am unable to change it in the BIOS of the mohterboard (MSI K8MM3-V K8M800). In windows I have the same problem with stablility using 3D but was able to fix it using Rivatuner and changing the AGP speed to 4X. I'm a new at Ubuntu so am not comfortable with Xorg files...so if it is possible and requires playing with the Xorg file can you please point to direct instructions on how its done. 
Is there a box with Ubuntu or nvidia drivers where I can just check off 4X?? Wishful thinking eh?

Cheers

Hi and welcome, I have a similar motherboard and how did you install the drivers for the graphics card?

---

### Post by Pettman on 2008-04-19
> **anthony4u said:**
> Hi all,

Is it possible to change AGP speed of the video card (Nvidia 7800 GS AGP) from 8X to 4X.  It seems to be highly unstable using 3D visuals (ie. glxgears).  I am unable to change it in the BIOS of the mohterboard (MSI K8MM3-V K8M800). In windows I have the same problem with stablility using 3D but was able to fix it using Rivatuner and changing the AGP speed to 4X. I'm a new at Ubuntu so am not comfortable with Xorg files...so if it is possible and requires playing with the Xorg file can you please point to direct instructions on how its done. 
Is there a box with Ubuntu or nvidia drivers where I can just check off 4X?? Wishful thinking eh?

Cheers

I might be different for nVidia cards (I've got ATi), but to set the agp mode you add 
```
Option "AGPMode" "4"
``` to the device section of your xorg.conf, remember to make a backup before you begin to tamper with it.

---

