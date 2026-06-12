---
title: "NVIDIA Geforce GTX 560 Ti - need a bit of help"
date: 2024-01-04
forum: Hardware
---

### Post by mon^rch on 2024-01-04
hi guys,

NVIDIA Geforce GTX 560 Ti worked perfectly                previously with the Hardware Drivers applet and everything: ie it recognized my card and had the drivers for it, etc. but with this new and wonderful distro (Minotaur) there's no drivers available. I tried the installer from NVIDIA but it failed. I gotta have opengl, I play Quake and Doom III, heh.

can anyone help? thanks.

---

### Post by #&amp;thj^% on 2024-01-04
can you see anything with:
```
apt policy nvidia-driver-525
```

---

### Post by BicyclerBoy on 2024-01-04
The GTX560 Ti is not supported by the last legacy drive 470 (which is patched for kernel 6.5).
You need 390.

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=mantic](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=mantic)
Version 390 latest touched in July 2023: Support linux 6.4 ABI (LP: #2025266).

To use the nvidia installer you need kernel headers & it is possible the driver is **NOT** compatible with latest kernel 6.5 ABI.
What was the build error?

Here 23.10 install detects the correct nvidia-470 for GTX660Ti (but not using it).

If you have a fast CPU you may find swrast & LLVMpipe to be fast enough.

---

### Post by #&amp;thj^% on 2024-01-04
@BicyclerBoy good call, I had a senior moment and was thinking 1560 Ti. good catch.
I do think OP will get better results with the PPA.

---

### Post by Yellow Pasque on 2024-01-04
> **1fallen said:**
> I do think OP will get better results with the PPA.

It's not going to work with the 6.5.x kernel. There's a version (390.157-0ubuntu8) that's patched for 6.5 in the mantic-proposed repo. For some reason, it never made its way into Ubuntu main repo or even the unofficial graphics driver PPA.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/2028165/comments/16](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/2028165/comments/16)

---

### Post by #&amp;thj^% on 2024-01-04
> **Yellow Pasque said:**
> It's not going to work with the 6.5.x kernel. There's a version (390.157-0ubuntu8) that's patched for 6.5 in the mantic-proposed repo. For some reason, it never made its way into Ubuntu main repo or even the unofficial graphics driver PPA.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/2028165/comments/16](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/2028165/comments/16)

Good Info I don't test that far back, so all this is new news to me. :)
Thanks Yellow Pasque

---

