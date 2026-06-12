---
title: "Hardware abstraction layer"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by Twelc on 2005-04-19
Hi

Yesterday, I recompiled my kernel.
When I boot with the new kernel, I get the following error message:
[B]Starting hardware abstraction layer:
00:36:32.768 [W] hald.c:302: Your kernel does not support capabilities; some features will not be available.[/B]

I was wondering if I remove a feature in the kernel in relation with HAL.
But I can find which one.

Any ideas? Or is it something else?
Thanks

---

### Post by milou on 2005-04-19
The same for me ! I don't understand, since I compiled from ubuntu package with the config file issued from an "already-compiled kernel ubuntu package :-( ...

---

### Post by az on 2005-04-19
> **Twelc]Hi

Yesterday, I recompiled my kernel.
When I boot with the new kernel, I get the following error message:
[B]Starting hardware abstraction layer:
00:36:32.768 [W] hald.c:302: Your kernel does not support capabilities said:**
> 

I was wondering if I remove a feature in the kernel in relation with HAL.
But I can find which one.

Any ideas? Or is it something else?
Thanks
How did you recompile your kernel?

Did you use the stock configuration found in your /boot directory?  Did you use the linux-tree package to get all the Ubuntu patches?

---

### Post by Twelc on 2005-04-19
> How did you recompile your kernel?Like I used to do it on Gentoo: 
# make && make modules_install
# cp System.map /boot/System.map-2.6.10
# cp arch/i386/boot/bzImage /boot/vmlinuz-2.6.10
# cp .config /boot/config-2.6.10
# mkinitrd -o /boot/initrd.img-2.6.10 /lib/modules/2.6.10

> Did you use the stock configuration found in your /boot directory?yep, I used  it in order to have a start - and then, removed few things - like Soundcards, video etc - and change the ACPI + CPU scaling options.

> Did you use the linux-tree package to get all the Ubuntu patches?nope - don't know that :/
I first did :
# apt-get install linux-source
and then I did :
# apt-get install build-essential kernel-package libncurses-dev

---

