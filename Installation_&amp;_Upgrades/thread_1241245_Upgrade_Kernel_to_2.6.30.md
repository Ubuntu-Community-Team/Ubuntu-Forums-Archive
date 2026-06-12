---
title: "Upgrade Kernel to 2.6.30"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by Nate Shoffner on 2009-08-15
I just tried to upgrade the kernel using KernelCheck HopeStar and I got this error:

> 
ABORT:  stage1 returned exit status 100


What would cause this?  Is there another way to upgrade the kernel?  By the way, I'm currently using 2.6.28.  Thanks!

---

### Post by esalnoj on 2009-08-15
Try this link: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

It is Master Kernel's main thread about kernel compilation.

---

### Post by master_kernel on 2009-08-17
Firstly, you need to upgrade to KernelCheck Lumen. And I think stage1 is the apt-get stage, so run dpkg --configure -a to fix any problems there.

---

