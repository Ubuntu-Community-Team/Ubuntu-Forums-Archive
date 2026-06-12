---
title: "How to retrieve data from old HDD"
date: 2008-08-15
forum: General Help
---

### Post by samjh on 2008-08-15
I'm currently running Hardy on an old IDE HDD.  This HDD is getting on a bit (three years now) and due to the nature of the data I work with, I'm looking at getting another drive (a SATA II type).

All critical files are backed up regularly, so they're no problem.  However there is a 10GB VM image (WinXP installation with Visual Studio and SQL Server) and about 9GB worth of less important files as well.  I'd rather not have to waste five DVD-Rs just for the sake of transferring them across HDDs (I know I can split, write, and cat them, but I don't like unnecessary consumption).

As prior planning prevents piss poor performance :), could some more experienced users point me in the right direction about installing the new drive and transferring the data over from the old one?  I've never done this on a Linux system before. :(

Is it a simple matter of:
1. Install new HDD as master.
2. Install Ubuntu on new HDD.
3. Hook up old HDD as slave.
4. Mount partitions (what mount points to use?  sda3=/backup and sda5=/home at the moment, and the files I want are in those).
5. Copy files.
:confused:

Are there going to be complications with changing a drive with an MBR on it from master to slave (I do NOT wish to boot from the old drive)?  What about the fact that one is an IDE drive and the other a SATA?


(DISCLAIMER: Yes, I did a search, as any veteran forum-goer should. No, the results were not helpful. Closest match was to do with mounting an old drive with Windows on it.  I'm talking about an old drive with Ubuntu on it.)

---

### Post by tech0007 on 2008-08-15
You did your homework quite well.  Also remember to set the boot sequence in the BIOS to start off with your new SATA drive first. After installing Hardy, you might even see your old ubuntu partition on your desktop automatically (no need to manually mount them).

---

### Post by samjh on 2008-08-16
Thanks for the confirmation.

I was hoping it would be relatively straight-forward. :)  On to the install...

---

