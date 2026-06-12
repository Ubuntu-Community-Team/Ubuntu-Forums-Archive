---
title: "Installation freezes on disk partitioning"
date: 2006-03-12
forum: Hardware &amp; Laptops
---

### Post by treuss on 2006-03-12
Hi,
after purchasing two new sata disks, I wanted to re-install breezy onto a big new partition, but unfortunately cannot get past the partitioning state. What happens:

    * Last message I see is "Starting up the partioner", after that there is a blue screen (could it have any other color ???) with an empty grey bar at the bottom
    * Last message on tty3 is "Reading all physical volumes. This may take a while...". I assume "a while" does not refer to hours..
    * On tty4, the last message is DEBUG: virtual package harddrive-detection
    * When I run ps on an opened terminal I see the following processes
          o ntfsresize -f -i /dev/scsi/...
          o grep ^You might resize at (surprisingly without any quotes...)
          o sed s/^You might resize at ..../
          o tail -n1
          o grep ^[0-9]*$
    * Trying to run fdisk -l /dev/sda on that terminal freezes

I've tried expert mode, but after gotting through a lot more questions I came to the same point. 
The problem seems to be kernel related, as when I open up a terminal and try to e.g. manually mount a partition, it freezes as well. The driver via_sata is loaded, and /dev shows correctly the partitions on both disks, so they have been recognized, but any attempt to access those freezes.

Any help appreciated,
              Torsten

---

### Post by nelson64 on 2006-03-12
When I Run Into This Problem I Run Partition Off Of Windows Xp Disk And I'm Able To Install Without Any Problems. What I Do I Run Windows Xp Install Disk . Hit Enter For Install F8 And Then Partition After Partition I Delete Partition... Re Partition...create Then  F3 ...plus  F3 To Quit Then I Reboot And Run Linux Install. This Has Worked Well For Me But May Or May Not Work For You . It Has However Worked On Several Systems I've Built . It Does Require A Windows 2000 Or Xp Disk . Hope It Helps...

---

