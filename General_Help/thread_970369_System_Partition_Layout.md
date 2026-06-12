---
title: "System Partition Layout"
date: 2008-11-04
forum: General Help
---

### Post by Xhip on 2008-11-04
Hello!

I have a 320GB hard disk that I want to "split" into several partitions, in order to install Linux/Ubuntu and Windows on it, with Linux being my default system. After several readings and after studying and analyzing the different possibilities, I got into the following layout (I have 4GB of RAM):

```

Prim /dev/sda1       /boot         94MB ext3 (boot)
Extd /dev/sda2                               (lba)
Logi     /dev/sda12  SWAP           4GB swap
Logi     /dev/sda11  /tmp           2GB ext3
Logi     /dev/sda10  /var           4GB ext3
Logi     /dev/sda9   /              8GB ext3
Logi     /dev/sda8   /usr          20GB ext3
Logi     /dev/sda7   /home        140GB ext3
Logi     /dev/sda6   FAT32 DATA    15GB fat32 
Logi     /dev/sda5   WIN GAMES     90GB ntfs 
Prim /dev/sda3       WINDOWS       15GB ntfs

```
  
What can you tell me about this layout, is it ok? I'm not a partition professional, so I wanted to hear from someone with more experience on this, because I wanted to maximize disk efficiency with this layout... I'm more curious about the size of Linux Partitions above and about the overall placement of the partitions...

Can you help on this? 
Best regards! :)

---

### Post by beno1990 on 2008-11-04
It seems fine for the most part to me, though personally I would have used 16-32GB for the / (root) partition, but 8GB should be enough if you don't plan on installing a lot of applications.

---

### Post by Xhip on 2008-11-04
Yes, but programs and applications are installed on the /usr directory, which is on a different partition, separated from the root /, as you can see above :)

---

### Post by Hiperi0n on 2008-11-04
I am not a big fan of doing a lot of partitions. If you have a large disk it is ok, but in the end I think some space is wasted. I only have a / and a swap partition and I'd probably make a /home one, no more. I guess there are some benefits of making a lot of partitions, but I like to squeeze all the free space I can get, I usually don't have much...

---

### Post by beno1990 on 2008-11-04
Oooh, sorry. I see it now, I must have missed it. :lolflag:

Seems fine to me, then. 20GB is more than enough for most.

---

### Post by Xhip on 2008-11-04
Bump
(sorry, thread was lost at page 10.. :sad:)

Can anyone post feedback?

---

### Post by Xhip on 2008-11-04
Anyone please?..

---

### Post by Xhip on 2008-11-05
:(
Well, since no one seems to care about my partition layout, I will be relying on the structure I posted above...

Thanks to the few people that replied.
Regards.

---

