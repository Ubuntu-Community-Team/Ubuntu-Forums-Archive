---
title: "Additional Drivers not detecting NVidia GeForce FX5500"
date: 2012-05-07
forum: Hardware
---

### Post by Aardwolf96 on 2012-05-07
Hi all, I recently upgraded to 12.04 by way of a clean install and fired up jockey-gtk to get drivers, and all i got was a nearly blank window showing "No proprietary drivers are in use on this system."  I don't know if this has been posted elsewhere, but a search on google returned nothing.

As mentioned in the title, I am using a NVidia GeForce FX5500 which worked perfectly with 11.10.  If any other specs are relevant, let me know and I'll post them.

Thanks in advance.

---

### Post by kelvin spratt on 2012-05-07
> **Aardwolf96 said:**
> Hi all, I recently upgraded to 12.04 by way of a clean install and fired up jockey-gtk to get drivers, and all i got was a nearly blank window showing "No proprietary drivers are in use on this system."  I don't know if this has been posted elsewhere, but a search on google returned nothing.

As mentioned in the title, I am using a NVidia GeForce FX5500 which worked perfectly with 11.10.  If any other specs are relevant, let me know and I'll post them.

Thanks in advance.
That is a old card use synaptic  or download from  [http://www.nvidia.co.uk/object/linux-display-ia32-173.14.31-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-173.14.31-driver-uk.html) they do the legacy drivers on the nvidia site

---

### Post by rajplay on 2012-05-07
> **Aardwolf96 said:**
> Hi all, I recently upgraded to 12.04 by way of a clean install and fired up jockey-gtk to get drivers, and all i got was a nearly blank window showing "No proprietary drivers are in use on this system."  I don't know if this has been posted elsewhere, but a search on google returned nothing.

As mentioned in the title, I am using a NVidia GeForce FX5500 which worked perfectly with 11.10.  If any other specs are relevant, let me know and I'll post them.

Thanks in advance.
Hi Aardwolf,
I had problems with drivers for GeForce 8600M on 12.04, but **Cavsfan** on this forum suggested me to follow the steps from [http://ubuntuforums.org/showthread.php?t=1948062](http://ubuntuforums.org/showthread.php?t=1948062) and it worked fine for me.
Hope this helps!

---

### Post by Aardwolf96 on 2012-05-07
kelvin: that broke it, but thanks anyway.
rajplay: I'll try that once I get out of console limbo...

---

### Post by Yellow Pasque on 2012-05-07
It's not going to work until nvidia updates their legacy driver to work with Xserver 1.11: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053)

---

