---
title: "Wireless Card and ndiswrapper"
date: 2010-03-23
forum: Hardware
---

### Post by amaress on 2010-03-23
Hey!

I've had Ubuntu for all of 3 hours and am TOTALLY lost...

I have a Gateway M-6752, and it has a Marvell wireless card, but I'm not sure which kinda.  I've seen in topics on here where people with Marvell cards have used ndiswrapper but I can't find any Marvell cards listed in the Maybe Working driver section let alone the working one.

I downloaded the driver from Gateway to see if I could get it to work, but it wont open the Setup.exe so I can't get the .sys files and such.

Help?

Thanks so much!;)

---

### Post by Fafler on 2010-03-23
Maybe you have a Windows machine nearby, where you could extract the files? Or you could try opening setup.exe with wine, but that might be a bit much for someone who has one used Ubuntu for 3 hours.

---

### Post by mandyb on 2010-03-23
find out what the wireless card is, post that and someone will be able to help.

get a terminal window, type

lspci -nnvv | grep 802.11

---

### Post by amaress on 2010-03-23
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:2a08] (rev 03)
    Subsystem: Marvell Technology Group Ltd. Device [11ab:2a08]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 10
    Region 0: Memory at f2000000 (32-bit, non-prefetchable) [size=64K]
    Region 1: Memory at f1000000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

That's what it comes up with when I just type lspci -nnvv, the | grep 802.11 part makes it return nothing, though...

Thanks!

---

### Post by mandyb on 2010-03-27
[http://ubuntuforums.org/archive/index.php/t-575785.html](http://ubuntuforums.org/archive/index.php/t-575785.html)

here is an old thread but same card, success using ndiswrapper.  Hope it helps.  If no luck and no one knowledgeable is responding try starting a new thread with "Marvel wireless-N" in the subject line..

---

