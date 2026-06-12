---
title: "Setting read-write option for mounted partition"
date: 2018-06-13
forum: Hardware
---

### Post by tomasyhy on 2018-06-13
I have a problem with mounted partition on ubuntu 18.04. Command 'mount' shows following line:
```
/dev/nvme0n1p3 on /media/xxxx/xxxxxxxxx type fuseblk (ro,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
```

I would like to set **rw **option for this partition. As I know I can do this by remount partition:
```
mount -o remount,rw /media/xxxxx
```

It works, but after reboot, it is signed as **ro. **How can I do this permanently especially if my partition is not listed in fstab?

---

### Post by deadflowr on 2018-06-13
If not in fstab how are you mounting it?

---

### Post by tomasyhy on 2018-06-14
I think it was mounted automatically. My Fstab file:
```
# /etc/fstab: staticfile system information.
#
# Use 'blkid' toprint the universally unique identifier for a
# device; this maybe used with UUID= as a more robust way to name devices
# that works even ifdisks are added and removed. See fstab(5).
#
# <file system><mount point>   <type>  <options>       <dump> <pass>
# / was on/dev/nvme0n1p4 during installation
UUID=25c0a93a-7b94-404d-ba33-a8812645b282/               ext4    errors=remount-ro 0       1
# /boot/efi was on/dev/nvme0n1p1 during installation
UUID=70D3-8A7F /boot/efi       vfat    umask=0077      0       1
/swapfile                                none            swap    sw              0      0
```

---

### Post by gabe. on 2018-06-19
Hi.
Is nvme0n1p3, by any chance, a windows ntfs partition?

---

### Post by deadflowr on 2018-06-19
[s]The nvme0n1p3 partition is the /boot/efi partition.
Or at least that's what it says it is in fstab.
And it's marked as formatted vfat.

Unless the description in fstab is wrong...[/s]


What does 
```
sudo blkid
```
and/or
```
sudo parted -l
```
show?

The blkid will output the UUIDs of the associated partition which we can match against what fstab has.
The parted -l will show disk and partition layouts.
For a little clarity.

---

### Post by gabe. on 2018-06-20
Isn't nvme0n1p3 mounted on /media according to his mount output and and nvme0n1p1 on /boot/efi as stated in his fstab?

---

### Post by deadflowr on 2018-06-20
> **gabe. said:**
> Isn't nvme0n1p3 mounted on /media according to his mount output and and nvme0n1p1 on /boot/efi as stated in his fstab?

indeed.
Nevermind my last post on that. I was probably tired.
Though we still need to outputs from the commands posted.

---

### Post by tomasyhy on 2018-06-28
Thanks for replays. Yes, it is windows ntfs partition. What is strange here is that sometimes after reboot I can write on this partition, sometimes not :o

sudo blkid:
```
/dev/loop0: TYPE="squashfs"/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/nvme0n1: PTUUID="da03d99a-9f92-490b-97d6-0fce17b3b360" PTTYPE="gpt"
/dev/nvme0n1p1: UUID="70D3-8A7F" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="85dcd01b-d914-4f73-b4b9-6d7acbf1d875"
/dev/nvme0n1p2: UUID="bd8f85a5-c9e9-439a-b55c-7446c1c84822" TYPE="ext4" PARTLABEL="Microsoft reserved partition" PARTUUID="622166a9-54bf-49d9-b86d-b958e4699f00"
/dev/nvme0n1p3: UUID="A23EB8BB3EB88A35" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="68d3649d-8800-4947-9a0c-c0eb7205a1f1"
/dev/nvme0n1p4: UUID="FC26FEF126FEAC30" TYPE="ntfs" PARTUUID="ddd01368-e2b7-4ee1-a460-e169d7a38e98"
/dev/nvme0n1p5: UUID="25c0a93a-7b94-404d-ba33-a8812645b282" TYPE="ext4" PARTLABEL="Basic data partition" PARTUUID="76aa10cb-fb37-4c8c-9ce8-38985b09b271"
/dev/sda1: LABEL="Storage" UUID="741B15937A99CA86" TYPE="ntfs" PTTYPE="dos" PARTUUID="c3bcf324-01"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/loop18: TYPE="squashfs"
/dev/loop19: TYPE="squashfs"
/dev/loop20: TYPE="squashfs"
/dev/loop21: TYPE="squashfs"
/dev/loop22: TYPE="squashfs"
/dev/loop23: TYPE="squashfs"
/dev/loop24: TYPE="squashfs"
/dev/loop25: TYPE="squashfs"
/dev/loop26: TYPE="squashfs"
/dev/loop27: TYPE="squashfs"
/dev/loop28: TYPE="squashfs"
/dev/loop29: TYPE="squashfs"


```

sudo parted -l
```
Model: ATA WDC WD10SPCX-24H (scsi)Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs




Model: NVMe Device (nvme)
Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  538MB  537MB   fat32        EFI System Partition          boot, esp
 2      538MB   555MB  16,8MB  ext4         Microsoft reserved partition  msftres
 3      555MB   314GB  314GB   ntfs         Basic data partition          msftdata
 4      314GB   315GB  823MB   ntfs                                       hidden, diag
 5      315GB   512GB  197GB   ext4         Basic data partition          msftdata



```

---

### Post by gpaunescu2 on 2018-07-03
Just disable hibernate in windows and it will work.

---

