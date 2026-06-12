---
title: "Cannot expand partition"
date: 2008-10-14
forum: General Help
---

### Post by LittleKoy on 2008-10-14
Here is my problem:

[[IMG]http://img205.imageshack.us/img205/8918/gpartedxw3.th.jpg[/IMG]](http://img205.imageshack.us/my.php?image=gpartedxw3.jpg)[[IMG]http://img205.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

As you can see, I have a quite good amount of space unformatted, and I would like to expand my 230gb partition to use them. But gparted only allows me to move it about 3gb to the right :(

---

### Post by drs305 on 2008-10-14
I had trouble seeing the snapshot but it looked like you are trying to expand a primary partition into an extended partition. Without going into all the details, you can't grow a primary partition into the light-blue bordered area (the extended partition).

You might move some of your logical partitions within the extended partitions to the right and then shrink the extended partition but without seeing the picture I can't give you more specifics.

For some basic information on partitioning:
[Disk Partitioning]("http://en.wikipedia.org/wiki/Disk_partitioning")

---

### Post by LittleKoy on 2008-10-14
[IMG]http://img205.imageshack.us/img205/8918/gpartedxw3.jpg[/IMG]

Can you see it now?

PS: What I'm trying to do in the end is to have a partition just for the OS, about 20gb, and the rest of the space a "data partition", where I just put data. If there is any simpler way to accomplice this, please share it :(

---

### Post by drs305 on 2008-10-14
There are lots of opinions on partitioning. Wait for more responses - you may very well get a better solution than what I offer.

There aren't really a lot of options available with the way the drive's partitions are currently set up.You can't expand sda1 or sda3 except for the 3GB you already mentioned. And there isn't space to transfer the entire contents of 1 or 3 entirely into the extended partition's empty space. 

For the moment, you could transfer some/all of your data files into a new partition in the empty space. You could also transfer your /home to the extended partition. One advantage would be that if you decide to upgrade to Intrepid at the end of the month you could keep your home partition and settings intact in the new partition (sdaX). When it came time to install Intrepid, you could make a 20GB primary partition at the beginning of the drive after moving sda1 and sda3 to the right a bit.

If I could save/backup all my data files to another medium, I would prefer to reformat the entire drive, then make a couple of primary partitions (or at least one for the Intrepid install) and make the rest an extended partition which you can carve up into as many partitions as you like. 

If you think you might want to make a separate home partition, here is a link:
[http://http://www.psychocats.net/ubuntu/separatehome]("http://http://www.psychocats.net/ubuntu/separatehome")
There is also good information at the site about planning partitions in general.

---

### Post by bodhi.zazen on 2008-10-14
The problem is that the unallocated space is contained within an extended partition.

You will have to do this in 2 steps. First resize sda2 => apply changes (this step will move the unallocated space out of the extended partition).

Step 2 resize sda1

---

### Post by LittleKoy on 2008-10-14
> **bodhi.zazen said:**
> The problem is that the unallocated space is contained within an extended partition.

You will have to do this in 2 steps. First resize sda2 => apply changes (this step will move the unallocated space out of the extended partition).

Step 2 resize sda1

I tried, but "resize/move" is gray on sda2...

EDIT: sorry, I had to swapoff a swap partition, now it works ;)
Looks like this is the cleanest way... I will surely put my home on the huge partition, that was actually my intention

Thank you guys ;)

---

### Post by bodhi.zazen on 2008-10-14
You have to do this from a live CD and unmount the swap partitions.

---

