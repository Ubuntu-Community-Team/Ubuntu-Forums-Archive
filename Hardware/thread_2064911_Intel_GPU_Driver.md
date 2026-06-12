---
title: "Intel GPU Driver"
date: 2012-09-30
forum: Hardware
---

### Post by GeForce 9500GT on 2012-09-30
[Can this be done]("http://www.techlw.com/2012/08/install-latest-intel-gpu-drivers-in.html") for an Intel 82945G/GZ Integrated Graphic Controller chipset as well? I have this GPU chip onboard in my HP Qompac desktop.

Spec:
Intel P4 - 3.0 GHz
2 Gig. memory

---

### Post by BicyclerBoy on 2012-09-30
Doubt you would see any improvement over the intel driver in recent kernels.
xorg-edgers will also upgrade the kernel.

Are you running 12.04?

The GMA900 is a old common netbook (atom) GPU.
There's not really any hardware capability to improve.
The glassen/xorg-edgers is working on support for sandy/ivybridge/haswell/valley-view etc.

Intel Extreme Graphics really meant extremeely crap..that's not the case with iCPU/GPUs..

Mind you, I'm sure xorg-edgers ppa has made the 945GME/ GMA900 run faster in my netbook in the past..
But also it broke parts of compiz/unity..
I have not done a direct A-B comparison with current mainline.
The speed improvements could already in the std mainline 12.04 kernel.

---

