---
title: "Strange RAID5 behaviour"
date: 2012-10-10
forum: Hardware
---

### Post by petersaints on 2012-10-10
I have a server running Ubuntu 10.04 LTS and it has run fine for the last 2 years or so. It has four 250GB SATA drives in RAID5.

Today someone reported that it was running very slow. I rebooted just to see if it would fix it, but it didn't.
I checked the load average and it was pretty high (3.x to 4.x on a Quad Core Xeon). It was uncommon... but than I checked with htop and it wasn't a CPU problem. Then I saw that every few seconds a few processes were being blocked for disk access.
One of them was jbd2/mda1-8, with a little research I leaned that it related with ext4 journaling. To ease things I increased the journaling interval in fstab to 600 seconds. This "solved" part of the problem. 

Besides jbd2 there are also a md0_raid5 and flush-9:0 process accessing and blocking disk access every few seconds. This ones didn't go away with the fstab change. And are still hitting hard on the server's resources. It becomes barely usable but it's still not running normally.

I checked mdadm details of the different RAID devices and they are all running fine with no failures.

It was when I looked at the /var/log/syslog that I noticed something strange. I was getting multiple errors and the interval is pretty much consistent with the abnormal disk use I'm having. A portion of the log can be seen below.

```

Oct 10 20:57:44 arttreatisesinportugal kernel: [ 3317.457083] ata1.00: status: { DRDY }
Oct 10 20:57:44 arttreatisesinportugal kernel: [ 3317.470374] ata1: hard resetting link
Oct 10 20:57:44 arttreatisesinportugal kernel: [ 3317.998092] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 10 20:57:45 arttreatisesinportugal kernel: [ 3318.190372] ata1.00: configured for UDMA/33
Oct 10 20:57:45 arttreatisesinportugal kernel: [ 3318.190379] ata1.00: device reported invalid CHS sector 0
Oct 10 20:57:45 arttreatisesinportugal kernel: [ 3318.190387] ata1: EH complete
Oct 10 20:58:20 arttreatisesinportugal kernel: [ 3353.356667] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct 10 20:58:20 arttreatisesinportugal kernel: [ 3353.370260] ata1.00: failed command: FLUSH CACHE EXT
Oct 10 20:58:20 arttreatisesinportugal kernel: [ 3353.383935] ata1.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Oct 10 20:58:20 arttreatisesinportugal kernel: [ 3353.383936]          res 40/00:00:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Oct 10 20:58:20 arttreatisesinportugal kernel: [ 3353.424793] ata1.00: status: { DRDY }
Oct 10 20:58:20 arttreatisesinportugal kernel: [ 3353.438216] ata1: hard resetting link
Oct 10 20:58:20 arttreatisesinportugal kernel: [ 3353.965609] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 10 20:58:21 arttreatisesinportugal kernel: [ 3354.158077] ata1.00: configured for UDMA/33
Oct 10 20:58:21 arttreatisesinportugal kernel: [ 3354.158083] ata1.00: device reported invalid CHS sector 0
Oct 10 20:58:21 arttreatisesinportugal kernel: [ 3354.158092] ata1: EH complete
Oct 10 20:58:56 arttreatisesinportugal kernel: [ 3389.294268] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct 10 20:58:56 arttreatisesinportugal kernel: [ 3389.307993] ata1.00: failed command: FLUSH CACHE EXT
Oct 10 20:58:56 arttreatisesinportugal kernel: [ 3389.321758] ata1.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Oct 10 20:58:56 arttreatisesinportugal kernel: [ 3389.321759]          res 40/00:00:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Oct 10 20:58:56 arttreatisesinportugal kernel: [ 3389.362738] ata1.00: status: { DRDY }
Oct 10 20:58:56 arttreatisesinportugal kernel: [ 3389.376168] ata1: hard resetting link
Oct 10 20:58:56 arttreatisesinportugal kernel: [ 3389.903208] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 10 20:58:57 arttreatisesinportugal kernel: [ 3390.095817] ata1.00: configured for UDMA/33
Oct 10 20:58:57 arttreatisesinportugal kernel: [ 3390.095823] ata1.00: device reported invalid CHS sector 0
Oct 10 20:58:57 arttreatisesinportugal kernel: [ 3390.095832] ata1: EH complete
Oct 10 20:59:32 arttreatisesinportugal kernel: [ 3425.231899] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct 10 20:59:32 arttreatisesinportugal kernel: [ 3425.245587] ata1.00: failed command: FLUSH CACHE EXT
Oct 10 20:59:32 arttreatisesinportugal kernel: [ 3425.259314] ata1.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Oct 10 20:59:32 arttreatisesinportugal kernel: [ 3425.259315]          res 40/00:00:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Oct 10 20:59:32 arttreatisesinportugal kernel: [ 3425.300188] ata1.00: status: { DRDY }
Oct 10 20:59:32 arttreatisesinportugal kernel: [ 3425.313532] ata1: hard resetting link
Oct 10 20:59:32 arttreatisesinportugal kernel: [ 3425.840842] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 10 20:59:33 arttreatisesinportugal kernel: [ 3426.033571] ata1.00: configured for UDMA/33
Oct 10 20:59:33 arttreatisesinportugal kernel: [ 3426.033577] ata1.00: device reported invalid CHS sector 0
Oct 10 20:59:33 arttreatisesinportugal kernel: [ 3426.033585] ata1: EH complete

```

What does does this mean? And how can I fix it? I'm afraid of doing something wrong because I have no easy physical access to the server. Any ideas of what it might be?

Thanks in advance.

---

