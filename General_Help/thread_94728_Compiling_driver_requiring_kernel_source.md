---
title: "Compiling driver requiring kernel source"
date: 2005-11-24
forum: General Help
---

### Post by Aber_Adrian on 2005-11-24
Me again!

Having just upgraded my kernel to 2.6.12-10 (from 2.6.12-9) I can't now compile the nvidia driver. It complains that it can't find the kernel source. I pointed it at the directory /usr/bin/linux-source-2.6.12 but it didn't like it. Is there a difference between 2.6.12-9 and 2.6.12-10 that might be causing this? And if so, where can I get the source? apt-get doesn't find anything other than linux-source-2.6.12.

Adrian

---

### Post by sapo on 2005-11-24
This is simple.

Type the following on a terminal:

uname -r

it will give you your current kernel version, then type:

sudo apt-get install linux-headers-<your kernel version>

With this the nvidia driver should compile :)

---

### Post by Aber_Adrian on 2005-11-24
[QUOTE=sapo]This is simple.

Type the following on a terminal:

uname -r

it will give you your current kernel version, then type:

sudo apt-get install linux-headers-<your kernel version>

With this the nvidia driver should compile :)[/QUOTE]

Brilliant! thanks. I'd installed the 686 sources and I have apparently the 386 kernel.

Adrian

---

