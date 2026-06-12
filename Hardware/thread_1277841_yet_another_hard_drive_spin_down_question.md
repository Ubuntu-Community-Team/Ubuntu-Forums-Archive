---
title: "yet another hard drive spin down question"
date: 2009-09-28
forum: Hardware
---

### Post by acranox on 2009-09-28
I'll try and keep this short.  I've got a box running Jaunty, it's got two Seagate 1TB SATA disks in it.  One disk is just for backups, so it sits idle for most of the day and then cranks away for an hour or so.  I'd like this disk to just spin down and park when it's idle.  I manually ran hdparm -y /dev/sdb and then used hdparm -C /dev/sdb to confirm the disk was in standby.
In the past 8 hours I checked it occasionally, and it remained in standby every time I checked on it.
Before I put it into standby the Start_Stop_Count was 398.
I access the disk, it spun up, and now the Start_Stop_Count is 555.
How did that happen?
I'd like to setup power management for the disk to spin it down when idle, but I don't want to kill it with excessive spinup/down cycles and head parking.
It's also worth noting that when I make changes to settings in /etc/hdparm.conf, they have no effect.  Running commands manually works though.  Anyone else with Jaunty have hdparm.conf actually work?

--Peter

---

