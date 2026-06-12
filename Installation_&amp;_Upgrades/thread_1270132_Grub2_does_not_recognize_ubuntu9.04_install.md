---
title: "Grub2 does not recognize ubuntu9.04 install"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by m10 on 2009-09-19
I have 3 OSs installed on my system:
Ubuntu KK 9.10;
Ubuntu JJ 9.04;
Windows Vista;
The KK install is an upgraded 9.04 and the JJ is an upgragraded 8.10.
From KK I installed Grub2 (removing grub-legacy).
It all went fine exept that now i can't boot into JJ as it does not appear in the Grub menu at boot time.
KK is installed on 2 partitions: 
sda1 as /;
sda11 (on the extended partition sda3) as /home.
JJ is installed on 5 partitions(all on the extended partition sda3):
sda5 as /home;
sda6 as /;(UUID=6400a729-cf60-4b98-b06e-c0dc067c7aa4)
sda7 as /boot;(UUID=a6752047-4fb8-4e7c-8ffd-13599957f3a4)
sda8 as /tmp;
sda9 as /var;
All linux partitions are ext4.
Vista is on sda2.
Further i have a swap partition on sda10.
I need to somehow get the JJ bootable(main production OS).
i already tried to add a custom entry through /etc/grub.d/09_custom but it does not work.trying to boot it gives me some error about mount that can't mount partitions and init missing and drops me into a BusyBox shell(?).
I have been told that it could be because of a broken initd(or something like that) and i got instructions how to update it with chroot but it did not help.
Any help is appreciated.
Thank you in advance.

(attached my partion table,my grub.cfg and my 09_custom)

as you can see update-grub _does recognize the 9.04 install but doesn't add any entries in grub.cfg

---

### Post by m10 on 2009-09-24
it just was my custom entry witch was wrong:|.
it should have been:
menuentry "Jaunty, 2.6.28-15-generic" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set a6752047-4fb8-4e7c-8ffd-13599957f3a4 
        linux /vmlinuz-2.6.28-15-generic root=UUID=6400a729-cf60-4b98-b06e-c0dc067c7aa4 ro quiet splash
        initrd /initrd.img-2.6.28-15-generic
}

also look at [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/392529](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/392529) for more info on this bug..

---

