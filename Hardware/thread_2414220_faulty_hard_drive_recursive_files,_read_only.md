---
title: "faulty hard drive recursive files, read only"
date: 2019-03-07
forum: Hardware
---

### Post by john5757 on 2019-03-07
I have a couple of SATA hard drives which I attempted to reformat with a gparted boot disk.
They have both become unusable, they are not seen on "disks" but are shown with "fdisk -l",
as Disk /dev/loop 0  7.5MiB----------etc  to   Disk /dev/loop 18 140.7 MiB----------etc.
Also they are reported as "read only"
Neither gparted or testdisk will allow me to format or do anything with them.
How can I completely erase/reformat these disks? I do not need to save/recover any data on them.
I just want to restore them to usable HD Drives.
I reformatted a third SATA HDD without any probs.
Thanks.

---

### Post by yancek on 2019-03-07
If you have no data on these drives, you should be able to boot GParted, highlight the specific drive (make sure you get the correct drive!) and then click the DEvice tab in GParted and create a new partition table of your choice.

---

### Post by oldfred on 2019-03-07
If mounted as loop device, it either is a hybrid drive which dd creates when your make a live installer drive or you just formatted drive, not a partition.

This will work for any drive that has no partition table, but if you run this on any valid drive, it will destroy your data.
 Reset USB flash that was dd'd to make it usable again
[https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266](https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266) & 
[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive)

---

### Post by john5757 on 2019-03-12
Thanks people, I'll give it a try Rgds.

---

