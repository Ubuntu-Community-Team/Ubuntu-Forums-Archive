---
title: "How to increase video ram for skylake graphics?"
date: 2016-08-31
forum: Hardware
---

### Post by anutosho on 2016-08-31
Hi,

I have a new mainboard Asus B150M-C with an Intel i3 6100 CPU.
It runs very well under Kubuntu Xenial with vdpau disabled and va enabled

The only problem is that there is very little video RAM assigned.
Here's the lspci output:
```

00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 06) (prog-if 00 [VGA controller])
        DeviceName:  Onboard IGD
        Subsystem: ASUSTeK Computer Inc. Skylake Integrated Graphics
        Flags: bus master, fast devsel, latency 0, IRQ 123
        Memory at f6000000 (64-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at f000 [size=64]
        [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

```

when I try to run 
```
glxgears -stereo
```
I get
```
"Error: couldn't get an RGB, Double-buffered, Stereo visual"
```
I'm using a 2650x1440 monitor so some more memory might be a good idea.

In another thread (with another mainboard) I read that the video memory can be set up in the BIOS, but I haven't found anything in the B150M-C BIOS.
ASUS says it can utilize up to 1024 MB shared video RAM but doesn't tell how to set that up.

Any idea?

---

### Post by Yellow Pasque on 2016-09-01
It's dynamically allocated (more RAM is allocated only as needed to maximize available RAM for the whole system) on modern Intel GPU's.

I don't know what glxgears stereo mode does, but I get the same error on my GTX950 with 2GB of dedicated RAM.

---

