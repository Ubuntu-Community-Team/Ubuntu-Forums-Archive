---
title: "smartmontools and RAID controllers - Ubuntu 10.04"
date: 2010-07-20
forum: Hardware
---

### Post by Silicon Knight on 2010-07-20
Hi All.  I spent quite a bit of time trying to figure out how to get SMART monitoring on my PERC 5i / LSI 8480E SAS controller (although I'm using SATA drives).

So basically reading smartmontools man page it says its compadible with PERC by using the following:
> smartctl -a -d megaraid,(x) /dev/sd(y)
[SIZE="2"]*Where (x) is your raid controller virtual disk and (y) is the disk in Ubuntu[/SIZE]

however as much as I tried I couldn't get it to work, all I would receive from that command was:
> =======> INVALID ARGUMENT TO -d: megaraid,2
=======> VALID ARGUMENTS ARE: ata, scsi, marvell, sat,3ware,N, hpt,L/M/N cciss,N <=======

Turns out the ubuntu version is slightly outdated and dosnt work with the megaraid trigger.  What I needed to do was upgrade so I found version smartctl 5.40 and it worked perfectly.  I was even able to use GSmartControl!

So if you find yourself in the same situation as me, where you want to monitor the SMART values of your PERC or LSI SAS controller smartmontools DOES work but, as I forgot to do... Be sure you have the latest version! :p  Hope this helps others as well!

---

### Post by Mikecronn on 2010-07-22
Hi there,

Thanks for the info.

How did you install the new smartmontools? I can't find a backported package...

Thanks,
Mike

---

