---
title: "stuck with wrong kernel"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by makno on 2009-06-21
I really need to get a normal kernel on my server. I updated to ubuntu desktop 9.04 starting from ubuntu 8.04. Unfortunally i couldn't use the standard install from cd as i don't have phisical access to the server and through vKVM from the .iso it kept crashing after partitioning the drives. I got OVH to install the the os for me but it comes with their kernel:
2.6.28.1-xxxx-std-ipv4-32

which apparently is a configuration for the servers...
i tried to install 2.6.30 from kernel.org without success, also with kernelcheck but server won't boot after i set it in lilo, or better it does boot but doesn't come up online so i'm stuck with the ovh kernel which doesn't allow modules and can't get either virtualbox or vmware to run.

---

### Post by jimv on 2009-06-22
This should do the trick.  If something goes wrong, you can always log back into the previous kernel in Grub (it will show up as a second entry).

sudo apt-get install linux-generic

---

### Post by master_kernel on 2009-06-22
You could also try the latest version of KernelCheck, if you haven't already.

---

### Post by makno on 2009-06-22
i installed kernelcheck last night but i'm trying to reinstall ubuntu from scratch now as things have gone wrong while trying to install grub :\

---

### Post by VastOne on 2009-06-22
> **master_kernel said:**
> You could also try the latest version of KernelCheck, if you haven't already.

+1 for kernelcheck

---

### Post by makno on 2009-06-23
well i had to reinstall 8.04 desktop in the end and upgrade to 9.04 desktop. only problem is now i cannot compile new kernel, not with source either with kernelcheck.
when i get to the make menuconfig i receive this error:
```
root@stocazzo:/usr/src/linux-2.6.30# make menuconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function 'conf_askvalue':
scripts/kconfig/conf.c:105: warning: ignoring return value of 'fgets', declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function 'conf_choice':
scripts/kconfig/conf.c:307: warning: ignoring return value of 'fgets', declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
 *** Unable to find the ncurses libraries or the
 *** required header files.
 *** 'make menuconfig' requires the ncurses libraries.
 *** 
 *** Install ncurses (ncurses-devel) and try again.
 *** 
make[1]: *** [scripts/kconfig/dochecklxdialog] Error 1
make: *** [menuconfig] Error 2
```

but i figured out that libncurses5 is installed and that i cannot install libncurses5-dev cause of the following error.
```
The following packages have unmet dependencies.
  libncurses5-dev: Depends: libncurses5 (= 5.7-2ubuntu1) but 5.7+20090207-1ubuntu1 is to be installed
```

is there a way to remove or replace libncurses5 as indicated?

---

### Post by jimv on 2009-06-23
I'm confused as to why you are trying to compile a kernel.

---

### Post by makno on 2009-06-24
the kernel that came with the installation of ubuntu from the server provider didn't have modules option enabled. the only way to run virtualbox or vmware was to recompile the kernel enabling modules so while i was there i decided to go for the 2.6.30

---

### Post by master_kernel on 2009-06-24
Try:
```
sudo apt-get build-dep libncurses5-dev
sudo apt-get install libncurses5-dev
```

And if you don't want to compile a new kernel, you could always go for the linux-generic package.

---

### Post by makno on 2009-06-24
tried that but was going nowhere. anyway i made it and i think i got into the idea of how it works now so shouldn't be a problem to compile a different one now. But still thanks for the answers :D

---

