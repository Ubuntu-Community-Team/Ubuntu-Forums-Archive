---
title: "Extra partitions question"
date: 2013-12-15
forum: Hardware
---

### Post by corbettlarsen on 2013-12-15
In installing other distros in the past I have accumulated a few extra partitions that I don't need but I'm not exactly sure which ones to delete/reformat so I can dual-boot ubuntu.
Here is a picture of my situation. 
[ATTACH=CONFIG]248614[/ATTACH]

---

### Post by carl4926 on 2013-12-15
You should boot up Ubuntu if you have it installed or use the live cd and take a screen in Gparted

---

### Post by Bucky Ball on 2013-12-15
Welcome

> **carl4926 said:**
> You should boot up Ubuntu if you have it installed or use the live cd and take a screen in Gparted

+1. Yes, as your pic means not a lot re. your Ubuntu partitions as Windows can not read them. Gives us no information. Gparted screenshot best.

---

### Post by corbettlarsen on 2013-12-15
Here is the table in Gparted.
[ATTACH=CONFIG]248632[/ATTACH]

---

### Post by oldfred on 2013-12-15
You only have one Linux partition and swap. I do label my partitions with gparted when I create them or when I forget I then use Disk Utility or Disk in new versions.
Lenovo's seem to add one or two extra. They put repair efi files in a second FAT32. 

All the rest of the partitions are a typical Windows UEFI install.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by carl4926 on 2013-12-15
I have to confess, it's very messy.
I really dislike these OEM installs. And I wouldn't like to say what could be removed.

---

