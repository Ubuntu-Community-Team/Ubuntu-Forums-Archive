---
title: "Grub2 problems."
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by maxideci on 2009-10-30
Yesterday, evening i started upgrade to 9.10. Everything went fine until last 30 seconds of installation. It threw two errors :

1) problems with +memtest20...or something for which i have submitted a bug report at [https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/463855](https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/463855)
2) grub-probe error, grub-probe: error: Cannot find a GRUB drive for /dev/sda9. Check your device.map.

The funny thing is, I had already upgraded my system's bootloader to Grub2 and used it for quite some time without any hitch. But now when i try to boot, the box pops up error as "grub-machine_fini" not found and shows up grub rescue menu. what do i do there ???

I booted using live usb stick, I have attached the output of boot_info_script (I found somewhere in this forum).

steps i followed :

root@ubuntu:~# mount /dev/sda9 /mnt -- This is my Linux root partition
root@ubuntu:~# mount --bind /dev /mnt/dev
root@ubuntu:~# mount --bind /proc /mnt/proc
root@ubuntu:~# chroot /mnt
root@ubuntu:/# grub-install /dev/sda9
**output** : [I]grub-probe: error: Cannot find a GRUB drive for /dev/sda9. Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
[/I]
my device map looks like this :
[I](hd0) /dev/sda
(hd1) /dev/sdb
[/I]
then i tried
root@ubuntu:/# grub-install /dev/sda
**output** : [I]grub-probe: error: Cannot find a GRUB drive for /dev/sda9. Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
[/I]
I have googled about this problem, but nothing works out in my way. Finally I have decided to fresh install, but when i reach the section about disk partition, 9.10 does not show any partition table at all. Does that mean my system's partition table is corrupt ??? i dont get how ??
I have now fixed my mbr using windows dvd, atleast now i can boot into windows, but i don't feel good.

can anyone help ??

i tried to probe for boot devie..
root@ubuntu:/# grub-probe -t device /boot/
**output** */dev/sda9*

I tried running Gparted, and see that, the partition table is gone, it shows complete disk as unallocated space.

the upgrade from 9.04 to 9.10 didn't finish correctly, as it threw up some error with +memtest...

I guess that's the reason why partition table is screwed up.

Is there anyway to recover partition table ??

Thanks.

---

