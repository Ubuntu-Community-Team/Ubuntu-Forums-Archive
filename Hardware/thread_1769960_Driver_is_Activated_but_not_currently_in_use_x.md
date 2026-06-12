---
title: "Driver is Activated but not currently in use :x"
date: 2011-05-28
forum: Hardware
---

### Post by Curse on 2011-05-28
I have an HP G50, just installed Xubuntu 11.04, and am having a video driver issue. 

I've tried both of the Nvidia driver options, and regardless of reboots they still say that the driver is activated but not in use. 

I've tried googling this issue but haven't come up with any sort of fix :x

Thanks!

---

### Post by Toz on 2011-05-29
Looks like a known bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/772207](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/772207) affecting quite a few. 

A potential solution here: [http://ubuntuforums.org/showpost.php?p=10744789&postcount=6](http://ubuntuforums.org/showpost.php?p=10744789&postcount=6) but be careful you install the correct kernel headers package. That posts states generic-pae - only install generic pae if you are using the pae kernel.```
uname -r
``` to show which kernel you are using.

---

