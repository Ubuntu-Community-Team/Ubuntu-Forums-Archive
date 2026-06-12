---
title: "sata addressing"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by sandwitch on 2007-06-10
Hello happy users,

I have a small question about sata drives. I use one external drive connected to an sata_sil card on pci. On the same chip is the dribe i boot from attached. Two other sata drives are connected to the motherboard on sata_via. They are configured as raid1. My issue is every time i switch on the external backup drive, my addressing changes sdb becomes sdc etc. This makes my raid0 unuseable, so it needs to  rebuild itself. There should be a way to give the sata ports fixed addresses? I thought this should be done in /etc/modprobe.d/. ut i cant find anything in google. Maybe some of you can point me in the right direction?

---

### Post by neptho on 2007-06-10
You can do this using UUID addressing:

```
%ls -l /dev/disk/by-uuid
lrwxrwxrwx 1 root root 10 2007-06-09 23:11 07D7-0317 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-06-09 23:11 4ca63889-0784-4309-b517-44b9a3a54e43 -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-06-09 23:11 a8de1ad3-1fa0-459c-aab9-1e71be6bee8e -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-06-09 23:11 da430233-e545-4ed0-a58c-4445540cc93d -> ../../sda4
%cat /etc/fstab
# /dev/sda4
UUID=da430233-e545-4ed0-a58c-4445540cc93d /               ext3    noatime,defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=a8de1ad3-1fa0-459c-aab9-1e71be6bee8e /home           ext3    noatime,defaults        0       2
# /dev/sda3
UUID=4ca63889-0784-4309-b517-44b9a3a54e43 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
%grep UUID /boot/grub/menu.lst
# kopt=root=UUID=da430233-e545-4ed0-a58c-4445540cc93d ro
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=da430233-e545-4ed0-a58c-4445540cc93d ro quiet splash
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=da430233-e545-4ed0-a58c-4445540cc93d ro single
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=da430233-e545-4ed0-a58c-4445540cc93d ro quiet splash
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=da430233-e545-4ed0-a58c-4445540cc93d ro single
```

I know the above is fairly terse, I offered a bit more of an explaination [in this thread](http://ubuntuforums.org/showthread.php?t=468664).

---

