---
title: "windows wont boot post ubuntu install"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by vikrant_me on 2009-05-10
I just installed ubuntu 9.04 on my usb hdd and am trying to get windows to boot of my other drive. But even adding the necessary entry in the grub it freezes at "Starting up ....."

fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25b4f467

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaeb9764b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          26      208813+  83  Linux
/dev/sdb2              27        2900    23085405    5  Extended
/dev/sdb5              27         288     2104483+  82  Linux swap / Solaris
/dev/sdb6             289        2900    20980858+  83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e29bbab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        5187    41664546    7  HPFS/NTFS
/dev/sdc2   *        5188       10409    41945715    7  HPFS/NTFS
/dev/sdc3           10410       10427      144585   83  Linux
/dev/sdc4           10428       13726    26499217+   5  Extended
/dev/sdc5           10428       13539    24997108+  83  Linux
/dev/sdc6           13540       13726     1502046   82  Linux swap / Solaris

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf8fba00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1          18      144553+  83  Linux
/dev/sdd2              19        1263    10000462+   5  Extended
/dev/sdd5              19         267     2000061   82  Linux swap / Solaris
/dev/sdd6             268        1263     8000338+  83  Linux

* My windows resides on /dev/sdc1 and my ubuntu is on  /dev/sdd 

My menu.lst 
title		ubuntu 9.04 (maxtor),kernel 2.6.28-11-generic
uuid		fe76a749-efd7-402e-acc6-f522d3c3fa40
kernel		/vmlinuz-2.6.28-11-generic root=UUID=a19a23e9-0edc-4f77-a2af-f0812410da62 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		ubuntu 9.04 (maxtor),kernel 2.6.28-11-generic (recovery mode)
uuid		fe76a749-efd7-402e-acc6-f522d3c3fa40
kernel		/vmlinuz-2.6.28-11-generic root=UUID=a19a23e9-0edc-4f77-a2af-f0812410da62 ro  single
initrd		/initrd.img-2.6.28-11-generic

title		ubuntu 9.04 (maxtor),memtest86+
uuid		fe76a749-efd7-402e-acc6-f522d3c3fa40
kernel		/memtest86+.bin
quiet

title 		windows

title 	        windows xp
root           (hd3,0)
makeactive
chainloader     +1

---

### Post by caljohnsmith on 2009-05-10
I think it would help to first get a clearer picture of your setup related to your Windows booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

John

---

