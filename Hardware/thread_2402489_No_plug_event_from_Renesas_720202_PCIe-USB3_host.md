---
title: "No plug event from Renesas 720202 PCIe-USB3 host"
date: 2018-09-30
forum: Hardware
---

### Post by dvallis on 2018-09-30
I'm working on a project that must use PCIe-USB3 cards with the Renesas 720202 host controller in a dual Xeon skylake server. Have tried both StarTech and Vantec cards to confirm it's not the hardware. They work in Windows. Card vendors say "It works under 16.04 for us". Both cards are recognized by lspci. (see below)

Problem is they absolutely do not recognize when a usb device is plugged in. lsusb shows no change. I can see the same devices when plugged into the Lewisburg PCH USB ports.

Behavior is identical under Ubuntu 16.04 kernel 4.4 and Ubuntu 18.04 kernel 4.15.0-34-generic-x86_64

I have tried the following fixes. None works.

```
iommu=off
iommu=soft
pci=nomsi
xhci_hcd.quirks=270336
usbcore.autosuspend=-1
```

I suspect the problem has to do with newness of the processor, [Intel Silver 4114]("https://ark.intel.com/products/123550/Intel-Xeon-Silver-4114-Processor-13_75M-Cache-2_20-GHz").

[SIZE=3]**Has anyone else found a solution? I found many threads but no definitive solution. REALLY need to solve this one.**[/SIZE]

Thanks in advance

```
lspci | grep -i usb
00:14.0 USB controller: Intel Corporation Lewisburg USB 3.0 xHCI Controller (rev 09)
1a:00.0 USB controller: Renesas Technology Corp. uPD720202 USB 3.0 Host Controller (rev 02)
1b:00.0 USB controller: Renesas Technology Corp. uPD720202 USB 3.0 Host Controller (rev 02)
1c:00.0 USB controller: Renesas Technology Corp. uPD720202 USB 3.0 Host Controller (rev 02)
1d:00.0 USB controller: Renesas Technology Corp. uPD720202 USB 3.0 Host Controller (rev 02)

sudo lspci -s 1a:00.0 -vvv
1a:00.0 USB controller: Renesas Technology Corp. uPD720202 USB 3.0 Host Controller (rev 02) (prog-if 30 [XHCI])
      Subsystem: Renesas Technology Corp. uPD720202 USB 3.0 Host Controller
      Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR+ FastB2B- DisINTx+
      Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
      Latency: 0, Cache Line Size: 64 bytes
      Interrupt: pin A routed to IRQ 44
      Region 0: Memory at aae00000 (64-bit, non-prefetchable) [size=8K]
      Capabilities: [50] Power Management version 3
            Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold-)
            Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
      Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
            Address: 0000000000000000  Data: 0000
      Capabilities: [90] MSI-X: Enable+ Count=8 Masked-
            Vector table: BAR=0 offset=00001000
            PBA: BAR=0 offset=00001080
      Capabilities: [a0] Express (v2) Endpoint, MSI 00
            DevCap:     MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
                  ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
            DevCtl:     Report errors: Correctable+ Non-Fatal+ Fatal+ Unsupported-
                  RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                  MaxPayload 128 bytes, MaxReadReq 512 bytes
            DevSta:     CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
            LnkCap:     Port #0, Speed 5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <4us, L1 unlimited
                  ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp-
            LnkCtl:     ASPM Disabled; RCB 64 bytes Disabled- CommClk+
                  ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
            LnkSta:     Speed 5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
            DevCap2: Completion Timeout: Not Supported, TimeoutDis+, LTR+, OBFF Not Supported
            DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
            LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
                   Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                   Compliance De-emphasis: -6dB
            LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
                   EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
      Capabilities: [100 v1] Advanced Error Reporting
            UESta:      DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
            UEMsk:      DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
            UESvrt:     DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
            CESta:      RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
            CEMsk:      RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
            AERCap:     First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
      Capabilities: [140 v1] Device Serial Number 13-00-00-00-92-43-14-08
      Capabilities: [150 v1] Latency Tolerance Reporting
            Max snoop latency: 0ns
            Max no snoop latency: 0ns
      Kernel driver in use: xhci_hcd
```

---

### Post by wildmanne39 on 2018-09-30
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by dvallis on 2018-09-30
Will do. Thx

---

