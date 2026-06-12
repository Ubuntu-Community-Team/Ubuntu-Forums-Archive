---
title: "mdadm trouble"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by ternarybit on 2009-10-20
I am trying to get a RAID 1 mirror running on my system hard disk. It is partitioned like this:

sda1 - ntfs (Windows & boot)*
sda2 - ext3 (Ubuntu / partition)
sda5 - swap
sda6 - ext3 (Ubuntu /home partition)

I found this article [(click here)]("http://www.excentral.org/archives/2005/03/14/mdadm-raid-1-migration") that describes what I want to do. In my ignorance, I assumed that using clonezilla to image my existing disk to the new disk would make things easier, but it didn't.

I booted into Ubuntu and tried to run the 'mdadm --create' command, only to find my sdb2 partition was busy and unusable, so I decided to load my Ubuntu live disc and install mdadm. Another mistake. I created /dev/md0 and /dev/md1 from sda2/sdb2 and sda6/sdb6, which succeeded. However, since mdadm was installed on the *live* OS, it wouldn't boot to /dev/md0 when I rebooted to the hard disk OS.

I thought I would be "smart" and take a clonezilla image of my entire drive before doing all this, so I would have a "reset button" in case of a problem like this. Well, for reasons I don't understand, restoring the **pre-mdadm** image does NOT bring me back to a bootable ext3 system partition. Ubuntu still recognizes /dev/sda2 as raid and won't boot it because it can't find the right UUID. I find this annoying and strange, since a clone should restore all that to how it was before, right?

My questions are:
[LIST=1]
[*]how can I reset my sda2 and sda6 to ext3 so I can boot like normal and try again?
[*]can someone please explain in fairly n00bish terms how to migrate to raid1 while using existing partitions?**
[/LIST]


*I understand that mdadm will NOT mirror ntfs partitions. I don't care, I just want my linux partitions mirrored.
**This question is not nearly as important as question 1. I am confident that with enough keyboard mashing I can figure it out, but if anyone would be so kind, I would greatly appreciate it!

---

