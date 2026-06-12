---
title: "Ubuntu doesn't see swap partition"
date: 2008-07-27
forum: General Help
---

### Post by notesetter on 2008-07-27
I just upgraded my notebook's RAM from 256 MB to 1 GB. Accordingly, I edited resized my swap partition so that it is now 2 GB instead of 512 MB. To do this, I had to shrink a FAT32 data partition in order to make room for the extra swap space. I used the GPartED LiveCD to resize the partitions.

The problem is, Ubuntu now doesn't see the swap partition at all. Do I need to set a new mount point for the swap partition? If that's the issue, how do I do it?

Is this a symptom of a different problem entirely?

Thanks,

Dave

---

### Post by Mister.Vash on 2008-07-27
post the contents of your fstab file
cat /etc/fstab

and the output of sudo fdisk -l

The will list how you are configured to mount the drives and the partition table

---

### Post by notesetter on 2008-07-27
Thank you.

> post the contents of your fstab file
cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=1614f97a-b3be-4b80-8233-710247963536 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda5
UUID=07FE-A522  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=f2ac9523-1315-4012-affd-2adc61150a74 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

> and the output of sudo fdisk -l

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae32ae32

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3040    24418768+   7  HPFS/NTFS
/dev/hda2            3041        8389    42965842+  83  Linux
/dev/hda3            8390        9729    10763550    5  Extended
/dev/hda5            8390        9469     8675068+   b  W95 FAT32
/dev/hda6            9470        9729     2088418+  82  Linux swap / Solaris
```

~D

---

### Post by Mister.Vash on 2008-07-27
can you post the output of
sudo blkid


so we can see if matches
the fdisk indcates that /dev/hda6 is your swap
/dev/hda6            9470        9729     2088418+  82  Linux swap / Solaris

so we want to see if the output from blkid matches for /dev/hda6
UUID=f2ac9523-1315-4012-affd-2adc61150a74 none            swap    sw              0       0

---

### Post by notesetter on 2008-07-28
> can you post the output of
sudo blkid

```
/dev/hda1: UUID="445661E80706EF78" TYPE="ntfs" 
/dev/hda2: UUID="1614f97a-b3be-4b80-8233-710247963536" TYPE="ext3" 
/dev/hda5: UUID="07FE-A522" TYPE="vfat" 
/dev/hda6: TYPE="swap" LABEL="ID_FS_USAGE=oth" UUID="9fbed646-2dcb-4c79-8981-f5b8cad06daf" 

```

---

### Post by Mister.Vash on 2008-07-28
ok, it looks like the partition tool changed it

what you will want to do is edit your fstab file so it has the correct uuid of the swap file

to do this, do the follow

```
cd /etc
```

!MAKE a backup copy of the current fstab!
```
sudo cp fstab fstab.backup
```

use gedit or whatever editor you like
```
sudo gedit fstab
```

the replace this line:
UUID=f2ac9523-1315-4012-affd-2adc61150a74 none swap sw 0 0

with:
UUID=9fbed646-2dcb-4c79-8981-f5b8cad06daf none swap sw 0 0

then restart and make sure it comes up as normal

---

### Post by notesetter on 2008-07-28
Okay,

So, in simple terms, I asked Ubuntu to tell me the new uuid of the newly resized swap partition was (which it politely did), then edited the file that Ubuntu uses in order to refer to that partition when needed with the updated uuid information.

Linux is cool.

Everything checks out. Sysinfo now tells me that I'm using 0% of my 2.0 GB swap partition.

Thanks,

~D

---

