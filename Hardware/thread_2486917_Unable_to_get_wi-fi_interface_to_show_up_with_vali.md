---
title: "Unable to get wi-fi interface to show up with valid drivers installed"
date: 2023-05-16
forum: Hardware
---

### Post by veleek on 2023-05-16
I have an HP T620 that I have freshly install Lubuntu 23.04 onto. I have found the device in “Additional Drivers” and downloaded the drivers successfully. I have rebooted a number of times but the wireless device never shows up.  I have also tried the same steps with Ubuntu and I get the same problem, so I don't believe it's Lubuntu related.  


I installed net-tools and ran ifconfig wlan0 and I get wlan0: error fetching interface information: Device not found. As far as I can tell the device is available, with a driver, but I’m missing a step here somewhere to get it to show up as a regular device and allow me to select a WiFi network.

I dug around as much as I can, and it seems like most of the existing issues with this device (BCM4253) are related to not being able to install the drivers properly, and AFAICT the drivers are installed and loaded properly.  

system-info: [https://paste.ubuntu.com/p/qT2jj7brWq/](https://paste.ubuntu.com/p/qT2jj7brWq/)


[COLOR=#203243][FONT=Arial] sudo lshw -C network
[/FONT][/COLOR]
```
 *-network
       description: Network controller
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:28 memory:fe800000-fe807fff memory:fe600000-fe7fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 0c
       serial: 7c:d3:0a:1e:69:a4
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=6.2.0-20-generic duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.1.20 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:35 ioport:e000(size=256) memory:fe900000-fe900fff memory:d0800000-d0803fff
```

[COLOR=#203243][FONT=Arial]sudo lspci -s 01:00.0 -vv

[/FONT][/COLOR]```
01:00.0 Network controller: Broadcom Inc. and subsidiaries BCM4352 802.11ac Wireless Network Adapter (rev 03)
        Subsystem: Hewlett-Packard Company BCM4352 802.11ac Wireless Network Adapter
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 28
        Region 0: Memory at fe800000 (64-bit, non-prefetchable) [size=32K]
        Region 2: Memory at fe600000 (64-bit, non-prefetchable) [size=2M]
        Capabilities: [48] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=2 PME-
        Capabilities: [58] MSI: Enable- Count=1/1 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Capabilities: [68] Vendor Specific Information: Len=44 <?>
        Capabilities: [ac] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset- SlotPowerLimit 0W
                DevCtl: CorrErr+ NonFatalErr+ FatalErr+ UnsupReq+
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr+ NoSnoop+
                        MaxPayload 256 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr+ NonFatalErr- FatalErr- UnsupReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <2us, L1 <32us
                        ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp+
                LnkCtl: ASPM Disabled; RCB 64 bytes, Disabled- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1
                        TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Range ABCD, TimeoutDis+ NROPrPrP- LTR+
                         10BitTagComp- 10BitTagReq- OBFF Via WAKE#, ExtFmt- EETLPPrefix-
                         EmergencyPowerReduction Not Supported, EmergencyPowerReductionInit-
                         FRS- TPHComp- ExtTPHComp-
                         AtomicOpsCap: 32bit- 64bit- 128bitCAS-
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- LTR- 10BitTagReq- OBFF Disabled,
                         AtomicOpsCtl: ReqEn-
                LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance Preset/De-emphasis: -6dB de-emphasis, 0dB preshoot
                LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete- EqualizationPhase1-
                         EqualizationPhase2- EqualizationPhase3- LinkEqualizationRequest-
                         Retimer- 2Retimers- CrosslinkRes: unsupported
        Capabilities: [100 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr-
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr+
                AERCap: First Error Pointer: 00, ECRCGenCap+ ECRCGenEn- ECRCChkCap+ ECRCChkEn-
                        MultHdrRecCap- MultHdrRecEn- TLPPfxPres- HdrLogCap-
                HeaderLog: 00000000 00000000 00000000 00000000
        Capabilities: [13c v1] Device Serial Number 74-c6-00-ff-ff-00-00-01
        Capabilities: [150 v1] Power Budgeting <?>
        Capabilities: [160 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=01
                        Status: NegoPending- InProgress-
        Capabilities: [1b0 v1] Latency Tolerance Reporting
                Max snoop latency: 0ns
                Max no snoop latency: 0ns
        Capabilities: [220 v1] Physical Resizable BAR
                BAR 2: current size: 2MB, supported: 1MB 2MB
        Kernel driver in use: bcma-pci-bridge
        Kernel modules: bcma, wl

```

---

### Post by veleek on 2023-05-17
I'm still digging for info here, as an example there this helpful thread: [[SOLVED] How to install a driver for the Broadcom series of PCI wireless cards (ubuntuforums.org)]("https://ubuntuforums.org/showthread.php?t=2214110"), but it still just points me towards which driver to download.  

The pci.id for my card is [14e4:43b1] (rev 03) which indicates that it _should_ just be the bcmw_kernel_source driver which is the one that I have installed, but still no luck.

---

### Post by veleek on 2023-05-17
Admins: I determined that this is not the appropriate form, I have created a new thread in the correct forum here:  [https://ubuntuforums.org/showthread.php?t=2486962](https://ubuntuforums.org/showthread.php?t=2486962)
This thread can probably just be deleted.

---

