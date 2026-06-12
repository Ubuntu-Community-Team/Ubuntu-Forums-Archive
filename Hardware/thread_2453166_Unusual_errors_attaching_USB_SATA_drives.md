---
title: "Unusual errors attaching USB SATA drives"
date: 2020-11-04
forum: Hardware
---

### Post by David_Partridge on 2020-11-04
```
Nov 04 13:35:41 charon udisksd[766]: Error probing device: Error sending ATA command IDENTIFY DEVICE to '/dev/sdc': Unexpected sense data returned:
                                     0000: 70 00 01 00  00 00 00 0a  00 00 00 00  00 1d 00 00    p...............
                                     0010: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00    ................
                                      (g-io-error-quark, 0)
Nov 04 13:35:41 charon udisksd[766]: Error probing device: Error sending ATA command IDENTIFY DEVICE to '/dev/sdd': Unexpected sense data returned:
                                     0000: 70 00 01 00  00 00 00 0a  00 00 00 00  00 1d 00 00    p...............
                                     0010: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00    ................
                                      (g-io-error-quark, 0)


```

Any ideas?

They're Seagate ST2000DM001 devices FWIW

---

### Post by CelticWarrior on 2020-11-04
The error has multiple causes and just says there was something wrong when communicating with the device. However, knowing they are 2TB Seagates, an hardware failure is more then likely.

---

### Post by David_Partridge on 2020-11-04
Yes I know they're not the most reliable, but in this case AFAICT they're working fine.

David

---

### Post by CelticWarrior on 2020-11-04
All hardware works fine until they don't.

---

