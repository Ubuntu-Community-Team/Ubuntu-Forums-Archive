---
title: "Drivers for Dell Monitor and Radeon Graphics card"
date: 2021-08-18
forum: Hardware
---

### Post by syed_b_huq on 2021-08-18
I have installed 21.04 and I am looking for the Drivers for my Display and Graphics card.

Display: Dell SE198WFPv
Graphics: Radeon X1300/X1550

1) Do I search for Linux driver at Vendor website ?
2) IF it is there and I download, what are the instructions to install ?
3) Is there a Linux community website where I could search for these Drivers ?

My Display says "Unknown". I guess I am running a default driver of some sort. My Graphics card current driver works but would be nice to use the correct one.

Tks
Syed

---

### Post by bcschmerker on 2021-08-18
[Your system packs an ATi Technologies RV530 GPU; the X.org radeon driver (package: xserver-xorg-video-radeon, should be in ubuntu Main Repository) would be correct. The X.org Radeon driver should be compatible with your Dell display.

---

### Post by QIII on 2021-08-19
By way of further explanation ...

ATI was purchased by AMD in about 2008.  Your ATI is, for all intents and purposes, AMD.

The moniter is showing as "unknown" because if it is old, it is not returning EDID information the the OS, which, therefore, cannot identify it specifically by OEM, model or any capabilities.

With AMD graphics, there are only two driver modules:  the open-source radeon and open-source amdgpu (onto which the proprietary AMDGPU_PRO may be added.)  Both drivers are modules already baked into the Linux kernel.  At install time, Ubuntu's installer determines which module supports your GPU (in this case the radeon module) and activates it.  There is no need for you to do anything further.

---

### Post by syed_b_huq on 2021-08-19
> **bcschmerker said:**
> [Your system packs an ATi Technologies RV530 GPU; the X.org radeon driver (package: xserver-xorg-video-radeon, should be in ubuntu Main Repository) would be correct. The X.org Radeon driver should be compatible with your Dell display.

Thanks for the response. Really appreciate it.

---

### Post by syed_b_huq on 2021-08-19
> **QIII said:**
> By way of further explanation ...

ATI was purchased by AMD in about 2008.  Your ATI is, for all intents and purposes, AMD.

The moniter is showing as "unknown" because if it is old, it is not returning EDID information the the OS, which, therefore, cannot identify it specifically by OEM, model or any capabilities.

With AMD graphics, there are only two driver modules:  the open-source radeon and open-source amdgpu (onto which the proprietary AMDGPU_PRO may be added.)  Both drivers are modules already baked into the Linux kernel.  At install time, Ubuntu's installer determines which module supports your GPU (in this case the radeon module) and activates it.  There is no need for you to do anything further.

Thanks for the detailed response. This issue can be closed. Thanks !

---

