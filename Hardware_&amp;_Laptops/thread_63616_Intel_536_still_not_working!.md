---
title: "Intel 536 still not working!"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by tariqf on 2005-09-08
Hi I've spent 2 days trying to get this modem working in hoary, I've been over and over the Intel 536 modem setup wiki and also tried the sl-modem drivers. In each case the module loads fine but I cannot see my modem with wvdial. Please please can someone help? 

lspci -vv:-
0000:02:02.0 Communication controller: Intel Corp. 536EP Data Fax Modem
        Subsystem: Intel Corp.: Unknown device 1000
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 0x10 (64 bytes)
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at fcc00000 (32-bit, non-prefetchable) [size=4M]
        Capabilities: [e0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2+ AuxCurrent=375mA PME(D0-,D1-,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

lsmod shows Intel536 and slamr loaded depending on which one I try to use. I create a sym link to /dev/536ep0 to /dev/modem and try vwdial but is says my modem is not responding. I have pci=routeirq ino my /boot/grub/menu.lst as 

/boot/vmlinuz-2.6.10-5-386 root=/dev/hdc1 pci=routeirq ro quiet splash


Any ideas anyone?

---

