---
title: "Manual Preparing Partitions, need help fast"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by Gralamin on 2009-03-29
I'm installing Ubuntu 8.10 on my Laptop, and I had premade my partitions. Partition Table if it matters is:
```
/dev/sda
  /dev/sda1 ntfs
  /dev/sda2 ntfs
  /dev/sda5 ntfs
  /dev/sda6 ext3
  /dev/sda7 swap
  /dev/sda4 ntfs
```
sda1 and sda4 are recovery partitions, sda2 is Vista ultimate, sda5 is Vista's swap, sda6 is where I want to install Ubuntu, and sda7 is Ubuntu swap.

Now the question is, how do I tell Ubuntu not to mess with certain partitions? All I want it to do is install onto sda6 and use sda7 as a swap.
Do I have to right click, edit partition, and select a use as for each partition I want to keep (And set sda2 to mount to /windows/)? Or can I just leave them all alone, and just tell it to use sda6 for installing? (All the other partitions have data, so I don't want them deleted)

Thanks for the help!

---

### Post by cariboo on 2009-03-29
You only have to setup /dev/sda6 as / and /dev/sda7 as swap, leave the rest of the partitons as they. When you are at the partition section chose manual partioning and then edit /dev/sda6 with a mount point of / and format it to ext3 and set the swap partion, and you should be good to go.

Jim

---

### Post by Gralamin on 2009-03-29
> **cariboo907 said:**
> You only have to setup /dev/sda6 as / and /dev/sda7 as swap, leave the rest of the partitons as they. When you are at the partition section chose manual partioning and then edit /dev/sda6 with a mount point of / and format it to ext3 and set the swap partion, and you should be good to go.

Jim

Awesome, I'll do so and hope it doesn't get rid of all my partitions. Thanks.

---

