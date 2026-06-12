---
title: "LiveCD installer's partitioner uses data units inconsistently"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by jasontan6 on 2009-04-26
I only noticed this when installing Jaunty just now, but I have a feeling that this probably existed since a few versions ago when they introduced the colored disk partitions bar in the installer.

Now if you pick the "Specify partitions manually (advanced)" option when setting up partitions during the Live CD installation, you will see a bar at the top showing the partitioning scheme of the hard disk selected. The size of the partitions is indicated in GB.

Below the bar is a list of all disks and partitions, however the sizes here are reported in MB.

What I have noticed, is that the MB beneath the bar is gibibytes (2^30 bytes), whereas the MB in the list below is megabytes (10^6 bytes).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=111155&stc=1&d=1240750849[/IMG]

Take the partition /dev/sdb1 for example. Beneath it's segment in the bar, it is reported to be 400 GB (**gibibytes**, 400 x **2^30** = **429,496,729,600 bytes**). In the list however, it is reported to be 429,496 MB (**megabytes**, 429,496 x **10^6** = **429,496,000,000**, close enough since errors for rounding must be taken into account).

I have double-checked and can confirm that /dev/sdb1 is in fact 400 gibibytes in size. I attached a screenshot of GParted showing the partitions on that disk, and it is indicated there 400 GiB (gibibytes). Windows also reports that the partition is 400 GB (gibibytes)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=111156&stc=1&d=1240750849[/IMG]

What I am saying is, there is inconsistency between the usage of decimal and binary powers in the interface of the LiveCD installer. I would assume that most novice users would be wondering why the values do not match if they took 429,496 MB from the list and divided it by 1024 to find that it is 419 and not 400 GB (as the bar states).

Has anyone noticed too? Do you think this should be filed as a bug / improvement request?

---

