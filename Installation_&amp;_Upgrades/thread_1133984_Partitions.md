---
title: "Partitions?"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by Pr0udDragon on 2009-04-23
Hi,

I'm a little stuck here.  I want to install Ubuntu to a dedicated partition on my portable hard drive, but I'm not sure what partitions to make.  Could you tell me what I need for it?  This is what I was thinking (but am not sure about):

45 GB  ext3
2 GB  linux-swap

The 45 GB for my data and the 2 GB swap because of my 1 GB of RAM.  Is this what I need to Ubuntu 9.04 and will it dual boot that way?  Thanks.

~Pr0udDragon

---

### Post by oldos2er on 2009-04-23
What is it going to be dual booting with?

---

### Post by Pr0udDragon on 2009-04-23
Vista.

---

### Post by oldos2er on 2009-04-23
How're your disks/partitions set up?

---

### Post by Pr0udDragon on 2009-04-23
Well, my internal hard drive is NTFS with a partition that has Windows XP installed on it.  My portable hard drive (the one I want Ubuntu on) has just the main partition, no other partitions are on it.  It, too, it NTFS.

This is all on a laptop if that would help at all.

---

### Post by oldos2er on 2009-04-23
When you install Ubuntu it will install its bootloader, Grub, to the MBR of your internal hard disk. It should recognize Vista and create a boot entry for it.

 When the installer runs its disk partitioner, you should choose manual installation, and from there you can create the partitions you want on your external drive.

 There's much more info here: [https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by Pr0udDragon on 2009-04-24
Okay, thanks!  I got it all installed and working like a charm.  Only thing is, I think the download servers are all loaded up, because my update download speeds were crawling.  Other than that, I'm loving it.

---

### Post by oldos2er on 2009-04-24
You can try different servers via the menus System, Administration, Software Sources, next to 'Download from' click Other, Select best server. The server speed should improve in a few days after the new release excitement has died down.

---

### Post by Pr0udDragon on 2009-04-25
Okay, thanks.  I'm probably going to have to re-install it because it's a lot slower than a Wubi install was.  I find it strange, because I installed Hardy with Wubi on my portable hard drive, and it ran at absolute full speed with almost zero bugs (the only bug was that I couldn't do an upgrade to a newer Ubuntu), whereas on a dedicated partition on the same portable hard drive is going slowly.  I can't even paint fire on the screen without it almost seeming like it either froze or crashed.  I appretiate the help, though!  Maybe if I get a computer just for Ubuntu, or I decide to ditch Vista, I will use this information to help me out again. =)

---

