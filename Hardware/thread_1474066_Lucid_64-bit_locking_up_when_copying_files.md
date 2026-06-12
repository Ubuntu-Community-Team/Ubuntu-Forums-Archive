---
title: "Lucid 64-bit locking up when copying files"
date: 2010-05-05
forum: Hardware
---

### Post by Norami on 2010-05-05
I'm running 10.04 64-bit on an Intel Core 2 Duo (64-bit processor). I've got 8GB of RAM, although Ubuntu reads it as 7.3 GB. That's the least of my worries, though. I'm having a major issue when copying files from one hard drive to another. Whether it's between two internal SATA drives, or between my main HD and a USB external. Every time I try and copy more than one file, my system locks up completely except for the mouse. I thought one day that it was just a lot of data being transferred slowly. But I left it for 2 days, and there was no progress. It' very frustrating to say the least! The last time I had this problem, it was in 9.04 Studio 64-bit. Actually, I always have this problem with the 64-bit version of Ubuntu. It seems that when the files are copying, the RAM gets an overload and freezes. Some sort of memory leak? It might not even be a RAM issue. I just noticed it spiking hardcore while watching the system monitor. My answer to this problem was always falling back to 32-bit software. I can't do that in this case, though. I need the 64-bit functionality.

---

### Post by P4man on 2010-05-05
Is your main drive one of the sata drives you are referring to? IOW, does it always happen when that drive is involved? If so, check your drive health in disk utility. You may also want to try replacing your sata cable(s).

Other thoughts:
-Check your log files in system > admin > log file viewer.
-try it copying to a linux filesystem (ext3/4), not ntfs. NTFS usually works fine, except when it has a very small unit allocation szize (like 2k).

---

### Post by Norami on 2010-05-05
The main hard drive is SATA, yes. There are several different scenarios that this has happened in.

SATA (EXT4) to SATA (NTFS), SATA (EXT4) to eSATA (EXT4), USB (NTFS) to SATA (EXT4), eSATA (FAT32) to SATA (NTFS). They all end up the same. It even freezes when I copy data from an NTFS partition to an EXT4 partition on the same drive. Also, all of my partitions are well over 50GB, some are around 200GB. So I know it's not a question of running out of space or anything like that. It's not always when the main drive is involved, either. I've got two internal HD's and an external USB/eSATA HD. Here are the different partitions:

Main HD (SATA):
266GB NTFS - Windows XP
225GB EXT4 - Ubuntu 10.04
9.5GB Swap - Ubuntu 10.04

Second Internal (SATA):
500GB NTFS - File Storage for both OS's

External (USB/eSATA):
50GB EXT4 - Ubuntu 9.10
2GB Swap - Ubuntu 9.10
50GB FAT32 - Storage
550GB NTFS - Storage

What sort of entries would I be looking for in the syslog? There are a lot of different error messages popping up (this isn't the only issue I'm having with Lucid). So, I'm not sure what to look for in the log file. The SATA cables are also brand new. I'm talking a day old, so I don't think it's the cables? Could be wrong, I guess. I never have any problems copying files in Windows XP (32-bit) and I never have any problems copying files with the 9.10 install on the external (32-bit).

---

### Post by P4man on 2010-05-06
If it happens across drives and filesystems I think you can rule out out a hdd hardware problem.

look for anything in "messages" or "syslog" at the exact time of the freeze (its time stamped, and if it freezes make note of the time).

Also, when it freezes does control alt f1 still give you a full screen terminal? 

Lastly, it may have little or nothing to do with copying files (though that may help trigger it as it increases the load on the cpu and the bus and what not). If you have desktop effects enabled in system > preferences > appearance, then try disabling it.

---

### Post by Norami on 2010-05-06
I feel like a n00b. I can't believe I didn't think about turning off the desktop effects. So far, I'm golden. It's been copying 80GB worth of video and music, and my system is still running everything like a champ. Appreciate the suggestions and help! I'm not going to mark this as solved until everything finishes copying (just in case).

---

