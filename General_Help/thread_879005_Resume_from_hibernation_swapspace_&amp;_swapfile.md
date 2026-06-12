---
title: "Resume from hibernation swapspace &amp; swapfile?"
date: 2008-08-03
forum: General Help
---

### Post by maestrobwh1 on 2008-08-03
In the process of fixing my usplash, I came across the fact that mu UUID for the swapspace (partition) was incorrect in /etc/initramfs-tools/conf.d/resume

Hibernate stopped working properly when I installed more RAM and I never really worked to fix it other than to assume that my RAM had become greater than my partitioned swapspace so I added a swapfile to my ubuntu partition so that together the two match my RAM.  I see that this might not "help" hibernation under some circumstances now.

Assuming that the machine hibernated only to the swapspace and did not use the sapfile, I would assume it would hibernate/wake again; however, is it possible to
1. add a swapfile to /etc/initramfs-tools/conf.d/resume
2. have two devices/items listed there?

currently the file has
RESUME=UUID=(the uuid of my swap partition)

So would I also just add to this
RESUME=/swapfile1

where swapfile1 is the name of the swapfile (listed in fstab)

[http://ubuntuforums.org/showthread.php?t=857565](http://ubuntuforums.org/showthread.php?t=857565)

---

