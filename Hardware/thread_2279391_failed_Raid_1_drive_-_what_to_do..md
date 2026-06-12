---
title: "failed Raid 1 drive - what to do."
date: 2015-05-23
forum: Hardware
---

### Post by Windowsxpnomore on 2015-05-23
Ubuntu 12.04.2

ok one of my seagate raid 1 disks has failed:
Apr 19 02:29:14 MediaServer kernel: [29600647.522090] md/raid1:md0: sda1: rescheduling sector 3998908672
Apr 19 02:29:17 MediaServer kernel: [29600650.684506] md/raid1:md0: read error corrected (8 sectors at 3999170856 on sda1)
Apr 19 02:29:20 MediaServer kernel: [29600653.899771] md/raid1:md0: read error corrected (8 sectors at 3999170864 on sda1)
Apr 19 02:29:20 MediaServer kernel: [29600654.053368] md/raid1:md0: redirecting sector 3998908672 to other mirror: sda1
Apr 19 02:29:46 MediaServer kernel: [29600680.046827] md/raid1:md0: sda1: rescheduling sector 4002066432
Apr 19 02:29:49 MediaServer kernel: [29600683.014274] md/raid1:md0: sda1: rescheduling sector 4002066688
Apr 19 02:29:53 MediaServer kernel: [29600686.309791] md/raid1:md0: read error corrected (8 sectors at 4002328808 on sda1)
Apr 19 02:29:56 MediaServer kernel: [29600689.500120] md/raid1:md0: read error corrected (8 sectors at 4002328816 on sda1)
Apr 19 02:29:59 MediaServer kernel: [29600692.673852] md/raid1:md0: read error corrected (8 sectors at 4002328824 on sda1)
Apr 19 02:29:59 MediaServer kernel: [29600692.673860] md/raid1:md0: redirecting sector 4002066432 to other mirror: sda1
Apr 19 02:30:02 MediaServer kernel: [29600695.806029] md/raid1:md0: read error corrected (8 sectors at 4002328832 on sda1)
......
Apr 19 03:04:24 MediaServer kernel: [29602751.941133] INFO: task jbd2/md0-8:562 blocked for more than 120 seconds.
Apr 19 03:04:24 MediaServer kernel: [29602751.943215] jbd2/md0-8      D ffffffff8180cbe0     0   562      2 0x00000000
Apr 19 03:37:24 MediaServer kernel: [29604725.744315] md/raid1:md0: sda1: rescheduling sector 4015099304
Apr 19 03:37:24 MediaServer kernel: [29604725.745457] md/raid1:md0: sda1: rescheduling sector 4015099560
Apr 19 03:37:24 MediaServer kernel: [29604725.885798] md/raid1:md0: Disk failure on sda1, disabling device.
Apr 19 03:37:24 MediaServer kernel: [29604725.885798] md/raid1:md0: Operation continuing on 1 devices.
Apr 19 03:37:24 MediaServer kernel: [29604725.894073] md/raid1:md0: redirecting sector 4015099304 to other mirror: sdc1
Apr 19 03:37:24 MediaServer mdadm[1426]: Fail event detected on md device /dev/md0, component device /dev/sda1
Apr 19 03:37:24 MediaServer kernel: [29604726.131057] md/raid1:md0: redirecting sector 4015099560 to other mirror: sdc1

I have the data all backup on another disk which is mounted in the server.

How do I physically know what disk is sda1 as both disks are the same make?

---

### Post by TheFu on 2015-05-23
Unplug 1 of them?  Is all the data gone or is it the same as before?  50/50 shot on the first attempt, regardless you will know which disk it is that has failed.

---

### Post by tgalati4 on 2015-05-23
You can install *smartmontools* to get the drives' serial number:

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
sudo smartctl -a /dev/sdb
sudo smartctl -a /dev/sdc

```

---

