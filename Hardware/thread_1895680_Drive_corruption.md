---
title: "Drive corruption"
date: 2011-12-15
forum: Hardware
---

### Post by patman0623 on 2011-12-15
Background: I was goofing around in VirtualBox earlier, when suddenly it crashed so hard I had to reboot my computer. The problem is, the drive that it was playing with is now corrupt; I don't know if this is VirtualBox's fault, or if it crashed because the drive has been going downhill for a while.

Description of the problem: I'm getting the following output, with minor changes, in my dmesg. The error is continually spamming dmesg, so that I can't even work in a non-GUI terminal (e.g., Alt-Ctrl-F1):
```
[ 3420.188180] ata1: EH complete
[ 3424.425283] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[ 3424.425294] ata1.00: irq_stat 0x40000008
[ 3424.425302] ata1.00: failed command: READ FPDMA QUEUED
[ 3424.425317] ata1.00: cmd 60/08:08:e2:2a:58/00:00:13:00:00/40 tag 1 ncq 4096 in
[ 3424.425321]          res 41/40:00:e2:2a:58/00:00:13:00:00/40 Emask 0x409 (media error) <F>
[ 3424.425328] ata1.00: status: { DRDY ERR }
[ 3424.425333] ata1.00: error: { UNC }
[ 3424.427145] ata1.00: configured for UDMA/133
[ 3424.427172] ata1: EH complete
[ 3428.508720] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[ 3428.508731] ata1.00: irq_stat 0x40000008
[ 3428.508740] ata1.00: failed command: READ FPDMA QUEUED
[ 3428.508755] ata1.00: cmd 60/08:00:e2:2a:58/00:00:13:00:00/40 tag 0 ncq 4096 in
[ 3428.508759]          res 41/40:00:e2:2a:58/00:00:13:00:00/40 Emask 0x409 (media error) <F>
[ 3428.508766] ata1.00: status: { DRDY ERR }
[ 3428.508771] ata1.00: error: { UNC }
[ 3428.510717] ata1.00: configured for UDMA/133
[ 3428.510732] ata1: EH complete
[ 3432.458695] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[ 3432.458705] ata1.00: irq_stat 0x40000008
[ 3432.458714] ata1.00: failed command: READ FPDMA QUEUED
[ 3432.458729] ata1.00: cmd 60/08:08:e2:2a:58/00:00:13:00:00/40 tag 1 ncq 4096 in
[ 3432.458733]          res 41/40:00:e2:2a:58/00:00:13:00:00/40 Emask 0x409 (media error) <F>
[ 3432.458740] ata1.00: status: { DRDY ERR }
[ 3432.458745] ata1.00: error: { UNC }
[ 3432.460721] ata1.00: configured for UDMA/133
[ 3432.460742] ata1: EH complete
[ 3436.408599] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[ 3436.408609] ata1.00: irq_stat 0x40000008
[ 3436.408617] ata1.00: failed command: READ FPDMA QUEUED
[ 3436.408632] ata1.00: cmd 60/08:00:e2:2a:58/00:00:13:00:00/40 tag 0 ncq 4096 in
[ 3436.408636]          res 41/40:00:e2:2a:58/00:00:13:00:00/40 Emask 0x409 (media error) <F>
[ 3436.408643] ata1.00: status: { DRDY ERR }
[ 3436.408648] ata1.00: error: { UNC }
[ 3436.410457] ata1.00: configured for UDMA/133
[ 3436.410484] ata1: EH complete
[ 3440.503240] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[ 3440.503251] ata1.00: irq_stat 0x40000008
[ 3440.503258] ata1.00: failed command: READ FPDMA QUEUED
[ 3440.503274] ata1.00: cmd 60/08:08:e2:2a:58/00:00:13:00:00/40 tag 1 ncq 4096 in
[ 3440.503277]          res 41/40:00:e2:2a:58/00:00:13:00:00/40 Emask 0x409 (media error) <F>
[ 3440.503285] ata1.00: status: { DRDY ERR }
[ 3440.503290] ata1.00: error: { UNC }
[ 3440.505261] ata1.00: configured for UDMA/133
[ 3440.505300] sd 0:0:0:0: [sda] Unhandled sense code
[ 3440.505306] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3440.505314] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[ 3440.505324] Descriptor sense data with sense descriptors (in hex):
[ 3440.505328]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 3440.505347]         13 58 2a e2 
[ 3440.505355] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[ 3440.505366] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 13 58 2a e2 00 00 08 00
[ 3440.505382] end_request: I/O error, dev sda, sector 324545250
[ 3440.505392] Buffer I/O error on device sda3, logical block 60
[ 3440.505401] Buffer I/O error on device sda3, logical block 61
[ 3440.505408] Buffer I/O error on device sda3, logical block 62
[ 3440.505414] Buffer I/O error on device sda3, logical block 63
[ 3440.505454] ata1: EH complete
```

The result is I can't run [FONT="Courier New"]badblocks[/FONT] on it either, because badblocks can only read one block per 35 seconds (out of 20482874 total). But I would really like to get the content off the drive without waiting for 26 years for badblocks to fix it (or not fix it). 

Is there a way for me to make the kernel quit from continually rechecking after a bad read and subsequently hanging system operations?

Note: I know the content is still on the drive, because the [FONT="Courier New"]ls[/FONT] command is still working when the system is mounted (albeit working slowly).

---

