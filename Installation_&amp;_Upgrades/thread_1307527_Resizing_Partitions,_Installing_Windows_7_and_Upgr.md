---
title: "Resizing Partitions, Installing Windows 7 and Upgrading Ubuntu"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by deathblossom on 2009-10-31
Okay, okay, this is what I want to do and I want to run it by to see if it makes sense and what problems I may face.

Basically, I have a 45GB Vista Partition,  a 13GB root partition, and a 157GB /home partition. Now, I want to 

1. Subtract 15 GB from the /home partition
2. Wipe the 45GB Vista Partition
3. Combine the wiped 45GB Vista partition and the 15GB
4. Install Windows 7 on this partition
5. Upgrade Ubuntu on my root partition

Now questions...

So gparted has a boot flag on my Vista partition, which I take it to mean that if I wipe it, I won't be able to boot...? If so, how do I fix that. I mean, is it safe to, say...

1. Subtract gigs, wipe Vista, combine using gparted from the Live CD
2. Boot up from my Windows 7 CD and install on empty partition
3. After installing Windows 7, boot up from my Ubuntu Live CD and try to install that on the boot partition...? Can I fix GRUB from there? Will it need to be fixed?

Sorry for handwringing.

---

### Post by unmole on 2009-10-31
As long as the 45GB and /home partitions are beside each other, you should have no problem doing whatyou intend. However if the 45GB partition and /home partition are separated by some other partiton between them, you will not be able to merge the two.

---

### Post by deathblossom on 2009-10-31
> **unmole said:**
> As long as the 45GB and /home partitions are beside each other, you should have no problem doing whatyou intend. However if the 45GB partition and /home partition are separated by some other partiton between them, you will not be able to merge the two.

Luckily, they're not right next to each other! :( Would I be able to move the empty space?

Basically, my system looks like this:

1. (1 mb of unallocated space...?)
2. Recovery drive
3. Vista
4. (3 GB of unallocated space...?)
5. Extended partition
   -Root partition
   -Home partition
   -Swap

So, I was thinking about perhaps doing the following in gparted:
(see attachment)

---

### Post by skyiscrying on 2009-10-31
You will need a more knowledgeable person than I. My solution would be to reformat - *after saving* what you want - and then use the Windows disc to partition, install Windows 7 and then your Ubuntu. Have a look at [http://screencasts.ubuntu.com](http://screencasts.ubuntu.com) - but I think they just show the basic partitioning. Good luck.

---

### Post by unmole on 2009-10-31
Real sorry to abandon you but my laptop battery died on me. Just in case you still want to continue. Here is what I suggest you do.
1-Resize the extended partition to fill the 3.38 MB.
2-Resize the extended partition again so that you have all the free space preceding it.
3-Delete the vista partition. This should leave you with continuous free space of about 60 GB.
4-Install Windows 7 on a new partition in free space.
5-Install Karmic in your old root partition.

---

### Post by deathblossom on 2009-10-31
Thanks! I managed to do the first steps. The only problem now is I can't boot from my Win7 DVD anymore. Usually I get a little prompt that says "Press any key to boot from CD/DVD", but now it just goes straight to GRUB.

ETA: False alarm! Win7 DVD was corrupted.

---

