---
title: "SATA only recognized sometimes in 7.10"
date: 2008-04-25
forum: Hardware
---

### Post by Hellishcross on 2008-04-25
**My Setup:**
SATA Drive with Windows XP
PATA Drive with Ubuntu 7.10
SATA is set to boot before PATA 

Grub gives me a choice of which OS to load
[B]
My Problem:[/B]
Ubuntu only recognizes my SATA drive sometimes... sometimes it doesn't see it.

Is there anyway to fix this from happening? :confused:

---

### Post by ph7 on 2008-06-07
I'm experiencing a similar problem, described in [this thread]("http://ubuntuforums.org/showthread.php?p=5133769#post5133769"). The difference is that I do not have dual boot. My setup:

PATA Kubuntu 8.04
SATA data

As you say sometimes Kubuntu recognizes the disk, sometimes it does not.

Anyone with a similar issue/solution?

---

### Post by Kor-Skarn on 2009-05-08
I've just installed the Jaunty and it seems I have the same problem: SATA link down. My kernel log says on and on:

[ 5159.397489] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4040000 action 0xe frozen
[ 5159.397493] ata2: irq_stat 0x00000040, connection status changed
[ 5159.397495] ata2: SError: { CommWake DevExch }
[ 5159.397500] ata2: hard resetting link
[ 5160.120025] ata2: SATA link down (SStatus 0 SControl 300)
[ 5160.120030] ata2: EH complete
[ 5163.586193] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
[ 5163.586197] ata2: irq_stat 0x00000040, connection status changed
[ 5163.586200] ata2: SError: { DevExch }
[ 5163.586204] ata2: hard resetting link
[ 5164.308023] ata2: SATA link down (SStatus 0 SControl 300)
[ 5164.308028] ata2: EH complete
[ 5166.053221] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
[ 5166.053224] ata2: irq_stat 0x00000040, connection status changed
[ 5166.053226] ata2: SError: { DevExch }
[ 5166.053230] ata2: hard resetting link
[ 5166.776023] ata2: SATA link down (SStatus 0 SControl 300)
[ 5166.776028] ata2: EH complete
[ 5167.035188] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
[ 5167.035190] ata2: irq_stat 0x00000040, connection status changed
[ 5167.035193] ata2: SError: { DevExch }
[ 5167.035196] ata2: hard resetting link
[ 5167.756023] ata2: SATA link down (SStatus 0 SControl 300)
[ 5167.756028] ata2: EH complete
[ 5176.936270] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
[ 5176.936274] ata2: irq_stat 0x00000040, connection status changed
[ 5176.936276] ata2: SError: { DevExch }
[ 5176.936281] ata2: hard resetting link
[ 5177.660025] ata2: SATA link down (SStatus 0 SControl 300)
[ 5177.660031] ata2: EH complete
[ 5178.829703] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
[ 5178.829706] ata2: irq_stat 0x00000040, connection status changed
[ 5178.829709] ata2: SError: { DevExch }
[ 5178.829713] ata2: hard resetting link
[ 5179.552025] ata2: SATA link down (SStatus 0 SControl 300)
[ 5179.552030] ata2: EH complete
[ 5179.882883] ata2: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
[ 5179.882886] ata2: irq_stat 0x00000040, connection status changed
[ 5179.882888] ata2: SError: { DevExch }
[ 5179.882892] ata2: hard resetting link

I have dual boot of Windows XP and Kubuntu 9.04 64-bit, but more importantly my primary disk (on which both systems are installed) is PATA and I have 2 other SATA disks - one of them is also Samsung 500 GB HDD. (What a coincidence...) 
I can mount and browse both disks, but it keeps throwing errors at startup and soiling my log in run-time.

---

### Post by Kor-Skarn on 2009-05-08
After further investigation it seems that I have a little different problem after all (see attached log if interested):

My PATA drive is identified wrongly as SATA drive (ata3); I don't know why. But  the real problem causes unconnected (?) SATA link (ata2), which is reported as down (correctly I suppose, since all my other SATA devices were successfully detected on other links), but the system keeps querying it indefinitely. Bugger.

---

### Post by Kor-Skarn on 2009-05-09
Well, problem solved. It was a matter of playing with my BIOS (lucky I know what it is and have all the nice documentation). Apparently I had an extra SATA port for RAID configuration on my mainboard (ASUS P5KC), which I never used, and it needed to be turned off (switching to AHCI mode didn't help). Works fine now...

Anyway, sorry for my spamming into this thread (I really thought that the problems were related in the beginning), at least it got livened up after a year :-) The "talking" helped figuring it out.

---

