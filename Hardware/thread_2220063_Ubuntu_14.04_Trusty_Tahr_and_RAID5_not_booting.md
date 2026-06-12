---
title: "Ubuntu 14.04 Trusty Tahr and RAID5 not booting"
date: 2014-04-26
forum: Hardware
---

### Post by RAMChYLD on 2014-04-26
So I'm trying to migrate my media center over to Ubuntu from Windows 7. I've recently put in three identical drives into the system and put on RAID 5. The installation discs picked up the array and allowed me to install to it and generally goes fine. However, upon restarting to boot into the system, the kernel can't find the boot device.
_dmesg | grep device_ returns the following error:
device-mapper: table: 252:0: raid: unknown target type
device-mapper: ioctl: error adding target to table

The error is repeated three times (I suspect this is because there are three drives in the system). After which I am dropped into the initramfs' busybox prompt.

Trying to run _dmraid -ay_ returns the same error and no progress can be made. The only option I have is to poweroff.

However if I boot from the LiveCD, I can mount and chroot the device.

Have I found a bug in Ubuntu? Shouldn't the device involved be *raid456* instead of just *raid*?

---

### Post by RAMChYLD on 2014-04-26
Nvm, fixed it myself. 

Steps to fix:
1. Boot from LiveCD
2. switch over to console ( [Ctrl]+[Super]+[F1] ) and do ' lsmod | grep raid '
3. mount the raid array to /mnt:
4. chroot /mnt
5. modify /etc/initramfs-tools/modules to include the modules listed in step 2 above.
6. rebuild initrd using mkinitramfs ( ' mkinitramfs -o /boot/initrd.img-3.13.0-24-generic 3.13.0-24-generic ' )
7. reinstall grub ( ' update-grub && grub-install /dev/mapper/<mapper-name> ' )
8. exit chroot
9. reboot
10. Profit!

List of modules displayed by the lsmod | grep raid :
raid0
dm_raid
raid1
raid10
raid456
async_raid6_recov
async_memcpy
async_pq
async_tx
raid6_pq

it seems pretty silly that the above aren't included in the default image, as they're required to boot a RAID array.

I've filed a bugreport, since these files are critical to allow a RAIDed system to boot.

---

