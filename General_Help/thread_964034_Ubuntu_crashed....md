---
title: "Ubuntu crashed..."
date: 2008-10-30
forum: General Help
---

### Post by Prominence on 2008-10-30
Can I get my stuff back? Somehow? Any possibility? My vista part of the computer can't detect the Ubuntu partition tho...

---

### Post by Wayne_V on 2008-10-30
Can you boot the LiveCD?

---

### Post by Prominence on 2008-10-30
Probably...what will that do?

---

### Post by Wayne_V on 2008-10-30
If you can boot the LiveCD and get to a shell you should be able to fsck your Linux partition and get it to mount.  Then you could either try to correct whatever is wrong so that it will boot again or you could copy the files you want to your windows partition.

---

### Post by Prominence on 2008-10-30
I'll just move it to windows..not sure about reinstalling Ubuntu now.

---

### Post by Prominence on 2008-10-30
Alright...I'm in the live CD boot...so I need your help, I want to get my files out safely, which way do you guys suggest?

---

### Post by Wayne_V on 2008-10-31
Assuming you have one hard drive (sda), here is a rough, untested guide:

Start a shell, then

$ sudo -s (make yourself root)
# fdisk -l /dev/sda
(see which are your windows & linux partitions)
# df -T
(see which are already mounted)
# fsck /dev/sda(x)   
(fsck any Linux paritions that are NOT mounted already -- see man fsck for other options)
# mkdir /mydata ; mount /dev/sda(x) /mydata
(mount your linux partiton)
(If your windows partition is not already mounted:  "mkdir /win ; mount /dev/sda(x) /win"
--- may need to add a fstype to this mount - see man mount if it complains).

Now just copy the files you want from /mydata to /win

---

