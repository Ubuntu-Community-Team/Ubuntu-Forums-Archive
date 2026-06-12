---
title: "Which driver for NVIDIA GT218 ION?"
date: 2013-04-25
forum: Hardware
---

### Post by arcull on 2013-04-25
Hi guys, I just bought a new asrock nettop ion 152D which comes with graphics card NVIDIA GT218 ION. So I put on ubuntu 12.04 64bit, and system runs almost fine, except for the graphics which looks a bit clumsy and slow. I have full resolution of monitor (1920x1080), but if I try to play a youtube video, I can do it only in small window mode, if I try to put it full screen it is hardly playing, so I guess the drivers are not ok. If I run glxgears test I get just about 60 fps, which is to low. I tried to install the restricted drivers via "Additional drivers" which were offered, but none of them does bring any improvement. Well I know this system is low performance, but it should be good enough to run video in full screen mode. So any advice is much appreciated, thanks in advance.

Some more card info:
```
02:00.0 VGA compatible controller: NVIDIA Corporation GT218 [ION] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: ASRock Incorporation Device 0a64
    Physical Slot: 0
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f7000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at de000000 (64-bit, prefetchable) [size=32M]
    I/O ports at dc00 [size=128]
    Expansion ROM at f6f80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb


```

---

### Post by arcull on 2013-04-30
I downloaded the dirvers for ION desktop graphics card directly from nvidia website and installed them. The installation script is smart enough to blacklist the existing module (noiveau) and builds a new one (nvidia), after reboot graphics work as it should. With glxgears I still get around 60 fps, but can watch youtube full hd movies in full screen without any problems, I even tried to installed some games like torcs and secret maryo chronicless and they work just fine.

---

