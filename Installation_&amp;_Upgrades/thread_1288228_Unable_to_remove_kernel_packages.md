---
title: "Unable to remove kernel packages"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by CooledCoffee on 2009-10-11
In order to save disk space, I constantly remove the kernel image files under /boot/  leaving only the newest version. Now I find out a better way of doing this is to remove the packages using the Synaptic Package Manager. However, it is too late. When I try to remove those packages whose files have already been deleted by me manually, I get the error message:
E: linux-restricted-modules-2.6.28-11-generic: subprocess installed post-removal script returned error exit status 1
E: linux-restricted-modules-2.6.28-13-generic: subprocess installed post-removal script returned error exit status 1
E: linux-restricted-modules-2.6.28-14-generic: subprocess installed post-removal script returned error exit status 1

What makes things worse is that after I update to Ubuntu 9.10 beta, the packages are automatically marked as to be removed. Every time I run synaptic, it tries to remove these packages, which is impossible. And when I try to install a deb package, it says your system has broken dependencies.

What should I do now? Can anyone help?

---

### Post by qmark on 2009-10-11
I did the same mistake and faced similar error messages. 
 I solved it by manually creating empty directories in /lib/modules which the post-remove script wanted to delete. After that I successfully removed those packages by Synaptic.
Surprisingly, now those directories contain some small amount of garbage. What is important:  Synaptic now works and is able to install other packages.

---

### Post by CooledCoffee on 2009-10-12
Problem solved!
Your reply was very helpful. Thanks a lot!

---

