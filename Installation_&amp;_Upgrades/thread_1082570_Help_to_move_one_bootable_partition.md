---
title: "Help to move one bootable partition"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by nowhere@cox.net on 2009-02-27
Hi,

I have a dual boot laptop (Vista/Intrepid) with a third bootable recovery partition (which is actually a stripped down XP system). I backed up the third partition with dd already but I was wondering how I could clone it all by itself on to a new hard drive then get it bootable again so I could use it to restore the vista installation it contains.

I can dd the image onto the hard drive but I'm not sure how to deal with the MBR so that it will boot. I've seen some grub resinstallation howto's and I bet I can do that no problem but this doesn't fix the windows booting tho from what I understand.

Once this is done I will "install" Vista then do a fresh Intrepid install.

Any help?
THANKS!

---

### Post by lindsay7 on 2009-02-28
Are you familiar with Acronis Home 2009 for clonings windows system drives?

---

### Post by caljohnsmith on 2009-02-28
One of the problems with dd is that it doesn't make the necessary changes to the partition table on the destination drive when you copy the partition over, so unless your destination partition is exactly the same size as the source partition, you will run into problems; thus it is important to manually set up the correct partition on the destination drive first. Another issue might be that the disk signature on your destination drive will be different than that of the source drive, and I've read that Vista uses that disk signature, so if it is different, it causes Vista problems. So it might be good to copy over the disk signature too. Is the destination HDD entirely empty, or do you have other partitions on it? How about posting the output of:
```
sudo fdisk -lu
```
Please identify your source drive and partition, and also which is the destination drive. Also, is the source drive and destination drive both the same type, i.e. IDE or SATA, or are they different? And are you trying to restore Vista to the destination drive I assume?

---

### Post by nowhere@cox.net on 2009-03-02
In fact what I would like to do is move only the restoration partition from my current drive which is triple boot, Restore, Vista, Ubuntu. The way I would like to do it is to move ONLY the restore partition, then restore the factory Vista, then run the LiveCD install. 

What I have ended up doing is to dd the entire small drive to the big one. Then I used Ubuntu LiveCD to wipe out the Vista and Ubuntu partitions. Then restore Vista. The first trial I did not wipe the partitions and the restore picked one (the wrong one) to which to restore Vista. A bonus was that I was able to resize all the partitions, rounding to cylinders since coming from the factory, the restore partition was off a bit and every partition after that was too. 

In any case, these seems to work fine and in fact I like not having to mess with the MBR.

---

