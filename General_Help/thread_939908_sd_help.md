---
title: "sd help"
date: 2008-10-06
forum: General Help
---

### Post by Awesomeness on 2008-10-06
how do i add a partition on a SD(2GB) and format it as Ext3?:confused:

---

### Post by ks07 on 2008-10-06
I would use gparted, as long as your careful you don't wipe your hard disk.
If you haven't already got it, it can be found in add/remove programs if you search for gparted. 

Once it is installed you should be able to open it from System>Administration>Partition Editor and then select the SD card and format it in the program.

See this thread for a similar question: [http://ubuntuforums.org/showthread.php?t=408030]("http://ubuntuforums.org/showthread.php?t=408030")

---

### Post by Awesomeness on 2008-10-06
it can't find my sd card:(
only my hard drives

---

### Post by ks07 on 2008-10-06
Hmm, does it show up in Places>Computer? 
Try opening a terminal window and use 
```
sudo fdisk -l
```
then copy and paste the results here.

---

