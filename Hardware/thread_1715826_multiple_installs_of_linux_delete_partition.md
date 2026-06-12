---
title: "multiple installs of linux delete partition"
date: 2011-03-27
forum: Hardware
---

### Post by tribalboy on 2011-03-27
Hi Guys,

  I have a dual boot laptop with Windows 7 & Ubuntu 10.10. I was having problems with the wireless drivers so I installed Natty Narwhal which seems to work fine. But now I am stuck with 3 partitions where one of the partitions is unused. I want to delete this partition and have tried that using GParted but it does not allow me to delete it. Can I merge it with my current partition where I have  Natty installed instead of deleting. Again this option is coming up as disabled in GParted. Any help would be appreciated

Thanks in advance

---

### Post by oldfred on 2011-03-27
There are only 4 primary partitions and the extended is a special type of primary that also can contain the logicals. If any logical is mounted then the entire primary is in effect mounted.

You have to run gparted from a liveCD to make sure no partitions are mounted and even then usually have to click on the swap partition and right click swap off (swaps are often in the extended). LiveCDs often load the swap (if found) to speed things up.

---

### Post by tribalboy on 2011-03-27
Thanks for the reply oldfred, I am a linux newbie & have not done admin tasks of this kind

I realise that the partition sda5 is inside sda4, do you mean to say that I can move sda5 & sda6 out of sda4 or merge ssda4 & sda5 if I run from a LiveCD & use GPArted or another tool

---

### Post by oldfred on 2011-03-27
No, You cannot move, but you may be able to copy partitions if you have room. But that leads to lots of issues that a new user may have trouble with. Duplicate UUIDs that cannot be  duplicates and resolving all those issues. It can be done.

Be sure to have good backups. Any partition editing has risks. Often the biggest risk is not the software but the user. I have many times clicked on something and then realized that that was not the right thing. I can reinstall in about an hour and have data reasonable well backed up,  so I am comfortable with my errors not totally destroying my system.

---

### Post by gordintoronto on 2011-03-27
You don't have an unused partition. You have a tiny little bit of unused space, but it is so small it's not worth worrying about.

You have a very small Dell utility partition, a small Dell (Windows) recovery partition, a Windows partition, and an extended partition which contains Natty and the Linux swap. Those two also consume the entire extended partition.

---

### Post by tribalboy on 2011-03-28
thanks for clearing my misconception gordintoronto, I will leave it at that, 

cheers

---

