---
title: "PXE Bootloader parameters for server install"
date: 2006-02-16
forum: Installation &amp; Upgrades
---

### Post by kiffer on 2006-02-16
I can't seem to get the pxe bootloader to do a server install with 5.04 Hoary.

At the boot prompt the only options that work are "linux" or "expert", both of which install the desktop. Having looked around for info I added a line for "custom" in pxelinux.cfg/default, this file is pasted below.

If I use the newly created custom option the install fails at the hard disk partitioning step, it displays the message "No partitionable media were found. Please check that a hard disk is attached to this machine". The disk is fine as if I revert to "linux" or "expert" the install works fine, proceeding through the disk partitioning. Any ideas?

```
display debian-installer/boot-screens/syslinux.txt
default linux

F1 debian-installer/boot-screens/f1.txt
F2 debian-installer/boot-screens/f2.txt
F3 debian-installer/boot-screens/f3.txt
F4 debian-installer/boot-screens/f4.txt
F5 debian-installer/boot-screens/f5.txt
F6 debian-installer/boot-screens/f6.txt
F7 debian-installer/boot-screens/f7.txt
F8 debian-installer/boot-screens/f8.txt
F9 debian-installer/boot-screens/f9.txt
F0 debian-installer/boot-screens/f10.txt

label linux
        kernel vmlinuz
        append vga=normal initrd=initrd.gz ramdisk_size=11057 root=/dev/rd/0 devfs=mount,dall rw --
label expert
        kernel vmlinuz
        append DEBCONF_PRIORITY=low vga=normal initrd=initrd.gz ramdisk_size=11057 root=/dev/rd/0 devfs=mount,dall rw --

label custom
        kernel vmlinuz
        append DEBCONF_PRIORITY=low ubuntu/install-type=custom vga=normal initrd=initrd.gz ramdisk_size=11057 root=/dev/rd/0 devfs=mount,dall rw --

prompt 1
timeout 0
```

Are the append parameters described anywhere that folks could point me to?

Many thanks.

---

