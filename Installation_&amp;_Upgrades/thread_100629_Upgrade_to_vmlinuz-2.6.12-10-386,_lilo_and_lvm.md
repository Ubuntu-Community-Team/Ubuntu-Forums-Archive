---
title: "Upgrade to vmlinuz-2.6.12-10-386, lilo and lvm"
date: 2005-12-08
forum: Installation &amp; Upgrades
---

### Post by cibao5 on 2005-12-08
Hello,

I recently ran an Ubuntu upgrade which installed an image for 2.6.12-10-386 Kernel.  However, when running lilo I get the following error message:

sh-3.00# lilo
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/dm'
device-mapper ioctl cmd 12 failed: No such device or address
Fatal: device-mapper: dm_task_run(DM_DEVICE_TABLE) failed

I believe this is LVM related.  Currently, my /boot partition is under an LVM partition, which yes, I know its not the best thing to do, but unfortunately, during the install, Ubuntu seemed to have bypassed my /boot partition and simply using my /.  Any help or direction will be appreciated.  I also understand that grub does not work very well with a /boot under an LVM partition.  I would also welcome any advice on how to move from /boot in LVM to a good old /boot.

Thanks for your help.

Cibao

---

### Post by tonym on 2005-12-08
I don't think /boot on LVM works.

To move your existing /boot,  assuming you have a partition available,  /dev/hda1 say.

Create file system.

mke2fs -cvj /dev/hda1

Mount it temporarily

mount /dev/hda1 /mnt

Copy files from existing /boot

cd /boot
cp -axv . /mnt

Unmount and remount as boot

cd
umount /mnt
mount /dev/hda1 /boot

Now try to run lilo again.  Assuming that works,  edit /etc/fstab to add an entry for your new /boot.

Regards

Tony.

---

### Post by cibao5 on 2005-12-15
This worked great!  I had a few warnings, but I was able to boot using the new kernel.

Thank you!

---

