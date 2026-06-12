---
title: "Dual-boot system, Windows partition is unreadable"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by Joule on 2007-03-09
I have a laptop on which I have a dual-boot setup with Edgy and XP.  The system froze the other day, and I had to reboot it.  Everything seemed fine.

I have my windows hard drive, HDA1, mounted on my desktop so I can access my files there.  I opened the folder, and it was empty, with the message, "Sorry, couldn't display all the contents of "hda1""

Well, foo.  So, I go looking in the partition information - it sees that it is an ntfs partition, it sees how much space i have used, how much I have free, etc.  But it shows no files.

I reboot, attempt to load Windows.  I get an error, "could not find file ... " (blah, I forget.  Whatever file was needed to start loading windows.  No  matter, it's because it simply won't see anything on the hard disk.)

What I would like ideally is a recommendation on a good piece of software that could help me figure my way through this.  Also, can someone help me with some commands that I might find useful in fixing this partition?  It appears that the data is intact, but for whatever reason, i just can't get to it.  

Any help is greatly appreciated.  Thank you.

---

### Post by mikewhatever on 2007-03-09
I am quite new and know not of any software or commands you are looking for. Can you post the output of the following in the terminal:
gksudo gedit /etc/fstab

---

### Post by Joule on 2007-03-09
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=b64e5e98-f3c8-431b-89ed-71679d8f2c26 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=7E8043DC80439A13 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=650fdc24-978b-41ba-b035-669e25c1675b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by mikewhatever on 2007-03-09
Well, the hda1 mount point looks ok, so I do not know what the problem is. Hope someone else will help you shortly.

---

### Post by redoscar3 on 2007-03-15
Joule,

You could try to use the ntfsfix utility that is available in Linux.  I think it is part of the ntfsprogs package.  Use of this utility is for situations where you had previously written to the ntfs partition and it is now found to be broken.  If you had never written to the Windows partition, then this probably isn't the way to correct the problem.

Another option might be to try to boot from the Windows install disk and attempt to repair the partition using chkdsk.  Hopefully this doesn't put your Linux partitions at risk.  And finally, if there is some way to use the Linux "captive" utility and the ntfs driver from your Windows install, you might be able to manage a repair.  Be cautious, research your options, and go slowly before choosing your weapon on this fix.

Hope this helps get things back to normal.

Red

---

### Post by awperk on 2007-03-15
I know you can't write to ntfs formatted partitions. I think there were some programs to make them accessible somewhere on the net. I had to use gparted and reformat the partition i wanted windows and ubuntu to be able to both read-write to. I'd suggest either making another partition with gparted and formatting it to FAT32, or reformatting your windows partition to FAT32 but i have never heard of reformatting without losing the data in that partition.

---

### Post by doobydave on 2007-03-17
My guess is your windows boot sector has become corrupted.

You could use a windows CD to log into the recovery console and type 'fixboot' but I would pop over to the msfn forums (with a detailed error message) first and post the question agian to those nice people over there.

---

