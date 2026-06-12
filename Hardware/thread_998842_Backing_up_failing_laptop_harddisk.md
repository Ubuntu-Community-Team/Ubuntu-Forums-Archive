---
title: "Backing up failing laptop harddisk"
date: 2008-12-01
forum: Hardware
---

### Post by Fake51 on 2008-12-01
First off, my apologies if I haven't searched the forums enough - however, I couldn't find a thread that matched quite what I'm looking at.

Basically, I've got a dell xps m1330 with a failing drive. It doesn't have bad sectors, it just doesn't like the general idea of getting up in the morning. Hence, all data appears to be in ok shape and I can get access to it. About time to do a backup and get a new drive.

I've ordered a 320GB drive and I want to clone my old disk onto it. The current setup looks like this:

60GB WinXP install
80GB Ubuntu
XGB various (dell media stuff etc)

I would much prefer copying the partitions as they are and either just add the rest of the space as a new partition or enlarge the ubuntu partition later on. Would dd be the best tool for this? Or is there something superwicked the does the job with less chance for me to mess it up?

And, a very important part: everything is on a laptop so I can't mount the two drives at the same time in desktop style. Instead I'm thinking of getting a usb to sataII cable and mounting the new disk that way, then copy things. Does anyone have experience with this? Can anyone point me in direction of a guide to help out? What do I need in order to get this setup working? Should I use systemrescuecd to get access to the system and that way be able to mount both disks without booting on one of them?
 How do I clone EVERYTHING - I'd love to avoid dealing with a disk that isn't bootable after the copy.

Any help at all appreciated.
Regards
Fake

---

### Post by Mizzou_Engineer on 2008-12-01
You will want to purchase a USB-to-SATA adapter so you can connect both drives to the laptop at the same time OR find a desktop with two or three SATA ports and power connectors. You will then connect the new hard drive in the same machine as the old one and then boot from a live CD such as your Ubuntu CD.

Then, you will partition the disk so you have a 60 GB partition, 80 GB partition, and then another partition for free space. dd is an excellent tool to copy the partitions from the old drive to the new one. 

At this point, you will have a clone of your original disk and then another empty partition. If you want to, you can leave this partition alone or you can use gparted and grow your Linux partition to take up that extra space (I know you can grow ext3 and XFS filesystems, not sure about ReiserFS.)

Good luck!

---

### Post by psusi on 2008-12-01
dd is a very dumb tool that is difficult to use correctly and copies EVERYTHING, including free space.  This type of job is much better suited to a smarter utility like partimage.

---

