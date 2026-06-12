---
title: "Installing Disk Partition Question"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by looi76 on 2008-12-05
[SIZE="3"][FONT="Georgia"]Hi,
   I want to install Ubuntu Linux on my computer. My hard-disk is divided into four partitions. On the first partition I have Windows XP Professional 32-bit installed on it. On the third and forth partitions I have files on them and on the **Second partition** I want to install Ubuntu. Now, in Ubuntu installation I have reached this part:

[IMG]http://img154.imageshack.us/img154/2594/05122008304qf3.jpg[/IMG]

If I continue, will Ubuntu be installed on the second partition?[/FONT][/SIZE]

---

### Post by jenkinbr on 2008-12-05
No.  What that is going to do is resize your second partition to it's minimum and then use the freed space. It's almost Identical, but not what you want.

To do what you want it to do, you will need to select the manual partioning option and click next.

After scanning devices, you should be presented with a list that has entries similar to the following: 
```
/dev/sda1
/dev/sda5
/dev/sda6
/dev/sda7
```

There will be a few other things in there as well, just ignore them for now.

Right-click on the entry for /dev/sda5 and select the edit option.

Change the settings for it to :
Use as >> ext3
Mount point >> /
Format? >> Yes [x]

Let us know if you have further questions.

---

### Post by theozzlives on 2008-12-05
In Ubuntu, you can have up to 4 Primary Partitions (sda1-sda4) and unlimited number of extended (sda5+) you want an extended for /swap and at least 2 primary (/ and /home). My root (/) is 10 GB and /home is 139 GB. I'd make /swap about 512 MB.

---

### Post by looi76 on 2008-12-05
Thnx, it worked :grin:

---

