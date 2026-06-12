---
title: "External hard drive questions"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by dje on 2007-09-06
I have just bought an external hard drive and i was wondering if just doing:

sudo umount /media/disk

is enough to safely unmount it. Is there a better command?

Also how can i rename the drive and partitions?

EDIT: found how to rename drives: [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

EDIT 2: I found that using the 'eject' command is a much better way of removing my hard drive, if i use that i can here the drive spinning down instead of just staying spinning when using the 'umount' command. With the umount command there was always a squeak when i turned it off

---

### Post by Kralizec on 2007-09-06
The umount command should be safe enough. I've always used that and had no problems. Also, if you do something in a way Ubuntu doesn't like (just unplugging the device, for instance) a little box pops up that says something about ejecting before safely removing the device. By unmounting the device the box doesn't come up.

---

