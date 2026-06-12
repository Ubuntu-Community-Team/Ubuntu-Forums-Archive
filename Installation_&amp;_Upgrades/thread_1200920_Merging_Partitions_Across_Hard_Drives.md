---
title: "Merging Partitions Across Hard Drives"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by Rempefiesta on 2009-06-30
Hello, 

Recently I have purchased a server and installed Ubuntu 9.04.  I installed Ubuntu on its own partition and partitioned the rest as empty space. The server also comes with a second hard drive, which is where the problem is coming from. I wish to merge the hard drives to become one partition. i searched the forums, but really wasn't able to pinpoint exactly on how to do it.  Any help would be appreciated.  Thank you for your time.

---

### Post by pastalavista on 2009-06-30
I'm not sure, but I don't believe you can without some sort of raid setup.

---

### Post by Rempefiesta on 2009-07-01
Would it be possible to place both of the unallocated partitions on both hard drives into /home when installing Ubuntu 9.04, or would that cause a conflict?

---

### Post by tommcd on 2009-07-01
I think installing Ubuntu using a LVM setup could accomplish what you are trying to do. LVM allows a lot of flexibility in changing partition sizes or merging partitions. See these 2 tutorials on LVM:
[http://distrowatch.com/weekly.php?issue=20090309#feature](http://distrowatch.com/weekly.php?issue=20090309#feature)
[http://distrowatch.com/weekly.php?issue=20090316#feature](http://distrowatch.com/weekly.php?issue=20090316#feature)

---

### Post by Rempefiesta on 2009-07-01
I read through your documentation you linked and installed Logical Volume Management through Synaptic, and it seems to be working now! Thank you very much!

---

### Post by tommcd on 2009-07-01
Glad you figured it out. Those tutorials were a bit involved. I have never used LVM myself. I have just read about it.

So you did not do a new install of Ubuntu using LVM? You just installed LVM from synaptic onto your existing Ubuntu and it just worked? Is that right?
If that is so, then I did not actually know you could do that. I thought that the only way you could use LVM was if you installed Ubuntu using LVM partitioning.

---

### Post by Rempefiesta on 2009-07-01
What I did was install Logical Volume Management through Synaptic, and setup my spare space on both of my hard drives as ext3 with gparted, then launched Logical Volume Management, set aside one as a logical volume then added the other hard drive partition to the first logical volume.  When I browse to the mount point of the space, it's showing ~480GB of free space (I have two 250GB hard drives, with 10GB set aside for Ubuntu). I'm assuming this is working correctly, as I haven't had much time testing this by filling that space, but it should hopefully read and write correctly.

---

