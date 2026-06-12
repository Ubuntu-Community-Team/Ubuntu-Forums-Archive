---
title: "Screen freezes with Nvidia GTX 760 [nvidia-384.90]"
date: 2017-11-24
forum: Hardware
---

### Post by thereaction on 2017-11-24
I'm running nvidia-384.90 proprietary driver on Nvidia GTX 760. Today after playing a video on Youtube I noticed an unusual stuttering -- the video was not in a fact a video but a slide-show. I tried another video hosting site to make sure the problem is not html5-related or something and my screen froze completely. I rebooted the system and launched a random game from Steam -- the screen froze immediately. After that I tried nvidia-340 and nouveau drivers but they behaved even more poor -- the screen froze several times the second I logged in the system. I'm pretty sure I've not made any critical changes to my system in a past week and this is a completely fresh install (a week or two old).

Here's my dmesg: [https://bpaste.net/show/607e0d3dd825](https://bpaste.net/show/607e0d3dd825)

And some selected parts of it:

```
[    2.012905] nvidia: loading out-of-tree module taints kernel.
[    2.012910] nvidia: module license 'NVIDIA' taints kernel.
[    2.012911] Disabling lock debugging due to kernel taint
[    2.018711] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[    2.023993] nvidia-nvlink: Nvlink Core is being initialized, major device number 244
[    2.024264] nvidia 0000:01:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=io+mem
[    2.024340] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  384.90  Tue Sep 19 19:17:35 PDT 2017 (using threaded interrupts)
[    2.025814] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  384.90  Tue Sep 19 17:05:19 PDT 2017
[    2.026604] [drm] [nvidia-drm] [GPU ID 0x00000100] Loading driver
[    2.026605] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:01:00.0 on minor 0
```

I should mention that I've never had any video driver related problems on my xUbuntu system before, so this behavior seems very strange to me.

---

