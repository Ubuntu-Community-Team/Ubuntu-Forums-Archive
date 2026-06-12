---
title: "[SOLVED] Triple OS partition resize problem"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by Absinthe Minded on 2009-01-04
Hi all,

My brother has a laptop with two installations of Windows on it and (single HDD), and he wants to add Ubuntu.

He's tried installing but when partitioning, the installer tries to resize one of the Windows partitions. He has 70GB free space on the disk, so should be plenty for Ubuntu.

Any ideas on why this is happening, or how to fix it?

Thanks,
Nick.

---

### Post by Elfy on 2009-01-04
It's not being told to install in the free space.

You need to create partitions in the free space either with the installer or the partion editor in the sys admin menu, I preferr the latter.

Create an extended in the free space. Inside the extended you need to create at the least a linux-swap and linux partition, might be worth doing a partiton for /home as well.

HArd to tell exactly what size to make the swap as you don't give ram size - but if you need top hibernate then swap should be equal to or greater than RAM. If not 1.5xRAM with less than 1GBRAM or 512MB - I find those values fine.

Make a ext3 partition of 10Gb 
Make swap partiton
MAke a ext3 partition with remaining space.

Once installer has reached partitioning stage - choose manual

Pick the 10Gb partition - Edit partition - choose use as ext3 and / from mountpoints
Pick the larger ext3 partition edit as above but choose /home as mountpoint

Continue with install

---

### Post by Absinthe Minded on 2009-01-04
forsetpixie, thanks for that!

I've spoken to my brother and read out your post to him, we're having the following problems:

Using the Partition editor on the livedisc, he's not able to create a swap partition within another partition, he says he's only able to create 3 separate partitions, i.e.

Make a ext3 partition of 10Gb 
Make swap partiton
MAke a ext3 partition with remaining space

If he then runs the installer, and chooses 'manual' at the partitioning stage - he's a bit confused at this bit:

> Pick the 10Gb partition - Edit partition - choose use as ext3 and **/ form mountpoints**He only has the option of '/' '/boot' '/home'... etc.

Also, he's got 1.5GB of RAM and wants to hibernate.

Cheers,
Nick.

---

### Post by Elfy on 2009-01-04
a spolling mistook

the mountpoints he needs are / and /home

/ is root and it won't proceed without that one.

If it won't let him make the swap in the extended make it a primary

---

### Post by Absinthe Minded on 2009-01-04
Excellent, he seems to have it all working now, so thank you, thank you, thank you!

I'm going to leave the thread open a while to make sure it all works, if he doesn't phone me back, I'll mark it as solved.

Happy New Year to you!

Nick.

---

### Post by Elfy on 2009-01-04
It's going to be worth him getting a username here I would suspect ;)

Glad I could help 

Sometimes it is worth joing an irc channel too for help.

---

### Post by Absinthe Minded on 2009-01-09
Ha ha, yes I'll tell him to do that!

Thank you very much for your help once again, forestpixie!

I think we're safe to mark this as solved.

Cheers,
Nick.

---

