---
title: "Configurating the kernel"
date: 2005-12-04
forum: General Help
---

### Post by jonan on 2005-12-04
I need to configurate my kernel, but I`m not able to do it, I saw a page were it said I`ve to do a $make config in /usr/src/linux/, but I haven`t got that folder, and I`ve try it with the two folders I`ve in /usr/src/, but it doesn`t work.:confused: 

Thanks;)

---

### Post by schdefan on 2005-12-04
you need to install the kernel sources first.
in a terminal type > uname -r and you will see your kernel version.
open synaptic and search for kernel-source of that version and install it.
When it's done go to teh folder /usr/src. You will see a folder e.g.
linux-source-2.6.12

you can build also a symbolic link to this archive with
> sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux

What do you need to configure?

schdefan

---

### Post by jonan on 2005-12-05
Thaks, but the problem is that I need to configurate the kernel for my Windows modem to work on Linux, this means I haven`t got acess to internet from my Ubuntu.:mad: 

What can I do?:rolleyes:

---

### Post by newuser111 on 2005-12-05
you need the restricted modules for your kernel for winmodem support, the only thing i can think of is downloading and burning that package to a cd and then using it to upgrade your computer

---

### Post by jonan on 2005-12-09
OK!!!:D 

I`ll do that, but were can I download the package:???:

---

### Post by Bachstelze on 2005-12-09
[http://packages.ubuntu.com/breezy/devel/linux-source-2.6.12](http://packages.ubuntu.com/breezy/devel/linux-source-2.6.12)

(assuming you're running the latest karnel available for ubuntu)

---

