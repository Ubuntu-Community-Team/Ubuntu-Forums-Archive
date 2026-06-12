---
title: "USB external hard drive files"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by Stoff on 2008-01-22
Hello!

It's so f*** annoying: I have this external USB hard drive. In the beginning, it is mounted. But once I try to copy a file from it, it is dismounted. By the way, under Windows XP this does not happen. 

If I try to mount it again, it says ..does not exist. That's what dmesg gives me:
...
[ 2473.216000] Buffer I/O error on device sdb1, logical block 48529414
[ 2473.216000] lost page write due to I/O error on sdb1
[ 2473.280000] scsi 3:0:0:0: rejecting I/O to dead device
[ 2473.280000] scsi 3:0:0:0: rejecting I/O to dead device
[ 2473.284000] scsi 3:0:0:0: rejecting I/O to dead device
[ 2506.104000] scsi 3:0:0:0: rejecting I/O to dead device
[ 2506.104000] scsi 3:0:0:0: rejecting I/O to dead device
[ 2506.104000] scsi 3:0:0:0: rejecting I/O to dead device
[ 2506.104000] scsi 3:0:0:0: rejecting I/O to dead device
[ 2506.104000] scsi 3:0:0:0: rejecting I/O to dead device
[ 2506.104000] scsi 3:0:0:0: rejecting I/O to dead device
[ 2506.104000] scsi 3:0:0:0: rejecting I/O to dead device
[ 2506.104000] scsi 3:0:0:0: rejecting I/O to dead device
[ 2506.108000] scsi 3:0:0:0: rejecting I/O to dead device
[ 2506.108000] scsi 3:0:0:0: rejecting I/O to dead device
[ 2506.108000] scsi 3:0:0:0: rejecting I/O to dead device
[ 2506.108000] scsi 3:0:0:0: rejecting I/O to dead device
[ 2506.108000] scsi 3:0:0:0: rejecting I/O to dead device
[ 2506.108000] ext3_abort called.
[ 2506.108000] EXT3-fs error (device sdb1): ext3_journal_start_sb: Detected aborted journal
[ 2506.108000] Remounting filesystem read-only

I mean, I have this important data on this drive and it loads only under Windows XP.

I truly hope that you guys can help me with this problem.

Thanks, 
Christoph

---

### Post by Daelyn on 2008-01-24
Looks like the file table/partition info is corrupt of some reason.

Maybe a Partition/filesystme check from within Linux can fix it for you, have you seen any info about it. fschk tool should do this fine.

If it fails, copy all the info off the HDD in WinXP.
Reboot to Linux, do a total wipe of it and repartition/reformat it.

There are other tools that might fix your issue, but, because you actually have access from within Windows, the risk is less by copying the info and wiping it. At least that's my opinion.

---

