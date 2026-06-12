---
title: "Radeon™ Software for Ubuntu 20.04"
date: 2021-07-12
forum: Hardware
---

### Post by thumper76 on 2021-07-12
I just noticed that AMD has new software drivers for Ubuntu 20.04 for download. (Radeon™ Software for Linux version 20.20 for Ubuntu 20.04). 
I'm not having any problems with graphics and I usually say " it ant broke don't fix it", but I'm wondering if anyone has tried these drivers and what the advantage is. I have a AMD Ryzen CPU with integrated Radeon graphics.

---

### Post by Yellow Pasque on 2021-07-13
I would not bother with them unless I had a workstation card and was interested in their rocm/opencl capability.

In general, normal users and gamers should stick with the open source drivers.

---

### Post by QIII on 2021-07-13
AMD is bringing back the "Radeon" branding for a lot of things.  (The fact that they are using the &#8482; symbol rather than ® as a US company indicates to me that they are in the process of registering the trademark but have not yet finished.  I believe Radeon was a trademark of ATI before AMD bought them out, so there may be some legal entanglements.  But, off topic ...) That driver is actually amdgpu.  If your graphics are working and the amdgpu module (driver) is loaded, you don't need to do anything new.

The drivers you see on the AMD site are generally useful for newer kernels where the amdgpu module may not have been updated -- or for when HWE updates occur.  For the vast majority of users, the amdgpu module already included in the kernel is loaded at install time and is just right for your system.

The more powerful stuff comes with AMDGPU-PRO, which is an overlay extension to amdgpu but is generally not necessary -- except for Steam games and high-end GPU processing.

---

### Post by thumper76 on 2021-07-13
Thanks for the reply. I guess the best rule of thumb is "if it ant broke don't fix it" Current drivers are working fine.

---

### Post by linuux on 2021-07-16
I thought the 'Radeon' stuff had to do with the proprietary AMDGPU-PRO driver?

---

### Post by QIII on 2021-07-16
The open source "radeon" driver (small "r") maintained by the open source community is suited for older AMD (and ATI) hardware not supported by the amdgpu driver maintained by AMD.  AMDGPU-PRO is the proprietary overlay.

AMD is re-introducing the "Radeon" trademark, which covers amdgpu (the Radeon Driver) and AMDGPU-PRO (the Radeon Pro Driver).  In general, they are talking about "Radeon Graphics" nowadays.  Again.  Also, you can download the drivers as a single "unified" Radeon package.  

It's all about branding.

---

