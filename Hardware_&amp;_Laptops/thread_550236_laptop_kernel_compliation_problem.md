---
title: "laptop kernel compliation problem"
date: 2007-09-13
forum: Hardware &amp; Laptops
---

### Post by bedwetter on 2007-09-13
I have an Asus F3SV A1 laptop and installed Feisty on it with relatively few problems.  To try and get the wireless working, I followed the instructions at: [http://forums.fedoraforum.org/forum/...d.php?t=159550](http://forums.fedoraforum.org/forum/...d.php?t=159550) .  The first step is adding a newer kernel and included a config file to use.  I ran into some trouble though: the new kernel (2.6.22.6) does not show up in the Grub menu on start up.  

I looked in /boot and noticed I am missing the files equivalent to: abi-2.6.20-16  and initrd.img-2.6-20-16 (these are for the previous kernel version I had in there)

Does anyone have any idea why this happened?

Thanks

---

### Post by nick_h on 2007-09-13
To add the new kernel to grub run:
```
sudo update-grub
```
You can generate an initrd file using *update-initramfs*.

The reason you have these problems is that you are not building the kernel the Ubuntu way. I suggest you read the [Master Kernel Thread](http://ubuntuforums.org/showthread.php?t=311158). If you build the kernel using make-kpkg it will create an initrd file for you and when you install the kernel package grub will also be updated.

---

### Post by bedwetter on 2007-09-14
Thanks for the reply.  I tried the commands you supplied, and it updated the menu list.  Unfortunately I got a kernel panic.

I think I will just start over by using the Master Kernel Thread instructions.  

Thanks again

---

### Post by trippinnik on 2007-09-14
i've usually had good luck following this guide: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

