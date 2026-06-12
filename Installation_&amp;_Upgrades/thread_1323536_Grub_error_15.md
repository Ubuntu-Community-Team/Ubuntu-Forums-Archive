---
title: "Grub error 15"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by zintinio on 2009-11-11
I will most likely reformat, it's no big deal. I need to know if it is possible to remove my files from the hard drive via a rescue live disk, or the Karmic live disk. I have an issue with Grub where I attempted to upgrade to GRUB2 (stupid, I know) and when I rebooted it said error 15. I already tried running a live disk to check out the system, and the filesystem was good, etc. Can I get my files onto another drive? Do I need root priveleges? Any help would be great.
EDIT:
I solved this. will post later

---

### Post by zintinio on 2009-11-11
[http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/](http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/)
I found this. It's GRUB 1.5 by the way.

---

### Post by zintinio on 2009-11-11
$ sudo mount /dev/sda1 /mnt
$ sudo mount --bind /dev /mnt/dev
$ sudo chroot /mnt
# nano /etc/default/grub
~edit this file~
# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found memtest86+ image: /boot/memtest86+.bin
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
done
 Out put of terminal while attempting to fix.
It works now anyway. I suggest a backup and clean install.

---

