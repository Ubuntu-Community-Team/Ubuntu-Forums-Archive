---
title: "[SOLVED] Lacie Big Disk"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by Ezetreal on 2007-09-05
Hi

   Here is my problem. For unknown reasons, my 400GB Lacie Big Disk drive's motherboard isn't powering up the drives anymore. I gave up on trying to fix it and instead got a case with the intention of accessing each 200GB WD drive separetely. Obviously windows couldn't read the drives, either one. It asked me to format them first. Out of the question, I need my data.
Better luck with linux. I could access in read and write one of my drives. The one that was set to master in the Lacie case. 
I am a total newbie (n00b if you prefer :) ) but my guess is the second drive is missing boot sector stuff. 
My drive was formatted in ntfs, i have ntfs3g installed, but the drive that did run showed up in fuseblk type.
Is there any way I can access that second drive ?  I am all eyes and ready to post any log or whatever that you ask for.
I am running Feisty by the way.

Thanks

---

### Post by ghantoos on 2007-09-06
can you post the error given by your mount command?
i suppose it looks like :

sudo mount /dev/sda1 /mnt/blah/ -t ntfs -o nls=utf8,umask=0222

cheers,

ghantoos

---

### Post by Ezetreal on 2007-09-06
Here is the result of the mount command and the demsg | fail.

the command was:   sudo mount /dev/sdb /mnt/USB -t ntfs -o nls=utf8,umask=0222

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ezetreal@ezetreal:~$ dmesg | tail
[ 8376.412000] sdb: assuming drive cache: write through
[ 8376.412000]  sdb:
[ 8376.432000] sd 7:0:0:0: Attached scsi disk sdb
[ 8376.432000] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 8439.608000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[ 8439.628000] printk: 948 messages suppressed.
[ 8439.628000] NTFS-fs warning (device sdb): is_boot_sector_ntfs(): Invalid boot sector checksum.
[ 8439.628000] NTFS-fs error (device sdb): read_ntfs_boot_sector(): Primary boot sector is invalid.
[ 8439.628000] NTFS-fs error (device sdb): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[ 8439.628000] NTFS-fs error (device sdb): ntfs_fill_super(): Not an NTFS volume.

I hope this helps.

I was wondering if there were any way i could copy the boot sector from the disk that worked into this disk. Does that sound ridiculous ?



Thanks for trying ghantoos.

---

### Post by Ezetreal on 2007-11-29
Huuuuum, still nothing ??

Is it hopeless ?

---

### Post by ghantoos on 2008-02-12
Just posting to give the final solution Eztreal and myself found.

Using testdisk and/or photorec Ezetreal was able to recover all the data (that he finally decided to erase...) of the hard disk.

Here are some *VERY* useful links:
[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Hope this is useful!

Cheers,

---

