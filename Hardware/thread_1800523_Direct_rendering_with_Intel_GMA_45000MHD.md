---
title: "Direct rendering with Intel GMA 45000MHD"
date: 2011-07-09
forum: Hardware
---

### Post by elldirash on 2011-07-09
Hello.

I recently bought a laptop with switchable graphics, and i managed to disable the dedicated graphics chip as i only need good graphics performance in windows (for games). However i would like to be able to run Unity 3D on the Intel GMA 4500MHD chip, but it seems that direct rendering is not enabled. From what i have read on different forums people are reporting that the 4500MHD works with direct rendering out of the box, so i cant figure out why it wont work for me. Running glxinfo gives a segmentation fault. Running 'lspci | grep VGA' returns:

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series] (rev ff)

I dont have an xorg.conf file. Could anyone get me started in the right direction towards getting this to work? I spent hours and hours searching forums without finding anyone with this problem, and i really dont know where to start as im relatively new to Linux.

Thanks in advance for any help.

---

