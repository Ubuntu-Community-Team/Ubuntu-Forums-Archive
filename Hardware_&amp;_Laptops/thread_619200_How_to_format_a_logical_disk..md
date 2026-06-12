---
title: "How to format a logical disk."
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by mifth on 2007-11-21
Hi, I've got a problem. One of my logical disks has corrupted sectors. Possibly just errors. It work bad, sometimes it does not want to be mouted. How to format it and resolve such a problem. Thank you.

Also could you say how to farmat diskettes and flash cards.

Thanks a lot friends.

---

### Post by dabl on 2007-11-21
I would use a GParted Live CD, made from the ISO [[COLOR="SeaGreen"]**here**[/COLOR]](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828) and re-partition that drive, and reinstall whatever is on it.  If it still gives errors, it is probably ready for the dumpster.

The Linux command to format floppy media is "mkfs" -- if you Google it I'm sure the particular usage options are available for review.

:)

---

### Post by mifth on 2007-11-21
Thank you! I suppose this is exactly what i need.

---

### Post by az on 2007-11-21
Check the partition for badblocks, using the badblocks command.


sudo badblocks /dev/sdxx -w -v -s

where sdxx is your partition.  That will perform a write test so all the data will be wiped.

---

### Post by mifth on 2007-11-21
Thank you, thank you very much! This is really cool. I was trying to look for formatting information, but  found only 'fdisk'.

---

