---
title: "kernel panic"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by traaf on 2005-08-01
HI there
newb on linux, i patched and compiled a kernel for 1st time

i had to do it to enable IT8212 controller on a asus p5gd1 motherboard

i used linux-2.6.11 from kernel.org
and alan cox' patch-2.6.11-ac7

but when i try to reboot on this kernel, i have a kernel panic
not syncing : VFS : unable to mount root fs on unknown-block (0,0)

fstab contains
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb2	/media/FAT	vfat	 rw,user,auto,umask=0	0	0
/dev/hdb5	/media/documents	vfat	 rw,user,auto,umask=0	0	0


```

and menu.lst contains
```

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.11ac7 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.11ac7 root=/dev/hda1 ro quiet splash fb1024x768
initrd		/boot/initrd.img-2.6.11ac7
savedefault
boot

```

and when i configured the kernel, i didn't forget to enable ext2 and ext3 filesystems
.config i used contains
```

CONFIG_EXT2_FS=y
CONFIG_EXT2_FS_XATTR=y
CONFIG_EXT2_FS_POSIX_ACL=y
CONFIG_EXT2_FS_SECURITY=y
CONFIG_EXT3_FS=y
CONFIG_EXT3_FS_XATTR=y
CONFIG_EXT3_FS_POSIX_ACL=y
CONFIG_EXT3_FS_SECURITY=y

```

so i don't understand what's hapenning
can someone help me fix this issue?

---

### Post by tseliot on 2005-08-01
Can you tell me the exact command with which you compiled the kernel?

---

### Post by traaf on 2005-08-01
# cd /usr/src
# tar zxvf /usr/src/linux-2.6.11.tar.gz
# cd /usr/src/linux-2.6.11
# cp /home/regis/patch-2.6.11-ac7.bz2 /usr/src/linux-2.6.11
# bzip2 -dc patch-2.6.11-ac7.bz2 | patch -p1
# mv /usr/src/linux-2.6.11 /usr/src/linux-2.6.11ac7
# cd /usr/src/
# ln -s linux-2.6.11ac7 linux 
# cd linux
# make xconfig
# make bzImage
# make modules
# make modules_install
# make install
# mkinitrd -o /boot/initrd.img-2.6.11ac7
# gedit /boot/grub/menu.lst

---

### Post by tseliot on 2005-08-01
this is an example of how to compile a kernel:

make xconfig
fakeroot make-kpkg clean (DON'T SKIP IT)
make-kpkg --rootcmd fakeroot --initrd --append_to_version -[COLOR=Red]amd64-k8[/COLOR] --revision [COLOR=Red]2.6.12-5.5[/COLOR] kernel_image kernel_headers [COLOR=Blue]modules_image[/COLOR]

You can put whatever you want instead of the parts in red. The part in blue is required only if you need to compile some modules.

P.S. If you don't have it, install "fakeroot" from synaptic

---

### Post by traaf on 2005-08-01
#make xconfig
#fakeroot make-kpkg clean
#make-kpkg --rootcmd fakeroot --initrd --append_to_version -i386 --revision 2.6.11ac7 kernel_image kernel_headers modules_image


correct?
for a P4 3GHz

---

### Post by tseliot on 2005-08-01
Yes, let me know if it works for you.

---

