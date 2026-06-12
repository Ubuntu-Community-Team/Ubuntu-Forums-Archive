---
title: "How to change stripped array to RAID5 array"
date: 2015-08-11
forum: Hardware
---

### Post by cwsmittenaar2 on 2015-08-11
I'm running Ubuntu 14.04 on a HP desktop for a multitude of reasons. (It's basically my test bed, and to keep my fingers in Ubuntu.)

I am trying to setup a RAID5 array. I was able to attach 3 USB drives of equal size (32GB) and configure them as a striped set in the LVM manager. Now I am having trouble locating any instructions on how to convert this to a RAID5 to protect the data. The OS is on the internal HDD of the PC along with the swap and other normal partitions. This is in preparation of setting up a new machine with a larger USB-RAID5 configuration so this is a learning setup.

Thanks for any and all help!

---

### Post by TheFu on 2015-08-11
Backup all the data.
Make the RAID set you want (I think this is a bad idea on USB)
Restore all the data to the RAID disks and wait.

I wouldn't leave it there long.  If I cared about the data, I'd use RAID1 and look to moving it to SATA or eSATA connected disks ASAP.

I've had some terrible luck with USB2 and USB3 devices, so perhaps I'm biased against it.

---

### Post by cwsmittenaar2 on 2015-08-12
Thanks for this reply. I am considering the USB as an alternative to SATA due to cost as I am retired and on a fixed income and can build up the required array over time. as opposed to the higher cost of the drives for the SATA array. I would think that having the USB devices in a RAID5 array would overcome the data loss problem as the use for this array is basically static data. (Data that will be seldom written to but read more often.) Unlike databases and documents from most businesses that are constantly changing, where the SATA drives are a definite bonus. Once the arrays are in place the back up system will be the next thing to be "revamped".  All a very slow process for us retired folks. ;)

---

### Post by TheFu on 2015-08-12
a) I retired from normal work about 8 yrs ago. I understand.  Plus we each have different priorities for our money in life.

b) SATA isn't anything special. It is what the drives inside those cheap USB enclosures are. I suspect you are thinking SAS, which are more expensive and have both higher performance AND longer warranties. USB drives often come with 90 day warranties, which is why they are so cheap.  The exact same drive, without the enclosure, will have a 1 yr or 3 yr warranty and be sold for 20% higher price.  It is a gimmick to save the vendor money by pushing failure risks to the purchaser quicker.  Having been screwed multiple times, I try to get 5 yr warranty disks now. That tiny bit extra cost is worth it to me to avoid the hassle of dealing with disk replacements 2x more often.

c) As you know, RAID never replaces backups. Actually, get the backups working before the RAID.  Bitrot happens on RAID sets too. So if data isn't re-written from time to time, it will be lost. Also, software RAID5 is slow - even over USB3. I force RAID re-checks weekly. One is running right now:
```
md1 : active raid1 sdc3[0] sdd3[2]
      1943010816 blocks super 1.2 [2/2] [UU]
      [====>................]  check = 22.9% (445535872/1943010816) finish=292.7min speed=85254K/sec
      
```

Thought I'd give a few more alternatives ... 

d) External JBOD enclosures don't have to be expensive.  Think $180, not $500.  Start with a cheap internal enclosure like this [http://www.amazon.com/Rosewill-5-25-Inch-3-5-Inch-Hot-swap-SATAIII/dp/B00DGZ42SM/](http://www.amazon.com/Rosewill-5-25-Inch-3-5-Inch-Hot-swap-SATAIII/dp/B00DGZ42SM/) that takes (3) 5.25 slots and puts (4) 3.5inch disks there for $45. **Wish I would have gotten a few of these years ago.**  Cheap PCIe JBOD SATA ports can be added to most systems if you've already used the 6 built-in SATA ports. For external enclosures there are options: [http://addonics.com/products/rtmpm6g.php](http://addonics.com/products/rtmpm6g.php) - picked up an earlier version of one of these for $120 years ago. I'd probably visit a used computer store for tower cases to find one with (6) 5.25inch bays for $5 - add an 80+ PSU then get an eSATA adapter from Addonics ($99). The right case can hold 20 drives if you plan ahead on the cooling.

Anyway - a few options for your consideration.

I found RAID5 added complexity (and issues that result during a failure) aren't worth it. Might want to search these forums for all the people looking for help with their RAID issues. BTW, I ran RAID5 for years at home - mostly just for the experience. Had a few failures in the beginning due to vibrations. Always had backups.  I never needed the backups except for user error (deleting the wrong files). These days all the RAID5 has been replaced by RAID1 for important stuff.  For media files, I don't use RAID, rather I have excellent backups.

Of course, I'm just 1 data point. Lots of people seem to be using RAID with USB. As I read their posts online, it was surprising that more people didn't seem to have issues. [https://serverfault.com/questions/10199/usb-drive-raid-array](https://serverfault.com/questions/10199/usb-drive-raid-array) has some suggestions about putting the USB disks on different buses.

---

### Post by cwsmittenaar2 on 2015-08-12
Thank you for the input. All good things to consider. But I must clear up something that I may not have been clear on, when I indicated USB, I meant the USB flash drives, the ones the people toss around in their pockets and purses or you'd find in the back corners of their desk drawers. Not the SATA drives inside the plastic case with a USB interface. I am looking to build a Large RAID from fairly large USB keys probably in the 256 or larger MB range to make over the TB size when completed for each drive. As the data will be mostly static this should not be a problem I would think, especially if on a calculated/regular basis to extend data/key life run the RAID re-checks as you suggest. Obviously the keys and USB bus would all need to be USB3 for speed. 

Thanks for you input it adds to the necessary base to get this project right and not have to re-do it mid-stream or later.

---

