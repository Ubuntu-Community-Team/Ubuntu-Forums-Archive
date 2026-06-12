---
title: "SATA Errors and read/write issues"
date: 2009-12-17
forum: Hardware
---

### Post by idlehands on 2009-12-17
This is on a 9.10 Ubuntu Server. 
I have 1 120gb harddrive in the box as a root partition, and then three WD 2tb drives in a reiserfs lvm2. I can consistently get these errors in /var/logs/messages:

```
Dec 14 10:47:54 Saturn kernel: [2494375.441716] ata4: hard resetting link
Dec 14 10:47:55 Saturn kernel: [2494376.350073] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 14 10:47:55 Saturn kernel: [2494376.390592] ata4.00: configured for UDMA/133
Dec 14 10:47:55 Saturn kernel: [2494376.390688] ata4: EH complete
Dec 14 10:47:55 Saturn kernel: [2494376.390888] sd 3:0:0:0: [sdd] 3907029168 512-byte hardware sectors: (2.00 TB/1.81 TiB)
Dec 14 10:47:55 Saturn kernel: [2494376.390930] sd 3:0:0:0: [sdd] Write Protect is off
Dec 14 10:47:55 Saturn kernel: [2494376.390979] sd 3:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA

```


This issue was also there on 9.04.

I've had the issues with the system since I got the drives, which are/brand new. Some googling on the errors suggested that its a motherboard issue, which I would be happier with than a drive issue. 

If there is a software fix though I'm open to ideas. I don't have enough space to make a backup of the system to preserve all the data on it at this point. I am not particularly worried about a system failure and losing the data as I accepted that with the setup. its having to rebuild the system and lose the data that way which would irritate me.

---

