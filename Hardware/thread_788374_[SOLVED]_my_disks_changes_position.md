---
title: "[SOLVED] my disks changes position"
date: 2008-05-09
forum: Hardware
---

### Post by malaTG on 2008-05-09
Hi everyone,

When I boot my computer sometimes my disks changes postion so that /dev/sda1 becomes /dev/sdb1 and so on....

I don't know if it matters if I have mixed IDE disks with SATA disks?

Anyway I would appreciate a solution to this problem...

Thx in advance

/Marcus

---

### Post by nick_h on 2008-05-11
This is nothing to be concerned about unless it causes a problem for you.

You can reference a drive by either UUID or LABEL instead of by device name.

Have a look at [How to fstab](http://ubuntuforums.org/showthread.php?&t=283131) for details.

To change a device label, look at [RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive).

---

### Post by malaTG on 2008-05-14
Hi,

First of all thank you for answering but I am not sure if we are talking about the same thing? Don you mean if I have external drives connected to my computer?

My problem is that I have 3 drives internally. Two IDE:s and one SATA. On one of the IDE:s I have my operating system. on the other IDE and the SATA drive I just store stuff. When I boot my computer linux sometimes sets the my disk as

sda = Operating system IDE
sdb = Other IDE
sdc = SATA drive

and sometimes it sets them the as

sda = SATA drive
sdb = Operating system IDE
sdc = Other ide

This creates a problem because when I write a mount text in my fstab sometimes the other IDE and the SATA drive doesn't get mounted. Here is the part of my fstab that sometimes become wrong

/dev/sdc1       /mnt/inspelningar   jfs   rw 0   0
/dev/sdb1       /mnt/intern_250GB   ext3  rw 0   0

How can I resolve this?

Thx in advance!

Marcus

---

### Post by nick_h on 2008-05-14
For internal drives I suggest you use UUID rather than LABEL or device name.  To find the UUID for your drives type:
```
ls -al /dev/disk/by-uuid/
```
Then edit your /etc/fstab and replace the device name (first column) with UUID=xxxxxxxxxx (where xxxxxxxxxx is the hex identifier listed in the ls command.)

You could also include a comment line to make it clear which drive you are mounting.

The UUID will not change until you put a new filesystem on the partition.

---

### Post by malaTG on 2008-05-15
Thank you very much nick! That did the trick

---

