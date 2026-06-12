---
title: "Deleted home directory"
date: 2006-01-15
forum: Hardware &amp; Laptops
---

### Post by sleepkreep on 2006-01-15
Ok, so I was installing an application from source.  A bug in the makefile caused a directory to be created, /~ .  I didn't need it so I meant to do rm -rf /~ but instead did rm -rf ~ .  Oops.  Now all the work I've done over the past 5 years is gone.  My entire life disappeared in front of my eyes.  To make matters worse, I apparently forgot to backup the /home directory when I installed Ubuntu. My /home directory is mounted from a second hard drive using reiserfs.  I backed up the partition and did reiserfsck --rebuild-tree -S but that found far too many files for me to sort through, try 32000.  There must be a way to find all the files and keep their filenames and locations.  Any tips?

---

### Post by mips on 2006-01-15
I was thinking about the recover command but I dont think it works on reiserfs file systems.

The best advice I can give you is to NOT use that drive for now untill such time as you find a solution to the problem else you could overwrite stuff you need.

I googled "recovering files from reiserfs ?" and got some results:
[http://www.antrix.net/journal/techtalk/reiserfs_data_recovery_howto.comments](http://www.antrix.net/journal/techtalk/reiserfs_data_recovery_howto.comments)
[http://forums.infoprosjoint.net/showthread.php?t=5821](http://forums.infoprosjoint.net/showthread.php?t=5821)
[http://www.acidfiles.com/soft/recover-files-resierfs.html](http://www.acidfiles.com/soft/recover-files-resierfs.html)
[http://www.freedownloadscenter.com/Utilities/Backup_and_Copy_Utilities/Kernel_ReiserFS___Data_Recovery_Software.html](http://www.freedownloadscenter.com/Utilities/Backup_and_Copy_Utilities/Kernel_ReiserFS___Data_Recovery_Software.html)

I have no idea how you would sort/name the files but maybe google around a bit.

Not to be nasty or anything but I think you learned a valuable lesson here, backups ! I've noticed this always happens after the fact.

---

