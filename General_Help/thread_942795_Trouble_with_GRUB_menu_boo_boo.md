---
title: "Trouble with GRUB menu boo boo"
date: 2008-10-09
forum: General Help
---

### Post by Racecar56 on 2008-10-09
Help! I installed Ubuntu hardy LTS on a HP Pavilion a6300f, I made a partition using the build-in partiton editor with Ubuntu's install program off of the live cd. The computer came with Windows 6.0 (vista home premium no sp1) and GRUB added a line to start the recovery instead of windows. I added a line with these options:

root  (hd0,0)
savedefault
makeactive
chainloader +1

When I boot it, it says:

Error 13: Invalid or unsupported executable format

Press any key to continue..._

Please help! :confused:
Thank you!

EDIT: More specific.

---

### Post by caljohnsmith on 2008-10-09
How about first posting:
```
sudo fdisk -lu
```
And we can work from there.

---

### Post by Racecar56 on 2008-10-09
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa1a27cd1

Device Boot Start End Blocks Id System
/dev/sda1 63 946644319 473322128+ 82 Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 946646190 956879594 5116702+ 83 Linux
/dev/sda3 956884320 976967119 9941400 7 HPFS/NTFS
Partition 3 does not end on cylinder boundary.

---

### Post by porchrat on 2008-10-09
You can boot from the liveCD...mount the HDD and then replace menu.lst with the backup (if you didnt create one then gedit should've provided one named menu.lst~)

---

### Post by caljohnsmith on 2008-10-09
OK, open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following at the end of the file:
```
title  Windows Vista
root (hd0,2)
makeactive
chainloader +1
```
Reboot, and let me know what happens when you choose it from the Grub menu.

---

### Post by Racecar56 on 2008-10-09
Error 13: Invalid or unsupported executable format

Press any key to continue..._

Same old rabbit hole... sigh.

---

### Post by caljohnsmith on 2008-10-09
> **Racecar56 said:**
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total [COLOR="Red"]976773168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa1a27cd1

Device Boot Start End Blocks Id System
/dev/sda1 63 946644319 473322128+ 82 Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 946646190 956879594 5116702+ 83 Linux
/dev/sda3 956884320 [COLOR="Red"]976967119[/COLOR] 9941400 7 HPFS/NTFS
Partition 3 does not end on cylinder boundary.
I didn't notice earlier, but it looks like your HDD's partition table is corrupt, because according to fdisk above, your Windows partition sda3 ends on a sector beyond the total number of sectors on the HDD. You'll have to try and fix your partition table with testdisk, so first enable all your repositories in System > Prefs > Software Sources (if you haven't all ready), and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", "Y" to search for Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen if you would like help recovering your partition. Also, just so it is easy to compare fdisk with testdisk, please also post:
```
sudo fdisk -l
```

EDIT: I'm so glad you caught that, meierfra, I didn't notice that his swap partition was so large. Unfortunately it looks like he is in a lot of trouble.

---

### Post by meierfra. on 2008-10-09
> /dev/sda1 63 946644319 473322128+ 82 Linux swap / Solaris

You have a 473GB Swap partition. It looks like you formated your Vista partition to Swap
To avoid further damage turn of you swap partition immediately:

```
sudo swapoff /dev/sda1
```

---

### Post by meierfra. on 2008-10-09
> Unfortunately it looks like he is in a lot of trouble.

Actually it is not as bad as it sound like. Formating a partition to swap does not do much damage.  Just change the type of sda1 back to "07" and then run chkdsk  from the Vista CD. I don't have much time right now, but I'm sure caljohnsmith can help you with the details.

---

### Post by Racecar56 on 2008-10-10
I don't have a Vista CD.

---

### Post by caljohnsmith on 2008-10-10
OK, first you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). I think the first step would be to try and recover your correct partition table, and then you can focus on recovering Vista; follow the steps in my previous post to use testdisk, and post back here the results.

---

