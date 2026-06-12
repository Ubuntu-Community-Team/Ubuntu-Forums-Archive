---
title: "ACPI Error: Namespace lookup failure"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by aashay on 2008-03-21
I usually get sudden spikes of disk activity (about 1sec for ever 5 mins or so) which causes videos and songs to freeze for the period. This happens only while running on a battery. Everything works great on AC. So I was looking around and found this in dmesg. 
```

aashay@kriz-jr:~$ dmesg | tail
[   35.376000] Bluetooth: RFCOMM TTY layer initialized
[   35.376000] Bluetooth: RFCOMM ver 1.8
[  145.140000] ACPI Error (dswload-0774): [PBST] Namespace lookup failure, AE_ALREADY_EXISTS
[  145.140000] ACPI Exception (psloop-0225): AE_ALREADY_EXISTS, During name lookup/catalog [20070126]
[  145.140000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.LPCB.BAT1._BST] (Node df821780), AE_ALREADY_EXISTS
[  145.140000] ACPI: Marking method _BST as Serialized
[  145.140000] ACPI Exception (battery-0206): AE_ALREADY_EXISTS, Evaluating _BST [20070126]
[  145.204000] ACPI Error (psargs-0355): [PBST] Namespace lookup failure, AE_NOT_FOUND
[  145.204000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.LPCB.BAT1._BST] (Node df821780), AE_NOT_FOUND
[  145.204000] ACPI Exception (battery-0206): AE_NOT_FOUND, Evaluating _BST [20070126]

```
I tried googling aroud but found only a handful of results, none of which pointed to possible solutions.
The spike in disk activity is not accompanied by any log message, so I dont really know what is causing it. The ACPI error is the only thing I could connect to it.

---

### Post by aashay on 2008-04-05
Been a few weeks since I posted this. Thought i'd bump this once. The lag is really annoying when watching videos. 
Btw, its not just the videos. The entire system freezes with a huge spike in disk activity. Its just that I noticed it while watching vids

---

