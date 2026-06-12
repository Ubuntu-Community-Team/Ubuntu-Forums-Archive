---
title: "Intel HDA Problems (10.04)"
date: 2010-09-22
forum: Hardware
---

### Post by HistoryMac on 2010-09-22
Not much to say really. Just installed Lucid on a new laptop (Compaq CQ42-138TU) and it doesn't seem to be too fond of my Intel HDA chip. Sound monitor and settings suggest that all is well, but alas, I hear nothing.

HDA-Analyzer shows:
```

Card:       0
Id:         Intel
Driver:     HDA-Intel
Name:       HDA Intel
LongName:   HDA Intel at 0xd4500000 irq 22

```
Amusingly, ```
 ubuntu-bug audio 
``` crashes after attempting a sound check. So that's not of much use.

Any ideas?

---

### Post by HistoryMac on 2010-09-25
Updating to the absolute latest build of Alsamixer seemed to fix everything, so it may well work out of the box with 10.10.

---

