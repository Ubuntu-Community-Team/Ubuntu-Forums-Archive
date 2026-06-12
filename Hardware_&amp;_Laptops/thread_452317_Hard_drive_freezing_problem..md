---
title: "Hard drive freezing problem."
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by prlewis on 2007-05-23
Hi,

Since switching to Kubuntu from Gentoo, I've noticed occasionally that the system freezes (except the mouse cursor) for a few seconds. After a brief wait, everything continues as normal.

I was looking for some clue as to what might be going on in the system logs, and the only thing which I can find is this from /var/log/messages:

May 23 12:11:10 nutkin kernel: [ 6449.700000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
May 23 12:11:10 nutkin kernel: [ 6456.700000] ata1: port is slow to respond, please be patient (Status 0xd0)
May 23 12:11:10 nutkin kernel: [ 6479.716000] ata1: soft resetting port
May 23 12:11:10 nutkin kernel: [ 6480.044000] ata1.00: ata_hpa_resize 1: sectors = 180468192, hpa_sectors = 195371568
May 23 12:11:10 nutkin kernel: [ 6480.044000] ata1.00: Host Protected Area detected.
May 23 12:11:10 nutkin kernel: [ 6480.044000]      current size : 180468192 sectors (92399 MB)
May 23 12:11:10 nutkin kernel: [ 6480.044000]      native  size : 195371568 sectors (100030 MB)
May 23 12:11:10 nutkin kernel: [ 6480.052000] ata1.00: ata_hpa_resize 1: sectors = 180468192, hpa_sectors = 195371568
May 23 12:11:10 nutkin kernel: [ 6480.052000] ata1.00: Host Protected Area detected.
May 23 12:11:10 nutkin kernel: [ 6480.052000]      current size : 180468192 sectors (92399 MB)
May 23 12:11:10 nutkin kernel: [ 6480.052000]      native  size : 195371568 sectors (100030 MB)
May 23 12:11:10 nutkin kernel: [ 6480.052000] ata1.00: configured for UDMA/100
May 23 12:11:10 nutkin kernel: [ 6480.216000] ata1.01: configured for UDMA/33
May 23 12:11:10 nutkin kernel: [ 6480.216000] ata1: EH complete
May 23 12:11:10 nutkin kernel: [ 6480.232000] SCSI device sda: 180468192 512-byte hdwr sectors (92400 MB)
May 23 12:11:10 nutkin kernel: [ 6480.232000] sda: Write Protect is off
May 23 12:11:10 nutkin kernel: [ 6480.640000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 23 12:11:10 nutkin kernel: [ 6480.664000] SCSI device sda: 180468192 512-byte hdwr sectors (92400 MB)
May 23 12:11:10 nutkin kernel: [ 6480.664000] sda: Write Protect is off
May 23 12:11:10 nutkin kernel: [ 6480.664000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

It looks like something might be misconfigured in the disk controller drivers, or else could it be a bug? I'm relatively sure that it's not a hardware fault, since I never experienced this under gentoo.

Any suggestions about what to do to fix this?

Cheers!

Pete.

---

### Post by hehe on 2007-05-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

I had also post a problem in [http://ubuntuforums.org/showthread.php?t=452123](http://ubuntuforums.org/showthread.php?t=452123). Last night I just recheck the kernel message and found the same dump with yours. Today I googled and find this bug in launchpad which looks a bit the same with our problem, it's related to CD drive instead of HD drive. Could be a bug in libata, but still I haven't have solutions for now.

Hope that someone sees this and have a solution for us :)

---

