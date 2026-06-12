---
title: "grub error 15 file not found"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by fkrogh on 2009-04-25
I've looked at other posts on this issue, but they don't seem to deal with my situation or at least I can't see what more to do after reading them.

I started with a small boot partition that was too small on hd0.  After booting I made a new boot partion on hd1 and switched directory names around so that /boot was on hd1.  This enabled an install of jaunty.  My BIOS lets me pick the disk that is first to boot from and thus I want to use hd1, which gives the error in the title.  I can still boot with hd0, but that has an old kernel in it.
Fdisk says both disks are bootable in their first partitions.  Grub has been installed on both disks.

==== Entries in menu.lst
...
# groot=e30be990-4184-4de2-81ce-e0b02a9dfae7
      (also tried # groot=(hd1,0)
...
title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		e30be990-4184-4de2-81ce-e0b02a9dfae7
root		(hd1,0)
kernel		/vmlinuz-2.6.28-11-generic boot=UUID=e30be990-4184-4de2-81ce-e0b02a9dfae7 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
...
(Note -- the line starting with boot is actually on the previous line.)

==== contents of /boot/grub
-rw-r--r-- 1 root root    197 2009-04-25 15:10 default
-rw-r--r-- 1 root root     30 2009-04-25 15:10 device.map
-rw-r--r-- 1 root root   8288 2009-04-25 15:10 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-04-25 15:10 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-04-25 15:10 installed-version
-rw-r--r-- 1 root root   8712 2009-04-25 15:10 jfs_stage1_5
-rw-r--r-- 1 root root   4981 2009-04-25 17:11 menu.lst
-rw-r--r-- 1 root root   4964 2009-04-25 16:27 menu.lst~
-rw-r--r-- 1 root root   7352 2009-04-25 15:10 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-04-25 15:10 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-04-25 15:10 stage1
-rw-r--r-- 1 root root 121740 2009-04-25 15:10 stage2
-rw-r--r-- 1 root root   9556 2009-04-25 15:10 xfs_stage1_5


==== contents of /boot
-rw-r--r-- 1 root root  508385 2009-04-01 15:46 abi-2.6.27-11-generic
-rw-r--r-- 1 root root  529118 2009-04-16 20:41 abi-2.6.28-11-generic
-rw-r--r-- 1 root root   91358 2009-04-01 15:46 config-2.6.27-11-generic
-rw-r--r-- 1 root root   96795 2009-04-16 20:41 config-2.6.28-11-generic
drwxr-xr-x 2 root root    4096 2009-04-25 17:11 grub/
-rw-r--r-- 1 root root 8152172 2009-04-25 08:34 initrd.img-2.6.27-11-generic
-rw-r--r-- 1 root root 7466671 2009-04-25 08:35 initrd.img-2.6.28-11-generic
drwx------ 2 root root   16384 2009-04-23 12:20 lost+found/
-rw-r--r-- 1 root root  128796 2009-03-27 10:15 memtest86+.bin
-rw-r--r-- 1 root root 1031799 2009-04-01 15:46 System.map-2.6.27-11-generic
-rw-r--r-- 1 root root 1456232 2009-04-16 20:41 System.map-2.6.28-11-generic
-rw-r--r-- 1 root root    1074 2009-04-01 15:48 vmcoreinfo-2.6.27-11-generic
-rw-r--r-- 1 root root    1074 2009-04-16 20:43 vmcoreinfo-2.6.28-11-generic
-rw-r--r-- 1 root root 2249232 2009-04-01 15:46 vmlinuz-2.6.27-11-generic
-rw-r--r-- 1 root root 3501776 2009-04-16 20:41 vmlinuz-2.6.28-11-generic

======= Some soft links in /
lrwxrwxrwx 1 root root 30 2009-04-25 08:34 /vmlinuz -> boot/vmlinuz-2.6.28-11-generic
lrwxrwxrwx 1 root root 30 2009-04-25 08:33 /vmlinuz.old -> boot/vmlinuz-2.6.27-11-generic

lrwxrwxrwx 1 root root   33 2009-04-25 08:34 /initrd.img -> boot/initrd.img-2.6.28-11-generic
lrwxrwxrwx 1 root root   33 2009-04-25 08:33 /initrd.img.old -> boot/initrd.img-2.6.27-11-generic

===== Some entries from /etc/fstab

# /dev/sda5
UUID=5dc6b6b2-d51a-4ba0-9d72-bf2e7b093901 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=ee81236c-bd4e-4533-be8d-6aa1b61df392 /oboot           ext2    noatime       0       2
# /dev/sdb1
UUID=e30be990-4184-4de2-81ce-e0b02a9dfae7 /boot		ext2    noatime	0       1
# /dev/sdb3
UUID=4f23dc42-ec6f-43d2-83b8-8f9659cf499a /media      ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=126b9123-3bfa-4a96-a86e-eab0545b76f7 none            swap    sw              0       0


All this seems consistent with what works when booting from hd0.  I've tried adding stuff from the menu.lst that fails to the one that works, and vice versa, but neither of these works when selecting what has been added.

Any ideas most welcome.  Thanks,
Fred

---

### Post by meierfra. on 2009-04-25
Use this in menu.lst

title Ubuntu 9.04, kernel 2.6.28-11-generic
[COLOR="Red"]uuid e30be990-4184-4de2-81ce-e0b02a9dfae7[/COLOR]
kernel /vmlinuz-2.6.28-11-generic [COLOR="Red"]root=UUID=5dc6b6b2-d51a-4ba0-9d72-bf2e7b093901[/COLOR] ro quiet splash
initrd /initrd.img-2.6.28-11-generic

---

### Post by fkrogh on 2009-04-25
Thank you, thank you, thank you!  All is now working.
Fred

---

### Post by meierfra. on 2009-04-25
> All is now working.
Great. 

> Thank you, thank you, thank you!
Your are welcome.

---

