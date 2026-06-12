---
title: "More than one fllesystems"
date: 2012-02-08
forum: Hardware
---

### Post by hkyng on 2012-02-08
I printed my screen here (below), on the top left there are 5 diff systems and i want to get rid of it because i believed it is making my net and laptop slows. How do i get rid of it? FYI: I replaced windows with Ubuntu 11.10 and it shows up like that. 
 

[IMG]http://i157.photobucket.com/albums/t51/meeyang_album/Filesystems.png[/IMG]

---

### Post by wojox on 2012-02-08
I can't see the picture. You have five diffrent partitions?

---

### Post by hkyng on 2012-02-08
I fixed it. Thanks for telling me.

I dont know if they are partitions or not but they said filesystem.

---

### Post by Bucky Ball on 2012-02-09
Welcome. Yea, partitions. Just not named so default to 'Filesystem'. 

Please mark thread as solved from 'Thread Tools' at top right (if your problem is solved that is) to help others. Also, a brief description of how you fixed your problem would be helpful to others. ;)

---

### Post by hkyng on 2012-02-09
my question was how do i get rid of it because i think it is slowing my netbook down.

---

### Post by jayshomebrew on 2012-02-09
If you want to delete those partitions, use disk utility.

1. you can get there by typing "disk utility" as shown:
[IMG]http://img546.imageshack.us/img546/3209/tmplf8zmq.png[/IMG]

2. then selecting the offending partions and selecting "delete partition" shown below.

**Warning:** Do not do this if you are _not sure of what you are doing._
Please read [https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition") and 
[http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/]("http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/")

[IMG]http://img515.imageshack.us/img515/8733/tmppzzpo6.png[/IMG]

---

### Post by hkyng on 2012-02-10
Well my SMART status says "Disk has a few bad sectors" and when I pressed SMART Data run self check #5. It shows...

Reallocated Sector Count 
Count of remapped sectors. When the hard rive finds a read/write/verification error, it marks the sector as "reallocated" and transfers data to a special reserved area (spare area)

Assessment is WARNING 

Value: Normalized 100; Worst 100; Threshold 10; Value 7 sectors.

I am clueless. What is wrong?

---

### Post by jayshomebrew on 2012-02-11
When hard drives are produced, they go thru an analysis stage, where sectors are analyzed, and firmware is updated to use valid sectors.  As the drive goes thru its normal lifecycle, more sectors can fail, and the firmware updates itself, recognizing those bad sectors and using good ones.  You can read this two different ways, one being that the drive is failing, and you should replace it. The other way is that your drive is just fine, and it is self-correcting (doing its job).  I would view this as the latter, and keep track of your drive as it corrects itself.  If these log messages continue to increase, I would be concerned of the drive's life and replace it.
You can download software that can do analysis of your drive from the manufacturer of the drive. search google for these:
seagate: seatools
western digital: lifeguard
hitachi: drive fitness test

---

