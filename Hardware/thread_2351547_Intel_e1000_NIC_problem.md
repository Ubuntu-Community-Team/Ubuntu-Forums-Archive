---
title: "Intel e1000 NIC problem"
date: 2017-02-04
forum: Hardware
---

### Post by mojo2007 on 2017-02-04
Hi, I brought a new NIC due to old one failing. It works fine for first few minuites after boot / reboot, sometimes can last nearly 30 mins. Initially I thought maybe a samba problem. I did a clean install of ubuntu 16.04 server just the other day  suspecting it was a software config somewhere before I spotted the log  message.

Is this a driver issue or is it sign's of a faulty NIC?

Any suggestions or help welcome!

kern.log I have the following message:

```
Feb  4 16:44:37 pc5 kernel: [ 1780.241870] irq 16: nobody cared (try booting with the "irqpoll" option)
Feb  4 16:44:37 pc5 kernel: [ 1780.241875] CPU: 2 PID: 0 Comm: swapper/2 Not tainted 4.4.0-62-generic #83-Ubuntu
Feb  4 16:44:37 pc5 kernel: [ 1780.241876] Hardware name: ASUSTeK Computer INC. V-P8H67E/V-P8H67E, BIOS 3603 02/16/2012
Feb  4 16:44:37 pc5 kernel: [ 1780.241877]  0000000000000086 2fcc3a807514da60 ffff88021f303e60 ffffffff813f7c63
Feb  4 16:44:37 pc5 kernel: [ 1780.241879]  ffff8800d5c1b600 ffff8800d5c1b6d4 ffff88021f303e88 ffffffff810ddcb3
Feb  4 16:44:37 pc5 kernel: [ 1780.241881]  ffff8800d5c1b600 0000000000000000 0000000000000010 ffff88021f303ec0
Feb  4 16:44:37 pc5 kernel: [ 1780.241882] Call Trace:
Feb  4 16:44:37 pc5 kernel: [ 1780.241883]  <IRQ>  [<ffffffff813f7c63>] dump_stack+0x63/0x90
Feb  4 16:44:37 pc5 kernel: [ 1780.241891]  [<ffffffff810ddcb3>] __report_bad_irq+0x33/0xc0
Feb  4 16:44:37 pc5 kernel: [ 1780.241892]  [<ffffffff810de047>] note_interrupt+0x247/0x290
Feb  4 16:44:37 pc5 kernel: [ 1780.241894]  [<ffffffff810db1f7>] handle_irq_event_percpu+0x167/0x1d0
Feb  4 16:44:37 pc5 kernel: [ 1780.241896]  [<ffffffff810db29e>] handle_irq_event+0x3e/0x60
Feb  4 16:44:37 pc5 kernel: [ 1780.241897]  [<ffffffff810de5b9>] handle_fasteoi_irq+0x99/0x150
Feb  4 16:44:37 pc5 kernel: [ 1780.241900]  [<ffffffff8103119d>] handle_irq+0x1d/0x30
Feb  4 16:44:37 pc5 kernel: [ 1780.241902]  [<ffffffff8183afdb>] do_IRQ+0x4b/0xd0
Feb  4 16:44:37 pc5 kernel: [ 1780.241905]  [<ffffffff818390c2>] common_interrupt+0x82/0x82
Feb  4 16:44:37 pc5 kernel: [ 1780.241906]  <EOI>  [<ffffffff816cb5ce>] ? cpuidle_enter_state+0x10e/0x2b0
Feb  4 16:44:37 pc5 kernel: [ 1780.241911]  [<ffffffff816cb7a7>] cpuidle_enter+0x17/0x20
Feb  4 16:44:37 pc5 kernel: [ 1780.241914]  [<ffffffff810c4522>] call_cpuidle+0x32/0x60
Feb  4 16:44:37 pc5 kernel: [ 1780.241916]  [<ffffffff816cb783>] ? cpuidle_select+0x13/0x20
Feb  4 16:44:37 pc5 kernel: [ 1780.241918]  [<ffffffff810c47e0>] cpu_startup_entry+0x290/0x350
Feb  4 16:44:37 pc5 kernel: [ 1780.241920]  [<ffffffff81051784>] start_secondary+0x154/0x190
Feb  4 16:44:37 pc5 kernel: [ 1780.241921] handlers:
Feb  4 16:44:37 pc5 kernel: [ 1780.241926] [<ffffffffc005a480>] e1000_intr [e1000]
Feb  4 16:44:37 pc5 kernel: [ 1780.241927] Disabling IRQ #16
```

Soon as this occurs the network speed on that interface becomes terrible, IRQ #16 relates to my new Intel NIC which is as follows:

lshw:
```
description: Ethernet interface
       product: 82546EB Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: enp6s1
       version: 01
       serial: 00:11:0a:85:15:00
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full ip=192.168.2.4 latency=32 link=yes mingnt=255 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:f7c80000-f7c9ffff memory:f7c40000-f7c7ffff ioport:d000(size=64) memory:f7c00000-f7c3ffff
```

ethtool:
```
Settings for enp6s1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: on (auto)
        Supports Wake-on: umbg
        Wake-on: d
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes
```

---

### Post by pqwoerituytrueiwoq on 2017-02-04
does it happen on a live session of 14.04?

it looks like your lan is a 100bit connection, is that correct?

I did find this which references your card (not sure if this is helpful at all)
[http://manpages.ubuntu.com/manpages/trusty/man4/em.4freebsd.html](http://manpages.ubuntu.com/manpages/trusty/man4/em.4freebsd.html)

i think i have had a issue like this before i think it was with a wifi card i think i added some driver options in /etc/modules
maybe it was on a old kernel with my raspberry pi model b, both maybe? at one point i had it just restart the networking service when it stopped working
i think one time i had a issue caused by the card not being fully seated in the slot


i have a similar card, cause i wanted WOL support which does not work on my onboard chip (still on 14.04)
ethtool:
```
Settings for eth3:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: on (auto)
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: yes
```
lshw
```
  *-network               
       description: Ethernet interface
       product: 82572EI Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth3
       version: 06
       serial: [snip mac address]
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=5.6-8 ip=10.0.0.50 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:29 memory:ef140000-ef15ffff memory:ef120000-ef13ffff ioport:d000(size=32) memory:ef100000-ef11ffff

```
lspci
```
05:00.0 Ethernet controller: Intel Corporation 82572EI Gigabit Ethernet Controller (Copper) (rev 06)
    Subsystem: Intel Corporation PRO/1000 PT Server Adapter
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 29
    Region 0: Memory at ef140000 (32-bit, non-prefetchable) [size=128K]
    Region 1: Memory at ef120000 (32-bit, non-prefetchable) [size=128K]
    Region 2: I/O ports at d000 [size=32]
    Expansion ROM at ef100000 [disabled] [size=128K]
    Capabilities: [c8] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee0f00c  Data: 41b4
    Capabilities: [e0] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
        DevCtl:    Report errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <4us, L1 <64us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        AERCap:    First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
    Capabilities: [140 v1] Device Serial Number [sniped mac address]
    Kernel driver in use: e1000e
```

---

### Post by mojo2007 on 2017-02-05
Thanks for reply, I'm running the nic into a wireless router. I have swapped the card to different port, so hope it's seated properly but same problem. Just occurred to me I've not tried a different cable. Failing that I will try some earlier distro's and that driver to see if anything will work. Otherwise I think it's a new card, not intel based :)

---

### Post by mojo2007 on 2017-02-07
I can't find a fix for this, I just assume card is failing. It's working at 10mb speed so I swapped it to feed my internet router which will never do more than 8mb and will buy a new one when it finally fails. The onboard NIC is working at full speed no problems with that, so all happy... for now :/

---

