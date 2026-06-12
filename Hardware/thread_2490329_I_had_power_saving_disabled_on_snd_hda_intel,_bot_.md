---
title: "I had power saving disabled on snd_hda_intel, bot not it is acting like it is enabled"
date: 2023-08-30
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2023-08-30
From my [FONT=monospace][COLOR=#000000]/etc/modprobe.d/alsa-base.conf[/COLOR][/FONT] file
```

[FONT=monospace][COLOR=#000000]# https://bbs.archlinux.org/viewtopic.php?pid=1766206#p1766206 [/COLOR]
options snd_hda_intel power_save=0 
options snd_hda_intel power_save=0 power_save_controller=N[/FONT]

```
```
[FONT=monospace][COLOR=#000000]$ sudo lspci -s 29:00.4 -vvv [/COLOR]
29:00.4 Audio device: Advanced Micro Devices, Inc. [AMD] Starship/Matisse HD Audio Controller 
        Subsystem: Micro-Star International Co., Ltd. [MSI] Starship/Matisse HD Audio Controller 
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+ 
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 0, Cache Line Size: 64 bytes 
        Interrupt: pin D routed to IRQ 48 
        IOMMU group: 23 
        Region 0: Memory at fc800000 (32-bit, non-prefetchable) [size=32K] 
        Capabilities: [48] Vendor Specific Information: Len=08 <?> 
        Capabilities: [50] Power Management version 3 
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+) 
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME- 
        Capabilities: [64] Express (v2) Endpoint, MSI 00 
                DevCap: MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited 
                        ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset+ SlotPowerLimit 0.000W 
                DevCtl: CorrErr- NonFatalErr- FatalErr- UnsupReq- 
                        RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+ FLReset- 
                        MaxPayload 256 bytes, MaxReadReq 512 bytes 
                DevSta: CorrErr- NonFatalErr- FatalErr- UnsupReq- AuxPwr- TransPend- 
                LnkCap: Port #0, Speed 16GT/s, Width x16, ASPM L0s L1, Exit Latency L0s <64ns, L1 <1us 
                        ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp+ 
                LnkCtl: ASPM Disabled; RCB 64 bytes, Disabled- CommClk+ 
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt- 
                LnkSta: Speed 16GT/s (ok), Width x16 (ok) 
                        TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt- 
                DevCap2: Completion Timeout: Range ABCD, TimeoutDis+ NROPrPrP- LTR- 
                         10BitTagComp+ 10BitTagReq- OBFF Not Supported, ExtFmt- EETLPPrefix- 
                         EmergencyPowerReduction Not Supported, EmergencyPowerReductionInit- 
                         FRS- TPHComp+ ExtTPHComp- 
                         AtomicOpsCap: 32bit- 64bit- 128bitCAS- 
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- LTR- OBFF Disabled, 
                         AtomicOpsCtl: ReqEn- 
                LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete- EqualizationPhase1- 
                         EqualizationPhase2- EqualizationPhase3- LinkEqualizationRequest- 
                         Retimer- 2Retimers- CrosslinkRes: unsupported 
        Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+ 
                Address: 00000000fee00000  Data: 0000 
        Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?> 
        Capabilities: [150 v2] Advanced Error Reporting 
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol- 
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol- 
                UESvrt: DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol- 
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr- 
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr+ 
                AERCap: First Error Pointer: 00, ECRCGenCap- ECRCGenEn- ECRCChkCap- ECRCChkEn- 
                        MultHdrRecCap- MultHdrRecEn- TLPPfxPres- HdrLogCap- 
                HeaderLog: 00000000 00000000 00000000 00000000 
        Capabilities: [2a0 v1] Access Control Services 
                ACSCap: SrcValid- TransBlk- ReqRedir- CmpltRedir- UpstreamFwd- EgressCtrl- DirectTrans- 
                ACSCtl: SrcValid- TransBlk- ReqRedir- CmpltRedir- UpstreamFwd- EgressCtrl- DirectTrans- 
        Capabilities: [370 v1] Transaction Processing Hints 
                Device specific mode supported 
                Steering table in TPH capability structure 
        Kernel driver in use: snd_hda_intel 
        Kernel modules: snd_hda_intel
[/FONT]
```

```
[FONT=monospace][COLOR=#000000]$ uname -r && lsb_release -a [/COLOR]
5.19.0-46-generic 
No LSB modules are available. 
Distributor ID: Ubuntu 
Description:    Ubuntu 22.04.3 LTS 
Release:        22.04 
Codename:       jammy
[/FONT]
```

---

### Post by pqwoerituytrueiwoq on 2023-08-30
looks like it was changed to enabled? 
```
cat /sys/module/snd_hda_intel/parameters/power_save
1
```

In-spite of my config file last being edited since Nov 26  2021 (the install date the OS)

---

### Post by #&amp;thj^% on 2023-08-30
For myself I use this:
```
sudo tee /etc/modprobe.d/snd-hda-intel.conf <<< "options snd_hda_intel power_save=0"

```
A reboot is needed, and now:
```
cat /sys/module/snd_hda_intel/parameters/power_save
0

```
Good Luck

---

### Post by pqwoerituytrueiwoq on 2023-08-30
i know a reboot is required, i have been using these options for years now (since Nov 26  2021) and suddenly it was not working a as of a few days ago

```
$ uptime 
 23:28:49 up 56 days, 16:24, 10 users,  load average: 2.53, 2.37, 2.26
```

i just set to back to disabled ```
echo 0 | sudo tee /sys/module/snd_hda_intel/parameters/power_save
```

---

