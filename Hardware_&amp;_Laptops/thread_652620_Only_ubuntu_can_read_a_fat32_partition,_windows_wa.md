---
title: "Only ubuntu can read a fat32 partition, windows wants to format it"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by dapaintballer331 on 2007-12-28
I installed Gutsy to my laptop, and to a ext3 partition on my 4gb flash drive. THe flash drive also has a 1gb fat32 partition, but only ubuntu can use the fat32 drive.

Laptop: 3 Partitions, Vista, Xp, and Ubuntu
Sandisk 4gb Cruzer: 3gb ext3 partition w/ grub, 1gb fat32

I overwrote the flash drive's mbr, so you can boot into grub then ubuntu.
I tried formatting this drive, making fat32 "logical", "primary", ntfs, everything I could think of.

Ubuntu always recognizes the partition, windows doesn't. Windows "paragon partition manager" reads the partitions fine. Windows only sees the ext3 partition, and wants to format it. Paragon&Windows Storage Manger fail to add drive letters to the fat32 partition, saying it "Isn't Enabled". With paragon, I tried "making it active" without any luck. I even had gparted try to repair device problems. No luck. 

Why can't windows read the fat32 (or ntfs when I temporarily changed it) partition? Is it the mbr?

---

### Post by meierfra on 2007-12-28
I just did the same thing on the Cruzer my  son got for Christmas (of course he has 4Gb, I have only have 1GB stick). Took  me a while but this worked at the end:

The Fat32 partition must be the first partition on the hard drive and it needs to have the boot flag.

---

### Post by dapaintballer331 on 2007-12-28
Thanks a lot, I had a feeling that was it, but I thought it might not matter. 

**What is "the boot flag"?**

PS. On ebay they have lots of brand new 4gb Cruzers for around $25 shipped. I bought two. Best thing about these drives is their speed, most drives aren't nearly fast enough to run an os on one. I can hardly notice its on a drive that can only read one thing at a time (compared to a hard drive with multiple disks)

---

### Post by meierfra on 2007-12-29
Actuallly I should have said "a boot flag" (since more than one partition can have a boot flag. Although that is not recommended)

"partition with a boot flag"  means the same as "active partion"

You can set  and remove  boot flags with gparted ( or whatever partition editor you are using)

If you  type "sudo fdisk -l" in a terminal  you will see that some partitions have a "*" in the second place. That are the ones with a boot flag. 

Ubuntu essentially ignores boot flags, but boot flags play a  role in the  Windows world.

---

### Post by dapaintballer331 on 2007-12-29
I deleted the fat32, moved the ext3 partition to the right, and recreated the fat32 partition. As you said, I added the boot flag to the fat32.

Now windows doesn't show either as a drive. I just checked, and it says that the fat32 partition is still sdeb, not a. The order changed, but not partition ids. Is there a way to switch the partition ids? (or does that not matter)

---

### Post by meierfra on 2007-12-29
Actually I had the same problem (sorry forgot). You can fix it with testdisk:

1) Enable the Universe Repository (although you probably already have it enabled)

Go to Systems-> Adminstration->Software Sources"
Click on the Box next to "Community-maintained Open Source Software (universe)

2) Install testdisk
```

sudo apt-get update
sudo apt-get install testdisk
```

3) Start testdisk:
```
sudo testdisk /dev/sde
```

press "enter" on  the first screes to "proceed"
press "enter" on  the next screen to  select "intel"
press "enter" on  the next screen to  select "analyse" 
press "enter" on  the next  screen to "proceed"
     Hopefully both of your partition will be in "green" 
press "enter" on  the next screen to "continue"
Use the right arrow key to select "write" and press Enter.
Press Y to confirm. 
(You can just close the terminal now, or follow the screen to quit the program properly)

That's it.

For more info on testdisk click on testdisk in my signature.

---

### Post by dapaintballer331 on 2007-12-29
I downloaded testdisk for windows earlier with no success. I'll try your guide and see how it goes.

---

### Post by meierfra on 2007-12-29
I just fixed a couple of typos (changed "first" to "next") But  I guess   you would ignore them anyway.

---

### Post by dapaintballer331 on 2007-12-29
Works!

Your testdisk tutorial was pretty straightforward, thanks.

For  the record, here is what I did. *I'm not sure if steps 1&2 are necessary.*
1. Moved the FAT32 partition so it was the first partition on the disk. It is still sde2, but it is the first partition that has data. It is still a primary partition, I didn't need to make it a "logical" or "extended" one.
2. Gave the fat32 partition a boot flag (via gparted)
3. Followed the above testdisk tutorial
4. (In Windows) Control Panel>Administrative Tools>Computer Management>Storage>Disk Management. Then right clicked the drive with the blue icon, selected add drive letter, and it worked.

---

### Post by meierfra on 2007-12-29
> Works!

Good!

> 
I'm not sure if steps 1&2 are necessary.

Interesting question. Maybe the fat32 partition  just has to be first in the partition table.

And the boot flag might not be necessary either.

I'll to some testing and let you know.

---

### Post by meierfra on 2007-12-29
Bootflag is NOT neccessary.

Next test will take a little longer.

---

### Post by meierfra on 2007-12-29
You were right: Step 1.  isn't necessary either.

Although Step 3 does not work without Step 1. Instead I used fdisk to   rewrite the partition table  (maybe there are better ways to do that but I don't know).

To summarize:

For windows to access a  partition on flash drive:

a)  The partition must  be  listed first in the partition table. 

b) The partition does NOT need a boot flag.

c)  The partition does  NOT  have to be  physically the first partition on the drive.


Of course it is easiest to achieve a)   during the initial partitioning of the flash drive.

---

