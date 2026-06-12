---
title: "random freeze for few seconds"
date: 2009-02-09
forum: Hardware
---

### Post by b4nsh33 on 2009-02-09
Hi, since several dyas ago, my machine freezes for a few seconds and im unable to open any program windows, this last for 60-90 seconds, i see this error in my /var/log/messages

Feb  9 15:23:31 mmiranda kernel: [  765.882215] ata1: EH complete
Feb  9 15:23:31 mmiranda kernel: [  765.882299] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
Feb  9 15:23:31 mmiranda kernel: [  765.882339] sd 0:0:0:0: [sda] Write Protect is off
Feb  9 15:23:31 mmiranda kernel: [  765.882408] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb  9 15:23:31 mmiranda kernel: [  768.356201] ata1.00: configured for UDMA/100
Feb  9 15:23:31 mmiranda kernel: [  768.356228] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb  9 15:23:31 mmiranda kernel: [  768.356238] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Feb  9 15:23:31 mmiranda kernel: [  768.356250] Descriptor sense data with sense descriptors (in hex):
Feb  9 15:23:31 mmiranda kernel: [  768.356256]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Feb  9 15:23:31 mmiranda kernel: [  768.356282]         03 12 e1 77 
Feb  9 15:23:31 mmiranda kernel: [  768.356294] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Feb  9 15:23:31 mmiranda kernel: [  768.356346] ata1: EH complete
Feb  9 15:23:31 mmiranda kernel: [  768.356698] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
Feb  9 15:23:31 mmiranda kernel: [  768.356865] sd 0:0:0:0: [sda] Write Protect is off
Feb  9 15:23:31 mmiranda kernel: [  768.357229] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb  9 15:24:31 mmiranda kernel: [  828.216174] CE: hpet increasing min_delta_ns to 33750 nsec


What should i check to solve this problem, i think this has appeared since my last update 2 weeks ago, before that , my ubuntu box worked like a charm.
my machine is a HP 8710W

---

