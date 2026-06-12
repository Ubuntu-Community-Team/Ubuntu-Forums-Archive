---
title: "Serial card issues"
date: 2010-05-08
forum: Hardware
---

### Post by gizmobay on 2010-05-08
I added a serial card to my xubuntu system. It worked well for about a year and then I started having issues of it just quit working and then it's work. I figure I'd buy another one so I did. I can't seem to get it to work at all. Lspci sees the card but 9.10 isn't loading the serial module thus it won't work. Here's the output from lspci.

```
01:08.0 Communication controller: Device 5372:6872 (rev 01)
        Subsystem: LSI Logic / Symbios Logic Device 0002
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin A routed to IRQ 12
        Region 0: I/O ports at df00 [size=8]
        Region 1: I/O ports at de00 [size=8]
        Region 2: I/O ports at dd00 [size=8]
        Region 3: I/O ports at dc00 [size=8]
        Region 4: I/O ports at db00 [size=8]
        Region 5: I/O ports at da00 [size=16]

```

dmesg doesn't show anything about trying to load the serial kernel module.

Anyone have any ideas?

---

### Post by Lucas81 on 2013-04-14
[FONT=book antiqua]Hi, try the following:
1. sudo chmod 777 /dev/ttySx
2. sudo setserial /dev/ttySx uart 16550A
3. Check with    setserial -g /dev/ttyS*
     You should get something like 
[/FONT][FONT=book antiqua]/dev/ttySx, UART: 16550A, Port: 0xe800, IRQ: 22[/FONT]

It understand it should work, nevertheless, I get     /dev/ttySx: No such device       Still struggling with it...

---

### Post by Bucky Ball on 2013-04-14
[I][B]Thread Closed

Reason:[/B][/I] Necromancy.

This thread hasn't seen any action for nearly three years. Put to sleep. To improve your chances of help please post a new thread in the appropriate sub-forum. Thanks and good luck.

---

