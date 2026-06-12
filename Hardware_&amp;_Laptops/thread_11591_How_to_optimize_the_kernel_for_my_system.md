---
title: "How to optimize the kernel for my system?"
date: 2005-01-17
forum: Hardware &amp; Laptops
---

### Post by jerome bettis on 2005-01-17
i just installed ubuntu and am pretty pleased with it so far, but there's a lot of stuff in the kernel i'll never need (printing, fax modem etc etc).  how would i go about removing the unnecessary stuff?

also, i'm guessing i've got a few services running that i don't need.  same thing, how do i stop the useless ones?

thanks a lot

---

### Post by nemin on 2005-01-19
[QUOTE=jerome bettis]i just installed ubuntu and am pretty pleased with it so far, but there's a lot of stuff in the kernel i'll never need (printing, fax modem etc etc).  how would i go about removing the unnecessary stuff?[/QUOTE]
You could disable unneeded kernel modules from loading or recompile your own kernel. See [www.kernel.org](www.kernel.org) to download the kernel and see the documentations to learn how to compile one on your own.

---

### Post by az on 2005-01-19
"i just installed ubuntu and am pretty pleased with it so far, but there's a lot of stuff in the kernel i'll never need (printing, fax modem etc etc). how would i go about removing the unnecessary stuff?"

The kernel that gets loaded when you boot is quite lean.  Most of the modules that you need are loaded by the initrd.  The kernel loads the initrd just after it first boots.  The initrd discovers the modules that you need and loads them.  Then iyou proceed with booting from your system on hard disk.  Services start up.  Hotplug is another service that will load modules for you.  You do not end up with a bunch of modules that you do not need sitting around in memory.

Ubuntu's kernel takes up less memory than Woody's 2.4.18-bf2.5 kernel on mysystem.

If you have hardware that you will never use, you can prevent the modules from being loaded.

The same goes for services that you do not need.  What services do you want to stop?

---

### Post by uberlinux on 2005-02-10
hey azz, 
dou know a site that can help you sort out what services do what, and how much you really need em?

---

### Post by Capitan on 2005-02-17
[QUOTE=azz]If you have hardware that you will never use, you can prevent the modules from being loaded.

The same goes for services that you do not need.  What services do you want to stop?[/QUOTE]

and how can I do that ?
on my desktop computer I use gentoo and there the modules are in the /etc/modules.autoload/kernel2.6 . where can I find this on ubuntu ?

---

### Post by ubuntu_fan on 2005-02-17
[QUOTE=jerome bettis]i just installed ubuntu and am pretty pleased with it so far, but there's a lot of stuff in the kernel i'll never need (printing, fax modem etc etc).  how would i go about removing the unnecessary stuff?

also, i'm guessing i've got a few services running that i don't need.  same thing, how do i stop the useless ones?

thanks a lot[/QUOTE]

If you're looking for extra performance, one of the simplest things you can do is to install the kernel that's optimised for you architecture, if you haven't already.

a.

---

