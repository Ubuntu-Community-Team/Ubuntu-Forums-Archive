---
title: "my kernel compilation"
date: 2005-02-18
forum: Hardware &amp; Laptops
---

### Post by onami on 2005-02-18
i've just complied a kernel, and I don't know how to stick it into grub. I was used to lilo, where i had to edit lilo.conf and run lilo, but here I can't fing grub.conf.
I know I have to use :
#grub
grub> setup .....

but I don't know exactly.
Can you please help me ?

---

### Post by az on 2005-02-18
You do not have to run anything.   Just change /boot/grub/menu.lst

Be sure to use the correct device (hd0,0) is hda1 (hd1,1) is hdb2...

You do not have to run anything for it to be updated.  Grub updates itself on the fly.  You can even change your config as you boot (press e)

---

### Post by jerome bettis on 2005-02-18
the next time you want to recompile just type these commands.  it creates a .deb package which updates the grub menu automatically.

sudo -s
apt-get install build-essential libc6-dev binutils bin86 modutils gawk shellutils grep libncurses5-dev kernel-package
cd /usr/src/linux

make menuconfig
make-kpkg clean
make-kpkg -rootcmd fakeroot --append-to-version  (your version number ie -custom.1.0) kernel_image modules-image > /dev/null
dpkg -i /usr/src/kernel-image-(version).deb

---

