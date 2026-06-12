---
title: "Configurating Kernel Sources"
date: 2008-08-28
forum: General Help
---

### Post by KailasNarendran on 2008-08-28
Hi!  I'm trying to install a Kvaser USB Leaf CAN card on a ubuntu 8.04.  I think i've got it working but googling around for how to configure kernel sources for installation has been a bit confusing and i was hoping someone might be able to clarify some things.

Before installing their linux drivers, you need to get kernel sources and headers.  Based on some posts i've seen around it looks like i need to create some symlinks as well to make sure that it's compatible with various naming conventions.  I believe i've done that:

```

root@kailas-laptop:/usr/src# ls -l
total 267812
lrwxrwxrwx  1 root src         19 2008-08-28 08:54 linux -> linux-source-2.6.24
lrwxrwxrwx  1 root src         19 2008-08-28 08:55 linux-2.6.24-19-generic -> linux-source-2.6.24
drwxr-xr-x 20 root root      4096 2008-08-28 08:50 linux-headers-2.6.24-19
drwxr-xr-x  6 root root      4096 2008-08-27 19:44 linux-headers-2.6.24-19-generic
drwxr-xr-x 23 root root      4096 2008-08-28 09:00 linux-source-2.6.24
-rw-r--r--  1 root root 273950720 2008-08-21 00:31 linux-source-2.6.24.tar
root@kailas-laptop:/usr/src# 

```

**Question #1 - Naming Conventions**

*Are there different standards about what you call the directory the source is in? It looks like there are 3: "/usr/src/linux", "/usr/src/linux-`uname -r`", and "/usr/src/linux-source-[version number]".  Are there any others?*

**Question #2 - How to handle**

*Is the right way to handle different conventions to create symlinks manually?*

Again, based on what i've seen around it looks like there are a couple of steps to "configure kernel sources".  Namely doing 3 things when in the kernel source directory:

```

root@kailas-laptop:/usr/src/linux-source-2.6.24# 
root@kailas-laptop:/usr/src/linux-source-2.6.24# make mrproper
<barf removed>
root@kailas-laptop:/usr/src/linux-source-2.6.24# make cloneconfig
<barf removed>
root@kailas-laptop:/usr/src/linux-source-2.6.24# make modules_prepare
<barf removed>

```

**Question #3 - where is cloneconfig?**

*I've seen many posts around that indicate you type the sequence above but for some reason my makefile doesn't have a "cloneconfig" target.  Was that something old that doesn't exist now?  I ended up using "oldconfig" and everything seemed to build (have yet to see if it actually works)*

**Question #4 - anything else?**

*Is that all you need to do to configure your sources for compiling?  Any other steps?  Anything that varies between distros on those other steps?*

It seems like you need to prepare kernel sources when compiling drivers.  The questions i've posed above remain unanswered and unclear after a fair amount of googling.  If anyone can answer it'd be helpful for me and hopefully a wider audience.

Thanks!

-kailas

---

