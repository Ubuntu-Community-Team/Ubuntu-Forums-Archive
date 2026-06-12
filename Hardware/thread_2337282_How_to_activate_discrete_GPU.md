---
title: "How to activate discrete GPU"
date: 2016-09-16
forum: Hardware
---

### Post by caspinos on 2016-09-16
Hello!

I've recently migrated to Ubuntu Gnome 16.04 from OpenSUSE 42 on my notebook HP Probook 450 G1:
APU: Intel  i5 4200M (Intel HD Graphics 4600)
GPU: AMD Radeon HD 8750M

On OpenSUSE I used to switch GPU to AMD by using DRI_PRIME command, but it doesn't seem to work here.

My cards are recognized correctly (i think):
```

lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8670A/8670M/8750M] (rev ff)

```

However Radeon GPU is not listed in xrandr output:
```

xrandr --listproviders 
Providers: number : 1
Provider 0: id: 0x47 cap: 0x9, Source Output, Sink Offload crtcs: 4 outputs: 4 associated providers: 0 name:Intel

```

What I have found out is that radeon kernel module is blacklisted in /etc/modprobe.d/radeon.conf. I've tried to disable blacklisting for this module and it worked:
```

lsmod |grep radeon
radeon               1515520  2
ttm                    94208  1 radeon
i2c_algo_bit           16384  2 i915,radeon
drm_kms_helper        147456  2 i915,radeon
drm                   364544  12 ttm,i915,drm_kms_helper,radeon

```
However, there is still only Intel in xrandr output.

Please note that I've installed OpenCL for Intel APU (for BOINC) before, maybe I broke sth than (I'm quite new in Linux).

Please help, after hours of Google'ing I still don't know where is the problem.


EDIT:

In full lspci -v output I've found the following:
```

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8670A/8670M/8750M] (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: radeon
    Kernel modules: radeon

```


EDIT2:

It seems to work now... I'm confused.
```

DRI_PRIME=1 glxinfo | grep "OpenGL renderer"
OpenGL renderer string: Gallium 0.4 on AMD OLAND (DRM 2.43.0, LLVM 3.8.0)

```


FINAL EDIT:

After disabling 'radeon' kernel module blacklisting DRI_PRIME command works correctly, despite only intel card returned by 'xrandr --listproviders' command.

---

