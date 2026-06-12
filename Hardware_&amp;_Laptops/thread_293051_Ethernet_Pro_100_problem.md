---
title: "Ethernet Pro 100 problem"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by trcha on 2006-11-04
Hello...

...I have a problem with integrated network adapter (Edgy Eft, 6.10). When I try:
ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device

In /etc/network/interfaces there is:
auto eth0
iface eth0 inet dhcp

and lspci -vv gives:

00:0a.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 05)
        Subsystem: Compaq Computer Corporation NC3161 Fast Ethernet NIC (embedded, WOL)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 66 (2000ns min, 14000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 9
        Region 0: Memory at 40200000 (32-bit, prefetchable) [size=4K]
        Region 1: I/O ports at 2000 [size=32]
        Region 2: Memory at 40100000 (32-bit, non-prefetchable) [size=1M]
        [virtual] Expansion ROM at 10000000 [disabled] [size=1M]
        Capabilities: [dc] Power Management version 1
                Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

Module e100 is also enabled:
lsmod | grep e100
e100                   38148  0
mii                     6912  3 8139cp,8139too,e100

Does anyone have idea what is wrong?

---

