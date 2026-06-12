---
title: "Nvidia GeForce Go 7600 - Dapper Drake - Envy"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by gypsumwolf on 2008-01-01
I have ubuntu dapper drake at the moment, I plan to update to the 7.10 in a few days.

I tried to see if my graphics card was working properly in so I tried to run Neverball and it was really slow and chopy.

I read on another forum that I should use Envy so I tried and Envy says I need python-central and I can not find that in Synaptic.

---

### Post by gypsumwolf on 2008-01-01
I downladed the driver from nvidia. I am not doing the Envy rout now.

During install I get this message:
 ```
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
```

---

### Post by angryfirelord on 2008-01-02
Install the appropriate linux-headers package for your system.

If that works, then go to this file:
```
gksu gedit /etc/default/linux-restricted-modules-common
```
and change this line:
```
DISABLED_MODULES="nvidia"
```
That way, Ubuntu's older nvidia driver won't load in its place.

---

