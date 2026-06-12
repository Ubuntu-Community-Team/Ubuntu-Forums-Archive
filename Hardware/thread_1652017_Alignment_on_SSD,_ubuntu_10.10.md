---
title: "Alignment on SSD, ubuntu 10.10"
date: 2010-12-24
forum: Hardware
---

### Post by NexusN on 2010-12-24
Hi everybody.
I have been struggling for a question right from I switched to ubuntu.
How should I align my SSD, OCZ Vertex2 60 GB?

I have been reading many posts, following the command in OCZ forum, but I don't know if I have get it correctly configurated.
Therefore, I would like to know if there is a simple method to check the alignment.
And in case I am still in the bad config, is there a easy way to get the job done?

Here is the method I adopted:
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=472998#post472998](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=472998#post472998)

Simply setting up a 100MB partition before the main 60 GB partition is fine?

Thank you.

---

### Post by NexusN on 2010-12-25
Oh, I am sorry that I just realize I may have put my post on the wrong board, as I am using Laptop and it is a hardware issue, but this is mainly the SSD's problem.
May admins move my post to the correct board for me in case necessary?
Thank you.

---

### Post by arapaho on 2010-12-27
'Align to cylinder' if you are talking about this option, is in Gparted - this program is on Parted magic live cd.
[http://partedmagic.com/doku.php?id=screenshots](http://partedmagic.com/doku.php?id=screenshots)
As far as I know it is important only if you use windows. For linux it is unimportant.

---

### Post by NexusN on 2010-12-27
> **arapaho said:**
> 'Align to cylinder' if you are talking about this option, is in Gparted - this program is on Parted magic live cd.
[http://partedmagic.com/doku.php?id=screenshots](http://partedmagic.com/doku.php?id=screenshots)
As far as I know it is important only if you use windows. For linux it is unimportant.

Thank you very much for your kind reply,
these days I have also been looking for the software that may help and I also found GParted.
From an experiment made by other users, 
formatting the disk with GParted 0.62 with Align to MiB will work!
He confirmed with comparing the speed test of AS-SSD with a installation with Windows 7 installation,
1. Partitioned by Windows 7 - Aligned
2. Partitioned by Gparted 0.62 Align to Cylinder - Not Aligned
3. Partitioned by Gparted 0.62 Align to MiB - Aligned
So I followed and hopefully things are fine.
[http://www.ubuntu-tw.org/modules/newbb/viewtopic.php?post_id=146074](http://www.ubuntu-tw.org/modules/newbb/viewtopic.php?post_id=146074)

---

