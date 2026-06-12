---
title: "HDD Bad Sectors?"
date: 2009-11-01
forum: Hardware
---

### Post by Meridianox on 2009-11-01
Hi, I'm running a desktop dual booting Win7 with Ubuntu 9.10. The main hard drive is fine, but I have a second empty drive in a single NTFS partition. Ubuntu on boot reports that this second drive is failing, in Disk Utility, it reports,

[INDENT]DISK HAS MANY BAD SECTORS - Reallocated Sector Count - Count of remapped sectors. When the hard drive finds a read/write/verification error, it marks the sector as "reallocated" and transfers data to a special reserved area (spare area). 55 sectors.[/INDENT]

I've also ran CHKDSK (chkdsk /R z: ) in Windows as well as SeaTools (Seagate hard drive diagnostics software), but neither of these can find anything wrong with the hard drive.

[INDENT]C:\Windows\system32>chkdsk /R z:
The type of the file system is NTFS.
Volume label is Files.

CHKDSK is verifying files (stage 1 of 5)...
  256 file records processed.
File verification completed.
  0 large file records processed.
  0 bad file records processed.
  0 EA records processed.
  0 reparse records processed.
CHKDSK is verifying indexes (stage 2 of 5)...
  282 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered.
CHKDSK is verifying security descriptors (stage 3 of 5)...
  256 file SDs/SIDs processed.
Security descriptor verification completed.
  13 data files processed.
CHKDSK is verifying file data (stage 4 of 5)...
  240 files processed.
File data verification completed.
CHKDSK is verifying free space (stage 5 of 5)...
  366250900 free clusters processed.
Free space verification is complete.
Windows has checked the file system and found no problems.

1465136127 KB total disk space.
     21592 KB in 8 files.
        16 KB in 15 indexes.
         0 KB in bad sectors.
    110919 KB in use by the system.
     65536 KB occupied by the log file.
1465003600 KB available on disk.

      4096 bytes in each allocation unit.
 366284031 total allocation units on disk.
 366250900 allocation units available on disk.[/INDENT]

Question is, does Disk Utility know something that CHKDSK doesn't and is there something actually wrong with the hard drive (and I should get it replaced by the manufacturer)? Or is Ubuntu just being silly? Any other things to test and verify?

Thanks.

---

### Post by rp3 on 2009-11-01
> **Meridianox said:**
> Hi, I'm running a desktop dual booting Win7 with Ubuntu 9.10. The main hard drive is fine, but I have a second empty drive in a single NTFS partition. Ubuntu on boot reports that this second drive is failing, in Disk Utility, it reports,



Question is, does Disk Utility know something that CHKDSK doesn't and is there something actually wrong with the hard drive (and I should get it replaced by the manufacturer)? Or is Ubuntu just being silly? Any other things to test and verify?

Thanks.

Mine on my laptop did the same, it wouldn't install 9.10, as this was a refirb laptop I thought maybe that was the issue, so I picked up a Faster HD and put it in, works great.  Maybe it was bad, maybe it wasn't but for 60 bux it was an easy cheap fix.

And now I have a new HD and don't have to worry about it...

---

### Post by Irihapeti on 2009-11-01
The new disk utility, Palimpsest, is simply reading data from smartctl, which is a utility that reads diagnostic information stored in the drive itself.

Sometimes the figures are out of line with what's really going on and need a correction factor applied, but smartctl and Palimpsest don't know that. Sometimes, I suspect that drives may already be on the way out but haven't done anything terrible yet - or maybe there have been some glitches that have been blamed on software.

If you are at all unsure, do regular backups. Even if you are confident the disk is OK, do regular backups. That way, you are covered.

---

### Post by mf4221 on 2009-11-01
Same here.

---

### Post by Meridianox on 2009-11-02
Hmmmm... Probably a bug:

[http://www.uluga.ubuntuforums.org/showthread.php?t=1298725&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1298725&page=2)
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1821587.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1821587.html)
[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136)

---

### Post by kkady32 on 2009-11-07
i have the same issue :bad sector
i download Hiren's Boot CD v.10.0 and run HDDRegenerator and this repair problem.
now,message from palimpsest is :'disk is healthy'

---

