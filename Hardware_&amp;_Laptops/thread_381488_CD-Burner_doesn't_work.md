---
title: "CD-Burner doesn't work"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by kaz_ on 2007-03-10
**[COLOR="Red"]UPDATE: I figure it out. I guess there was a problem with having two cd drives on the save ide cable.[/COLOR]**


I'm running Edgy Eft and am trying to get a HP CD-Writer Plus to work. I noticed that after installing it, it took Ubuntu a long time to start up. If I put a cd in it, it doesn't see the cd. If I click on CD-ROM 2 under Computer, it says "Unable to mount the selected volume...mount: special device /dev/hdc does not exist". In dmesg it says:

hdc: WO ,_}vE cd-rom xm-6602b, ATAPI CD/DVD-ROM drive
hdc: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
hdc: set_drive_speed_status: error=0x04 { AbortedCommand }
...
ide-cd: cmd 0x5a timed out
hdc: lost interrupt
hdc: ATAPI 46X CD-ROM CD-R/RW drive, 1408kB Cache, (U)DMA
Uniform CD-ROM driver Revision: 3.20
hdc: lost interrupt
...
ide-cd: cmd 0x3 timed out
hdc: lost interrupt
...
ide-cd: cmd 0x3 timed out
hdc: lost interrupt
hdc: lost interrupt
ide-cd: cmd 0x3 timed out
hdc: lost interrupt
ide-cd: cmd 0x3 timed out
hdc: lost interrupt
hdc: lost interrupt
ide-cd: cmd 0x3 timed out
hdc: lost interrupt
ide-cd: cmd 0x3 timed out
hdc: lost interrupt
hdc: lost interrupt
ide-cd: cmd 0x3 timed out
hdc: lost interrupt
ide-cd: cmd 0x3 timed out
hdc: lost interrupt
hdc: lost interrupt

I'm really frustrated. Any help would be appreciated. I'll update later if I get some more info. Thanks

Kaz

---

### Post by Kinslayer on 2007-04-16
I had a problem with long startup & shutdown times.  The problem was my cd rom & dvd rom weren't mounting properly.  They were attached to the same ide cable.  How I fixed it was I shutdown the system, unplugged the cables from each, & rebooted.  It started right up.  Aha.  I shutdown again, which took less than a minute instead of the usual 5-10 minutes.  I connected one drive, started up, & it loaded quickly.  I repeated this with the second drive, with no problems.  A third time with both booted up quickly, and it hasn't been an issue since, at least for the couple of days since I've done this.

---

