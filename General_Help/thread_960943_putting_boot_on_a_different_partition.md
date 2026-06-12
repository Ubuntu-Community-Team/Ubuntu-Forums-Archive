---
title: "putting /boot on a different partition"
date: 2008-10-27
forum: General Help
---

### Post by galoisien on 2008-10-27
One thing that I would like to do is put /boot on a separate partition I specially made to store kernels, bootloader data and so forth. I've just taken up Linux again (I'm way more used to Slackware) and I really would have wished the installer would have asked me where exactly I wanted to set my mountpoints. Now that I have a /boot folder physically located where I would NOT like it to be (on my main Linux partition!), is there anything I need to know before attempting to move it (through a livecd). My current plan is to copy /boot to the actual partition where I want it to be stored, edit fstab while loading the liveCD, physically delete /boot off the main partition so there'll be no conflict, and then set the new partition as /boot mount point. 

I mean, for me /boot has always been on a separate partition for me, and it's been that way for eight years, and that's how I would like for it to remain.

I can't even begin to fathom the process of trying to get a new ubuntu-compatible kernel.

---

### Post by alienprdkt on 2008-10-27
the installer does ask if you want a customized partition table... there you would have used the 
/boot  ext2
/      ext3

but you may now beable to try g-partition / resize and create new partition...
[https://help.ubuntu.com/community/HowtoPartition#Resizing%20an%20old%20partition](https://help.ubuntu.com/community/HowtoPartition#Resizing%20an%20old%20partition)

---

### Post by cicatrix1 on 2008-10-27
What is the advantage of having it on a seperate partition unless you're using LVM?

---

### Post by alienprdkt on 2008-10-28
> **cicatrix1 said:**
> What is the advantage of having it on a seperate partition unless you're using LVM?

The boot partition is just a nice way to have the boot stuff kept separate. I also have mine read-only.

---

### Post by sdennie on 2008-10-28
> **cicatrix1 said:**
> What is the advantage of having it on a seperate partition unless you're using LVM?

I agree with this sentiment.  For a long time I always had a separate /boot partition because "that's the way it's done".  Once I started building lots of custom kernels I realized that having a separate /boot was a huge hassle (it filled up) unless you are using LVM or RAID and are forced to do it.

Regardless, it's non-trivial to split off a proper /boot partition.  You'll have to resize the original root, move /boot to the new partition with permissions intact, fix /etc/fstab and /boot/grub/menu.lst to know about the new UUIDs of the partitions (the latter may be as simple as running update-grub), etc.  If you are coming from Slackware, this may not sound too onerous but, it may actually be easier to backup /etc and /home and just re-install to create your boot partition.

---

