---
title: "Resizing reiserFS partition"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by moccah on 2005-12-06
Hi there
I`m running Ubuntu on my laptop, and have a single disk (/dev/hda) with three partitions, /dev/hda1 is mounted as / and dev/hda2 is mounted as /home, the last is mounted as swap. My question in mind was;
can i resize the /home (dev/hda2) partition without loosing data, or make the disk corrupted ? And in any case, how ?

Regards
Tor Aage

---

### Post by afhp on 2005-12-06
From a quick look at the repositories, gparted supports resizing on reiserfs3 ; both "reiserfsprogs" and "progsreiserfs" claim to have a resizing tool. 

I haven't tried any of these tools myself (I tend to rather add disks...) so I can't say how reliable they are. You should backup anyway.

---

### Post by moccah on 2005-12-15
Anyone got any suggestions ?

Can I resize the partition to a smaller size ?

---

### Post by psusi on 2005-12-15
Yes, boot from the livecd and fire up gparted and resize away.  Should work like a charm.  

I've resized both reiserfs and ntfs using the command line tools several times with no problems.

---

### Post by hatefulthreatening on 2005-12-15
Be careful. I'd back up my data anyway.

A good third of my files were completely fried by the last reiserfs resize that I did. Sure the partition was resized but the data was corrupted.

Oddly enough ntfs and hfs worked flawlessly.

This was at least a year ago. Things may have improved since then.(Or I might have screwed something up in the first place.

---

