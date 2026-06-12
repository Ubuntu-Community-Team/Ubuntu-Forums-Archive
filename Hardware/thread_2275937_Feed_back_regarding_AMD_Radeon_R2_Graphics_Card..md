---
title: "Feed back regarding AMD Radeon R2 Graphics Card."
date: 2015-04-29
forum: Hardware
---

### Post by kagashe on 2015-04-29
I own Lenovo Notepad G50-45 which has AMD Radeon R2 Graphics Card integrated into AMD E1-6010 APU. There are other Laptops of HP, Dell etc with this card which are there on Ubuntu Certified Hardware.

This APU was launched by AMD in April 2014. I installed Ubuntu 14.04.1 in dual boot on my Lenovo Notepad. The Open Source Radeon driver was not working but fglrx driver worked.

The update of April 12 2015 broke the fglrx driver and I had to remove it.

Today I installed Kernel 3.16 through LTSEnablementStack with following command:
```
sudo apt-get install --install-recommends linux-generic-lts-utopic xserver-xorg-lts-utopic libgl1-mesa-glx-lts-utopic libegl1-mesa-drivers-lts-utopic
```

The open source Radeon Driver is working perfectly well with 3D support on Ubuntu 14.04 now (with Kernel 3.16).

Kamalakar

---

