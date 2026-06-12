---
title: "Seagate External USB/Firewire Drive- Label &amp; UUID Issue"
date: 2008-11-25
forum: Hardware
---

### Post by Magneto on 2008-11-25
I have a Seagate 400gb ST3400601CBRK External USB/Firewire drive. For some reason I can pull UUID and Label's off it using blkid 
```
/dev/sdc1: LABEL="SEA1" UUID="0000-0F12" TYPE="vfat" 
```
but when trying to use them in fstab and trying a mount -a it always comes back with an error 
```
mount: special device /dev/disk/by-label/SEA1 does not exist
```
and the same for when specifying the UUID```

mount: special device /dev/disk/by-uuid/0000-0F12 does not exist
```

I can mount it by device id but I'm wondering why it can't be recognized by its UUID or Label????????? Any of you  guys run into something similar? (nothing is mispelled or out of case etc)
I haven't tried this in firewire mode since it works fine now as a USB drive.

---

### Post by taurus on 2008-11-25
Can you post your /etc/fstab?

```
cat /etc/fstab
```

---

### Post by Magneto on 2008-11-26
it wont work with this 
```
LABEL=SEA1	/data2		vfat	defaults	0	0	
```

or with the  UUID=0000-0F12 instead of "LABEL=*"
 
The system won't recognize the UUID or Label of the external drive when attempting to mount it. The system does recognize the label and uuid fine via blkid  

```
/dev/sda1: UUID="1EC0A791C0A76DA9" LABEL="Data3" TYPE="ntfs" 
/dev/sdb1: UUID="666CC6836CC64E0D" TYPE="ntfs" 
/dev/sdb2: UUID="a5cf611a-3711-4e7b-b0c3-f3c77d138882" TYPE="reiserfs" 
/dev/sdb3: UUID="532E44FECBF350A4" LABEL="Data1" TYPE="ntfs" 
/dev/sdc1: LABEL="SEA1" UUID="0000-0F12" TYPE="vfat" 
```

Visible here by ID

ls /dev/disk/by-id -lah```

total 0
drwxr-xr-x 2 root root 320 2008-11-25 19:36 .
drwxr-xr-x 6 root root 120 2008-11-25 14:22 ..
lrwxrwxrwx 1 root root   9 2008-11-25 14:22 ata-ST3200822A_4LJ0K71T -> ../../sda
lrwxrwxrwx 1 root root  10 2008-11-25 14:22 ata-ST3200822A_4LJ0K71T-part1 -> ../../sda1
lrwxrwxrwx 1 root root   9 2008-11-25 14:22 ata-ST3500320AS_9QM5X62C -> ../../sdb
lrwxrwxrwx 1 root root  10 2008-11-25 14:22 ata-ST3500320AS_9QM5X62C-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-11-25 14:22 ata-ST3500320AS_9QM5X62C-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  10 2008-11-25 14:22 ata-ST3500320AS_9QM5X62C-part3 -> ../../sdb3
lrwxrwxrwx 1 root root   9 2008-11-25 14:22 scsi-1ATA_ST3200822A_4LJ0K71T -> ../../sda
lrwxrwxrwx 1 root root  10 2008-11-25 14:22 scsi-1ATA_ST3200822A_4LJ0K71T-part1 -> ../../sda1
lrwxrwxrwx 1 root root   9 2008-11-25 14:22 scsi-1ATA_ST3500320AS_9QM5X62C -> ../../sdb
lrwxrwxrwx 1 root root  10 2008-11-25 14:22 scsi-1ATA_ST3500320AS_9QM5X62C-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-11-25 14:22 scsi-1ATA_ST3500320AS_9QM5X62C-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  10 2008-11-25 14:22 scsi-1ATA_ST3500320AS_9QM5X62C-part3 -> ../../sdb3
lrwxrwxrwx 1 root root   9 2008-11-25 19:36 usb-ST340063_3A_354E463248563154-0:0 -> ../../sdc
lrwxrwxrwx 1 root root  10 2008-11-25 19:36 usb-ST340063_3A_354E463248563154-0:0-part1 -> ../../sdc1

```

Disappears by label

 ls /dev/disk/by-label -lah
```
total 0
drwxr-xr-x 2 root root  80 2008-11-25 14:22 .
drwxr-xr-x 6 root root 120 2008-11-25 14:22 ..
lrwxrwxrwx 1 root root  10 2008-11-25 14:22 Data1 -> ../../sdb3
lrwxrwxrwx 1 root root  10 2008-11-25 14:22 Data3 -> ../../sda1

```



Doesn't show up here either

ls /dev/disk/by-uuid -lah
```
total 0
drwxr-xr-x 2 root root 120 2008-11-25 14:22 .
drwxr-xr-x 6 root root 120 2008-11-25 14:22 ..
lrwxrwxrwx 1 root root  10 2008-11-25 14:22 1EC0A791C0A76DA9 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-11-25 14:22 532E44FECBF350A4 -> ../../sdb3
lrwxrwxrwx 1 root root  10 2008-11-25 14:22 666CC6836CC64E0D -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-11-25 14:22 a5cf611a-3711-4e7b-b0c3-f3c77d138882 -> ../../sdb2

```

I just answered my own question as to why it fails. 


There are no links in /dev/disk/by-label or by-uuid for my usb drive. Is this a HAL issue or kernel? I can create them but I really want to know why it isnt working.

*********

edit
*****
Im pretty sure it has something to do with it being configured as a scsi drive or a failure/bug/weirdness in a kernel module. 
I was able to set it to mount via /dev/disk/by-path. That should prevent an issues in case its position as sdc changes.

FYI for anyone with a similar issue - this is the line I used in fstab.
```
/dev/disk/by-path/pci-0000:00:1d.7-usb-0:4:1.0-scsi-0:0:0:0-part1       /data2          vfat    defaults        0       0
```

---

### Post by Magneto on 2008-11-26
i see now this is a udev issue

I think this is the problem [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/102097/comments/24](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/102097/comments/24)

external usb drive with a fat32 partition over 250gb in size causes some error where udev won't create a symlink for by-uuid or by-label

---

