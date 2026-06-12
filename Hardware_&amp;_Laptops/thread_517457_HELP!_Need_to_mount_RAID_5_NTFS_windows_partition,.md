---
title: "HELP! Need to mount RAID 5 NTFS windows partition, stuck on a readme/howto..."
date: 2007-08-04
forum: Hardware &amp; Laptops
---

### Post by blackjackel on 2007-08-04
Trying to use this thread to sucessfully mount my windows XP NTFS partition.... :

[http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758)

so far: dmraid -r shows all the harddrives and even says raid 5 but I don't know where to go from here as he is telling you how to add partitions, I don't want to do that.. I just want to see my XP partition.

---

### Post by blackjackel on 2007-08-04
am i posting this in the wrong section?

---

### Post by fjgaude on 2007-08-10
All that's left is to mount the raid array. Here's what we suggest you do:

```
sudo dmraid -tay
```

From there you see an ERROR msg showing your device name. Take it and mount to a point you have already created, like:

```
sudo mkdir /media/raid
```

Then mount:

```
mount /dev/mapper/sil_xxxxxxxxxx /media/raid
```

using the part after mapper for your unique situation.

That should do it. If you use sudo mount your array will be at root permission. If you haven't already be sure to study the man pages for dmraid. Then you can place a line in your fstab file so it gets mounted as you boot up. Let us know how you make out, please.

Good raiding,

frank

---

