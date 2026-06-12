---
title: "ntfs partition accessible in ubuntu but not in windows 7"
date: 2010-10-10
forum: Hardware
---

### Post by hourna on 2010-10-10
i have a dual boot of ubuntu 10.10 and windows 7 ultimate. both are 64 bit and located in the same 160 gb harddrive. when i try to access my 1 tb hard disk which is an ntfs drive, windows 7 can't open it. it says drive must be formatted. when i check the disk, windows says the capacity of the disk is just 32 mb. even bios says it is 32 mb. however, when in ubuntu, i can access without encountering any problems. i have tried copying, pasting, reading. nothing went wrong. i think the most interesting thing here is after i restart the computer and boot into the windows 7, again my drive is there and working.

is the problem is related with ubuntu or its ntfs support? what the heck ubuntu is doing to reach my drive that win7 can't?

and how can i access the drive in win7? did anyone have similar issue?

i think my problem is quite unique and interesting =)

---

### Post by hourna on 2010-10-13
still waiting some help.

---

### Post by efflandt on 2010-10-13
I don't know if Vista and Win7 do anything different with ntfs than XP or earlier.  But I know that if you are going to resize a Vista or Win7 OS partition, that is best done from that OS itself.

Have you tried removing everything from the drive that you want to keep, removing all partitions (or room for a partition) and creating and formatting a partition from Win7.  I have no trouble accessing partitions from Linux that Win7 formatted (or any ntfs partitions from Linux).  But other than dying disks with bad sectors, I have not had any trouble accessing XP created ntfs partitions from Win7.

Maybe it is a permission issue where Win7 cannot figure out who has permission to access that partition.  Is it the only partition, or are there other partitions on the drive?  And is it a primary of logical partition?

---

### Post by oldfred on 2010-10-14
Is the drive showing as RAW?

If anyone has an NTFS drive showing up as RAW, use Windows Active Partition Recovery. Just right click on your partition and select "Fix Boot Sector"

You can also use testdisk to build a boot sector, but then I think it is XP type, but still should work unless you want to install Vista or 7.

---

### Post by luvshines on 2010-10-14
I am facing similar issues and still waiting for replies:
[http://ubuntuforums.org/showthread.php?t=1592003](http://ubuntuforums.org/showthread.php?t=1592003)

---

