---
title: "AMD 5500XT (Navi/RDNA) GPU support in Ubuntu 20.04?"
date: 2020-10-13
forum: Hardware
---

### Post by vishalrao on 2020-10-13
Are people here running the Radeon 5000 series Navi/RDNA GPUs (like the 5500XT) stable on Ubuntu 20.04 LTS with its current kernel version 5.4-48 ?

From what I could see online, it's not stable on kernel 5.4 but I wonder if Canonical have backported any amdgpu fixes from newer kernel releases?

I believe the hardware enablement will only come around Feb 2021 to make this concern moot but until then I was hoping for some good news.

Thanks!

---

### Post by CatKiller on 2020-10-13
I don't use AMD graphics but, if it does turn out that you need newer stuff than what's currently available in an LTS Ubuntu release, you can get newer versions of the kernel from the [mainline archive](https://wiki.ubuntu.com/Kernel/MainlineBuilds), and there are several PPAs that will get you newer Mesa, like [this one](https://launchpad.net/~kisak/+archive/ubuntu/turtle).

---

