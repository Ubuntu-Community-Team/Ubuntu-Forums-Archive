---
title: "Bizarre RAID problem"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by abrahamsmith on 2008-01-26
3 weeks ago, I build a new server with a kernel software RAID5, built with mdadm.  Since then, every weekend (either Saturday or Sunday morning) the RAID drops a drive with the following error:

```

Jan 26 04:45:32 albus kernel: [224527.949216] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jan 26 04:45:32 albus kernel: [224527.949225] ata1.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x0 data 0 
Jan 26 04:45:32 albus kernel: [224527.949227]          res 00/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Jan 26 04:45:38 albus kernel: [224530.497119] ata1: port is slow to respond, please be patient (Status
 0xd0)
Jan 26 04:45:42 albus kernel: [224532.736545] ata1: device not ready (errno=-16), forcing hardreset
Jan 26 04:45:43 albus kernel: [224533.037420] ata1: SRST failed (errno=-19)
Jan 26 04:45:43 albus kernel: [224533.037427] ata1: reset failed (errno=-19), retrying in 10 secs
Jan 26 04:45:53 albus kernel: [224537.798104] ata1: SRST failed (errno=-19)
Jan 26 04:45:53 albus kernel: [224537.798110] ata1: reset failed (errno=-19), retrying in 10 secs
Jan 26 04:46:03 albus kernel: [224542.558788] ata1: SRST failed (errno=-19)
Jan 26 04:46:03 albus kernel: [224542.558794] ata1: reset failed (errno=-19), retrying in 35 secs
Jan 26 04:46:16 albus linksys: Updated tock.no-ip.org to 69.134.0.133
Jan 26 04:46:38 albus kernel: [224559.221182] ata1: SRST failed (errno=-19)
Jan 26 04:46:38 albus kernel: [224559.221188] ata1: reset failed, giving up
Jan 26 04:46:38 albus kernel: [224559.221191] ata1.00: disabled
Jan 26 04:46:38 albus kernel: [224559.221313] end_request: I/O error, dev sda, sector 976772992
Jan 26 04:46:38 albus kernel: [224559.221321] md: super_written gets error=-5, uptodate=0
Jan 26 04:46:38 albus kernel: [224559.221325] raid5: Disk failure on sda, disabling device. Operation continuing on 5 devices
Jan 26 04:46:38 albus kernel: [224559.313158] RAID5 conf printout:
Jan 26 04:46:38 albus kernel: [224559.313164]  --- rd:6 wd:5
Jan 26 04:46:38 albus kernel: [224559.313167]  disk 0, o:0, dev:sda
Jan 26 04:46:38 albus kernel: [224559.313169]  disk 1, o:1, dev:sdb
Jan 26 04:46:38 albus kernel: [224559.313171]  disk 2, o:1, dev:sdc
Jan 26 04:46:38 albus kernel: [224559.313172]  disk 3, o:1, dev:sdd
Jan 26 04:46:38 albus kernel: [224559.313174]  disk 4, o:1, dev:sde
Jan 26 04:46:38 albus kernel: [224559.313176]  disk 5, o:1, dev:sdf
Jan 26 04:46:38 albus kernel: [224559.320202] RAID5 conf printout:
Jan 26 04:46:38 albus kernel: [224559.320206]  --- rd:6 wd:5
Jan 26 04:46:38 albus kernel: [224559.320209]  disk 1, o:1, dev:sdb
Jan 26 04:46:38 albus kernel: [224559.320210]  disk 2, o:1, dev:sdc
Jan 26 04:46:38 albus kernel: [224559.320212]  disk 3, o:1, dev:sdd
Jan 26 04:46:38 albus kernel: [224559.320214]  disk 4, o:1, dev:sde
Jan 26 04:46:38 albus kernel: [224559.320216]  disk 5, o:1, dev:sdf
Jan 26 04:46:38 albus mdadm: Fail event detected on md device /dev/md0, component device /dev/sda

```

The drive /dev/sda is unresponsive after this event, and I have to reboot and do **mdadm /dev/md0 --add /dev/sda**.  Once the parity is rebuilt, everything is fine.

This is extremely annoying, and for about 12 hours the RAID is degraded (hence at risk of  complete failure).   I can't figure out what the hell is going on.




Here are some notes:
[LIST]
[*]There is no evidence that the drive is actually failing.  Extensive SMART tests have been done.
[*] Daily and weekly cron jobs appear to have finished an hour-or-so before the failure event, but the regularity still makes me suspicious of an errant cron job.  I've tested all of the cron jobs individually, and none of them seem to be a direct cause.
[*] This is Ubuntu 7.10, fully updated, also running mythtv and various servers
[*] The SATA controller is an nVidia MCP55, which, along with the MCP51, has some similar errors on lkml from last Fall, but they are inconclusive.
[/LIST]



How can these benign failures be so regular? 
Anyone else have similar problems?  Any ideas, no matter how crazy?

---

### Post by samosamo on 2008-01-26
Funny that it only happens on the weekend, I guess you don't think that is a coincidence.  Is there anything cron'd for the weekend that is hdd intensive?

I recommend enterprise server hard drives built for 24/7 operation, I personally run WD Caviar RE2's (as oppose to regular Caviar) but Barracuda ES's are just as good.

---

