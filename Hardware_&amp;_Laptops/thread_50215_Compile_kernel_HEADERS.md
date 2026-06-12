---
title: "Compile kernel HEADERS?"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by tseliot on 2005-07-19
Hi, I've compiled my kernel (2.6.12) and I would like to know how to compile the headers as I need to install the latest nvidia drivers.

Thanks in advance.

---

### Post by luca_linux on 2005-07-19
Just open Synaptic and install the packages: build-essential, linux-kernel-headers and linux-headers-your_kernel_version.

If you have compiled your custom kernel from sources, you just to need keep the sources directory and install the package buld-essential.

---

### Post by az on 2005-07-19
[QUOTE=tseliot]Hi, I've compiled my kernel (2.6.12) and I would like to know how to compile the headers as I need to install the latest nvidia drivers.

Thanks in advance.[/QUOTE]

If you compiled the kernel yourself, use the linux source tree for headers.  The headers are actually a replacement for the full kernel source.

If you made your kernel into a kernel package, you can use the kernel_headers optiopn in kernel-package.

---

### Post by tseliot on 2005-07-19
Wel,l when I type sudo sh NVIDIA-Linux-x86_64-1.0-7667-pkg2.run --kernel-source-path /usr/src/linux-2.6.12.3 the installer tells me it is not the right kernel source (which is not true).

What should I do?

---

### Post by Sav on 2005-07-20
[QUOTE=tseliot]Wel,l when I type sudo sh NVIDIA-Linux-x86_64-1.0-7667-pkg2.run --kernel-source-path /usr/src/linux-2.6.12.3 the installer tells me it is not the right kernel source (which is not true).

What should I do?[/QUOTE]

Did you create a symlink to your linux source folder?

sudo ln -s /usr/src/linux-2.6.12.3 /usr/src/linux

---

### Post by tseliot on 2005-07-20
Yes, I did it but the installer of the nvidia drivers doesn't seem to be aware of it.

---

