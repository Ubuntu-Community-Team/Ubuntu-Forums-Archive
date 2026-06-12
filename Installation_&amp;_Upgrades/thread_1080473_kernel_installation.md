---
title: "kernel installation"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by uint on 2009-02-25
Hi,

I'm new to the linux kernel. I have downloaded
the kernel source from [www.kernel.org](www.kernel.org), and built it
(using make). now I should copy the kernel image and 
set it up to boot. 
The kernel image is at arch/i386/boot/bzImage
should I copy it to /boot ?
In addition, I can't find the files /boot/grub/grub.conf
or /ect/lilo.conf for the image configuration...
so how do I set the new image up to boot?

Thanks!

---

### Post by Neo_The_User on 2009-02-25
Don't build kernels using make. Don't use lilo. To answer your question, do the following commands.

```

sudo cp arch/x86/boot/bzImage /boot/vmlinuz-custom

```

Edit the config

```

sudo nano /boot/grub/menu.lst

```

It should look LIKE this.

```

title           Custom kernel
root            (hd0.0)
kernel          /boot/vmlinuz-custom root=/dev/sda1 ro

```

Keep me posted on how everything goes. I compile kernels daily with Ubuntu. I always compile them differently too. I'd say I'm highly experienced with this sorta thing so feel free to ask away.

---

### Post by uint on 2009-02-25
OK, thanks! but what do you mean not to build the
kernel using make? so how will I create the kernel image
after changes I'm doing?

how do I switch between the regular kernel and my kernel ?

one more thing - I'm trying to type "make modules_install"
but I get Permission denied...

---

### Post by uint on 2009-02-25
oops, I don't know what I have done but now ubuntu
doesn't boot, not from the default and not from the new
kernel (maybe because of the sudo make modules_install ?)

It starts only from "Ubuntu 8.10, kernel 2.6.27-7-generic"

---

### Post by Neo_The_User on 2009-03-08
...

This is why I use my home directory and do fakeroot make-kpkg --revision=custom kernel_image kernel_headers kernel_source when I first started compiling my first kernels.

btw the make modules_install.... if you insist:

```

sudo make clean && sudo make && sudo make modules_install

```

---

