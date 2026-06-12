---
title: "AMDGPU Pro 21.50"
date: 2022-03-18
forum: Hardware
---

### Post by tuxianer2 on 2022-03-18
Hey folks,

I got the following issue, I received my Slimbook on the weekend and started to install Kubuntu. Since I am in need of DaVinci Resolve (requires OpenCL) I installed the latest AMDGPU Pro Driver 21.50.1 alongside with Kernel 5.13 and remove any older Kernel. The installation went smootish ... However when restarting the system and passing through SDDM into the main system I see a screen that has window artefacts at random places and simply is not usable at all.

Based on some research I have then set the Tearfree paramenter in /etc as well as in /usr based on one comment I saw. Howeve in either case I cannot get it work. Ultimately I had to downgrade the Kernel via mainline to Version 5.6.19 and install an old AMDGPU Pro driver 20.20.

In this combination I was not expierencing any issue. Question here, has anybody got this to work and or what am I missing to get the latest AMDGPU Pro Driver running with Ubuntu 20.04.4 for which the driver has been released?


P.S. I tried the same with Ubuntu Gnome and Wayland and here I have the same behaviour rendering it unusable.

---

