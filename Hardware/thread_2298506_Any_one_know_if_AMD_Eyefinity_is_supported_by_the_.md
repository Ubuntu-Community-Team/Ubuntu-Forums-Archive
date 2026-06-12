---
title: "Any one know if AMD Eyefinity is supported by the open source Radeon driver?"
date: 2015-10-11
forum: Hardware
---

### Post by Joe_DePalma on 2015-10-11
I recently acquired a HIS Radeon HD 6570 PCI-e card for a cheap build I am doing.  It has the DisplayPort, VGA and DVI outputs, so it is Eyefinity compatible as long as I use an Active DisplayPort-to-whatever adapter for three monitor support.  I haven't built the PC yet, but I know the 6570 itself is supported with the open source driver and was wondering if Eyefinity is as well.  I've been digging but no one seems to know or has tried it. Thanks!

---

### Post by him610 on 2015-10-11
Support for the Eyefinity display controler is available in the Linux kernel device driver amdgpu and accessible via the DRM/KMS API.

RE: [https://en.wikipedia.org/wiki/AMD_Eyefinity]("https://en.wikipedia.org/wiki/AMD_Eyefinity")

---

### Post by Joe_DePalma on 2015-10-11
Thanks for the reply.  From your post, it sounds like I have to install the proprietary fglrx drivers to be able to use the Eyefinity feature.   I have never had luck with the proprietary drivers and have bricked my OS more than a few times.  Maybe I will try again and have some luck.

---

### Post by QIII on 2015-10-11
If you have bricked your machine with the fglrx driver, you have probably not done something correctly.  I haven't had problems with the drivers since before AMD bought ATI.

Could you describe the process you use to install the driver?

---

### Post by Joe_DePalma on 2015-10-11
I followed the directions on the Binary Install page ([https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)) to the letter and every time I've done it, nothing but a black screen and me doing a fresh install.  This has happened a few times so I have up on it and simply use the radeon driver.  As this build if for a docked laptop, I'll probably just find a USB graphics card and hope it has enough power.  I've heard of some people having luck with DisplayLink products.

---

### Post by QIII on 2015-10-11
Section 3.1?

What release and point release of Ubuntu are you using?

Has this been with laptops?  If so, are they hybrid setups with mixed AMD and Intel graphics?  Are they muxed (multiplexed) systems or muxless?

---

### Post by Joe_DePalma on 2015-10-12
Yes - section 3.1.  I never tried using the instructions of section 4 or downloading direct from AMD.  

I am using Ubuntu 14.04.3 LTS with the most current Kernel (3.16)

Yes, this has been done on a laptop. Specifically a Lenovo W500 (64-bit, C2D T9900, 8 GB RAM).  It is a hydrid setup, with the integrarted card an Intel GM45 HD and the discrete a AMD Mobility Radeon HD 3650.  I believe they are muxed.  

Thanks for your assistance.

---

### Post by QIII on 2015-10-12
The fact that it is a muxed system will cause the issues you describe.  There is some discussion about this in the wiki.  While you can use the open source Radeon driver and set up switchable graphics, using the proprietary driver and Eyefinity will likely be impossible.

Does you BIOS/UEFI allow you to completely ignore the on-board intel graphics?

---

### Post by jernej-jerin on 2015-11-20
> **hgh9mrp said:**
> Support for the Eyefinity display controler is available in the Linux kernel device driver amdgpu and accessible via the DRM/KMS API.

RE: [https://en.wikipedia.org/wiki/AMD_Eyefinity](https://en.wikipedia.org/wiki/AMD_Eyefinity)

> **Joe_DePalma said:**
> Thanks for the reply.  From your post, it sounds like I have to install the proprietary fglrx drivers to be able to use the Eyefinity feature.   I have never had luck with the proprietary drivers and have bricked my OS more than a few times.  Maybe I will try again and have some luck.

Read his post again and check the Wikipedia link. You DO NOT NEED proprietary drivers (i.e. fglrx), the open source version of drivers (i.e. radeon) is enough to enable Eyefinity feature. I am just writing this post from a computer, where I have one monitor that is 4K and the other one is QHD and they work perfectly from the same graphic card AMD FirePro W4100. At first I also installed proprietary drivers, because I thought I need them, which brought me nothing but headache (read as in lag, choppiness, flickering, etc.). With the open source drivers it is a breeze.

---

### Post by QIII on 2015-11-20
Careful, now.  The OP is talking about a laptop with muxed graphics, which renders all promises void.  A dedicated card on a desktop or a muxless laptop is an entirely different beast.

---

