---
title: "sd 0:0:0:0: [sda] Write Protect is off  (strange)"
date: 2008-10-14
forum: General Help
---

### Post by jolly79 on 2008-10-14
Hi guys

My main drive sda is acting strange, my /var/log/messages
fills up with the same message:

jolly79@jolly79-server:~$ tail -f /var/log/messages
Oct 14 08:39:33 jolly79-server kernel: [ 3124.765396] sd 0:0:0:0: [sda] Write Protect is off
Oct 14 08:39:33 jolly79-server kernel: [ 3124.765432] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 14 08:41:34 jolly79-server kernel: [ 3245.610981]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Oct 14 08:41:36 jolly79-server kernel: [ 3247.320369] ata1: soft resetting link
Oct 14 08:41:36 jolly79-server kernel: [ 3247.923998] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 14 08:41:37 jolly79-server kernel: [ 3247.956406] ata1.00: configured for UDMA/100
Oct 14 08:41:37 jolly79-server kernel: [ 3247.956426] ata1: EH complete
Oct 14 08:41:37 jolly79-server kernel: [ 3247.978605] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Oct 14 08:41:37 jolly79-server kernel: [ 3247.978641] sd 0:0:0:0: [sda] Write Protect is off
Oct 14 08:41:37 jolly79-server kernel: [ 3247.978659] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FU

Can enybody help me, i have triede everything now.

Cheers

-Gustav

---

### Post by jolly79 on 2008-10-14
enybody.....?

Is this a bad thing happening on my log...

---

### Post by alberto ferreira on 2008-10-14
I believe this is perfectly normal because you need to be able to write to the drive.

The question is: Are you having problems, at all? - If so, enumerate them.

---

### Post by jolly79 on 2008-10-14
Hi

Yes im having some problems, it&#347; hard to describe.
But it fells like the sytem is really buggy.

It takes forever to open folders, programs hang alot.
system is generaly slow.

I can se the ram dosent fill up, and programs hang.
I have just ran a memtest, and found some errors on two of my ram sticks.
so i took them out and im now running on 2gb and with a amd pehnon with four cors.

sorry for my bad english :-)

---

