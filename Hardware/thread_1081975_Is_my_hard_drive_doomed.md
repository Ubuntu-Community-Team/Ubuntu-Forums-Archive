---
title: "Is my hard drive doomed?"
date: 2009-02-27
forum: Hardware
---

### Post by Iesos on 2009-02-27
My work-computer (a IBM thinkpad (old one: 600X)), running a server ubuntu, had a rather severe hardware failure the other night. The computer did not boot and the ubuntu installation cd (this case the server) did not manage to find a hard drive at all. After taking out the hard drive, blowing it like its a NES-game, and plugging it in, it works fine. The messages that indicate the drive failure were:

[QUOTE="/var/log/messages"]Feb 26 23:10:33 unimatrix4 kernel: [3933153.060223] ata1: link is slow to respond, please be patient (ready=0)
Feb 26 23:10:33 unimatrix4 kernel: [3933158.040203] ata1: device not ready (errno=-16), forcing hardreset
Feb 26 23:10:33 unimatrix4 kernel: [3933158.040231] ata1: soft resetting link
Feb 26 23:10:33 unimatrix4 kernel: [3933159.820926] ata1.00: configured for UDMA/33
Feb 26 23:10:33 unimatrix4 kernel: [3933159.820981] ata1: EH complete
Feb 26 23:10:33 unimatrix4 kernel: [3933159.824560] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Feb 26 23:10:33 unimatrix4 kernel: [3933159.856464] sd 0:0:0:0: [sda] Write Protect is off
Feb 26 23:10:33 unimatrix4 kernel: [3933159.857315] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA[/QUOTE]

And the questions I ask myself now is:
* is my computer going to be fine?
* is my computer going to crash? (Is it most likely just the hard drive?)
* is my computer gonna turn into a NES-like device, in which I have to take out and blow the hard drive everytime I want to boot?

Anyone who have any experiance with old hard drives and/or those error messages?

---

### Post by smani on 2009-02-27
It does not necessaryly have to have something to do with the harddrive - many people had problems with (s)ata drives on recent kernel that produced similar messages, i.e. see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706). I also experienced the problem on a PC, the cause was a crappy DVD-Reader firmware. If you want to check the health of your harddisk, try looking at it's SMART data.

---

