---
title: "nVidia restricted drivers"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by strumica on 2007-12-14
Hi, Just installed Ubuntu 7.04 on my desktop, and I can not enable the nVidia driver in the Restricted drivers manager. I click on the check box but nothing happens, it still remains unchecked. Have FX5200.

---

### Post by snkorea on 2007-12-14
$ sudo apt-get install linux-restricted-modules-$(uname -r)
$ sudo apt-get install nvidia-glx 
$ sudo nvidia-xconfig
restart X
$ nvidia-settings
restart X

---

