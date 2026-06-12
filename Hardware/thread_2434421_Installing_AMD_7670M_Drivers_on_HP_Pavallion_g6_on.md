---
title: "Installing AMD 7670M Drivers on HP Pavallion g6 on Ubuntu 18.04"
date: 2020-01-05
forum: Hardware
---

### Post by jainik-x on 2020-01-05
hi, i have a HP Pavallion G6 Laptop
it has an Inbuilt Intel Graphics AND AMD RadeonHD 7670M 

i am having problems finding the AMD7600Series drivers and its Confusing which Driver to install..
i am Using Ubuntu 18.04

---

### Post by QIII on 2020-01-06
You do not need to "find a driver".  It is part of the Linux kernel.  

There are currently two drivers for AMD products:  The open source Radeon driver and the open source AMDGPU driver (AMDGPU-PRO is a proprietary overlay to AMDGPU and only works if AMDGPU supports your card.).

When you install Ubuntu, the appropriate driver is selected based on which supports your GPU.

There is nothing further you need to do.

You have a hybrid system:  Intel integrated and AMD dedicated.  Unfortunately, the GPU manufacturers have not provided the Linux community with any good ways to use both and toggle between them.  Your BIOS/EFI may have a setting to select one or the other on start up.

---

