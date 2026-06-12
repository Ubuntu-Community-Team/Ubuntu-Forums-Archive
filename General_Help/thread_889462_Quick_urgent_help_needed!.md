---
title: "Quick urgent help needed!"
date: 2008-08-14
forum: General Help
---

### Post by VengeZ on 2008-08-14
Ok well i want to dual - boot
Ok, well on Vista, I created a partition using the quick way..

this is the way I did it..
I have 500GB HDD
1)Right click computer > manage
2) Disk management
3) Created the partition..

I named it G:, and its ntfs (149GB), its called ubuntu, but im on the manual install and no idea and what to click and what to put in the boxes?? 

please help i'm really a newbie :(



(SORRY ABOUT PICTURES, NO IDEA HOW TO CROP, REALLY SORRY!)
[IMG]http://i33.tinypic.com/24fahab.png[/IMG]
[IMG]http://i35.tinypic.com/rlwft1.png[/IMG]

---

### Post by VengeZ on 2008-08-14
need quick help please :(, i need to get this done before I do my night shift

---

### Post by geenux on 2008-08-14
> 
I named it G:, and its ntfs (149GB), its called ubuntu, but im on the manual install and no idea and what to click and what to put in the boxes??

It must be an ext3 partition which have "/" for mount point
- one partition swap (~1go)
- eventually one partition "home" which contains your Ubuntu documents and configurations

---

### Post by mcduck on 2008-08-14
Remove that partition, and then either let the installer create the necessary partitions into the empty space, or create yourself a / partition, with Ext3 file system, and a swap partition.

(you'll need 2 partitions for Ubuntu, one is not enough. And NTFS won't work for Linux system partition, it's not able to handle Linux-style file permissions and ownerships)

---

### Post by VengeZ on 2008-08-14
What size should these be, (out of 140G)

---

### Post by sayakb on 2008-08-14
Keep the / about 20GB (Though personally, 10GB is enough), the swap = 2* RAM size (or same as your RAM size) and the rest as /home.

---

### Post by sayakb on 2008-08-14
Plus, while posting threads, keep these in mind:
1. Give your thread a descriptive title (unlike "n00b here" or "need help")
2. Use the attachments button to add images :) (the *clip* icon towards the right side of the smiley icon..)

Welcome to the forums :)

---

