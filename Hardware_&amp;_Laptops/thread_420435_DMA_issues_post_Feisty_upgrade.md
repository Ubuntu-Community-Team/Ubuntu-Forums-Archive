---
title: "DMA issues post Feisty upgrade"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by grendelkhan on 2007-04-23
Upgraded my Edgy server to Feisty over the weekend and all is well except for one thing.  I have a 250 GB hard drive that I have mounted just to do xfs dumps of my other file systems.  There is a second identical hard drive hung off the same controller (but different channel).  When I do and xfs dump from hde (first channel - drive with 3 partitions on it) to hdg (my backup target filesystem) I immediately start getting drive unavailable errors and eventually, if I let it go on, the whole system will lock up.

Here's the odd bit, if I disable DMA on the drive with the filesystem being dumped, the errors go away and it reads off there just fine.  It takes forever and a day, but it runs.

I didn't have any of these issues under Edgy, these cron jobs ran just fine, and I know I've had DMA issues on my Feisty workstation, but I didn't see anything like this in the beta forum.

Any ideas?

---

