---
title: "Splitting disk into two partitions without formatting."
date: 2018-01-05
forum: Hardware
---

### Post by kuskusk265 on 2018-01-05
Hello, I siwtched to Ubuntu from Winodws two months ago. So far, I cant complain, way better... I run Ubuntu from separate 150GB HDD. Then I have another 1 TB HDD which contains 150 GB Windows (C:) partition and then 755GB Data partition (D:, NTFS, linux /dev/sda3) I have mounted the sda3 partition into linux as RW and worked so far so good, but I think I wont be switching back to windows, only occasionally for Games that I cant run in linux... I would like to keep my Windows files from sda3 partition, but have two separate partitions like lets say NTFS windows personal files (450GB) and ext4 partition for linux data (300GB) -  splitting the sda3. So is there anyway how to  the Data partition without having to Format it? Backup is not possible at the moment since I dont have any capable volume. Thanks in advance

---

### Post by sccman on 2018-01-05
There is indeed a way. The easiest way is through GParted.

Install and run GParted:

```
sudo apt install gparted && sudo gparted
```

Then if your drive isn't listed already go to GParted -> Devices -> /dev/sda. Then on the list right click on /dev/sda3 and select resize and enter 286,102 mebibytes (300 GB) for ext4. Do the same for the NTFS partition only using 429,153 mebibytes (450 GB).

---

### Post by kuskusk265 on 2018-01-05
Yes, I tried Gparted, but,well I have around 200GB data i would like to have on ext4 and then around 420GB data for windows, so Gparted wont let me  resize less than used space. And all those files are on the Data drive

---

### Post by sccman on 2018-01-05
Oh okay you're looking to split the Windows partition (which has the games) into two partitions: one with the Windows OS and the other with Games?

---

### Post by coffeecat on 2018-01-05
@kuskusk265, if I am reading you correctly, what you ask is impossible.

You say that you have a 755GB Data partition in which you have your Windows files which you want to keep, but you want to have two separate partitions, one 450GB NTFS, and one 300GB ext4. This sounds as though you want to convert the 750GB NTFS partition into two partitions with different filesystems. If this is what you mean, you cannot avoid formatting something.

sccman has suggested resizing the partition, but in the light of what you say - quoted below - I would strenuously advise you not to do that.

> **kuskusk265 said:**
> Backup is not possible at the moment since I dont have any capable volume. Thanks in advance

**Any manipulation of any kind with any partitioning tool - Gparted included - runs the small risk of something going wrong with consequent data loss. Please do not even think of doing anything with your partitions until you have made adequate backups of your data. If you don't have backup media already, get some.**

You also make this curious comment:

> **kuskusk265 said:**
> 755GB Data partition (D:, NTFS, linux /dev/sda3)

Your sda3 partition is either formatted with NTFS or with a Linux filesystem - it cannot have both at once.

---

### Post by ajgreeny on 2018-01-05
I am slightly confused about what partitioning you want by the time you have finished, and if you want to remove Windows completely.  However, you can not make changes to the filesystem on a partition without formatting

I would also give you a warning that if you keep an NTFS partition on the disk you should also have a windows install in order that you can do any repairs to NTFS that might be needed in future, eg chkdsk, as that is not possible as far as I'm aware in Linux. The utility **ntfsfix**, provided by ntfs-3g, will repair some minor faults but **is not a replacement for chkdsk**.

---

### Post by kuskusk265 on 2018-01-05
Nono, I meant that in Win its D: and in linux it is linked under /dev/sda3. Nevermind. Ill just format it, games are games. I will re-download them. I could stuff photos and music somewhere... Yes I know I made it a bit confusing, I just mean that I want to Split the 750 gb partition into two smaller partitions, one stays NTFS and the scond one will be ext4, I thought it would be impossible, but I tried to ask, you never know.

---

### Post by sccman on 2018-01-05
If you have enough extra space you could shrink the partition and make a second partition, move some games over to it, shrink the partition again, move more games over, and rinse and repeat. It can be tedious but it's quicker than re-downloading all your games.

---

### Post by kuskusk265 on 2018-01-05
This came to my mind too, but it would be very time consuming, but somewhere I saw theres automated script for that. Others said Parted Magic mini distro can do it, but I didnt found it in here. Thank you very much and if anyone knows any script/program that can do this automatically, please let me know.

---

