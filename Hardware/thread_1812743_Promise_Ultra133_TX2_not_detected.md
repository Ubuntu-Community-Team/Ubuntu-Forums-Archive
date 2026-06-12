---
title: "Promise Ultra133 TX2 not detected"
date: 2011-07-26
forum: Hardware
---

### Post by sonic_d on 2011-07-26
Hello,

I just recently switched from Debian to Ubuntu (11.04). Within Debian I used to config and build the kernel from source. Right now with Ubuntu it seems to be a bit different than I am used to with Debian

Within the machine that I am using I have a Promise Ultra133 TX2 with 3 IDE drives connected to it.
It seems when booting the machine all three IDE drives are detected, but when booting into Ubuntu none of them is detected.

After running 'dmesg' I do not even see the Promise Ultra133 TX2 controller being detected.

I have searched this and other forums but was unable to find a solution. Does anyone have any experience with this issue and able to give some tips/pointers? Thanks in advance.

---

### Post by sonic_d on 2011-07-27
After doing a 'lspci -vv' it seems that the controller is somehow installed, but the drives connected to it are not detected in some way. Please see below for the lspci -vv output
 
```

05:02.0 Mass storage controller: Promise Technology, Inc. 20269 (rev 02) (prog-if 85)
        Subsystem: Promise Technology, Inc. Ultra133TX2
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64 (1000ns min, 4500ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: I/O ports at dc00 [size=8]
        Region 1: I/O ports at d880 [size=4]
        Region 2: I/O ports at d800 [size=8]
        Region 3: I/O ports at d480 [size=4]
        Region 4: I/O ports at d400 [size=16]
        Region 5: Memory at febf8000 (32-bit, non-prefetchable) [size=16K]
        [virtual] Expansion ROM at 80808000 [disabled] [size=16K]
        Capabilities: [60] Power Management version 1
                Flags: PMEClk- DSI+ D1+ D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: pata_pdc2027x
        Kernel modules: pata_pdc2027x

```
 
 
Still not able to find any information on what might be the problem. Anyone?

---

