---
title: "Missing ntfs files after Windows returns from hibernation"
date: 2008-09-11
forum: General Help
---

### Post by csati on 2008-09-11
Hello!

I think I made a huge mistake, but I hope someone can help to recover my data. I have a Windows XP SP2 and an Ubuntu multibooting on my computer.

I've hibernated Windows, the computer turned off. The next time I restarted it I've chosen Ubuntu in the bootloader (grub), and it loaded up. Then I tried to mount one of the NTFS Windows partitions under ubuntu. I had to use the "-o force" option. (I think that was because Windows is not shutting it down properly if it goes into hibernation.) I moved (yes, silly me) a folder to the ntfs partition.

Then I restarted, woke Windows up, and the folder is missing! I tried a software named NTFS undelete, but it doesn't look like this folder has ever been there...

Any help would be appreciated! Thanks in advance!

csati

---

### Post by Shadow stewart on 2008-09-11
Restart your computer insert the windows xp cd and then choose boot from cd rom, after processing is complete select the option repair by pressing r from keyboard and after turning setup in dos mode select the window drive to repair default is 1. After that type the command chkdsk and press enter


[Outsourcing Solution in Call Center](http://www.iwaayconsultant.com)

---

### Post by sv1cdn on 2008-09-11
csati, I believe Ubuntu can not mount a hibernated NTFS partition!

---

### Post by csati on 2008-09-11
Hi!

I tried a Windows application to recover the files rather then chkdsk, but they seemed to be already overwritten.

I have the following partitions:
#1 windows system
#2 windows data
#3 windows swap
#4 linux
#5 linux swap

My stuff was on "linux", I moved it in linux to "windows data" while Windows was hibernated. Linux was ABLE to mount the partition with the "-o force" option. :(

---

### Post by vanadium on 2008-09-11
You will only be able to recover that data with specialized data recovery software. Never use -force mount unless you know why. If an ntfs disk does not mount automatically in Linux, the first thing you should do is repair it under MS Windows (just loading and completely exiting Windows would have worked in this case).

---

### Post by csati on 2008-09-11
So is it absolutely too late now?

What data recovery software can you recommend?

Is there a possibility of recovering the "place of moved files" on the ext3 partition?

---

### Post by csati on 2008-09-11
--------------------------------------------------------------------------------

So is it absolutely too late now?

What data recovery software can you recommend?

Is there a possibility of recovering the "place of moved files" on the ext3 partition?

---

### Post by vanadium on 2008-09-11
I am unfortunately not familiar with data recovery tools. testdisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)) is free data recovery software, but I have no experience with it whatsoever.

---

