---
title: "anyone using an SSD? did you align partitions to erase blocks?"
date: 2009-08-14
forum: Hardware
---

### Post by graysky on 2009-08-14
I'm waiting on the 2nd gen Intel SSDs to copy my / and /home to the faster I/O device.  In the meantime, I'm reading up on these things and have found numerous sources that suggest aligning partitions on SSD's to the erase block of the device.  I found two major sources detailing the process.  [This one](http://blog.aloisiojr.com/?p=28) shows a setup using parted and explains the process.

I'm just posting to solicit feedback from the community on this issue.  Does Aloisio have it right in that blog post?


My partition scheme for the 80 gig ssd will be pretty simplistic:

20 gigs of NTFS as partition #1
15 gigs of ext4 as partition #2
200 meg of ext3 for /boot as partition #3
rest of the drive for /home as partition #4

I'll keep /var and /data partitions on my HDD.

Glad to hear more comments about this so I can do it right the first time :)

---

