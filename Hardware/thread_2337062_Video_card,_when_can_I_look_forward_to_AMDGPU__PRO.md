---
title: "Video card, when can I look forward to AMDGPU / PRO, if at all?"
date: 2016-09-14
forum: Hardware
---

### Post by buenaventura16 on 2016-09-14
Dear Ubuntu Forums,

I am sure similar questions have already been posted, but I've looked at many of them and not really deduced a conclusive answer.

I'm on Xubuntu 16.04, I previously used fglrx (during 15.04) but was forced to switch to FOSS driver - which in many cases (to my happy surprise) gave better performance that the proprietary driver, however, recently I've been wanting to play some more 3D-intensive games (such as WINE+Mirror's Edge, TF2 on higher settings, Witcher2 etc) and they do perform quite badly, even tweaked to the very lowest settings. Therefore, I often wonder about my future prospects of using AMDGPU/PRO instead. But when, if at all?

First off, my video card. I have an Acer Aspire E15 laptop, and on a sticker it says "AMD Radeon R5 M240 with 1GB dedicated VRAM" - searching for such a video card rarely brings anything sensible up though, and I understand that hardware like this often have various marketing names etc. So this is what **lspci -vvnn | grep VGA** gives:
```
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] [1002:9851] (rev 05) (prog-if 00 [VGA controller])
```

My question is, what does that mean? Once during my forays in trying to find The True Name of my video card, I came upon various island names, and came to the conclusion that mine was either Oland or Mullins? I think that I established that it supports "GCN 1.0", which then should mean that AMDGPU and/or PRO will be supporting it, right?

1. Is it correct that I will be able to use AMDGPU (open source driver), and possibly AMDGPU-PRO also, with this card?
2. When? Can i be notified of when this is possible?

Thank you for clarifying!
:KS

---

### Post by buenaventura16 on 2016-09-17
If you do not know, where should I ask?

---

### Post by Yellow Pasque on 2016-09-17
[https://en.wikipedia.org/wiki/AMD_Radeon_Rx_200_series#Mobile_products](https://en.wikipedia.org/wiki/AMD_Radeon_Rx_200_series#Mobile_products)

The important thing to look at with regards to the AMDGPU support is the architecture the chip is based on (because, as you noted, the marketing name is confusing). In your case, you have a GCN 1st generation (more commonly known as GCN 1.0) chip.
See: [http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-SI-Next-4.9](http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-SI-Next-4.9)
Ubuntu 16.10 will have kernel 4.8 and I have no idea if they will enable this support until 17.04. You will probably be able to use a custom kernel and get it working.

---

### Post by buenaventura16 on 2016-09-18
> **Temüjin said:**
> [https://en.wikipedia.org/wiki/AMD_Radeon_Rx_200_series#Mobile_products](https://en.wikipedia.org/wiki/AMD_Radeon_Rx_200_series#Mobile_products)

The important thing to look at with regards to the AMDGPU support is the  architecture the chip is based on (because, as you noted, the marketing  name is confusing). In your case, you have a GCN 1st generation (more  commonly known as GCN 1.0) chip.
See: [http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-SI-Next-4.9](http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-SI-Next-4.9)
Ubuntu 16.10 will have kernel 4.8 and I have no idea if they will enable  this support until 17.04. You will probably be able to use a custom  kernel and get it working.

I see, thanks! That brings more questions:

1. So where would I start looking to try it out, do you know of any  guide or such? That is, compiling/using a kernel configured to use that  support, and installing the right driver etc.
2. Would it be worth it at this point, could I expect better performance  from (FOSS) AMDGPU compared to the (FOSS) radeon driver I currently  use?
3. If I manage to use that new kernel + AMDGPU, can I then use AMDGPU-PRO?

Thank you again! I should be able to deduce these things myself, but at this point I am stumped.

---

### Post by Yellow Pasque on 2016-09-18
1. The final kernel 4.8 isn't even released yet. Wait a month or two until kernel 4.9 starts releasing and then check: [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
If you're lucky, they will enable the support for you and you won't need to build your own kernel.
2. The 3D performance is going to depend more on what 3D driver you use (open source "radeonsi" or proprietary AMDGPU-PRO) rather than what kernel module you use
3. Yes

---

### Post by buenaventura16 on 2016-09-19
> **Temüjin said:**
> 1. The final kernel 4.8 isn't even released yet. Wait a month or two until kernel 4.9 starts releasing and then check: [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
If you're lucky, they will enable the support for you and you won't need to build your own kernel.
2. The 3D performance is going to depend more on what 3D driver you use (open source "radeonsi" or proprietary AMDGPU-PRO) rather than what kernel module you use
3. Yes

OK, thanks for the info! 

1. I guess it will be done when the 4.8 folder is called just 4.8 and not 4.8rc# ? And then, how do I add it?
2. Can I check anywhere when 4.8 is done, if it supports me?
3. Will AMDGPU-PRO be available in the ubuntu (non-free) repos at that time, or will I have to get it from AMD?

Thanks again for your time! I'm sure I'm not the only semi-hw-noob gamer who wants this cleared up.

---

### Post by Yellow Pasque on 2016-09-19
1. It will be called 4.9rc and then [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

2. I have no idea whether Ubuntu mainline kernel will enable the appropriate switch (CONFIG_DRM_AMDGPU_SI). I'm guessing if Ubuntu mainline doesn't, someone will build a kernel (maybe in a PPA) so that folks don't have to roll their own kernel.

3. I don't know

EDIT: You may also need newer libdrm (2.4.71)

The bottom line is that if someone doesn't make a nice PPA to make it easy, folks that are uncomfortable with experimental system components are probably better off waiting for Ubuntu 17.04

---

### Post by buenaventura16 on 2016-09-19
> **Temüjin said:**
> 1. It will be called 4.9rc and then [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

2. I have no idea whether Ubuntu mainline kernel will enable the appropriate switch (CONFIG_DRM_AMDGPU_SI). I'm guessing if Ubuntu mainline doesn't, someone will build a kernel (maybe in a PPA) so that folks don't have to roll their own kernel.

3. I don't know

Okay, so I guess that in two months I will google "AMDGPU ppa kernel 4.9" and see what comes up. If someone is planning to publish such a kernel in a ppa (or knows of someone who will/might), please tell me!

And if someone know the answer to q3 (whether AMDGPU-PRO might be included in ubuntu repos), please do speak up.

---

