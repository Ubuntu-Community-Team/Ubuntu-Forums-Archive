---
title: "Best configuration to install"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by paiorlolo on 2009-09-12
Hi, I have an AMD Atholn dual core 2.1 GHz, 3 GB ram, 320 GB free space (laptop).

I'd like to have both installed: Windows XP and Ubuntu Jaunty.

Correct this please:

I'm planning to have three partitions
1) Windows XP OS
2) Ubuntu Jaunty OS
3) FAT Partition (for storing data)

a) How do u suggest to manage the 320 gb free space in those 3 partitions? (and also how much for the swap partition?) - Software should be installed in the respective OS partitions (not in the data partition, i know it depends on which programs i'm going to install... but aproximately for some office usage) (only big games will be installed in data partition)
b) is it ok to have it in FAT partition? So i can access from, both, XP and Jaunty... (could it be NTFS?)

thanks! :D

---

### Post by cariboo on 2009-09-12
If you have nothing installed, I would suggest a 50Gb partion for Windows, a 50Gb partition for Ubuntu and the rest 220Gb NTFS for data.

---

### Post by paiorlolo on 2009-09-12
> **cariboo907 said:**
> If you have nothing installed, I would suggest a 50Gb partion for Windows, a 50Gb partition for Ubuntu and the rest 220Gb NTFS for data.

NTFS? will I be able to read and write from linux that partition?
And how much for the swap? (in addition to the 50 gb of linux)

---

### Post by falconindy on 2009-09-12
> **paiorlolo said:**
> NTFS? will I be able to read and write from linux that partition?
And how much for the swap? (in addition to the 50 gb of linux)
Rule of thumb: Linux can do anything Windows does, and then some. It will happily read and write to NTFS partitions.

4gb should be plenty for a swap partition. It's generally recommended that your swap partition is twice the size of your total RAM.

---

### Post by hyperAura on 2009-09-12
it is stated in some forums that swap should be double the physical memory but in my opinion 4 gb should be ok as falconindy said..

---

### Post by paiorlolo on 2009-10-06
Thank you all for your answers ^^

---

