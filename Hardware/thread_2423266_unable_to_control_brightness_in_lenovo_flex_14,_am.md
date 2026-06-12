---
title: "unable to control brightness in lenovo flex 14, amd ryzen 5 3550u with radeon vega 8"
date: 2019-07-19
forum: Hardware
---

### Post by sourabh141984 on 2019-07-19
I bought a new mentioned laptop. I am able to dual boot windows and ubuntu 18.04 without any problem. In ubuntu everything seems to work fine except that I am unable to control brightness in anyway.  It should be noted that the keyboard keys for controlling brightness do show the animation for increasing/decreasing brightness but nothing actually happens. I tinkered with various grub related settings( in /etc/defaults/grub file) mentioned in many forums but nothing works.  **xbacklight **also doesn't work. 
In Setting->Details my lapptop shows the following entries for processor and graphics.
[LIST]
[*]processor : AMD® Ryzen 5 3500u with radeon vega mobile gfx × 8
[*]Graphics : llvmpipe (LLVM 8.0, 128 bits)
[/LIST]
I am totally at a loss here. Any help would be appreciated.

---

### Post by sourabh141984 on 2019-07-22
It turns out just upgrading the kernel from 4.18.xx  to 4.20 solved the problem. I used the app named  **ukuu ** to upgrade the kernel.
The details section in ubuntu settings now shows 
Grahics :  AMD® Raven

---

