---
title: "Possible to enable highmem wihtout kernel compile?"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by Avatharian on 2009-07-16
On a previous install of ubuntu, i recompiled my kernel in order to enable the high memory option, so i could use all 4GB of memory on my 32-bit install. In the end, it seemed to work, but it was a very long and drawn-out process that I would rather not repeat again. My question is if the is a way to enable high memory without having to totally recompile the kernel, or if not, what would be the easiest and quickest way of recompiling for the option?

---

### Post by regala on 2009-07-16
> **Avatharian said:**
> On a previous install of ubuntu, i recompiled my kernel in order to enable the high memory option, so i could use all 4GB of memory on my 32-bit install. In the end, it seemed to work, but it was a very long and drawn-out process that I would rather not repeat again. My question is if the is a way to enable high memory without having to totally recompile the kernel, 

no, there is not.

> 
or if not, what would be the easiest and quickest way of recompiling for the option?


I don't understand... You already recompiled your own kernel, didn't you ?
if you used kernel-package and created a .deb suited to install the kernel you recompiled, it is straightforward to do it, again. If you did the more used "make menuconfig; make; make modules_install; cp arch/wherever/it/is/bzImage /boot/vmlinuz" then you should do the same, which will only recompile what has changed BUT, IIRC, changing highmem setting will trigger the rebuild of every single C file.

It is just a matter of minutes so I don't understand. Whatever method you used before, use it again to rebuild and overwrite your current kernel.

---

### Post by Cato2 on 2009-09-02
> **Avatharian said:**
> On a previous install of ubuntu, i recompiled my kernel in order to enable the high memory option, so i could use all 4GB of memory on my 32-bit install. In the end, it seemed to work, but it was a very long and drawn-out process that I would rather not repeat again. My question is if the is a way to enable high memory without having to totally recompile the kernel, or if not, what would be the easiest and quickest way of recompiling for the option?

The simplest approach is to just install a Server kernel - this may or may not work well for you, but it will give you 4GB RAM.  Be sure to check that it works with multimedia, restricted drivers for ATI/NVidia, VMware, etc.

See [http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/) for the commands to use.  Only takes 10 mins to try.

---

### Post by miklcct on 2009-09-03
There is a pae kernel in the repository starting from 2.6.31 for 32-bit systems.

---

