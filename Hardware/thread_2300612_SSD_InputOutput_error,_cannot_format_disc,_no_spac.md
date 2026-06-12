---
title: "SSD Input/Output error, cannot format disc, no space left issue"
date: 2015-10-27
forum: Hardware
---

### Post by jarko2 on 2015-10-27
Hi you Guys,

Recently when I was coping something to my disc (I knew that there might be not enough space on it) after a while system just freeze so after 20 minutes without any reactions whatsoever I've reset computer and since then Ubuntu cannot boot, I've tried recovery mode but there is no home directory on it and fstab doesn't exist. When I've loaded LiveCD I tried to format partition but **gparted** doesn't see my disc, and **ubuntu->discs** tool is unable to format it claiming input/output error. I've tried to **gdisc** tool and its start with that messages

GPT fdisk (gdisk) version 0.8.8

Problem reading disk in BasicMBRData::ReadMBRData()!
Warning! Read error 22; strange behavior now likely!
Warning! Read error 22; strange behavior now likely!
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present

I cannot write any changes with new table partition where gdisc says 

Warning! An error was reported when writing the partition table! This error
MIGHT be harmless, or the disk might be damaged! Checking it is advisable.

can i do anything else to fix SSD  ? (i don't even worry about the data anymore , just wanna to install new system with new partiotion table).

---

### Post by yancek on 2015-10-27
Once you get past 95% disk full, you are likely to have problems booting so bear that in mind in the future.  Use any Linux Live CD/flash drive and do a filesystem check on the partitions using the fsck command.

---

