---
title: "Partitions unavailable"
date: 2016-01-31
forum: Hardware
---

### Post by prickett2 on 2016-01-31
I recently cloned one drive to another using Clonezilla because my partition was out of space.  It appeared to be successful as I was able remove the old drive and boot from the new one.

I then created a new, larger partition, and tried to clone the small partition's data to the larger one.  The small partition didn't appear as a source.

After playing with it for a while, I said screw it, and reinstalled Ubuntu Mate with a reformat.  Even now, though, when running GPARTED it tells me partitions 2 and 3 have been written butn "we have been unable to inform the kernel of the change".  I've rebooted several times to no avail.  I only see sda1, sda2, and sda5 in GPARTED.

Any help?

---

### Post by Vladlenin5000 on 2016-01-31
Help with what exactly? Try posting a screenshoot of GParted and explaining what the problem really is...

---

### Post by oldfred on 2016-02-01
When you cloned it did it also copy UUID? Duplicates are not allowed.

Post this to see if duplicates:
 sudo blkid -c /dev/null -o list

---

### Post by yoshii on 2016-02-01
gParted has a function for creating a new UUID.  But you need to manually make this match the entry inside of /etc/fstab or the system won't boot because it's looking for the wrong UUID.

---

### Post by prickett2 on 2016-02-02
> **oldfred said:**
> When you cloned it did it also copy UUID? Duplicates are not allowed.

Post this to see if duplicates:
 sudo blkid -c /dev/null -o list

It doesn't appear to have duplicates:

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              14ae0d38-a51e-4d03-8617-e96a83ec30ee
/dev/sda5  swap             [SWAP]         5d4f8020-d08d-4918-9428-758c6ef698e9
/dev/sdb1                   (not mounted)  
/dev/sdb2  ntfs             /media/patti/F888DA1688D9D2EC F888DA1688D9D2EC

---

### Post by Bucky Ball on 2016-02-02
No, no UUID duplicates, but no sda2 or 3 either. :-k

How about the output of:

> sudo blkid

---

### Post by prickett2 on 2016-02-03
[sudo] password for patti: /dev/sda1: UUID="14ae0d38-a51e-4d03-8617-e96a83ec30ee" TYPE="ext4" PARTUUID="01ac609d-01"
/dev/sda5: UUID="5d4f8020-d08d-4918-9428-758c6ef698e9" TYPE="swap" PARTUUID="01ac609d-05"
/dev/sdb2: UUID="F888DA1688D9D2EC" TYPE="ntfs"
/dev/sdb1: PARTUUID="8ff68ff6-01"

---

### Post by prickett2 on 2016-02-03
[sudo] password for patti: /dev/sda1: UUID="14ae0d38-a51e-4d03-8617-e96a83ec30ee" TYPE="ext4" PARTUUID="01ac609d-01"
/dev/sda5: UUID="5d4f8020-d08d-4918-9428-758c6ef698e9" TYPE="swap" PARTUUID="01ac609d-05"
/dev/sdb2: UUID="F888DA1688D9D2EC" TYPE="ntfs"
/dev/sdb1: PARTUUID="8ff68ff6-01"

---

### Post by oldfred on 2016-02-04
Post this:
sudo fdisk -lu
sudo parted -l

---

### Post by prickett2 on 2016-02-04
```
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/sda: 186.3 GiB, 200049647616 bytes, 390721968 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x01ac609d

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 382486527 382484480 182.4G 83 Linux
/dev/sda2       382488574 390721535   8232962   3.9G  5 Extended
/dev/sda5       382488576 390721535   8232960   3.9G 82 Linux swap / Solaris

Disk /dev/sdb: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x8ff68ff6

Device     Boot  Start        End    Sectors   Size Id Type
/dev/sdb1           63       2047       1985 992.5K 42 SFS
/dev/sdb2  *      2048     206847     204800   100M 42 SFS
/dev/sdb3       206848 1465147119 1464940272 698.6G 42 SFS

====================================================
Model: ATA FUJITSU MHY2200B (scsi)
Disk /dev/sda: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  196GB  196GB   primary   ext4            boot
 2      196GB   200GB  4215MB  extended
 5      196GB   200GB  4215MB  logical   linux-swap(v1)

Model: ASMT 2105 (scsi)
Disk /dev/sdb: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1049kB  1016kB  primary  ntfs
 2      1049kB  106MB   105MB   primary  ntfs         boot
 3      106MB   750GB   750GB   primary  ntfs
```

---

### Post by Bucky Ball on 2016-02-04
Please use code tags for your terminal output as not doing so loses the format and wastes space. Thanks. 

See the link in my signature for how. They have been added to your last post as an example.

---

### Post by oldfred on 2016-02-05
SFS is dynamic partitions which is Microsoft proprietary & does not work with Linux nor some Windows tools.

```
 Device     Boot  Start        End    Sectors   Size Id Type
/dev/sdb1           63       2047       1985 992.5K 42 [COLOR=#ff0000]SFS[/COLOR]
/dev/sdb2  *      2048     206847     204800   100M 42 [COLOR=#ff0000]SFS[/COLOR]
/dev/sdb3       206848 1465147119 1464940272 698.6G 42 [COLOR=#ff0000]SFS[/COLOR]


```

You need to undo the dynamic partitions.
       Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

    
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

### Post by prickett2 on 2016-02-05
I'm wondering how these Microsoft partitions even go there.  

I originally cloned a drive that started life housing Windows.  But I wiped the drive and installed Ubuntu.  At that point, the partitions were correct.  After unsuccessfully cloning that old drive to a new bigger drive, I formatted the new drive when I reinstalled Ubuntu. 

When installing Ubuntu and specifying you want to format the drive, doesn't it wipe out the partitions?

---

### Post by oldfred on 2016-02-06
If you use the full drive install option, it will erase partition table.

But if it cannot see the partitions correctly, the installer just fails. That is usually preferred as then you have special partitions that you may not want to overwrite.

---

### Post by prickett2 on 2016-02-06
How can I reformat the entire drive so after reinstalling, I'll have the partitions correctly?

---

### Post by oldfred on 2016-02-06
Backup any data in the Windows partitions you want.

Not sure if now the newest version of gparted will see SFS or not.
Otherwise you can use Windows tools to delete the partitions.

---

