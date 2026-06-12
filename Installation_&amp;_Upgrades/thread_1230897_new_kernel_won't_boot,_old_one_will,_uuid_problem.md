---
title: "new kernel won't boot, old one will, uuid problem"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by whistlingtony on 2009-08-03
Hi all,

I recently had to do a fresh reinstall.  Everything went fine. I then did an upgrade, and a new kernel was installed. Aha! The new kernel won't boot. It complains about...

ALERT! /dev/disk/by-uuid/932e05da-88e2-4eec-ab84-4c11e74ebeec does not exist. 
Dropping to a shell!


The funny thing is that it's the same setup as my old kernel, which boots fine. any ideas? I tried looking on the almighty internet, but no luck. I'm copying my /etc/fstab and my /boot/grub/menu.lst. I'd love some help on this one!

-Tony

p.s. I bet it's a problem with udev, or my initramfs. Why did we ever go away from simplicity? All these new freak'in files and wacky thing to work around problems instead of just fixing the damn problems.....


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=932e05da-88e2-4eec-ab84-4c11e74ebeec /               ext2    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=2634831c-1e92-47b1-836e-9ebdde222348 /home           ext3    relatime        0       2





title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		932e05da-88e2-4eec-ab84-4c11e74ebeec
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=932e05da-88e2-4eec-ab84-4c11e74ebeec ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		932e05da-88e2-4eec-ab84-4c11e74ebeec
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=932e05da-88e2-4eec-ab84-4c11e74ebeec ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

---

