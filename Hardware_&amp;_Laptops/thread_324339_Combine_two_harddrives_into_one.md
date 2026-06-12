---
title: "Combine two harddrives into one?"
date: 2006-12-23
forum: Hardware &amp; Laptops
---

### Post by Forgotten on 2006-12-23
Hello,

I am need of some assistance. I have no clue if this is possible, but, I am willing to try to ask.

I have two, soon to be more, harddrives that are a bit on the old side. As of now I got two plugged into the tower with Ubuntu 6.10 with the second drive (empty right now) with the jumper set to slave.. Not master...

Here are the stats:

**Primary:**
Model: Quantum Fireball CX13.5
Size: 12.59GB
Path: /dev/hda

**Slave:**
Model: Fujitsu MPE3102AT
Size: 9.54GB
Path: /dev/hdb

Now my question is, how do combine the storage capacity of the two, so instead of having two storage disks with one with 12GBs and the other with 9GBs, have one disk with 21GBs... Even though I have two physical disks, I want them to combine, in a sense.

Also note: I can't seem to view the second harddrive anywhere other than in GParted... And yes I wiped it clean and reformatted it to Ext3.

Thanks everyone!

---

### Post by budgie9 on 2006-12-23
> **Forgotten said:**
> Hello,

I am need of some assistance. I have no clue if this is possible, but, I am willing to try to ask.

I have two, soon to be more, harddrives that are a bit on the old side. As of now I got two plugged into the tower with Ubuntu 6.10 with the second drive (empty right now) with the jumper set to slave.. Not master...

Here are the stats:

**Primary:**
Model: Quantum Fireball CX13.5
Size: 12.59GB
Path: /dev/hda

**Slave:**
Model: Fujitsu MPE3102AT
Size: 9.54GB
Path: /dev/hdb

Now my question is, how do combine the storage capacity of the two, so instead of having two storage disks with one with 12GBs and the other with 9GBs, have one disk with 21GBs... Even though I have two physical disks, I want them to combine, in a sense.

Also note: I can't seem to view the second harddrive anywhere other than in GParted... And yes I wiped it clean and reformatted it to Ext3.

Thanks everyone!

I think what you are wanting to do, is to make the second drive an Extended part of your first drive.
This is something we used to do in DOS and in Windoze. 
What you need to do first is to make sure you back up all your data, as the first disk is better wiped and re-partitioned, if needs be. Then you can break up  -partition- the second disk, but you install it as an Extended partition of the first disk, rather than as a seperate disk. It will still be seen as a second disk, but all the drive letters will follow on. Is this what you are looking for?

---

### Post by Forgotten on 2006-12-24
Thats more or less of what I want. That seems fine.

I just wanted to use the storage of both hard drives, nearly seamlessly.

---

### Post by kerry_s on 2006-12-24
I would just keep it separate but combine it as one install.

Example:
hda1 = swap 1024mb (aka: 1gig)
hda2 = /  (aka: root partion)11.41GB
hdb = /home (aka: user accounts)9.54GB

---

