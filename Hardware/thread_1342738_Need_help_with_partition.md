---
title: "Need help with partition"
date: 2009-12-01
forum: Hardware
---

### Post by fyrlaus on 2009-12-01
Hi!

I have installed ubuntu 9.10. I have a 250gb harddrive that there is 2 partitions on. nr1:80gb(ext4) nr2:170gb(ext4). I have been using windows for some time and the biggest partition as a keeper for music, pictures etc. 

Now I have transfered all my files to the smallest partition, and I want to delete to bigger partition and merge both so I will have only one partition 250gb.

I have tried using gparted and have deleted and formated the biggest partition, but there is no option for merge thoose two. any idea?

If not possible, is it possible to sett my home folder to point to my bigger partition? So all my music, picture etc are stored in my home folder, but are stored in the bigger partition and not on the default loaction which is the smaller partition.

---

### Post by IcarusR on 2009-12-01
A google search led me to this page...
[http://ubuntuforums.org/showthread.php?t=1173282]("http://ubuntuforums.org/showthread.php?t=1173282")

Please not these lines in the above post

> THIS TUTORIAL IS NOT VERY BEGINNER-FRIENDLY. I do not guarantee that this tutorial will work for you as it has for me. Before going any further, backup your system, and read over my tutorial, making sure that you are comfortable with all of these commands. Messing with partitions is dangerous work, and even if done correctly can leave you with a GRUB error or two.



I believe you can 'reset' home mount point by editing /etc/fstab & changing the partition that is mounted as home.

---

### Post by Kevbert on 2009-12-01
Welcome to Ubuntu.
Using gparted just delete the old partition you no longer require. Now you should be able to resize the first partition to any size you like.

---

### Post by Grenage on 2009-12-01
There is no 'merge' option per se, what you can do is:

Delete the 170GB partition.
Expand the 80GB partition to use up the extra space.

---

### Post by fyrlaus on 2009-12-01
I dont see any expand button. Is it via gparted? Livecd?

---

### Post by oldfred on 2009-12-01
Gparted and it is on the liveCD. The partition must be unmounted. Click on the partition you want to change.

---

### Post by Kevbert on 2009-12-01
> **fyrlaus said:**
> I dont see any expand button. Is it via gparted? Livecd?

In gparted once you've deleted a partition you should be able to access the 'Resize' menu option.

---

