---
title: "ntfs partiton resized ubunutu doesnt recognize it"
date: 2013-08-21
forum: Hardware
---

### Post by pariah-112 on 2013-08-21
ok so here are the specs for my box:

Disk 0:
BASIC DISK
Partitions: SYSTEM RESERVED, WINDOWS 8, UBUNTU and swap

Disk 1:
DYNAMIC DISK:
Partitions: WINDOWS 7, LAPTOP,LAPTOP BACKUP, BACKUP 1

OK so heres the deal. When i first installed ubuntu it was able to recognize all partitions on DISK 0 and DISK 1.
However, i resized my DISK 1 partiton so that BACKUP1 could take up all the free space i had left over.
I resized via the WINDOWS 8 disk management utility.

When i use ubuntu, Ubuntu displays the partitions in both drives excluding partition BACKUP 1 on DISK 1.
How can i access my BACKUP 1 partiion from ubuntu?

---

### Post by oldfred on 2013-08-22
Linux does not work with dynamic partitions, that is proprietary Windows. And Windows does not make it easy to undo, but made it the default and automatic if adding new partitions. Better to use the more standard basic partitions and then use extended partition with logical partitions. Some Windows tools also do not work with dynamic since it is not the standard basic partitioning system.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

### Post by pariah-112 on 2013-08-22
Thanks Oldfred for your awesome reply.
However, since i extended the volume backup to take up the free space most of the third party utilities will not convert the disk back to basic.
Is there anyway that i can undo this extended volume ? 
i want to do that because i think that the programs might work if i can undo that action on extending the drive.

---

### Post by oldfred on 2013-08-22
I think the undo works best if you do not have more than 4 partitions, but if in your extending the logical partitions they do not align with the physical partitions then that may be why you cannot undo it. 
Most that I have seen with the issue have easily undone it but the logical partitions were still aligned withe the physical. Do not know enough about the details of dynamic partitions to know if you can tell if you have resized back or not?

---

