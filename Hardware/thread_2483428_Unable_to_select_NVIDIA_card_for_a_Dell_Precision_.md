---
title: "Unable to select NVIDIA card for a Dell Precision 7770 Mobile Workstation"
date: 2023-01-30
forum: Hardware
---

### Post by anjanesh2 on 2023-01-30
I'm trying to get a customized Precision 7770 Mobile Workstation

```
Intel Core i9-12950HX (30 MB cache, 24 threads, 16 cores, 2.30 GHz to 5.00 GHz, vPro)
Ubuntu® Linux® 20.04, DCA enabler
Intel UHD Graphics
128 GB, 1 x 128 GB, DDR5, 3600 MHz CAMM Module
1 TB, M.2 2280, Gen 4 PCIe x4 NVMe, SSD

```

But I can't seem to select either of :
```
NVIDIA® RTX™ A1000, 4 GB GDDR6
NVIDIA® RTX™ A3000, 12 GB GDDR6
NVIDIA® RTX™ A4500, 16 GB GDDR6
NVIDIA® RTX™ A5500, 16 GB GDDR6
NVIDIA® GeForce RTX™ 3080 Ti, 16 GB GDDR6

```

Is it okay if i stick to Intel UHD Graphics ? I'm doing only web development in Laravel and Django and maybe SpringBoot and need to use Docker extensively apart from regular apt-get install.

---

### Post by TheFu on 2023-01-30
Laptops have limited power, so fancy discrete GPUs may not work due to the added power requirements.

If you aren't gaming (FPS games) or doing video editing, then the intel iGPUs are fine since around the 3rd generation.  They will playback any videos with mpeg2/h.264 or h.265 codecs fine thanks to hardware and driver support that is built in.  Linux support for intel iGPUs has been fantastic for about 10 yrs. They are the least trouble of all GPUs.

Web development doesn't care about the GPU if you are doing typical web apps. Typical office productivity stuff all works great on almost any integrated GPU today.  I think some server-only GPUs are Maxxtor (800x600 GPUs) and those suck, but any workstation or desktop won't have one of those.

Of course, you should ask Dell these questions. They have forums too.

---

