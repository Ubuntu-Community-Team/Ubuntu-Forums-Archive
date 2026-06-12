---
title: "Intel Graphics Driver"
date: 2005-08-08
forum: Hardware &amp; Laptops
---

### Post by nic2 on 2005-08-08
According to the Intel website their Linux drivers for Intel® Graphics have been released to major distributions and some distributions should contain native Intel Graphics support.  

Is this already supported under the Hoary Hedgehog release?  If not, will it be supported by the Breezy Badger release?

---

### Post by s_p_a_r_k_y on 2005-08-09
Do you have the i810 chipset? I remember a few friends who had onboard intel agp cards on their Dells at college. When I booted with knoppix to fix problemos, i remember seeing i810. Hope this helps, put it into your /etc/X11/xorg.conf file under the video driver settings.

---

### Post by raghav_p on 2005-08-09
I'm running an i855 intel extreme graphics and everything works fine out of the box except external vga monitor, but that too has a driver to get it working.

---

