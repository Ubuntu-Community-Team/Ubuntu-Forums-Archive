---
title: "Problem creating partition with Disk Space after 4tb"
date: 2008-10-02
forum: Hardware
---

### Post by jcustenborder on 2008-10-02
Hello all, 

I'm having some issues with creating a partition with my Hardy box. I have a raid controller with 8x1tb drives in RAID 6 presenting a single disk to the OS. I have been able to easily create the first partitions which are 2TB each. Fdisk will not create the final partition. parted will create it but the partition table is not readable after that. Gparted gives an interesting error message which I added in a screenshot.  My kernel is 2.6.26.3 x64. What am I doing wrong? Thanks for the assistance in advance.  

Output from fdisk trying to create the partition. 
```

Command (m for help): p

Disk /dev/sda: 6000.7 GB, 6000740401152 bytes
255 heads, 63 sectors/track, 729548 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ac932

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243153  1953126441    7  HPFS/NTFS
/dev/sda2          243154      486365  1953600390    7  HPFS/NTFS

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 3
No free sectors available

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
e
Partition number (1-4): 3
No free sectors available

Command (m for help):


```

```

GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print

Disk /dev/sda: 6001GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2000GB  2000GB  primary
 2      2000GB  4000GB  2000GB  primary

(parted)

```

---

### Post by nixscripter on 2008-10-03
Looks like the offset of a partition is flowing over the DOS partition table's offset. Try creating an extended partition instead?

---

### Post by jcustenborder on 2008-10-03
Thanks for the response! I tried creating it as an extended partition using fdisk. It errored out as well saying "No free sectors available"  The example output is in my first port. It just does the same thing as a primary partition. Here is the output of parted. It also ate the partition table again and cannot read it. I have to restore it each time with sfdisk. 

```

$ sudo sfdisk /dev/sda < sdb.fixed.txt
Checking that no-one is using this disk right now ...
OK

Disk /dev/sda: 729548 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

sfdisk: ERROR: sector 3518486429 does not have an msdos signature
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+ 243152  243153- 1953126441    7  HPFS/NTFS
/dev/sda2     243153  486364  243212  1953600390    7  HPFS/NTFS
/dev/sda3     219015+ 462198- 243183  1953367447+   f  W95 Ext'd (LBA)
/dev/sda4          0       -       0          0    0  Empty
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63 3906252944 3906252882   7  HPFS/NTFS
/dev/sda2     3906252945 7813453724 3907200780   7  HPFS/NTFS
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
Successfully wrote the new partition table

Re-reading the partition table ...

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```

```

(parted) print all

Disk /dev/sda: 6001GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2000GB  2000GB  primary
 2      2000GB  4000GB  2000GB  primary

(parted) mkpart ?
Partition type?  primary/extended? extended
Start? 4000GB
End? 6001GB
(parted) print
(parted) print all

```

---

### Post by nixscripter on 2008-10-04
Okay, more research says that 4 TB is the limit of a disk accessable DOS partition table -- period. I'm afraid you'll have to use the GUID partition table:

[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)

Downsides:

1. You can't boot from it with most hardware.
2. You'll have to use parted from now on, because fdisk can't understand this type of partition table.
3. You'll have a harder time getting anyone else to read it either.
4. You'll need to _[compile your own kernel]("https://help.ubuntu.com/8.04/installation-guide/i386/kernel-baking.html")_.

---

### Post by jcustenborder on 2008-10-04
This is the best news so far. I'm not booting off this disk nor do I plan to. Can I convert or change this disk over to a GPT disk?

---

### Post by nixscripter on 2008-10-04
Hypothetically, if you open **parted**, delete the DOS disk label, and create a GPT disk label with all your partitions in the same place, it should be smart enough to move them (because the GPT is bigger).

But I've never tried it, I don't know. Always run a backup before you play with partitions and real data.

---

