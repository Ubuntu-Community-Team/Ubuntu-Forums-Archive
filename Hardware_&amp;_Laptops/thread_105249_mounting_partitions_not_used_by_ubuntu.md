---
title: "mounting partitions not used by ubuntu"
date: 2005-12-18
forum: Hardware &amp; Laptops
---

### Post by robin_egenes on 2005-12-18
I have Ubuntu 5.04 booting from hda and Mandrake 10.1 booting from floppy.
 I would like to access Mandrake data from Ubuntu and vice versa.
Any help would be appreciated. Thanks.

Here is fdisk report on hda:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *             1        2560    20563168+  83  Linux
/dev/hda2            2561        9729    57584992+    5  Extended
/dev/hda5            2561        3324      6136798+  83  Linux
/dev/hda6            9400        9729      2650693+  82  Linux swap / Solaris
/dev/hda7            3325        3464      1124518+  82  Linux swap / Solaris
/dev/hda8            3465        6023     20555136    83  Linux

Partition table entries are not in disk order

I think it just that I don't understand the mount process as yet.

---

### Post by aysiu on 2005-12-18
Can you also post the output of these two commands? ```
df -h
cat /etc/fstab
```

---

### Post by robin_egenes on 2005-12-18
Thank you very much for answering so quickly. I have been 'away' for a while and didn't get to answer till now.

The output you suggested is below:

me@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              20G  3.7G   15G  20% /
tmpfs                 443M     0  443M   0% /dev/shm
df: `/.dev': No such file or directory
none                  5.0M  2.8M  2.3M  56% /dev
/dev/sda1             125M  111M   14M  90% /media/usbdisk
/dev/hdc1             1.9G  1.3G  636M  67% /home/me/windisk
/dev/fd0              1.4M  871K  553K  62% /home/me/floppy

me@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
me@ubuntu:~$

'windisk' and 'floppy' directories I am trying out mount commands and got help on the windows drive at dalnet #ubuntu but got no answer to this question.

---

