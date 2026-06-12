---
title: "error during boot"
date: 2006-01-24
forum: Installation &amp; Upgrades
---

### Post by kyle8k on 2006-01-24
I recently installed Ubuntu with the 2.6.12 kernel. I want to set up a dual boot with the 2.6.15 kernel. I am somewhat new when it comes to linux. So i downloaded the new kernel, compiled it using:
make mrproper
make menuconfig
make install
make modules
make modules_install

and made the grubs menu.lst read:
title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,5)
kernel		/vmlinuz-2.6.12-9-386 root=/dev/hda7 ro quiet splash
initrd		/initrd.img-2.6.12-9-386
savedefault
boot

title		New Kernel
root		(hd0,5)
kernel		/vmlinuz-2.6.15 root=/dev/hda7 ro quiet splash
initrd		/initrd.img-2.6.15
boot

i got errors. After looking at a couple other posts, i tries:

sudo mkinitrd -o /boot/initrd.img-2.6.15
sudo depmod -v 2.6.15

i restarted and tried booting and it gave me

modprobe: FATAL: could not load /lim/modules/2.6.15/modules.dep
umount: devfs: not mounted
pivot_root: no such file or directory
/sbin/init:428 cannot open dev/console: no such file
kernel panic- not syncing

thanks in advanced

---

