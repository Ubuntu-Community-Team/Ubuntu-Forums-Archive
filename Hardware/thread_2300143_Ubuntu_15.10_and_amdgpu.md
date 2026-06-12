---
title: "Ubuntu 15.10 and amdgpu"
date: 2015-10-23
forum: Hardware
---

### Post by tragedypoet on 2015-10-23
Hi at all,

I upgraded my Kubuntu installation today from 15.04 to 15.10 and was curious about the new AMDGPU driver since the fglrx doesn't work at the moment (and you really don't want to use it). My Graphics card is a Radeon HD 7870 (GHZ Edition), if more hardware info is needed, just tell me.

```

alex@gurren:~$ uname -a
Linux gurren 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

I installed the following packages: ```
xserver-xorg-video-amdgpu libdrm-amdgpu1
```

After a few reboots, needed to purge the fglrx completely from the system, everything seems to work fine, but there are a few things that worry me.

First the output of the Xorg.0.log doesn't say a word about the driver
```

alex@gurren:~$ cat /var/log/Xorg.0.log | grep radeon
[    11.939] (II) modeset(0): [DRI2]   DRI driver: radeonsi
[    11.939] (II) modeset(0): [DRI2]   VDPAU driver: radeonsi
[    11.963] (II) AIGLX: Loaded and initialized radeonsi

```

Then the output of lsmod
```

alex@gurren:~$ lsmod | grep radeon
radeon               1519616  5
ttm                    94208  1 radeon
i2c_algo_bit           16384  2 i915,radeon
drm_kms_helper        126976  2 i915,radeon
drm                   356352  12 ttm,i915,drm_kms_helper,radeon

alex@gurren:~$ lsmod | grep amd
amdkfd                122880  1
amd_iommu_v2           20480  1 amdkfd


```

After I enter a ```
modprobe amdgpu
``` it looks like this:

```

amdgpu                811008  0
amdkfd                122880  1
amd_iommu_v2           20480  1 amdkfd
ttm                    94208  2 amdgpu,radeon
i2c_algo_bit           16384  3 i915,amdgpu,radeon
drm_kms_helper        126976  3 i915,amdgpu,radeon
drm                   356352  13 ttm,i915,drm_kms_helper,amdgpu,radeon

```

```

alex@gurren:~$ cat /usr/share/X11/xorg.conf.d/10-amdgpu.conf 
Section "OutputClass"
        Identifier "AMDgpu"
        MatchDriver "amdgpu"
        Driver "amdgpu"
EndSection

```

Did I do something wrong? Is there anything I need to do to load it automatically or do I understand something wrong here and everything is fine?

---

### Post by myromance123 on 2015-10-24
The AMDGPU driver cannot be used on a  HD7870. It also cannot be used on my R9 390 which is supposed to be current generation.

The only cards it does work with are cards that have the following chips in them (and future chips beyond these):
1. Tonga (R9 285, R9 380)
2. Carrizo (APUs?)
3. Fiji (R9 Fury, R9 Nano, R9 Fury X, R9 Fury X2)

All older cards **WILL NOT BE SUPPORTED BY AMDGPU**. This includes quite a number of current cards as well, many of the 300 series cards are not supported.

So, all that hype that AMDGPU was the future? It's not for those of us currently. When it comes out, you will need to buy a new card. It's not meant to make the older cards perform better. The older cards will likely be left with the performance they currently have for quite some time, since AMD needs to sell new cards (very bad tactic which will lose customers).

The current hope is for the Vulkan driver. This really depends on whether previous games that were released will get a Vulkan update though. If they don't, we won't see any performance improvements there either. At the very least, your card should be supported when Vulkan releases.

By default your card and mine will only make use of RadeonSI in the Open Source Mesa driver.

---

### Post by tragedypoet on 2015-10-24
Well that's too bad :(, but thanks for the info. Saved me a few hours of debugging this whole stuff.

Then let's hope the Vulcan driver is as much based on the Mantle as they say, since this one was supported by the 7870.

I think I can mark that one as solved, if I find the option for that somewhere...

---

### Post by myromance123 on 2015-10-24
No problem, I feel your pain too. I bought this card in high hopes I'd be getting the latest. I had no idea AMD counts their generations by chips, and not the actual card series number... Had to find that out the hard way.

All the best mate.

---

### Post by bcellin on 2016-05-22
My graphic card was not supported on beginning but now it is supported by amdgpu. Mine is a R7 M265. Try again on kernel 4.6.

ps: how can you test if it's working? I run lsmod | grep radeon and get nothing. I run lsmod | grep amdgpu and I get same results from you. I think it's working but when I run a game using DRI_PRIME=1 it performs the same as executing without parameters, that is, executing with integrated graphics.

---

