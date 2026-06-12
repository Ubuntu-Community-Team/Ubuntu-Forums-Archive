---
title: "Do you have to use the GRUB bootloader?"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by JamieLD on 2009-01-11
Hello!

I was just wondering when installing Ubuntu, do you have to install the GRUB bootloader? Its quite annoying having to go all the way to the bottom every time you want to boot Windows.

Thanks,
Jamie

---

### Post by frost151n on 2009-01-11
Have a look at this- [https://help.ubuntu.com/8.10/installation-guide/i386/device-names.html](https://help.ubuntu.com/8.10/installation-guide/i386/device-names.html)

Then you can do this- [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

If you already have Ubuntu installed then you need to 
1. Install Grub to your Ubuntu partition
2. Install EasyBCD in Windows.

Then use EasyBCD to
1. Restore Win MBR
2. Add Ubuntu to the MBR

There is a command that installs grub, unfortunately i don't know that command. Hopefully someone else can help you with that.

---

### Post by boof1988 on 2009-01-11
> **JamieLD said:**
> Hello!

I was just wondering when installing Ubuntu, do you have to install the GRUB bootloader? Its quite annoying having to go all the way to the bottom every time you want to boot Windows.

Thanks,
Jamie

One way you can solve this, is add static boot stanzas to menu.lst (in the proper areas, of course).  It's possible to set menu.lst to default-load your preferred OS and have the alternate very nearby (next line).

Let me know if you are interested and I'll try to help you set it up.

---

### Post by chex_m8 on 2009-01-11
> **JamieLD said:**
> Hello!

I was just wondering when installing Ubuntu, do you have to install the GRUB bootloader? Its quite annoying having to go all the way to the bottom every time you want to boot Windows.

Thanks,
Jamie
You can edit the GRUB menu which is a lot easier then trying to use windows boot loader. 
sudo gedit /boot/grub/menu.lst
then place a # in front of the title of all the OS entries you don't need, this will move windows up the list. I usually comment out any old kernels that are still listed in the GRUB menu.Notice the # in front of the title.
example:
#title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		82e16a90-9053-49d7-b4e0-c355b1097cbf
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=82e16a90-9053-49d7-b4e0-c355b1097cbf ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		82e16a90-9053-49d7-b4e0-c355b1097cbf
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=82e16a90-9053-49d7-b4e0-c355b1097cbf ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-7-generic

---

