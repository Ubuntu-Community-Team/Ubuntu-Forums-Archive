---
title: "Sony DVD"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by Lary Grant on 2007-06-18
I have a Sony DVD burner on a multi-boot system.  It is working for both playback and burning in Dapper, but not when I boot from my fresh Feisty partition.  I forget what all I had done in Dapper to get it working.

The symptoms in Feisty are:

K3B displays the spash screen then freezes the whole machine.  I have to do a hard reboot.

A DVD that I have previously burned in Dapper shows up in Feisty but it looks like all the files are empty and does not play back.

In Feisty, the automatic DVD burning thang that comes up when I insert a blank DVD (I have no idea what DVD burning software it is running automatically... it is not K3B)  seems to work, but the DVD ends up being blank at the end of the process.

Thanks!

---

### Post by Lary Grant on 2007-06-18
I tried accessing the DVD through the shell.  I tried doing an "ls" on one of the directories on the DVD and got:
[INDENT]ls: video_ts: Input/output error
[/INDENT]
I'm seeing these errors in "dmesg":
[INDENT][  625.671092] sr 1:0:1:0: SCSI error: return code = 0x08000002
[  625.671100] sr1: Current: sense key: Hardware Error
[  625.671103]     Additional sense: Logical unit communication CRC error (Ultra-DMA/32)
[  625.671112] end_request: I/O error, dev sr1, sector 1108
[/INDENT]

---

### Post by Lary Grant on 2007-06-19
Can someone at least give me some tips to help troubleshoot the problem?

---

