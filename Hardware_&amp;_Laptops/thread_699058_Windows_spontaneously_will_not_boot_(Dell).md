---
title: "Windows spontaneously will not boot (Dell)"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by jalexstark on 2008-02-17
Symptoms:

Windows XP Media would not boot on Dell Inspiron E1505.  Installation DVD would not boot without the hard-drive removed.  This started without apparent explanation.

Blue screen of death with "driver error" "STOP: 0x000000CA (0x00000001,...)"

Proximate cause unknown.  Forum postings suggest pressing of Media Direct button instead of power-on button.

Test:
parted / gparted complain of "overlapping partitions".  A Dell recovery partition has phantom duplicate.

Solution:
Do not delete files: full recovery possible.
(This one I tried with apparent success) Delete spurious copy of partition in fdisk, leaving, in our case, low-numbered FAT partition.  Adjust grub/menu.lst and grub-install.  Reboot and windows starts normally, with a safe-mode restart.  (Get expert help with this.)

Scenario:
Partition duplicate had apparently existed quite happily for some time.

Dell evidently included a "recovery" partition.

Resized and created partitions, installed Ubuntu.  Apparently bugs in fdisk / parted or whatever created a duplicate.

Used Ubuntu for a year.  Problem suddenly occurred.  Found fix largely by chance.  Applied as above.

Now parted (still) complains of overlapping partitions, but system works.

Most immediate known action was to install windows service pack.  This may not have been the actual cause of the boot problems.





#    Device Boot      Start         End      Blocks   Id  System
# /dev/sda1            8863        9123     2096451    c  W95 FAT32 (LBA)
# /dev/sda2   *           7        2291    18354262+   7  HPFS/NTFS
# /dev/sda3            2292        9123    54878040    f  W95 Ext'd (LBA)
# /dev/sda4            9124        9729     4867695   db  CP/M / CTOS / ...
# /dev/sda5            2292        3066     6225124+  83  Linux
# /dev/sda6            3067        3449     3076416   82  Linux swap / Solaris
# /dev/sda7            3450        4743    10393441+  83  Linux
# /dev/sda8            4744        8862    33085836    b  W95 FAT32




# Before fix-attempt
#    Device Boot      Start         End      Blocks   Id  System
# /dev/sda1            8863        9123     2096451    c  W95 FAT32 (LBA)
# /dev/sda2   *           7        2291    18354262+   7  HPFS/NTFS
# /dev/sda3            2292        9123    54878040    f  W95 Ext'd (LBA)
# /dev/sda4            9124        9729     4867695   db  CP/M / CTOS / ...
# /dev/sda5            8863        9123     2096451   dd  Unknown
# /dev/sda6            2292        3066     6225124+  83  Linux
# /dev/sda7            3067        3449     3076416   82  Linux swap / Solaris
# /dev/sda8            3450        4743    10393441+  83  Linux
# /dev/sda9            4744        8862    33085836    b  W95 FAT32

---

### Post by tgalati4 on 2008-02-17
I thought XP Media was hardcoded to Intel-based boards with ViiV technology.  It's basically XP Pro with 64-bit extensions that are used when showing video.  I wasn't aware that you could successfully load it on non-ViiV compliant hardware.

What was the original OS that was installed on this machine?

---

