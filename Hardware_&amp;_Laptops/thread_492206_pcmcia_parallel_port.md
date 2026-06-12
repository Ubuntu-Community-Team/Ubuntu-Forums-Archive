---
title: "pcmcia parallel port"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by dothemango on 2007-07-04
hello

I'm using a pcmcia card to realize a parallel port on my notebook. The card is based on a 
 "Oxford Semiconductor Ltd VScom 011H-EP1" chip

```

03:00.0 Parallel controller: Oxford Semiconductor Ltd VScom 011H-EP1 1 port parallel adaptor (prog-if 03 [IEEE1284])
        Subsystem: Oxford Semiconductor Ltd Unknown device 0000
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 17
        Region 0: I/O ports at 1420 [size=8]
        Region 1: I/O ports at 1428 [size=4]
        Region 2: I/O ports at 1400 [size=32]
        Region 3: Memory at 54000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 1
                Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0+,D1-,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

root@hermine:~# 


```
 
My problem is that the driver sets the io-address space to  0x1420-0x1422

```

root@hermine:~# cat /proc/ioports |grep parport
    1420-1422 : parport0
root@hermine:~# 

```

Most of the software does not expect the io-ports at this addresses. I wanted to ask if there is a possibility to change the io-addresses (driver parameter etc..)


mango

---

### Post by hotairmgt on 2007-08-09
lucky you - i got the same card, downloaded ubuntu from linuxcnc.org and all i get is:

0000:07:00.0 Parallel controller: Oxford Semiconductor Ltd VScom 011H-EP1 1 port parallel adaptor (prog-if 03 [IEEE1284])
        Subsystem: Oxford Semiconductor Ltd: Unknown device 0000
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 10
        Region 0: I/O ports at 4020 [disabled] [size=8]
        Region 1: I/O ports at 4028 [disabled] [size=4]
        Region 2: I/O ports at 4000 [disabled] [size=32]
        Region 3: Memory at 6c000000 (32-bit, non-prefetchable) [disabled] [size=4K]
        Capabilities: [40] Power Management version 1
                Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0+,D1-,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

why are the ports disabled???? any idea????

---

### Post by dothemango on 2007-08-11
hmm that's a good question.
In my case the card worked out of the box. I also used the card under windows (there you have the same problem  with the ports).  but may be the driver under windows activates your io-ports.

---

### Post by hvymtlsteve on 2008-02-14
> **hotairmgt said:**
> lucky you - i got the same card, downloaded ubuntu from linuxcnc.org and all i get is:

0000:07:00.0 Parallel controller: Oxford Semiconductor Ltd VScom 011H-EP1 1 port parallel adaptor (prog-if 03 [IEEE1284])
        Subsystem: Oxford Semiconductor Ltd: Unknown device 0000
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 10
        Region 0: I/O ports at 4020 [disabled] [size=8]
        Region 1: I/O ports at 4028 [disabled] [size=4]
        Region 2: I/O ports at 4000 [disabled] [size=32]
        Region 3: Memory at 6c000000 (32-bit, non-prefetchable) [disabled] [size=4K]
        Capabilities: [40] Power Management version 1
                Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0+,D1-,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

why are the ports disabled???? any idea????

Are you still having this issue?
I know the thread is a bit old but I just plugged an expresscard version of this into my lappy and it worked out of the box. 
Maybe you need to modprobe it?

As for the driver address... I haven't had any such issue because the software looks for /dev/parport0 instead of an address... Would be nice if your software had a configuration file where it got the address to look for, then you wouldn't have to try to assign an address to the hardware through its driver.

---

