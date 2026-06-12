---
title: "Dapper Changed My FAT32 Volume Name ??"
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by jpepin on 2006-05-31
I recently installed the Dapper LTS RC.  After it was all up and running I used Gparted to resize a FAT32 partition on another drive.  Everything works great, and I retained all of my data, except for the partition's volume name.  Now, when I mount the FAT32 partition, it shows up on the desktop with the name "y> </html>"  

I have it mounted as /media/storage, and it's set to mount automatically via fstab, although it does the same thing regardless of the mount point or method of mounting (auto or manual)  

It also shows up with the same name if I boot into my Breezy partition (it used to show up as "storage" before the resize)

Any ideas on how I can change the name back to "storage"?

---

### Post by gslo on 2006-05-31
The same thing happened to me ,so I installed mtools and followed the instructions on this link.
Hope this helps,it worked perfectly for me.

gslo
[http://ubuntuforums.org/showthread.php?t=155676&highlight=Rename+mtools](http://ubuntuforums.org/showthread.php?t=155676&highlight=Rename+mtools)


scroll to bottom for info on fat partitions/drives

---

### Post by jpepin on 2006-05-31
For a quick Follow-Up:

mtools looked neat, but it didn't have any effect.  So I took the drive out of my ubuntu system and hooked it up to a windows box.  It showed up correct in windows, so I was stumped.  So I used Partition Magic and resized the partition again, and that fixed it.  It now shows up with the correct volume name.  So it must have something to do with the way Gparted created the FAT32 partition table.  Thanks for the help

---

