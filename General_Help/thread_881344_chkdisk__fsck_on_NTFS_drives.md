---
title: "chkdisk / fsck on NTFS drives?"
date: 2008-08-05
forum: General Help
---

### Post by kooldino on 2008-08-05
How do I run a scandisk / chkdisk / fsck on my ntfs-3g mounted NTFS drives?

---

### Post by kooldino on 2008-08-06
bump

---

### Post by p_quarles on 2008-08-06
1) Don't bump within 24 hours, please :)
2) you can try using ntfsfix (part of the ntfs-3g suite)
3) There's no substitute for Windows in this case, and you shouldn't be using NTFS unless you're running a Windows system.

---

### Post by dcstar on 2008-08-06
> **p_quarles said:**
> 
2) you can try using ntfsfix (part of the ntfs-3g suite)


Install the ntfsfix package, then in a terminal:

```
sudo ln -s /usr/bin/ntfsfix /usr/sbin/fsck.ntfs
sudo ln -s /usr/bin/ntfsfix /usr/sbin/fsck.ntfs-3g
```

That will ensure that the command "fsck /dev/your-partition" will work for NTFS partitions.

---

### Post by kooldino on 2008-08-06
> **p_quarles said:**
> 1) Don't bump within 24 hours, please :)
2) you can try using ntfsfix (part of the ntfs-3g suite)

Ok, I unmounted the disk and ran: 
```

sudo ntfsfix /dev/sda1  

```
It spat out:

```

Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.

```

So...did that fix whatever was "corrupt" about it?

> 3) There's no substitute for Windows in this case, and you shouldn't be using NTFS unless you're running a Windows system.

Well, I used to run a dual boot, but I don't any longer.

Perhaps there's some kind of boot disk (maybe even UBCD) that I could use to check the disk?

---

### Post by dcstar on 2008-08-06
> **kooldino said:**
> Ok, I unmounted the disk and ran: 
```

sudo ntfsfix /dev/sda1  

```
It spat out:

```

Mounting volume... OK
Processing of $MFT and $MFTMirr **completed successfully**.
NTFS volume version is 3.1.
**NTFS partition /dev/sda1 was processed successfully**.

```

So...did that fix whatever was "corrupt" about it?
.........

It didn't find any problems.

You asked how to run this check and you have your answer, you didn't say there was anything wrong with anything.

---

### Post by kooldino on 2008-08-06
> **dcstar said:**
> It didn't find any problems.

You asked how to run this check and you have your answer, you didn't say there was anything wrong with anything.

Sorry, I forget what I was running, but I got messages that said the disk was corrupt and needed to be scanned.

---

### Post by frankstrudel on 2009-07-02
sorry to bump, but did you solve this problem?

any help appreciated!

---

### Post by dillinger417 on 2009-08-06
> **dcstar said:**
> Install the ntfsfix package, then in a terminal:

```
sudo ln -s /usr/bin/ntfsfix /usr/sbin/fsck.ntfs
sudo ln -s /usr/bin/ntfsfix /usr/sbin/fsck.ntfs-3g
```

That will ensure that the command "fsck /dev/your-partition" will work for NTFS partitions.

Just for the record, I tried this and this was the result:

( My initial link creation worked OK, I just included this first line so we are clear I created link )
```

jared@jared-desktop:/dev$ sudo ln -s /usr/bin/ntfsfix /usr/sbin/fsck.ntfs-3g
ln: creating symbolic link `/usr/sbin/fsck.ntfs-3g': File exists
jared@jared-desktop:/dev$ sudo fsck /dev/sdb2
fsck 1.41.4 (27-Jan-2009)
fsck: fsck.ntfs-3g: not found
fsck: Error 2 while executing fsck.ntfs-3g for /dev/sdb2
jared@jared-desktop:/dev$ sudo /usr/bin/ntfsfix /dev/sdb2
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sdb2 was processed successfully.


```

I originally was getting errors from ntfs-3g about record # not having FILE magic e.g.
```
ntfs_mst_post_read_fixup: Invalid argument
Aug  6 10:06:52 jared-desktop ntfs-3g[2022]: Record 50682 has no FILE magic (0xf2e282c3) 
```
as well as messages from the kernel like
```
Aug  6 10:12:38 jared-desktop kernel: [ 2443.940075] ata8.00: limiting speed to UDMA/100:PIO4
Aug  6 10:12:38 jared-desktop kernel: [ 2443.940081] ata8.00: exception Emask 0x10 SAct 0x0 SErr 0x1810000 action 0xe frozen
Aug  6 10:12:38 jared-desktop kernel: [ 2443.940085] ata8: SError: { PHYRdyChg LinkSeq TrStaTrns }
Aug  6 10:12:38 jared-desktop kernel: [ 2443.940091] ata8.00: cmd c8/00:08:e3:6f:93/00:00:00:00:00/e3 tag 0 dma 4096 in
Aug  6 10:12:38 jared-desktop kernel: [ 2443.940092]          res d0/00:08:e3:6f:93/00:00:00:00:00/e3 Emask 0x12 (ATA bus error)
Aug  6 10:12:38 jared-desktop kernel: [ 2443.940094] ata8.00: status: { Busy }
Aug  6 10:12:38 jared-desktop kernel: [ 2443.940099] ata8: hard resetting link
Aug  6 10:12:44 jared-desktop kernel: [ 2449.877038] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Aug  6 10:12:44 jared-desktop kernel: [ 2449.892224] ata8.00: configured for UDMA/100
Aug  6 10:12:44 jared-desktop kernel: [ 2449.892248] ata8: EH complete
Aug  6 10:12:44 jared-desktop kernel: [ 2449.903682] sd 7:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Aug  6 10:12:44 jared-desktop kernel: [ 2449.903731] sd 7:0:0:0: [sdb] Write Protect is off
Aug  6 10:12:44 jared-desktop kernel: [ 2449.903734] sd 7:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Aug  6 10:12:44 jared-desktop kernel: [ 2449.903759] sd 7:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  6 10:12:52 jared-desktop ntfs-3g[2022]: Inode is corrupt (388): Input/output error
```
and
```
Aug  6 10:40:39 jared-desktop kernel: [ 4125.193249] ata8.00: configured for UDMA/33
Aug  6 10:40:39 jared-desktop kernel: [ 4125.193267] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Aug  6 10:40:39 jared-desktop kernel: [ 4125.193271] sd 7:0:0:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
Aug  6 10:40:39 jared-desktop kernel: [ 4125.193275] Descriptor sense data with sense descriptors (in hex):
Aug  6 10:40:39 jared-desktop kernel: [ 4125.193276]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Aug  6 10:40:39 jared-desktop kernel: [ 4125.193282]         0c 3d be 03 
Aug  6 10:40:39 jared-desktop kernel: [ 4125.193285] sd 7:0:0:0: [sdb] Add. Sense: Recorded entity not found
Aug  6 10:40:39 jared-desktop kernel: [ 4125.193290] end_request: I/O error, dev sdb, sector 205372931
Aug  6 10:40:39 jared-desktop kernel: [ 4125.193295] Buffer I/O error on device sdb2, logical block 23111257
Aug  6 10:40:39 jared-desktop kernel: [ 4125.193317] ata8: EH complete
Aug  6 10:40:39 jared-desktop kernel: [ 4125.193843] sd 7:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  6 10:40:46 jared-desktop kernel: [ 4131.992710] ata8.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Aug  6 10:40:46 jared-desktop kernel: [ 4131.992714] ata8.00: BMDMA stat 0x4
Aug  6 10:40:46 jared-desktop kernel: [ 4131.992720] ata8.00: cmd c8/00:08:03:bd:3d/00:00:00:00:00/ec tag 0 dma 4096 in
Aug  6 10:40:46 jared-desktop kernel: [ 4131.992721]          res 51/10:00:03:bd:3d/10:00:10:00:00/ec Emask 0x81 (invalid argument)
Aug  6 10:40:46 jared-desktop kernel: [ 4131.992724] ata8.00: status: { DRDY ERR }
Aug  6 10:40:46 jared-desktop kernel: [ 4131.992725] ata8.00: error: { IDNF }
```

I was having issues mounting the drive, but when I was finally able to run ntfsfix, it reported nothing unusual, and then checking my drive (w/ most my music )several of the folders that started w/ C that were previously missing, reappeared and were playable so it *seems* to have fixed the issue, but I may still have a bad drive so we will see.

---

### Post by frankstrudel on 2009-08-07
Thanks, and fingers crossed with your drive...

---

### Post by colorprint on 2010-04-07
ntfsfix only marks the filesystem as 'dirty', not fixing it really
[http://linux-ntfs.org/doku.php?id=ntfsfix](http://linux-ntfs.org/doku.php?id=ntfsfix)

---

### Post by bakegoodz on 2010-05-30
ntfsfix is very limited in fixing ntfs problems. For my external drive formated ntfs, I just keep a XP boot disk. I just bootup to the recovery console and run chkdsk. It works with a esata drive, not sure if recovery console supports USB

---

