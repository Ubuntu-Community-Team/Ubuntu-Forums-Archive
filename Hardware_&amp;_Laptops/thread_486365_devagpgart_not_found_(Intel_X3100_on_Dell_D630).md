---
title: "/dev/agpgart not found (Intel X3100 on Dell D630)"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by albertonym on 2007-06-27
OK, I am trying to install the system on Dell D630 with Intel X3100 video card but I cannot start my Xserver. I've got xserver-xorg-video-intel package but Xserver returns an error after not finding /dev/agpgart. I have intel_agp module loaded but not agpgart (it is not in lsmod). I tried building agpgart as a module and loading it via /etc/modules and tried building it in the kernel (under Device Driver -> Character devices -> --- /dev/agpgart). I even updated the kernel to the latest one (2.6.21.5). Still, no /dev/agpgart. Help!!!

---

### Post by albertonym on 2007-06-29
Well, I upgraded my kernel to 2.6.21.1 and it solved the problem.

---

