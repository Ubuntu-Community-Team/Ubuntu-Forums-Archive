---
title: "Problem with cloned hard drive partition ... HELP!"
date: 2009-03-07
forum: Hardware
---

### Post by SkankinRatFink on 2009-03-07
Hello. So here's the skinny---

I recently built this computer. It has one SATA hard drive. Installing operating systems, I set up the partitions like this----

Primary #1 - NTFS (Windows XP)
Primary #2 - NTFS (Windows 7)
Primary #3 - EXT2 (Ubuntu Studio)
Extended #4
- Logical (#5) Swap space
- Logical (#6) NTFS (All my files go here)

It's a 320-gig hard drive. XP gets 10 gigs, Win7 gets 25, Ubuntu gets 12, and swap space gets 2. I left the bulk of the hard drive space for my files. By my quick and dirty math it's approximately 270 gigs. I know about the decimal/binary discrepancy between advertised and actual---- Point is, it is definitely well over 200 gigs I have left for this NTFS partition.

Anyway. All the files I wanted on this partition were on a dedicated 80 gig IDE drive ("Buddy"). I burned a CloneZilla disc, and cloned the 80 gig partition from the IDE drive into the 200-something gig partition that I had set up on my new SATA drive. CloneZilla specifically told me that it supports cloning a smaller partition into a larger one. **Here's my problem**- Ubuntu Studio is reporting two different sizes for this partition, and both of them are showing up as nearly full.

If I get the drive info from Nautilus, it says the partition is 72.5 gigs in size, 71.7 used. This is pretty much where that 80 gig drive was. It was almost full.

[IMG]http://i44.tinypic.com/5le6tw.png[/IMG]

Now, when I look at the partition from GParted, here is what I get ...

[IMG]http://i44.tinypic.com/16c742d.png[/IMG]

It lists the partition as 249.22 gigs, which is more like it. But it says 248.45 gigs of it are used!! This is impossible because I have not added any files to the partition since the clone.

Someone please help, I would like to use all the space this hard drive is supposed to offer me. Thanks a lot!!

---

### Post by SkankinRatFink on 2009-03-07
OK, I'm worried I did something that goes beyond Linux----

I get the same phenomenon in Windows XP. I get the 72 gig partition in [Drive Properties](http://i42.tinypic.com/309lb3l.png) and 249 gigs in [Disk Management](http://i44.tinypic.com/2w23f2o.png). Click the links for screenshots.

Also, if it makes any difference, this SATA drive is in AHCI mode.

---

### Post by Nefir on 2009-03-16
Skankin, did you manage to resolve your problem? I just found your post and it seems you are having the [same problem as me]("http://ubuntuforums.org/showthread.php?t=1097436"). 

Unlike you, I cloned my old partitions using Partimage onto an external HDD, then back onto the laptop's new HDD.

If you heard anything since posting this, let me know!

---

### Post by SkankinRatFink on 2009-03-16
I did manage to clear up my problem ...

I simply deleted the partition, manually created the 249-gig partition, and copied the files over manually. This worked for me because it was just a data partition, no operating system. If the partitions you're working with are not system partitions, you could do the same thing.

This is the only solution that anybody offered me (from a different message board).

---

### Post by Nefir on 2009-03-16
> **SkankinRatFink said:**
> I did manage to clear up my problem ...

I simply deleted the partition, manually created the 249-gig partition, and copied the files over manually. This worked for me because it was just a data partition, no operating system. If the partitions you're working with are not system partitions, you could do the same thing.

This is the only solution that anybody offered me (from a different message board).

Thank you for the info! I just managed to actually resolve my problem by doing this (which did not involve re-creating the partition):

1) Boot into a rescue LiveCD with Gparted
2) Run the Gparted disk check on all partitions

Apparently it also uses some tool to resize partitions that are not correctly sized - something fsck does not do on its own.

And thats all! Now my partitions are sized correctly.

---

