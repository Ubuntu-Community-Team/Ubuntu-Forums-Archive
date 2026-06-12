---
title: "2nd Disc Mounts But Thinks It's Filesystem"
date: 2008-10-29
forum: General Help
---

### Post by joey-elijah on 2008-10-29
A curious issues here, my second HD - 160gb - mounts, but when i go into it it has my 'linux filesystem' files on it; i.e 'home', 'usr' etc etc.

Obviously it's mounting but linked to my 'linux' harddrive' right? When i go to the 'properties' of the 2nd drive it says, quite clearly, ~160GB free.. Which is right since there's nothing on it.

How can i fix this? 

fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x682a8121

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156286976    b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9730    78148604   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7087ef7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

```If i try to unmount it via 'umount' i get told the following: -
```
umount: /: device is busy.         (In some cases useful info about processes that use          the device is found by lsof(8) or fuser(1)) umount: /media/disk: not mounted
```Should i post my etc/fstab? 

Many thanks!

---

### Post by geirha on 2008-10-29
Yes, post your /etc/fstab.

---

### Post by joey-elijah on 2008-10-29
here's etc/fstab

```
proc            /proc           proc        defaults    0   0
UUID=48F6-7247     /               ext3        defaults,errors=remount-ro,relatime    0   1
UUID=08417625-7107-48f0-a27c-e4b1e4f2e737       /media/drv0       ntfs-3g         defaults      0   0
/mnt/4608Mb.swap  none  swap  sw  0 0
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
```

---

### Post by geirha on 2008-10-29
```
UUID=48F6-7247     /               ext3        defaults,errors=remount-ro,relatime    0   1
```
That UUID looks like the UUID of a FAT filesystem.
run ```
sudo blkid
``` to get the UUID of all filesystems, and replace the UUID of the above fstab-line with the correct UUID for your linux partition.

Then add a new line for your fat-partition to mount it somewhere else. E.g.:
```
UUID=48F6-7247 /media/*something* vfat defaults,uid=*yourusername*,umask=002,fmask=113 0 0
```

And remember to create the mount point you choose (/media/*something* in the example above.
```
sudo mkdir /media/*something*
```

---

### Post by joey-elijah on 2008-10-29
Ahh all done. The 160GB is showing up in places now, but can't be mounted. i assume a reeboot will fix that.

Thanks!

---

### Post by joey-elijah on 2008-10-30
Still got issues.

Although the 160GB drive now shows up in Places, it won't mount. From 'places' i don't have sufficient 'privileges' and from the command line it doesn't exist.

```
proc            /proc           proc        defaults    0   0
UUID=08417625-7107-48f0-a27c-e4b1e4f2e737     /               ext3        defaults,errors=remount-ro,relatime    0   1
UUID=08417625-7107-48f0-a27c-e4b1e4f2e737       /media/drv0       ntfs-3g         defaults      0   0
/mnt/4608Mb.swap  none  swap  sw  0 0
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
UUID=4908-E7F9 /media/extradisk vfat defaults,uid=yourusername,umask=002,fmask=113 0 0
```

blkid gives the correct UUID for it: -

```
/dev/sda1: UUID="08417625-7107-48f0-a27c-e4b1e4f2e737" TYPE="ext3" 
/dev/sdb1: UUID="4908-E7F9" TYPE="vfat" 
/dev/sdc1: UUID="5D5165E912592A10" LABEL="ExTeRnAl DriiiiVe" TYPE="ntfs" 
/dev/sdb2: UUID="48E2-4D5A" TYPE="vfat" 
/dev/sda2: UUID="48E2-4D5A" TYPE="vfat" 

```

Any ideas?

---

### Post by geirha on 2008-10-30
Seems the UUID of the ntfs filesystem is wrong too. Should fix that as well.

On the line for your vfat filesystem, the word *yourusername* should be replaced by your username, or else you won't have write access. Alternatively (or in addition) you can add gid=*agroup* to the list of options to give all members of the group *agroup* write access to it. 

Also, did you create the mount-point /media/extradisk? ```
sudo mkdir /media/extradisk
``` after that, try mounting it manually ```
sudo mount /media/extradisk
```

A bit odd that blkid lists /dev/sda2 and /dev/sdb2 btw. They don't show in the output of fdisk -l ...

---

