---
title: "Resizing reinserfs partition."
date: 2005-11-27
forum: General Help
---

### Post by Nevermore on 2005-11-27
I installed ubuntu on my desktop, on a 10Gb partition, now i wish to resize that partition up to 20Gb, how can i do that?
consider that at the end of the 10Gb partition there is the 400Mb swap partition.
i tried many ways but noone seems to work.
Thanks

---

### Post by Randy Sparks on 2005-11-27
You're going to have to use GNU Parted or another partition resizing program that understands ReiserFS. I've never used this so can't offer any advice. You might take a look at Ranish Partition Manager: [http://www.ranish.com/part/](http://www.ranish.com/part/).

You'll have to do it via the rescue mode of the Ubuntu CD to do all this because you can't resize a partition that's currently mounted (ie that's in use). 

It sounds like you'll have to delete the swap partition to make space and then recreate it later on. If the partition order changes, you'll have to update your /etc/fstab file.

---

### Post by magnusbb on 2005-11-27
I wouldn't recommend it! Resizing ReiserFS partitions is dangerous. Last time I did it, i corrupted mine, and had to start all over again. 

I would rather make a new partition in the empty space and mount it as a /usr or /home partition.

---

### Post by kosmic on 2005-11-27
I think you should have looked at LVM in the first time you instaled Ubuntu.

---

### Post by Nevermore on 2005-11-27
[QUOTE=kosmic]I think you should have looked at LVM in the first time you instaled Ubuntu.[/QUOTE]

what do u mean kosmic?
i should have installed the disks using LVM?

---

