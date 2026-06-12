---
title: "Ubuntu Support of Advanced Format Drive"
date: 2010-11-11
forum: Hardware
---

### Post by foureyesboy on 2010-11-11
I would like to know if Ubuntu (or Linux, if there exists such a distro or a particular version) supports Advanced Format Drive 4096 byte sector, or if any special handling is needed for such a drive.

The reason why I raise this question is that recently my Windows 7 hard disk gets slower and slower in performance and finally the Windows 7 can no longer boot up.  As a result the NTFS corrupted after several unsuccessful boot.  And the performance degradation seemed to get more serious every time after I mounted the NTFS partitions on Linux and copied some files to it.

The Windows 7 resides on a WD 1TB (Black) HDD, one of the drives that use 4096 byte sectors instead of traditional 512 byte sectors.

WD has documented that if running Windows XP on this new Advanced Format Drive, a utility is needed to run to align the partition created by Windows XP.  WD also claims that Windows Vista/7 doesn't require this step.  But they didn't mention about Linux.

I have done some searches on the internet, but what I found cannot come up with a conclusion.  Some say Linux is not yet ready for these new Advanced Format Drives and some say manual attention needed in creating the partition to ensure they start at block 64 or its multiples.

Since the information is so confusing, could anyone kindly point out if Linux support 4096 byte sector or not.  Could that be this problem, if in case that Linux does NOT support these Advanced Format Drives, that causes the performance degradation and finally filesystem corruption on the Advanced Format Drive?

I have run chkdsk on Windows 7 and it does show 4096 byte cluster size.  While on Ubuntu, I ran a fdisk -l it shows both Logical/Physical sector size are 512 bytes.  Obviously there is a discrepancy in the sector size, and using 4096 byte sector requires less bits for CRC which I'm afraid will cause a problem. 

I apologize that this problem is too long.  Thanks in advance.

---

### Post by srs5694 on 2010-11-12
See [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) I wrote on the topic a few months ago for IBM developerWorks. In short, the issue isn't really one of Linux's (or any OS's) compatibility; it's a question of whether the partitions are laid out in an optimal way when they're created. You can check on this by typing "sudo fdisk -lu" (the trailing "u" is critically important) and checking whether the partition *start* sectors are all divisible by 8. If they are, the disk is properly partitioned; if not, the disk is not properly partitioned. (This assumes you've *not* used the "XP compatibility" jumper; if you've used that, partitions should all have start sectors one *less* than divisible-by-8 values.)

The behavior you describe sounds to me more like the disk is getting heavily fragmented than anything else. Windows includes the ability to defragment disks, so you could boot into Windows and use the disk defrag utility to improve performance, if this hypothesis is correct. There could be other problems, too, like hardware failures (which you could diagnose with a SMART utility) or perhaps filesystem corruption (use Windows' CHKDSK to fix this).

---

### Post by psusi on 2010-11-12
No special handling needed; install 10.04 or later on the drive and be happy.  Do not set the xp compatibility jumper.  Unless you actually install XP first, and then things get tricky.

---

### Post by foureyesboy on 2010-11-14
Thanks srs5694, that's a very informative and helpful article you wrote.

I've double-checked that drive and its partition does start from sector 2048.  So now ruling out the possibility of being mis-aligned, I think the hard drive may have hardware problem.

Thanks.

Thanks psusi also for your information.

---

### Post by rich1842 on 2011-04-23
[http://wdc.custhelp.com/app/answers/detail/a_id/5655/~/how-to-install-a-wd-advanced-format-drive-on-a-non-windows-operating-system](http://wdc.custhelp.com/app/answers/detail/a_id/5655/~/how-to-install-a-wd-advanced-format-drive-on-a-non-windows-operating-system)

That page gives useful info regarding Advanced Format Drives.

( I have spread that address around a little because so many are having problems. I started to google before I opened the package - where there is a warning - and thought I would have to return my new drives. Now I am shifting data onto them at 80+ MiB/s - I have never moved data so fast! )

---

