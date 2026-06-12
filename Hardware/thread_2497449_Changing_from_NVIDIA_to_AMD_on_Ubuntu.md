---
title: "Changing from NVIDIA to AMD on Ubuntu"
date: 2024-05-05
forum: Hardware
---

### Post by drew1121 on 2024-05-05
I am currently upgrading from a 1660 Super to an RX 7600 and would like to know how i would go about it on Ubuntu. 
Would i have to delete the NVIDIA drivers and would i have to do it before or after changing out the gpu.

---

### Post by him610 on 2024-05-05
You will not need the nvidia drivers so you can delete them. AMD GPUs are supported by Ubuntu. You may consider updating the BIOS of your motherboard if it needs it.

---

### Post by drew1121 on 2024-05-05
Should i do this before or after i put the new card in?

---

### Post by QIII on 2024-05-06
Remove the Nvidia driver before adding the AMD GPU.  Otherwise you will likely encounter conflicts.

---

### Post by MAFoElffen on 2024-05-07
> **him610 said:**
> ...AMD GPUs are supported by Ubuntu.
I believe what he meant to say is that the opensource AMD drivers are support by the Linux Kernel. Ubuntu is a Linux Ditribution, so it does support AMD amd_gpu Graphics in Kernel.

The timing of the process would be, on the last boot with the NVidia Card, uninstall the NVidia graphics drivers. Shutdown. Switch the Cards. Boot up with the AMD GPU installed.

---

