---
title: "Acer Travelmate C102Ti: This is not a laptop"
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by MadeR on 2007-07-24
I own two laptops, both Acer travelmates:
one is a C102Ti, the other one is a C204TMi.
The C102Ti, source of my problems, is upgraded with the latest official bios.
I installed Kubuntu Feisty Fawn on both.

The symptom:
while the C204TMi correctly shows the Power Manager icon in system tray, the C102Ti does not.
So I tried launching it by hand from konsole:
```
mader@aurin:/proc$ X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
[b]No battery found.
This is not a laptop, quitting ...[/b]

```

why does it happen?
is battery so damaged that bios does not recognize it?

---

### Post by domino1241 on 2008-01-13
bumpity bump bump

Feisty, Kubuntu, IBM Thinkpad T20, same error

---

### Post by priegog on 2008-02-18
For both of you (but specially you, author, I'm looking into buying a used TravelMate C102TI.
Can you confirm the problem has been solved in gutsy or hardy? Thanks a lot

---

