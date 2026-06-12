---
title: "Toshiba Portege 2010 Display"
date: 2010-11-10
forum: Hardware
---

### Post by gdesilva on 2010-11-10
Hi,

I installed Ubuntu 9.10 on an old Toshiba Portege 2010 laptop. The installation itself was successful apart from the fact that the video card is not properly recognized and has defaulted to 800x600 display. Desktop Settings states that the monitor is 'UNKNOWN'.

I would appreciate if anyone can suggest how to fix this problem. Thanks.

---

### Post by gdesilva on 2010-11-13
For the benefit of those who may come across the same problem - it appears that the problem lies with the video driver used by the 9.10. Exactly the same problem was discussed and solved[ here]("http://ubuntuforums.org/showthread.php?t=806835&highlight=portege").

Essentially all I had to do was to download the Trident video driver from Unstable Debian archives, unpack it and copy the driver trident_drv.so to /usr/lib/xorg/modules/drivers/ to replace the existing driver.

Details are already discussed in the above post.

---

