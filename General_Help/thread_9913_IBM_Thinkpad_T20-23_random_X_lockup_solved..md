---
title: "IBM Thinkpad T20-23 random X lockup solved."
date: 2005-01-02
forum: General Help
---

### Post by JLB on 2005-01-02
May apply to other laptop models. See lspci output snippet below. 

I was having random lockups with X in Ubuntu Warty and Hoary. Problem usually manifested itself when scrolling within an app such as firefox.

Turns out a small change to the xorg.conf file (XF86Config file in warty) solved this issue. This applies to the following S3 Inc. 86C270-294 Savage/IX-MV video card commonly found on older IBM thinkpads such as the T-20-23 series. 

lspci -vv output snippet :

```
0000:01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13) (prog-if 00 [VGA])
        Subsystem: IBM ThinkPad T20
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (1000ns min, 63750ns max), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at f0000000 (32-bit, non-prefetchable) [size=128M]
        Capabilities: <available only to root>
``` 

Make the following change to your xorg.conf config file:

```
Section "Device"
        Identifier      "S3 Inc. 86C270-294 Savage/IX-MV"
        Driver          "savage"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
        **Option "ShadowStatus"   "on"** ### <----- added to solve lockup in X problem
EndSection
```

Hope this helps someone out :) 
Regards!
JL

---

