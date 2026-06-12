---
title: "List of graphics cards supported by 22.x"
date: 2022-10-19
forum: Hardware
---

### Post by softfoot on 2022-10-19
I have just installed ubuntu-22.04.1-desktop-amd64 on a PC, but as of 22.x it no longer supports my graphics card.

Is there a definitive list of supported cards ???

They must offer at least OpenGL 3.1

I am NOT a Linux guru so the driver should just work with little or no hacking.

Regards,
Dave

---

### Post by TenPlus1 on 2022-10-19
Would help if you listed your graphics card make and model.

---

### Post by csae2608 on 2022-10-21
can tell you that graphics cards that i used are compatible with 22.04

nvidia t400 (with nvidia-driver)
amd rx 550 (with amdgpu or without)
amd wx2100 (with amdgpu or without)

official amdgpu drivers are officially only supported for LTS Kernel, which is a bit of a limitation, but besides, for 22.04 it is functioning.
the installation of AMDGPU however, is a bit tricky on 22.04 , since the driver-package seems to have some error with the repository; on 18,04 and 20.04 no such issues.
the opensource RADEON driver however functions flawlessly, but lacks some features.

---

### Post by kurt18947 on 2022-10-24
I just buy AMD/ATI pulls off Ebay. I don't know what version of OpenGL they support, they work fine for office type work. I've never messed with advanced graphic/video editing or gaming so can't help there. They cost around $20 - $30 which is a fraction of what even low end new video cards cost. They use the Radeon driver so plug 'em in and they work.

---

