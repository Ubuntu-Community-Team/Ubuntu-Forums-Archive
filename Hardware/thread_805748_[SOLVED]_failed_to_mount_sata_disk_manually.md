---
title: "[SOLVED] failed to mount sata disk manually"
date: 2008-05-24
forum: Hardware
---

### Post by ikki_72 on 2008-05-24
Note: once i tried setting up LVM with this disk but i kinda gave up then it couldn't be booted up so i did fresh install. This disk is not the main i use for installation, simply want to use it to store data.

I tried to mount it:
```
umarzuki@lalaland:~$ sudo mount /dev/sda1 simpan/
mount: unknown filesystem type 'LVM2_member'

```
i suspected it was caused by the partition table, so i try to wipe it
```
umarzuki@lalaland:~$ sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00757354 s, 67.6 kB/s

```
then the i got same error when i tried to mount it..what could cause this? How would i be able to mount this hardisk?

---

### Post by sisco311 on 2008-05-24
> **ikki_72 said:**
> Note: once i tried setting up LVM with this disk but i kinda gave up then it couldn't be booted up so i did fresh install. This disk is not the main i use for installation, simply want to use it to store data.

I tried to mount it:
```
umarzuki@lalaland:~$ sudo mount /dev/sda1 simpan/
mount: unknown filesystem type 'LVM2_member'

```i suspected it was caused by the partition table, so i try to wipe it
```
umarzuki@lalaland:~$ sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00757354 s, 67.6 kB/s

```then the i got same error when i tried to mount it..what could cause this? How would i be able to mount this hardisk?
Please post the output of:
```
sudo fdisk -l
```

---

### Post by ikki_72 on 2008-05-24
> **sisco311 said:**
> Please post the output of:
```
sudo fdisk -l
```

here
```
umarzuki@lalaland:~/Desktop$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4787    38451546   83  Linux
/dev/sda2            4788        4998     1694857+   5  Extended
/dev/sda5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```

---

### Post by cdtech on 2008-05-24
With LVM:

You don't mount an "LVM" partition the same way you mount a regular partition

```
pvs
```
this will list your volume groups
like this:
/dev/hda2 VolGroup01
/dev/hdb2 VolGroup00

```
lvdisplay /dev/VolGroup01
```
this will show the lv name needed to mount

mount /dev/VolGroup00/LogVol00 /tmp/mnt (or whatever your home mount point in that volume is)

Hope this helps.....

---

### Post by ikki_72 on 2008-05-24
```
umarzuki@lalaland:~/Desktop$ sudo lvdisplay /dev/VolGroup01
  Volume group "VolGroup01" not found
umarzuki@lalaland:~/Desktop$ sudo lvdisplay
  No volume groups found

```
what do i do then?

oh my god! maybe it's in my main hardisk...looks like i have to wipe the partition table then, do a fresh install..

---

### Post by cdtech on 2008-05-24
Are you still trying to setup the LVM?

Did you type pvm?

---

### Post by ikki_72 on 2008-05-24
no...i'm not going to do lvm anymore (actually last incident freaked me out)

---

### Post by cdtech on 2008-05-24
LOL!

OK, gotcha....

---

### Post by ikki_72 on 2008-05-24
but the problem is..even after i did what i said above, the error still produced.
```
umarzuki@lalaland:~$ sudo mount /dev/sda1 disk/
mount: unknown filesystem type 'LVM2_member'

```
how do i rid any info about lvm?

---

### Post by ikki_72 on 2008-05-24
i add another info
```
umarzuki@lalaland:~$ vgdisplay 
  No volume groups found
umarzuki@lalaland:~$ lvdisplay 
  No volume groups found
umarzuki@lalaland:~$ lvscan
  No volume groups found
umarzuki@lalaland:~$ lvmdiskscan 
  0 disks
  0 partitions
  0 LVM physical volume whole disks
  0 LVM physical volumes

```
what i want is to have **sda1** mounted on **/home/umarzuki/disk**

---

### Post by ikki_72 on 2008-07-06
i simply wite zero bits onto that hardisk which in effect wiped every single data on it with```
sudo dd if=/dev/zero of=/dev/sdb1
```then i prepare new filesystem for it```
sudo mkfs.ext3 /dev/sdb1
```after that, it can be mounted again

---

