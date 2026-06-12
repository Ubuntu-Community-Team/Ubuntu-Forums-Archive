---
title: "Aspire one_storage_expansion"
date: 2009-02-07
forum: Hardware
---

### Post by mynydd on 2009-02-07
I had linpus os on the 'one', I inserted a 8GB sd card into the storage expansion slot and it got set up for Linpus.
I am now running Ubuntu 8.10, and the sd card has 2.6GB of files from Linpus that I cannot delete because I am not 'the owner'. I cannot change the permissions either. I hope I can do it through the terminal.............can anyone help with the code?

---

### Post by taurus on 2009-02-07
```
sudo rm filename
```

---

### Post by mynydd on 2009-02-07
> **taurus said:**
> ```
sudo rm filename
```

Thanks for the quick response but I need some more help.
The sd card is /media/disk so I entrered in the terminal sudo rm /media/disk/bin (bin being one of the folders) I got 'Is a directory'. So what did I do wrong?
Actually I cannot create a new folder or save to any of the 8GB drive!

---

### Post by taurus on 2009-02-07
If you want to delete /media/disk/bin and everything in it. then you would run

```
sudo rm -rf /media/disk/bin
```
What filesystem is your 8GB drive?

```
sudo fdisk -l
```

---

### Post by mynydd on 2009-02-07
> **taurus said:**
> If you want to delete /media/disk/bin and everything in it. then you would run

```
sudo rm -rf /media/disk/bin
```
What filesystem is your 8GB drive?

```
sudo fdisk -l
```

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000181e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/sdb: 8019 MB, 8019509248 bytes
247 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Disk identifier: 0x000da3c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1022     7825423    b  W95 FAT32

---

### Post by taurus on 2009-02-07
Try remounting it with

```
cd
sudo umount /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
ls -la /media/sdb1
```
Now see if you can write or delete stuff in /media/sdb1.  Don't forget to _unmount_ it first before you unplug it.

```
sudo umount /media/sdb1
```

---

### Post by mynydd on 2009-02-07
mynydd@mynydd-netbook:~$ cd
mynydd@mynydd-netbook:~$ sudo umount /dev/sdb1
umount: /dev/sdb1: not found
mynydd@mynydd-netbook:~$ sudo mkdir /media/sdb1
mkdir: cannot create directory `/media/sdb1': File exists
mynydd@mynydd-netbook:~$ sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
mount: special device /dev/sdb1 does not exist
mynydd@mynydd-netbook:~$ ls -la /media/sdb1


Plus when I unmount it I can then see cdrom 0, cdrom 1, sdb1

---

### Post by taurus on 2009-02-07
Did you have the drive plugged in when you ran those commands from a terminal?

---

### Post by mynydd on 2009-02-07
Yep.

---

### Post by mynydd on 2009-02-07
I have redone : sudo fdisk -l


Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000181e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris
mynydd@mynydd-netbook:~$

---

### Post by taurus on 2009-02-07
> **mynydd said:**
> I have redone : sudo fdisk -l


Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000181e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris
mynydd@mynydd-netbook:~$

As you can see from your output, that drive didn't show up.  Unplug it and then plug it back in and run that command, sudo fdisk -l, again.  Otherwise, post the output of this new one with the your sd plugged in.

```
dmesg | tail
```

---

### Post by mynydd on 2009-02-08
mynydd@mynydd-netbook:~$ dmesg | tail
[  102.173640] EXT3 FS on mmcblk0p1, internal journal
[  102.175154] EXT3-fs: mounted filesystem with ordered data mode.
[  111.736298] PPP generic driver version 2.4.2
[  112.956506] NET: Registered protocol family 10
[  112.958935] lo: Disabled Privacy Extensions
[  115.441510] PPP BSD Compression module registered
[  116.537983] PPP Deflate Compression module registered
[  123.788030] eth0: no IPv6 routers present
[  198.617667] type=1503 audit(1234091178.117:5): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB0" pid=6522 profile="/usr/sbin/cupsd"
[  198.617738] type=1503 audit(1234091178.117:6): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB1" pid=6522 profile="/usr/sbin/cupsd"
mynydd@mynydd-netbook:~$ 

I also ran the list command again and got the same result. But the sd card is there and on my dektop. But still can't write files or create folders on it.

---

