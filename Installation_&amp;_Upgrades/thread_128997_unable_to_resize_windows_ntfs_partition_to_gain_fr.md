---
title: "unable to resize windows ntfs partition to gain free space"
date: 2006-02-12
forum: Installation &amp; Upgrades
---

### Post by veighjay on 2006-02-12
hi

having problem resizing my windows ntfs partition. i have toshiba satellite laptop with a 60g hdd which is currently all taken up by my win os as an ntfs partition. the ubuntu install starts fine. i am following steps from [http://www.users.bigpond.net.au/hermanzone/](http://www.users.bigpond.net.au/hermanzone/) on the ubuntu+ntfs page. i select manually edit partition, select the ntfs partition, select to change the size of it, type in my new size which is between the minimum and maximum values, hit enter.... instead of any progress screen, i get a blank screen (blank ubuntu screen as in the white bar at the bottom is still there) for a while (10min?), then goes back to the partition table where things are exactly as they were before, ie. no new partition or free space.

one other thing to mention is that after the first go, when i tried again, the minimum value for the resize had changed from 28gb to 512b! i panicked and aborted install, restarted and phew, windows and all my files are still there......

any help would b much appreciated....

thanks....

---

### Post by aysiu on 2006-02-12
I've never had any problems [using DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142) to resize NTFS partitions.

---

### Post by lzfy on 2006-02-12
You can do this in Windows very easy with Partition Magic

---

### Post by az on 2006-02-12
[QUOTE=veighjay]hi
 i get a blank screen (blank ubuntu screen as in the white bar at the bottom is still there) for a while (10min?), then goes back to the partition table where things are exactly as they were before, ie. no new partition or free space.

..

any help would b much appreciated....

thanks....[/QUOTE]

Go to the third console (CTRL-ALT-F3) and see what error messages appreaed after your done that.  I am assuming it is reproduceable.  CTRL-ALT-F1 to get back to the first screen.

---

### Post by mcduck on 2006-02-13
Did you run defrag in windows before you tried this? If not, resizing that partition would be a pain to do as all files are scattered all over that partition. So start windows in safe mode and run defrag.

---

### Post by veighjay on 2006-02-13
thanks for the replies...

**mcduck**- i did do a defrag b4 i started... just for good measure, i did it again... and again...

**azz**- this is what the f3 screen said:

insmod /lib/modules/2.6.12-9-386/kernel/drivers/block/floppy.ko

fatal: error inserting floppy (/lib/modules/2.6.12-9-386/kernel/drivers/block/floppy.ko no such device)

insmod /lib/modules/2.6.12-9-386/kernel/drivers/block/floppy.ko

fatal: error inserting floppy (/lib/modules/2.6.12-9-386/kernel/drivers/block/floppy.ko no such device)

file descriptor 3 left open
file descriptor 4 left open
file descriptor 5 left open
file descriptor 6 left open
no matching physical volume found

file descriptor 3 left open
file descriptor 4 left open
file descriptor 5 left open
file descriptor 6 left open
no volume groups found
reading all physical volumes. this may take a while

file descriptor 3 left open
file descriptor 4 left open
file descriptor 5 left open
no matching physical volumes found

file descriptor 3 left open
file descriptor 4 left open
file descriptor 5 left open
no volume groups found
reading all physical volumes. this may take a while

**aysiu**- thanks for the tip... things were a little different to what u described, but i used disk drake and it worked! 

**lzsfy**- thanks, i'm sure it too would have worked...


so, i have now a reduced windows ntfs partition of 28gb, leaving me about 30 free.... so i'll go back and startup the ubuntu install, and do the fat32 and ext3 and swap partitions on the rest and finish installing... does that sound about right?

thanks heaps again for all ur help....

ps. **azz**- so do those above errors mean anything? i'd still b interested to know.... cheers..

---

### Post by infoburner on 2006-02-13
you should try gparted
heres a link [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

its a live linux cd that makes it freaking easy to resize any file system, include ntfs. i used it to resize a ntfs partition on my laptop only two hours ago, and now am dual booting! its great! its really really really easy too! graphical interface, click and drag resize etc etc

---

