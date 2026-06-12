---
title: "Would fsck in ubuntu fix my external fat32 hard drive--------------------------------"
date: 2009-07-03
forum: Hardware
---

### Post by npm1 on 2009-07-03
hello i want to the equivalent to scandisk in windows/dos which usually scan and try to fix errors in fat32/ntfs file systems-----
i understand that:
------------------------------------------------------------------------------------------------------------------------
 				 				**Re: Scandisk** 			
 			 			 		   		 		 		usually you do not need to run such a programm manually because it is done every now and then automatically at bootup.

if you want to do that manually you have to unmount the drive first.

the used program is already installed and its called **fsck**

use **tune2fs** if you want to change the fsck-intervall at mount-time.

read **man tunefs** for options
-----------------------------------------------------------------------------------------------------------------------

but the question how -to repair my external hard drive using those functions

can u please hlp cos and make the instructions as specific to the hard drive and clear to me-----as possible



the hard drive comes up with 73 folders,free space 170gb
when i go into any folder the is and it says 0 items,170gb
please i do not want to loose my data on the fat32 file system

---

### Post by quixote on 2009-07-04
fsck only works on linux (ext3 and similar) filesystems, so it won't do any good for a fat32 drive.

An ugly text-based but effective program called testdisk is worth trying in the situation you describe, which sounds like your partition table is bad.  (I'm not sure scandisk can deal with that, but if it can, why not run that if you have a Windows machine available?)

To use testdisk:  You can use synaptic in the LiveCD to "install" it. (Since you're in the CD environment it won't really install it, but you can use it until you reboot.)  First make sure the third-party software is enabled, reload, and install testdisk.  Then instructions on how to recover a partition are [here]("http://www.howtoforge.com/data_recovery_with_testdisk").  Another site with screenshots [here]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step").

Hope this helps.

---

### Post by paddym on 2011-11-26
The 'reply' above is misleading.
I am only posting in an old thread so no-one else is misled by it.

fsck.vfat also called dosfsck or fsck.msdos is the 'fsck' for FAT based file systems like FAT32 and has worked fine for me and my customers quite a few times.
(testdisk also has it's uses but may or may not be the answer for everone...)

P.S.
If you are here because you have a hard drive problem try to stay cool about it because that reduces the chances that you will make things worse.

Don't forget that there are plenty of good 'how-to' write ups and even a few live CDs designed for disc and filesystem repair and recovery.

Be prepared to search and read a bit first if your data really is precious to you.

If you are in any doubt about any of the recovery procedures consult with several different people who actually know what they are talking about. Even then, try to understand the steps you are taking.

Good luck.

---

### Post by nothingspecial on 2011-11-26
This thread is old and mouldy.

Closed.

---

