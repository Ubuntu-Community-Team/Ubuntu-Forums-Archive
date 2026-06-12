---
title: "Does high memory support kernel work with soundcard?"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by vixensjlin on 2007-10-28
I am using Gusty 7.10 x86(32bit) with my Lenovo/IBM T61 (Nvidia/ICH8 family audio controller).  The system works fine in shipped kernel, except it cannot see all 4 GB ram.  (kernel with high memory support to 4G just can not to utilize all 4G ram for some reasons)

Consider all my applications are good under 32bit environment, I saved all old kernel setting (sudo make oldconfig) and compile my own kernel (kernel 2.6.22.9 with 64GB ram high memory support, by using [this method]("http://ubuntuforums.org/showthread.php?t=56835")).  My own kernel is able to see all 4GB RAM now, and the Nvidia support can be done by manual installation/compilation, everything happy, except.... the soundcard can not work under 64GB high memory support.

Any help/suggestion would be greatly appreciated. The attached pictures are the screen captures of generic kernel and the my own kernel with error message about soundcard.

---

