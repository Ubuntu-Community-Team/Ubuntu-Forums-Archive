---
title: "Nautilus not showing label for hard drive"
date: 2009-07-23
forum: Hardware
---

### Post by mfearby on 2009-07-23
Today I bought two 1.5 TB Seagate drives and put them in [_this_]("http://www.vantecusa.com/front/product/view_detail/213") external USB enclosure (setting it to JBOD so that I can see both drives, even though the manual suggests the JBOD setting to be a concatenation of both disks into one, I'm seeing both). I have formatted both /dev/sdd1 and /dev/sde1 and here's the relevant output from "mount":

/dev/sdd1 on /media/Chock A Block 1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sde1 on /media/Chock A Block 2 type ext3 (rw,nosuid,nodev,uhelper=hal)

My problem is that when I turn on the drive, Nautilus shows both volumes, but named as follows:

[LIST]
[*]1500.3 GB Media
[*]Chock A Block 1
[/LIST]

As you can see, the /dev/sde1 volume isn't appearing using the label I gave it with GParted. Does Nautilus not pay attention to that many significant characters, and is somehow having to use the generic description because it would otherwise not be able to tell the difference? Will I have to use a shorter and more varied naming scheme to differentiate the two drives?

Thanks.

---

### Post by mfearby on 2009-07-23
I think I solved it. I hadn't clicked on the second drive on that enclosure. As soon as I did, its description changed.

---

