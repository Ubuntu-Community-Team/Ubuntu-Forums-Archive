---
title: "Any workaround for having more than 4 partitions?"
date: 2008-08-07
forum: General Help
---

### Post by xtrumanx on 2008-08-07
[IMG]http://img261.imageshack.us/img261/6522/screenshotdevsdagpartedsc1.png[/IMG]

The above image shows how my partitions are currently configured. I had a 60 GB partition which I split into 15/45 GB pieces and I've installed Windows on the 15GB one. Now I'm stuck with a 45 GB partition which I can't use due to the 4 maximum partition limit.

I tried at first to delete the 15GB partition and create a new extended partition (from the unallocated space) but when I try to do so, the option of creating an extended partition is grayed out. Can anyone tell me why that is or give me an idea for a solution?

Thanks all of you with your replies. Snowpine's solution worked.

---

### Post by jerome1232 on 2008-08-07
Can't you delete that 15 Gb patition and grow the extended partition to fill in the space?

Edit: looks like you might have to do it from a live cd though because it is mounted and you can't grow/shrin a mounted partition

---

### Post by mixmaster on 2008-08-07
You can only have 4 primary partitions.  Delete one and create an extended partition in which you can create as many logical partitions (filesystems) as you like.

---

### Post by bigken on 2008-08-07
try using the gparted liveCD like others have said delete 15gig join it to the 45gig and create an extended partition good luck

---

### Post by snowpine on 2008-08-07
You already have an extended partition: sda1. Boot from a Live CD, move sda2 as far right as it will go, and expand sda1 to fill the space. Then you can create a new 45gb partition in sda1, next to sda5.

---

### Post by bigken on 2008-08-07
looking at your chart you already have an extended partition

---

### Post by sandysandy on 2008-08-07
u can do what snowpine says. 

alternately just delete swap partition. that will free one primary partition. 

u can then create primary partition from free space.

in the extended partition sda1 move sda5 and in free space thus generated create SWAP partition.

regards

---

