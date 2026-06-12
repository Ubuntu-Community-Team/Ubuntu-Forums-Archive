---
title: "Partition Trouble"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by Spunkbubble on 2009-04-05
Hi,

I'm trying to install Ubuntu 8.10 on a partition with Windows Vista. I've got a roughly 900 GB hard drive, and I shrunk the Vista partition in Windows using the hard drive manager tool, so I should have around 85 GB of space for Ubuntu.

However, when it comes to installation, I see the following screen:
[IMG]http://http://filesocket.com/download/20cInstallation_Trouble[/IMG]
As far as I can tell, it's not recognising either an 85 GB partition or my entire 900 GB hard drive, only these 2 which don't exist.

Do I just really have the wrong end of the stick here?

---

### Post by taurus on 2009-04-05
From Ubuntu LiveCD, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Spunkbubble on 2009-04-05
Thanks for the fast response.

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b0cee50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      110455   887224316    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

---

### Post by taurus on 2009-04-05
You have two harddrives on your machine?  Which harddrive did you modify, making room to install Ubuntu?

Otherwise, you can open gparted (System -> Administration -> Partition Editor) and have a look at your /dev/sda & /dev/sdb.

---

### Post by Spunkbubble on 2009-04-05
I have only one hard drive, not two :?

I'll have a look now.

---

### Post by Spunkbubble on 2009-04-05
Ok, I've had a look at both and this is what they look like:
```
**/dev/sda**
Partition: unallocated
Filesystem: unallocated
Size: 465.76 GiB
Used: ---
Unused: ---
Flags:

**/dev/sdb**
Partition: unallocated
Filesystem: unallocated
Size: 465.76 GiB
Used: ---
Unused: ---
Flags:
```

---

### Post by taurus on 2009-04-05
Can you post a screenshot of gparted (Applications -> Accessories -> Take Screenshot)?

---

### Post by Spunkbubble on 2009-04-05
Same information shows up with both.

---

### Post by taurus on 2009-04-05
Somehow gparted thinks the whole harddrive is unallocated.  Since you use vista to shrink your harddrive, can you create a partition and format that unallocated space to something like fat32 or ntfs.  Now see if gparted from Ubuntu LiveCD can detect both partitions.

---

### Post by Spunkbubble on 2009-04-05
Alright, I'm in Vista right now formatting the partition. The only option available was NTFS rather than FAT, will that make a difference?

---

### Post by Spunkbubble on 2009-04-05
I've formatted the partition, labelled it "G", and it's recognised as being blank and the correct size in windows "my computer" GUI, but Gparted still gives the same information on both /sda and /sdb.

---

### Post by ronparent on 2009-04-05
Hey guys, this looks suspiciously like a raido array! Window sees it as a sigle hard drive. Gparted from a live cd will see it as two unformatted disks. Under those circumstances formating in windows which already has the raid drivers installed you will get the correct results. If you try to run an install from the desktop install cd you will destroy the array!!! Once you take note of this situation you will have to perform an install from the alternative cd.

---

### Post by ronparent on 2009-04-05
Look at the drop down box with sda in it and verify rhat sdb exists in the drop down.

---

### Post by Spunkbubble on 2009-04-06
Yeah, it exists alright. :)

It's still exactly the same as sda.

---

### Post by ronparent on 2009-04-06
Now if you do the arithmetic, your 'hard drive' capacity is the sum of the two parts. They work in unison as a raid array and the whole array (with your windows installation and data) will be lost beyound recovery if you try to format it with gparted. This in itself is not a grievious fault in linux/ubuntu since the software exist on an alternate install disk that would permit recognition and reformatting of raid arrays with gparted without breaking the array. 

Fortunately I averted disater, in my case, by installing to a small (50 Bb) separate drive I had put into my system for that purpose. Because that had worked around the problem I am not familiar enough with installing ubuntu directly to a raid0 system to advise you on how to. I suggest you post on that specific topic (help installing to raid0). This is still a rare and obscure problem in the installation forum community, but probably the best place to post since the server forum advice may overwhelm you with technical detail. You may have to bump a few times to get attention. Good luck, and. may the ubuntu gods be with you.

---

### Post by mundackal on 2009-04-06
Even i too hav this issue. i am new to linux. i have a Laptop with Vista made a partition and installed ubuntu 7.10. it was ok.then i did a windows defragmentation and now i cant login to ubuntu.it hangs on a dos kind of window. Why so. and how can i get the updates of ubuntu with wireless networks

---

### Post by Spunkbubble on 2009-04-06
Ok, well I'm glad I posted here then before doing anything stupid :)

Where do you advise I repost this?

---

