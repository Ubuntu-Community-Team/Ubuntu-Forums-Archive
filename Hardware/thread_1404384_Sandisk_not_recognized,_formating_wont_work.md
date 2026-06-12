---
title: "Sandisk not recognized, formating wont work"
date: 2010-02-11
forum: Hardware
---

### Post by caspertk on 2010-02-11
I dual boot with Windows and Ubuntu. I have a Sandisk Cruzer 2GB, that shows up in Ubuntu but not in Windows. I can read files, and copy them FROM the drive but not to the drive. It tells me there's not enough space. I tried removing files from the drive to make space for other files, but it still wont let me write to it. 
When i go into windows it tells me the device is unknown and doesn't recognize it. 
I used a bootable partition manager and formatted the drive 3 times. I tried NTFS, FAT32, and FAT16. I tested each one of those in windows, and i couldn't bring up the drive. 
I went into device management and tried to install the newest drives, but it said there was no better software than what I had on it. There's nothing on it...   -.- 
Should i just junk this thing? Or can anyone help me?

Toshiba Satellite A305
Dual boot: XP (sp3) & Ubuntu(9.04)
Sandisk Cruzer Micro 2GB

---

### Post by theozzlives on 2010-02-11
I have a Cruzer that came with that encription stuff. I just deleted that and it works fine.

---

### Post by caspertk on 2010-02-11
I did that when I first got it. But that's not the problem. There's nothing on it right now.

---

### Post by kelvin spratt on 2010-02-11
I had a similar  problem with win7 I got round it by making the partition bootable then it worked fine.
I also got the same problem with my mp4 player in win7 did the same. 
No problems in Linux.

---

### Post by caspertk on 2010-02-11
How would I make the partition bootable? Would that work between xp and ubuntu?/

---

### Post by redbook4574 on 2010-02-11
> **caspertk said:**
> How would I make the partition bootable? Would that work between xp and ubuntu?/

Use gparted in linux mark partition as bootable.

---

### Post by Manyette on 2010-02-11
> **caspertk said:**
> I did that when I first got it. But that's not the problem. There's nothing on it right now.

If there is nothing on it, I would suggest that you format it with ubuntu and use the "VFAT" format, which should be compatible with everything.

---

