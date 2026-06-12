---
title: "Having trouble deleting a partition"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by Sarai the Geek on 2009-05-02
This morning, I woke up and thought, "hmm, I should dual boot Linux Mint, just for kicks". So, using gparted I created the partition, installed, etc, all went well. I tried Mint, liked it okay but not enough to let it keep the forty or so GB I had so graciously given it. So I deleted the partition... or so I thought.
It won't let me resize my Ubuntu partition back to it's normal size. I believe this is because the /dev/sda2 partition didn't get deleted, but I can't figure out how to get it to go away. All of the space in it is unallocated.

A picture of what my gparted looks like is attatched. Note that I have been using the Gparted live cd to do all my partitioning, I just loaded the gui to take the screenshot. :)

---

### Post by _Purple_ on 2009-05-02
You will not be able to delete /dev/sda2 without deleting /dev/sda5 and /dev/sda6.

---

### Post by Sarai the Geek on 2009-05-02
> **_Purple_ said:**
> You will not be able to delete /dev/sda2 without deleting /dev/sda5 and /dev/sda6.


Do I need them?

---

### Post by _Purple_ on 2009-05-02
Yes, you need keep one swap partition. Why don't you create a new partition inside the extended partition with the unused space?

As for two swap partitions, I am not sure if you have to edit your /etc/fstab if you delete one. May be you can delete one of the swap partitions and remove its entry from fstab.

---

### Post by Sarai the Geek on 2009-05-02
> **_Purple_ said:**
> Yes, you need keep one swap partition. Why don't you create a new partition inside the extended partition with the unused space?

As for two swap partitions, I am not sure if you have to edit your /etc/fstab if you delete one.

Well... this was my plan:

After I had my hard drive restored to the way it was I was going to make a new, much smaller partition, probably 30, 35 GB (the two I have right now are about 70 each) on which I was going to put XP. The virtual machine is more trouble than it's worth, methinks. 

But, I suppose I could just create the XP partition within the unallocated space. Without the 20GB virtual machine on my Ubuntu partition I'm sure I'll have more than enough space to last me the next few months, after which I am getting a new, larger computer (w00t!) and reviving my old Macbook to play the part of a photoshop, itunes, etc computer.

Not exactly what I wanted, but c'est la vie, right?

---

### Post by _Purple_ on 2009-05-02
You can also resize your extended partition so that it only holds the swap partition and then you have the unused space outside extended partition.

---

