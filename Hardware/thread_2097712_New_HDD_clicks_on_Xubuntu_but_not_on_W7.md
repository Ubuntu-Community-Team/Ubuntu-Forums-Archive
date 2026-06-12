---
title: "New HDD clicks on Xubuntu but not on W7?"
date: 2012-12-24
forum: Hardware
---

### Post by Merrattic on 2012-12-24
Dell Precision M6500. Just swapped out the 64gb SSD for a 256gb SSD and the 250gb HDD for a 750gb HDD. Dual booting Windows 7 and Xubuntu 12.04. Cloned W7 with Clonezilla on the SSD, then installed Xubuntu as dual boot. The HDD is mostly used for files storage, a few Windows 7 programs also installed on there. Xubuntu full installed on the SSD. Trim settings done for the SSD.

Under Windows 7 everything is fine, under Xubuntu I get a click from the HDD every few minutes (I am assuming it is the HDD clicking and not the SSD!). Have tried an hdparm setting but this doesn't seem to make any difference:
```
sudo hdparm -B 254 /dev/sdb
```Any other ideas?

---

