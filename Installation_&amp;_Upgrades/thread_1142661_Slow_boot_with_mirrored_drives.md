---
title: "Slow boot with mirrored drives"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by Jildert on 2009-04-29
My Ubuntu 8.04 server is slow during start-up and running applications. First i was running Redhat, now i've upgraded the sytem from 512MB Ram to 2GB ram and from 2*32GB HD IDE to 2*500GB S-ATA disks. And installed Ubuntu 8.04 server

After re-installing the system it was a lot slower. The server is running apache, mysql, samba. MySQL queries are slower and a lot of other things are also slow.

System
Intel(R) Pentium(R) 4 CPU 2.40GHz
2GB Ram
2*500 GB HD (software raid 1)

```
#cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sda2[0] sdb2[1]
      4883648 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[1]
      439449920 blocks [2/2] [UU]

unused devices: <none>

```Here is the output of bootchart [ATTACH]111672[/ATTACH]<-- here

---

### Post by Jildert on 2009-05-05
anyone?

---

