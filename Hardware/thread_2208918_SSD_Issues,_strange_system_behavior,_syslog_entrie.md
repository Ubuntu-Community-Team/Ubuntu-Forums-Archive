---
title: "SSD Issues, strange system behavior, syslog entries"
date: 2014-03-03
forum: Hardware
---

### Post by dan9550 on 2014-03-03
This has been an ongoing issue for a long period although it does not occur frequently on the odd occasion i have had my main ssd basically remove itself from the system causing anything that attempts to read from disk fail. I have also had the occasional freeze and more commonly freezing during or just after boot at the logon screen. Even after replacing the SATA cable and re installing ubuntu, i'm starting to wonder is this a hardware issue or operating system issue i would really like some help with this.

Here is what appeared in my syslog about 30 minutes ago when my entire system lost its root filesystem.

```
Mar  3 17:03:40 dan9550 kernel: [15972.413558] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90202 action 0xe frozenMar  3 17:03:40 dan9550 kernel: [15972.413561] ata3: irq_stat 0x00400000, PHY RDY changed
Mar  3 17:03:40 dan9550 kernel: [15972.413564] ata3: SError: { RecovComm Persist PHYRdyChg 10B8B }
Mar  3 17:03:40 dan9550 kernel: [15972.413568] ata3: hard resetting link
Mar  3 17:03:41 dan9550 kernel: [15973.371915] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Mar  3 17:03:41 dan9550 kernel: [15973.373309] ata3.00: configured for UDMA/133
Mar  3 17:03:41 dan9550 kernel: [15973.373319] ata3: EH complete
```

---

### Post by phidia on 2014-03-03
Perhaps [this]("http://ubuntuforums.org/showthread.php?t=2057183") is related or helps hopefully.

---

