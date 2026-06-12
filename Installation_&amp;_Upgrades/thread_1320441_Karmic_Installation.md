---
title: "Karmic Installation"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by nervous137 on 2009-11-09
I was wondering if I could get a bit of help. I upgraded from 9.04 to 9.10, which didn't go well. I have reinstalled 8.10 but now have 4 x 30 GB partitions. How do I determine which ones were created during the 9.10 upgrade.
Many thanks in advance

David

---

### Post by kio_http on 2009-11-09
Its best do select manual and do partitioning. You can custommise it to your liking and know what has been done. This way problems like this do not occur.

---

### Post by nervous137 on 2009-11-09
Mmm thanks for that information I will remember for the next time. Is there an easy way of determining which partitions I can delete. it is on my work dual boot machine (XP) and IT would be mighty cross if I do anything to XP.
TIA

D

---

### Post by rygar on 2009-11-09
some things that might be useful:

In GParted, you can see the file structure for each partition.  "gksudo gparted" to run, or "sudo apt-get install gparted" if it isn't installed.

NTFS or FAT32 is a Windows partition, whereas ext2, ext3, and ext4 are Linux partitions.

Another thing you might try is mounting all of your partitions in your current Ubuntu installation (double click on them from 'Computer')

Now if you type "df" from the terminal, it will tell you which partition (e.g. /dev/sda1/) belongs to which folder.  Look through the contents of the folders, figure out which ones you need and which you can delete.

Lastly, you can load Ubuntu from a Live CD and run GParted.  This is very useful, as it will allow you to delete the partitions you dont want, and merge that unused space into existing partitions.

Hope this helps!

---

### Post by nervous137 on 2009-11-09
Thanks that is great, I'll get onto that. Once again thanks for everyones help.

D

---

