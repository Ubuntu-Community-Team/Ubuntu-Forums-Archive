---
title: "xp partition with bad name /pdfprefl"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by koho on 2006-12-19
Hi everybody, there's something strange with my FAT32 win partition.
Ubuntu has recognize it correctly and it is displayed on my Desktop like a hard drive (and this is ok) but its name is </pdfprefl (with the </)
What does this mean?
I cannot figure how to change it.
If I look in "Places>Computer" that partition is just icon without a name.
However I can see and use the files contained into it.
What's wrong?
Where can I change what and how to show on my Desktop?

Thank you

koho

---

### Post by xyz on 2006-12-19
Hi,
Please post the outputs of:
```
sudo fdisk -lu

and

cat /etc/fstab
```
Thx.

---

### Post by koho on 2006-12-19
```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    24579449    12289693+   c  W95 FAT32 (LBA)
/dev/hda2        24579450    25623674      522112+  82  Linux swap / Solaris
/dev/hda3        25623675   117210239    45793282+  83  Linux

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=807c5f90-6212-46e0-bf06-ecb545673cbf /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=B456-FDA3  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=6f816e1d-d165-47cc-ba3d-60e894009f4d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

Freshly installed Ubuntu 6.10
thank you
koho

---

### Post by xyz on 2006-12-19
Hi koho,
It seems you need:
[Mtools is a collection of utilities to access MS-DOS disks from Unix without mounting them]("http://mtools.linux.lu/")
It should be useful to achieve your goal under Ubuntu. I checked...it is also available in Synaptic:
> Tools for manipulating MSDOS files
Mtools is a collection of utilities to access MS-DOS disks from Unix
without mounting them. It supports Win'95 style long file names, OS/2
Xdf disks, ZIP/JAZ disks and 2m disks (store up to 1992kB on a high
density 3 1/2 disk).

Also included in this package are commands to eject and manipulate
the write/password protection control of Zip disks.
It seems these strange partition names identfy your partition instead of just designating it by name (for instance hda3)

You can also change that partition name booting into Windows....
Let me know! Good luck to you.

---

### Post by koho on 2006-12-19
thank you, let me try..

koho

---

### Post by koho on 2006-12-19
I had a look at mtools but I think the problem is not there.
I need to know which program handles the hard disk's icons on the desktop and I have to look inside its config file and understand why my fat partition has this strange name or no name.

any clues?

thank you

koho

---

### Post by waffen on 2006-12-19
Hi,

I have the same problem, only with the FAT32 partition, because the NTFS appears fine.

This problem appear in my old :-D  Dapper and right now in my Edgy. In the past that correct when I upgrade to Edgy.

Any idea?

---

### Post by koho on 2006-12-21
now the problem has changed.. Xp refuses to load and asks to be reinstalled.. maybe it's a divine sign? ;) 

we'll see...

koho

---

### Post by xyz on 2006-12-22
> **koho said:**
> now the problem has changed.. Xp refuses to load and asks to be reinstalled.. maybe it's a divine sign? ;) 

we'll see...

koho
Hi koho,
Can you see GRUB...I mean can you still choose (with arrows) between Ubuntu or Windows?

---

### Post by koho on 2006-12-22
Magically win stopped to work so I reinstalled It.
I had to re-run grub setup (tons of guides available on the forum) and now I have a fresh win copy.
Now the problem has changed again.. No xp drive on desktop..
maybe because this time I've chosen ntfs instead of fat.
Let me work around It..

ciao

---

### Post by koho on 2006-12-22
Following a tutorial now I automount xp partition on boot but It is not shown on Desktop.
That's ok for me.
The strange </pdfprefl problem still remains open, maybe renaming the partition could help but now it's too late for me, **waffen** you can experiment if renaming the partition under win can help.

Thank you all for your help
Merry Christmas

koho

---

