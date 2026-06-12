---
title: "Assign Volume Label"
date: 2014-07-08
forum: Hardware
---

### Post by kakashi_12 on 2014-07-08
Ubuntu 14.04, ext4
I don't think I was given the option during install to give a Volume Label to the partitions. I would like to do so now.
I installed GParted and tried to do so, but the option is grayed out.
Any other ideas?

---

### Post by Bashing-om on 2014-07-08
kakashi_12; Hi !

The way I do it is from the command line with the 'tune2fs' tool:
```

sudo tune2fs -L {label} {devicename} 
example: sudo tune2fs -L "Raring" /dev/sda8

```
run terminal commands:
```

sudo blkid
sudo fdisk -lu

``` to be absolutely sure of the partitions.

[INDENT][INDENT]the geekiness in all of us
[/INDENT][/INDENT]

---

### Post by grumblebum2 on 2014-07-08
You can also use gparted from a live cd/usb as the partition won't be mounted.
Bashing-om's way would be how I would do it though.

---

### Post by kakashi_12 on 2014-07-08
Thank you both. I did it via Terminal.
Unfortunately I could not label my swap partition. Not a big deal though.
When I tried I got this....
"kakashi_12@Apevia:~$ sudo tune2fs -L "swap" /dev/sda2
tune2fs 1.42.9 (4-Feb-2014)
tune2fs: Bad magic number in super-block while trying to open /dev/sda2
Couldn't find valid filesystem superblock.
kakashi_12@Apevia:~$ "

---

### Post by Bashing-om on 2014-07-08
kakashi_12; a fact .

Swap has no file system imposed on it, and the system has a irrefutable 'label' "swap" on that partition.

As this matter is now concluded:
Please mark this thread solved;
 aides others seeking the solution,
 helps keep the forum clean and 
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]"Happy trails to you
[INDENT][INDENT][INDENT][INDENT]'til we meet again"[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kakashi_12 on 2014-07-08
just wanted to confirm that was the case with swap. thanks.
i'm on it.....

---

### Post by kakashi_12 on 2014-07-14
Actually, this isn't working.  It shows when I put that cmd in, butdoes not show volume label in windows and does not show in clonezilla. Clonezilla shows all othet labels which I've created with windows.

The only way I know which one it is in linux is cause it says ext4.

---

### Post by Bashing-om on 2014-07-14
kakashi_12; Well,

Now that just is not right.
Let's look at the present labels, then change the labels as desired.
Post back - between code tags - the outputs of terminal commands:
```

sudo blkid
sudo fdisk -lu

``` If the Window's system is versions late 7 or 8, then the partition scheme will require a different tool to look at that partitioning.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by kakashi_12 on 2014-07-14
```

/dev/sda1: LABEL="WindowsXP" UUID="02C48140C4813747" TYPE="ntfs" 
/dev/sda2: LABEL="Windows7" UUID="105A381C5A380150" TYPE="ntfs" 
/dev/sda3: LABEL="Server2008" UUID="84161FC8161FB9DE" TYPE="ntfs" 
/dev/sdb1: LABEL="Ubuntu" UUID="43d2ffbb-727c-4f52-b0eb-52e6fea4a793" TYPE="ext4" 
/dev/sdb2: UUID="e409a88f-af21-4659-8fbb-eca9f6fecc9d" TYPE="swap" 
/dev/sdc1: LABEL="UserData" UUID="EA14ABD814ABA653" TYPE="ntfs" 
/dev/sdh1: SEC_TYPE="msdos" LABEL="PublicZone" UUID="DA84-F6C3" TYPE="vfat" 
```

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x3d153d14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   206852939   103426438+   7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/sda2       206854144   514054143   153600000    7  HPFS/NTFS/exFAT
/dev/sda3       514054144   976771071   231358464    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00047b7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   585936895   292967424   83  Linux
/dev/sdb2       585936896   625141759    19602432   82  Linux swap / Solaris

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x59ca6226

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1250260991   625129472    7  HPFS/NTFS/exFAT

Disk /dev/sdh: 724 MB, 724566016 bytes
16 heads, 32 sectors/track, 2764 cylinders, total 1415168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *          32     1415167      707568    6  FAT16
```

Yes, I'm using Windows 7. But like I said I _also _use CloneZilla (which is Linux based). And I still don't see the label.

---

### Post by Bashing-om on 2014-07-14
kakashi_12; Hummm;

No fault found from the operating system's point of view. Partition labels, as you can see, are there.
As I do not have CloneZilla installed, and have no experience with the utility, I can not advise why it does not recognize the partition labels.
Others will have to advise in this instance.

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]othertimes I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kakashi_12 on 2014-07-14
would I damage the partition or OS (or would it be daring) if I used Windows Disk Management utility to create the volume label?

---

### Post by Bashing-om on 2014-07-14
kakashi_12; YUK !

Windows will not recognize a linux file system - unlike ubuntu deals with Windows. I would highly expect if Windows tools were applied that it would indeed break the ubuntu system.

I do suggest that you start a new thread with CloneZilla labeling as the theme, will gain the greater audience for this particular situation.
If that meets your approval, please mark this thread solved -> top of post -> thread tools.

Windows tools for Windows problems, 
[INDENT][INDENT][INDENT]ubuntu tools for ubuntu situations.[/INDENT][/INDENT][/INDENT]

---

