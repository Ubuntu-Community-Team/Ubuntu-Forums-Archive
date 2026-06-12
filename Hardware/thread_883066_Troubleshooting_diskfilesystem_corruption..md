---
title: "Troubleshooting disk/filesystem corruption."
date: 2008-08-07
forum: Hardware
---

### Post by captaintrav on 2008-08-07
Yesterday I started to have trouble reading certain files on a 500gb ext3 partition I have mounted for storage/backup purposes.

I checked /var/log/messages, have lots of entries like this for the past week or so:

```
Aug  6 21:02:49 tbird kernel: [114941.226727] attempt to access beyond end of device
Aug  6 21:02:49 tbird kernel: [114941.226735] sdb1: rw=0, want=23548135088, limit=976768002
```


So I unmount the partition, run fsck, and get lots of this:

```
Inode 5734439 has INDEX_FL flag set but is not a directory.
Clear HTree index? yes

Inode 5734439, i_size is 5245066037214557465, should be 0.  Fix? yes

Inode 5734439, i_blocks is 2978642201, should be 0.  Fix? yes

Inode 5734437 has INDEX_FL flag set but is not a directory.
Clear HTree index? yes

Inode 5734437, i_size is 7687059029158035282, should be 0.  Fix? yes

Inode 5734437, i_blocks is 1586999798, should be 0.  Fix? yes


```

Now, the partition is usable, but I lost a few files in the process.  I ran the manufacturer's (Western Digital) diagnostics on the drive, and it checks out.

So I start going through the past logs to find out when this started, and found that the trouble started after this event:

```
Jul 29 02:21:33 tbird kernel: [70618.590538]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Jul 29 02:21:33 tbird kernel: [70618.590551] ata2: hard resetting link
Jul 29 02:21:33 tbird kernel: [70619.029895] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 29 02:21:33 tbird kernel: [70619.044092] ata2.00: configured for UDMA/133
Jul 29 02:21:33 tbird kernel: [70619.044105] ata2: EH complete
Jul 29 02:21:33 tbird kernel: [70619.046916] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Jul 29 02:21:33 tbird kernel: [70619.048232] sd 1:0:0:0: [sdb] Write Protect is off
Jul 29 02:21:33 tbird kernel: [70619.051277] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support
```

Any ideas what I should be checking?  I'm not really familiar with Linux system error messages as opposed to Windows, so I don't know how worried to be.  I have 3 SATA drives in the system on the same controller (plus a SATA DVD-RW) and only one has had issues, so I'm thinking maybe a defective or loose data(or power) connection (the partition mounted as root gets thrashed a lot more and hasn't had any issue like this before); but I also wonder if it might be some sort of bug, since the files that got corrupted were large files > 1GB in size.  Suggestions or comments welcome.

---

### Post by YaroMan86 on 2008-08-16
I can't quite say as to why your partition failed. Perhaps it experienced a dirty unmount (Power failure? Hard reset?).

Your lost files might be in lost+found. You'll need to be in root to take a look in there.

---

