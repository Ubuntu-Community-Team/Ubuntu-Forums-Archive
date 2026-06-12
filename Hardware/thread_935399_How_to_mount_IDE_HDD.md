---
title: "How to mount IDE HDD"
date: 2008-10-01
forum: Hardware
---

### Post by orangecakez on 2008-10-01
I have an IDE HDD and I bought an IDE to USB adapter. I connected the connector to the HDD and plugged it into my USB port, and I plugged the power in as well, but when I try to mount it, it gives me an error: > mount: /dev/sdb: can't read superblock

dmesg | tail:
```
~$ dmesg | tail
[437202.031193] usb-storage: device scan complete
[437202.032235] scsi 7:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[437202.047126] sd 7:0:0:0: [sdb] Attached SCSI disk
[437202.047222] sd 7:0:0:0: Attached scsi generic sg2 type 0
[437251.944530] FAT: unable to read boot sector
[154323.320484] RPC: Registered udp transport module.
[154323.320490] RPC: Registered tcp transport module.
[437651.011347] FAT: unable to read boot sector

```

[size=1]Never mind, I just forgot to plug in the power supply cord...[/size]

---

