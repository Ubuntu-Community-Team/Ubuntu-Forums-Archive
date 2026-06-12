---
title: "/lib/modules/2.6.24-23-server/build missing"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by Agner on 2009-06-05
I am trying to build a custom driver in x64 Ubuntu. The make fails because the symlink /lib/modules/2.6.24-23-server/build is missing

My makefile contains:
[FONT="Courier New"][INDENT]KERNELDIR := /lib/modules/`uname -r`/build
obj-m := myecho.o
default:
	$(MAKE) -C $(KERNELDIR) M=`pwd` modules
[/INDENT][/FONT]

Please help

---

### Post by Agner on 2009-06-06
Everything works when I create the link manually with:

sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build

but why is this link missing?

---

### Post by Agner on 2009-06-07
-

---

### Post by a271828 on 2010-11-14
I got the same problem.

After Ubuntu update on my hardware computer could not start with 
> 2.6.32-22-generic

As it was suggested in /boot/grub/menu.lst I selected previous kernel
 > 2.6.31-16-generic

However 
> /lib/modules/2.6.31-16-generic

was missing while having:
> 
uname -r
2.6.31-16-generic


As result I could not install some packages like dahdi... they could not find needed headers.

It took me a while to figure this out. I had to include 

> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main

In order to get missing headers.

Why Ubuntu is not smart enough to catch this problem and automatically fix?

---

