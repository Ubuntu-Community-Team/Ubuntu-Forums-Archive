---
title: "Gutsy and nvidia on dv2055ea"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by cRoW2k on 2007-10-19
hi folks.

I've gutsy from tribe 5 and nvidia driver works well. Upgrade after upgrade (untill RC) the driver installed with Envy doesn't load at boot. The system load the driver comes with Ubuntu so nvidia-glx say me that: You do not appear to be using the NVIDIA X driver ecc ecc..

my lsmod:
nvidia              ** 6221776**  36 
i2c_core               26112  1 nvidia
agpgart                35016  2 nvidia,intel_agp

but if i search for nvidia.ko: 
ls -l /lib/modules/2.6.22-14-generic/nvidia/nvidia.ko
-rw-r--r-- 1 root root **7581350** 2007-10-19 17:42 /lib/modules/2.6.22-14-generic/nvidia/nvidia.ko

it's 1mb greater! 

i've try to disable restricted manager, Compiz ecc. But the system load continously the defalt nvidia module.

What's the matter?
thanks

---

