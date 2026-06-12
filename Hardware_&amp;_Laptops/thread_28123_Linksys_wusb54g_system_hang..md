---
title: "Linksys wusb54g system hang."
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by jkndrkn on 2005-04-18
I am using ndiswrapper with the linksys wusb54gv1.inf driver.

This is the only solution I've found yet that allows me to connect to the internet.

However, it is reponsible for spontaneous system hangs.

Anyone else had this problem? I checked linuxant, and they suggested that some windows drivers require more than the 4k of stack size provided in most linux kernels. They suggested the following kernel patch:

[http://www.linuxant.com/driverloader/wlan/downloads-patches.php](http://www.linuxant.com/driverloader/wlan/downloads-patches.php)

Am I on the right track? I'm running an nvidia graphics card, so I'm not ruling out the possibilites of the card causing the hangs. However, the system hangs occur mainly while I am connected to the internet, leading me to suspect that ndiswrapper is the culprit.

Any suggestions?

Thanks..

---

### Post by jkndrkn on 2005-04-20
Problem solved it *was*  the nvidia card. Using nvidia-glx and nv drivers caused my system to hang. I am running smoothly using vesa drivers now.

Thanks.

---

