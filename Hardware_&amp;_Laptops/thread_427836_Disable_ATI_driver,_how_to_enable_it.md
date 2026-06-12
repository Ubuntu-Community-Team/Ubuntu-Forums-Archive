---
title: "Disable ATI driver, how to enable it?"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by blacklisted on 2007-04-29
I disabled my ATI drivers in 7.04, and now X will not start up, all I get is a terminal. How do I set up my system so it uses the proper drivers again?

---

### Post by 67GTA on 2007-04-29
type "sudo dpkg-reconfigure xserver-xorg" and change the graphics driver to"vesa". This should allow you to boot back into gui desktop. Then you can try to re-enable the driver.

---

