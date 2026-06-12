---
title: "Btrfs filesystem leaking free space?"
date: 2011-10-06
forum: Hardware
---

### Post by $p00ky on 2011-10-06
Dear all,

My free space is lower than my total space minus my used space, as shown by "df -h"'
```
root@ubuntu:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              16G  9.5G  1.8G  85% /media/cf55cf06-7622-4e8c-89d4-3ff3276a3a4e
```16-9.5=6.5, not 1.8!

I tried to use the resize2fs command, it does not work (both when mounted and not):
```
root@ubuntu:~# resize2fs /dev/sda5
resize2fs 1.41.14 (22-Dec-2010)
resize2fs: Device or resource busy while trying to open /dev/sda5
Couldn't find valid filesystem superblock.
```Then btrfsctl -r max'
```
root@ubuntu:~# btrfsctl -r max /dev/sda5
ioctl:: Inappropriate ioctl for device
```btrfs-show'
```
root@ubuntu:~# btrfs filesystem show /dev/sda5
failed to read /dev/sr0
Label: none  uuid: cf55cf06-7622-4e8c-89d4-3ff3276a3a4e
    Total devices 1 FS bytes used 9.02GB
    devid    1 size 15.32GB used 15.32GB path /dev/sda5

Btrfs Btrfs v0.19

```sync
```
root@ubuntu:~# btrfs filesystem sync /media/cf55cf06-7622-4e8c-89d4-3ff3276a3a4e
FSSync '/media/cf55cf06-7622-4e8c-89d4-3ff3276a3a4e'
```de
```
root@ubuntu:~# btrfs filesystem df /media/cf55cf06-7622-4e8c-89d4-3ff3276a3a4e
Data: total=10.29GB, used=8.57GB
System, DUP: total=8.00MB, used=4.00KB
System: total=4.00MB, used=0.00
Metadata, DUP: total=2.50GB, used=460.41MB
Metadata: total=8.00MB, used=0.00
```resize max
```
root@ubuntu:~# btrfs filesystem resize max /media/cf55cf06-7622-4e8c-89d4-3ff3276a3a4e
Resize '/media/cf55cf06-7622-4e8c-89d4-3ff3276a3a4e' of 'max'
ERROR: unable to resize '/media/cf55cf06-7622-4e8c-89d4-3ff3276a3a4e'

root@ubuntu:~# btrfs filesystem resize max /dev/sda5
Resize '/dev/sda5' of 'max'
ERROR: unable to resize '/dev/sda5'
```Any idea how to retrieve the 4.7G missing?

---

### Post by nox24 on 2011-10-20
Hi,

try this:

```
btrfs filesystem balance /media/cf55cf06-7622-4e8c-89d4-3ff3276a3a4e
```Hope I could help you. ;)

---

### Post by jmate24 on 2011-10-30
try ```
sudo btrfs filesystem defrag /dev/sda5
```

and make sure it is not mounted either.

---

### Post by jmate24 on 2011-10-30
but you have to be in a tty so type Ctrl+Alt+F2.

then sudo unmount /dev/sda5

---

