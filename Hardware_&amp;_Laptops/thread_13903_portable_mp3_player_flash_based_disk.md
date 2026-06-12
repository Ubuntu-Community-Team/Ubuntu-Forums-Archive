---
title: "portable mp3 player flash based disk"
date: 2005-02-03
forum: Hardware &amp; Laptops
---

### Post by lassegs on 2005-02-03
Ive searched through this forum, and others and I cannot find a solution to my problem. I've got flash disk based portable mp3 player, named NAPA (The name doesn't matter). My brother has a Creative MuVo, also flash disk based. The same problem goes for both the players.
When I plug the mp3 players into the usb, the disk is recognized and i can browse folders and files. I can also write, but when I delete files, the space is not freed. 
For example: The disk is 512 mb large, 256 mb is used and 256 mb is free. then i delete 128 mb, but there are still only 256 mb free!

I've tried formating the disk with cfdisk, it seems to me that the disks use fat16 and fat32. I get no errors when formating but when i try to remount it, gnome tells me: "bad superblock or unrecognized fs" (or something like that, you know what I mean,

To free the space again, and make the disk recognizable to Ubuntu, I must format it to fat32 in Windows.  :-( 

Some help please?

---

### Post by Nis on 2005-02-03
[QUOTE=lassegs]Ive searched through this forum, and others and I cannot find a solution to my problem. I've got flash disk based portable mp3 player, named NAPA (The name doesn't matter). My brother has a Creative MuVo, also flash disk based. The same problem goes for both the players.
When I plug the mp3 players into the usb, the disk is recognized and i can browse folders and files. I can also write, but when I delete files, the space is not freed. 
For example: The disk is 512 mb large, 256 mb is used and 256 mb is free. then i delete 128 mb, but there are still only 256 mb free!

I've tried formating the disk with cfdisk, it seems to me that the disks use fat16 and fat32. I get no errors when formating but when i try to remount it, gnome tells me: "bad superblock or unrecognized fs" (or something like that, you know what I mean,

To free the space again, and make the disk recognizable to Ubuntu, I must format it to fat32 in Windows.  :-( 

Some help please?[/QUOTE]
 Check the hidden trash folder in Nautilus for each disk.  Tell Nautilus to show hidden files (Ctl + H or under View menu) and delete anything from the Trash folder.  It should be named something like .trash-username.  The reason Nautilus doesn't copy the "deleted" file over to the trash on the hard disk is because that operation could take some time, and if the "deleted" file were to be un-deleted the removable drive would have to be available or the file wouldn't know where to go.  See if that works.

On a related note, my MuVo used to have 64MB but I screwed some how and now it only holds 10MB (don't ever pull it out without unmounting it first).  Maybe I'll be able to fix this one day.

---

### Post by lassegs on 2005-02-03
Well, that fixed the problem. Thx man!

---

