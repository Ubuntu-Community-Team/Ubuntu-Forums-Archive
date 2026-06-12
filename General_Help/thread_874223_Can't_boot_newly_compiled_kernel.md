---
title: "Can't boot newly compiled kernel"
date: 2008-07-29
forum: General Help
---

### Post by DemaSRV on 2008-07-29
Hi, I've been experimenting with compiling my own kernel, and I've managed to do it however I can't get update-grub to add it to my menu.lst.  Whenever I run update-grub, it is recognizing the new kernel and says that the file has been changed but when I look at it, nothing is different and its the same case after reboot.  I remember when I was finished compiling the kernel, I opted to keep my old menu.lst.

What I need help with, is being able to enable my new kernel in grub.

---

### Post by DemaSRV on 2008-07-30
^

---

### Post by logos34 on 2008-07-30
Then manually add an entry to /boot/grub/menu.lst.  Here's mine from a KernelCheck compile (-ultimate-10,00):

> title        Ubuntu Studio 8.04 (64-bit) 2.6.26-ultimate (/dev/sda7)
root         (hd0,6)
kernel       /boot/vmlinuz-2.6.26-ultimate root=UUID=d77656b5-aa1c-4375-8bfa-b517cebff023 ro splash resume=/dev/sda8
initrd       /boot/initrd.img-2.6.26-ultimate

---

