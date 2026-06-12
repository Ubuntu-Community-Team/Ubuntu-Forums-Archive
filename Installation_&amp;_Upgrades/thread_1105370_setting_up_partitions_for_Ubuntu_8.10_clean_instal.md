---
title: "setting up partitions for Ubuntu 8.10 clean install w/2 drives"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by danebramaged on 2009-03-24
setting up partitions for Ubuntu 8.10 clean install w/2 drives 
Time for some serious spring cleaning.

I have 2 seagate sata drives. They are indentical 320 Gig drives. My problem is this: When I except the defaults for Ubuntu it wants to dump everything on just one drive even though it clearly sees the other as /dev/sdb1. It also defaults to ext3, but I want to see what JFS, XFS and ReieserFS can do.

So I have to do a manual install but here's the thing: If I make nice big primary partitions swap / /boot /tmp /usr /usr/local /opt and /var beginning with SCSI(0,0,0), I am still going to have well over 250 Gig of free (unused) space.

Now the obvious thing to do would be to make a /home partition however, I want to create a swap and /home partion on my second drive. If I have two /home partions (one on each drive) the system will not allow that. I can only have one /home partition. If I put it on the second physical drive then I have 250 Gig of unused space left on SCSI(0,0,0). 

I want to know how to have one whopping big /home partition on both drives and not waste any space. 

Directions on how to mirror these two drives would also be acctepable.

---

### Post by deanjm1963 on 2009-03-24
I have something similar, I keep a good size root partition - 20gb or so, same amount for home. But for the rest of the drive and my second drive I make other partitions, e.g. /video (300gb) /stuff (music-pics-etc 100gb) /documents (where I keep all my work) /downloads (torrents etc). Basically my home partition keeps nothing but system settings etc.

JFS is great, XFS is also good but you need to use the alternate install if you wish to use it for your root partition, reiserFS is also very good, but very slow at mounting drives/partitions.

Hope this helps.

---

### Post by danebramaged on 2009-03-24
When I except the defaults during a Ubuntu install, it just slops everything onto SCSI(0,0,0).  That's not what I want.  The second option it gives you is to pick either one of the two drives, but in any case, you still wind up only mounting one drive, not two.  The third option is "manual".  

The only way I am going to get what I want is to use the manual option, obviously.  But how do I get the /home partition to "span" the last half of the first drive and all of the second drive since I can only have one /home partition to begin with?

---

