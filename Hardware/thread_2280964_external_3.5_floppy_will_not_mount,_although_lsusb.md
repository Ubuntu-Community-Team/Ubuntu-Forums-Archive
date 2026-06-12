---
title: "external 3.5 floppy will not mount, although lsusb finds it"
date: 2015-06-03
forum: Hardware
---

### Post by ikman on 2015-06-03
Hi, I am trying to read some old files from a 3.5-inch floppy disk that has been inserted into an external USB connected Toshiba PA3109U-1FDD 
My Ubuntu  OS finds the disk as a TEAC but before mounting gives this error message:

Error mounting /dev/sdb at /media/ikmguy/disk1: Command-line `mount -t "auto" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb" "/media/ikmguy/disk1"' exited with non-zero exit status 32: mount: /dev/sdb: can't read superblock
 (udisks-error-quark, 0)

From my desktop the Applications -> Accessories -> Disks   dialog window shows the floppy to be a TEAC TEAC FD-05PUB as /dev/sdb

lsusb command also finds the device as:
Bus 003 Device 006: ID 0644:0000 TEAC Corp. Floppy

SO I think I must be close to being able to read the files but when I try a manual mount command as root such as
```
mount -t auto /dev/usb /media/floppy
```
I get the following error:
```
mount: /dev/usb is not a block device
```

What should I try next?

Thank you,

---

### Post by dino99 on 2015-06-03
looks like a formatting issue, or a corrupted block; so boot a gparted live usb/cd to try reading the diskette, and maybe rebuild its table (gparted menu option) which is safe for the data

note: you might use the system mounted name into /media/xxxxx

---

