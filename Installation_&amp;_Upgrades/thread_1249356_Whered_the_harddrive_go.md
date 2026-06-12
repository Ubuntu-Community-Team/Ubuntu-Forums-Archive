---
title: "Whered the harddrive go ?"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by Gusss on 2009-08-25
So I installed Ubuntu. Something went wrong with my installation , basically I cocked it up, and now my windows harddrive is showing a lostt of 120 gb, but my ubuntu partition is only 30 gigs. So I want to wipe unbuntu from my dual boot machine , get my vista partition back to 320 gb and then reinstall ubuntu properly. Any suggestions ?

---

### Post by giftedwon on 2009-08-25
run  the  partition tool from the live cd

GPARTED

---

### Post by stlsaint on 2009-08-25
pop in the livecd for ubuntu and go to system>admin>partition editor...here you will be able to see all hdd and partitions on your system...you will see the ubuntu partition and vista partition. Vista cannot read the ext2/3 or 4 filesystem's. after you are at the partition screen you will be able to delete partitions to unallocated and then add them back to vista...once that is done i recommend you boot into vista and use the disk management tool to create another partition for ubuntu then boot back into the live cd and do a Manual install and select the right partition and you should be golden!

---

