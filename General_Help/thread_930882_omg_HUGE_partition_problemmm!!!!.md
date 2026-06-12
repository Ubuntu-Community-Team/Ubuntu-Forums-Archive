---
title: "omg HUGE partition problemmm!!!!"
date: 2008-09-26
forum: General Help
---

### Post by Hoaxe on 2008-09-26
I'm having a huge partition problem right now. I only noticed when my windows partition was getting a BSOD when trying to load windows.

when the BSOD happened, i thought no problem because dell gave me windows cd with the laptop. So i open the partition manager and, to my horror, NONE OF MY PARTITIONS ARE VISIBLE!!! oh man i am freaking out. and I just got this design job on a deadline so tight it could choke a microbe!

the partition editor is showing me my entire 150GB hardrive as unallocated. clearly this can't be true since I am using it. furthermore, the Device information is telling me that the DiskLabelType is unrecognized. If i want to set a DiskLabel, it will erase all my data!!!!:(:(

I even tried booting on a live CD and the partition editor gave me the same deal.

I also just noticed that, nautilus is showing me 3 mount points, except one of the mount points is shown twice as a duplicate for some reason, but the other one is fine. All the mount points (even the duplicates) mount correctly as they always did. the only difference is one of them is doubled, literally putting a file in one makes it appear in the other. 

Am I going to have to backup and restore??? that is going to suckkkk so hardddd!!!

I need some help :(

clarify:

it's not so much the fact that windows doesn't start. It's that I can't erase that partition to re-install it.

that is the big issue. If the partition editor can not see any of my partitions, even on a live CD, that's a big problem no?

---

### Post by russlar on 2008-09-26
Sorry dude. BSOD's happen when using Windows.

---

### Post by oilchangeguy on 2008-09-26
> **russlar said:**
> Sorry dude. BSOD's happen when using Windows.

very helpful.

---

### Post by Hoaxe on 2008-09-26
ok, how do i reinstall windows if there are no perceivable divisions in my hard drive!!!!

pointing out that windows BSODs helps in no way with the matter of the missing partion data and shows that you didn't read my post at all but rather took a pot shot at microsoft on a linux forum.

---

### Post by oilchangeguy on 2008-09-26
> **Hoaxe said:**
> I'm having a huge partition problem right now. I only noticed when my windows partition was getting a BSOD when trying to load windows.

when the BSOD happened, i thought no problem because dell gave me windows cd with the laptop. So i open the partition manager and, to my horror, NONE OF MY PARTITIONS ARE VISIBLE!!! oh man i am freaking out. and I just got this design job on a deadline so tight it could choke a microbe!

the partition editor is showing me my entire 150GB hardrive as unallocated. clearly this can't be true since I am using it. furthermore, the Device information is telling me that the DiskLabelType is unrecognized. If i want to set a DiskLabel, it will erase all my data!!!!:(:(

I even tried booting on a live CD and the partition editor gave me the same deal.

I also just noticed that, nautilus is showing me 3 mount points, except one of the mount points is shown twice as a duplicate for some reason, but the other one is fine. All the mount points (even the duplicates) mount correctly as they always did. the only difference is one of them is doubled, literally putting a file in one makes it appear in the other. 

Am I going to have to backup and restore??? that is going to suckkkk so hardddd!!!

I need some help :(

have you tried booting into safe mode? when the computer starts press F8, when the menu appears, select safe mode. and see if windows will start that way. and have you made any changes to windows? bsod's just don't happen for no reason. most likely a driver problem.

---

### Post by Hoaxe on 2008-09-26
> **oilchangeguy said:**
> have you tried booting into safe mode? when the computer starts press F8, when the menu appears, select safe mode. and see if windows will start that way. and have you made any changes to windows? bsod's just don't happen for no reason. most likely a driver problem.

it's not so much the fact that windows doesn't start. It's that I can't erase that partition to re-install it.

that is the big issue. If the partition editor can not see any of my partitions, even on a live CD, that's a big problem no?

but i will try your advice anyways and see what happens.

---

### Post by Hoaxe on 2008-09-26
> **oilchangeguy said:**
> have you tried booting into safe mode? when the computer starts press F8, when the menu appears, select safe mode. and see if windows will start that way. and have you made any changes to windows? bsod's just don't happen for no reason. most likely a driver problem.

it didn't help.

i didn't really expect it to.

this is really going to suck if i can't get the partition editor working again...

---

### Post by EmanresuusernamE on 2008-09-26
Here's the thing, are you looking to recover the data from your windows partition, or do you just want to flat out start all over again?

If you want to start all over again and gparted detects your drive, but doesn't say that you have any partitions, then just create a new set of partitions.  If you want to save your data first, try booting the windows installation CD and see if chkdsk can help you out.  If it can detect the drives, perhaps it can repair them as well.

---

### Post by EmanresuusernamE on 2008-09-26
Also, for windows XP to properly find some disks without drivers, you'll need to play with the bios settings and remove the SATA enhancements.  Then windows XP should detect them.

---

### Post by Hoaxe on 2008-09-26
i got gpart to guess my partition, i'm using this article:
[http://www.linux.com/feature/57748](http://www.linux.com/feature/57748)

gpart returned an error which helped me find a related thread on the help forum here from not too long ago, no solutions seems to be confirmed, either in title or in post but i am on a good route i feel: 
[http://ubuntuforums.org/showthread.php?p=5747825](http://ubuntuforums.org/showthread.php?p=5747825)

---

### Post by caljohnsmith on 2008-09-26
If you want to try and rescue your current Windows, you could rebuild the HDD's partition table with "testdisk". But if you don't care about the Windows that is on your HDD, I agree with EmanresuusernamE, I would just wipe the HDD clean and repartition it with gparted. If you would like specific instructions of how to go about any of this, including using testdisk, let me know.

---

### Post by louieb on 2008-09-26
Please post your partition table.
Application>Accessories>Terminal
```
sudo fdisk -l
```(lowercase L at the end)

---

### Post by Hoaxe on 2008-09-26
> **louieb said:**
> Please post your partition table.
Application>Accessories>Terminal
```
sudo fdisk -l
```(lowercase L at the end)

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           19132       19457     2618563+   c  W95 FAT32 (LBA)
/dev/sda2   *           1        2168    17414428+   7  HPFS/NTFS
/dev/sda3            6886       19457   100984590    f  W95 Ext'd (LBA)
/dev/sda5           19132       19457     2618563+  dd  Unknown
/dev/sda6            6887       18437    92783376   83  Linux
/dev/sda7           18438       19131     5574523+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by Hoaxe on 2008-09-26
gpart was of no help, kinda looking for a lifeline here... why isn't gparted seeing my partition table?

---

### Post by louieb on 2008-09-26
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        2168    17414428+   7  HPFS/NTFS
/dev/sda3            6886       19457   100984590    f  W95 Ext'd (LBA)
/dev/sda6            6887       18437    92783376   83  Linux
/dev/sda7           18438       19131     5574523+  82  Linux swap / Solaris
/dev/sda1           19132       19457     2618563+   c  W95 FAT32 (LBA)
/dev/sda5           19132       19457     2618563+  dd  Unknown

Partition table entries are not in disk order

```I've rearranged the fdisk output in start order. Two things are wrong with the table one minor and one major.   

The major one is primary partition sda1 is inside extended partition sda3. 
That alone will cause GParted and all of the parted based partition programs to see that something is wrong and  is why GParted reports you have a empty disk. 

The 2nd problem is sda5 and sda1 are on the same area of disk.

I agree with** caljohnsmith** suggestion of using testdisk. What I would do is download, burn and boot to a  [SystemRescueCd]("http://www.sysresccd.org/Main_Page")  and run the program called **testdisk**. I belive testdisk will be the easiest way to fix your partition table.  testdisk has some  diagnostic tests thats the next thing I would run.   

fdisk could fix it too. but fixing it with fdisk not an easy task. 
[Partitioning with fdisk]("http://tldp.org/HOWTO/Partition/fdisk_partitioning.html")
[Recovering a Deleted Partition Table ]("http://tldp.org/HOWTO/Partition/recovering.html")

---

