---
title: "Is there a CLI GPU Stress test"
date: 2020-04-01
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2020-04-01
I am looking for a way to put the gpu under load without having lighdm running cause what i want to try requires having the gpu under load and lightdm closed, well technically you can do it with it open, but it is gonna crash the entire system and reboot

---

### Post by CatKiller on 2020-04-01
[https://foldingathome.org/](https://foldingathome.org/)

---

### Post by pqwoerituytrueiwoq on 2020-04-01
It does not seem to detect my GPU
My cards vendor ID is 5249 (sub vendor is 1458) and the device id is 1002 (according to my cards vBIOS)
```

~$ cat /sys/class/drm/card0/device/{device,vendor,revision,vbios_version}
0x67df
0x1002
0xe7
xxx-xxx-xxx
~$ cat ./GPUs.txt |grep Ellesmere
0x1002:0x67c0:1:5:Ellesmere PRO [Radeon RX 470]
0x1002:0x67c7:1:5:Ellesmere Pro [Radeon Pro WX 5100] 122
0x1002:0x67df:1:5:Ellesmere XT [Radeon RX 470/480/570/580/590]

``````

27:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X] (rev e7) (prog-if 00 [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd Ellesmere [Radeon RX 470/480/570/580]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 80
    Region 0: Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Region 2: Memory at f0000000 (64-bit, prefetchable) [size=2M]
    Region 4: I/O ports at e000 [size=256]
    Region 5: Memory at fce00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 256 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 8GT/s, Width x16, ASPM L1, Exit Latency L0s <64ns, L1 <1us
            ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp+
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 8GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis-, LTR+, OBFF Not Supported
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR+, OBFF Disabled
        LnkCtl2: Target Link Speed: 8GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete+, EqualizationPhase1+
             EqualizationPhase2+, EqualizationPhase3+, LinkEqualizationRequest-
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee00000  Data: 0000
    Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150 v2] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [200 v1] #15
    Capabilities: [270 v1] #19
    Capabilities: [2b0 v1] Address Translation Service (ATS)
        ATSCap:    Invalidate Queue Depth: 00
        ATSCtl:    Enable+, Smallest Translation Unit: 00
    Capabilities: [2c0 v1] Page Request Interface (PRI)
        PRICtl: Enable- Reset-
        PRISta: RF- UPRGI- Stopped+
        Page Request Capacity: 00000020, Page Request Allocation: 00000000
    Capabilities: [2d0 v1] Process Address Space ID (PASID)
        PASIDCap: Exec+ Priv+, Max PASID Width: 10
        PASIDCtl: Enable- Exec- Priv-
    Capabilities: [320 v1] Latency Tolerance Reporting
        Max snoop latency: 1048576ns
        Max no snoop latency: 1048576ns
    Capabilities: [328 v1] Alternative Routing-ID Interpretation (ARI)
        ARICap:    MFVC- ACS-, Next Function: 1
        ARICtl:    MFVC- ACS-, Function Group: 0
    Capabilities: [370 v1] L1 PM Substates
        L1SubCap: PCI-PM_L1.2+ PCI-PM_L1.1+ ASPM_L1.2+ ASPM_L1.1+ L1_PM_Substates+
              PortCommonModeRestoreTime=0us PortTPowerOnTime=170us
        L1SubCtl1: PCI-PM_L1.2- PCI-PM_L1.1- ASPM_L1.2- ASPM_L1.1-
               T_CommonMode=0us LTR1.2_Threshold=0ns
        L1SubCtl2: T_PwrOn=10us
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu

```
edit i think i got that fixed, but there is the issue i expected, there are no work units to get...
```

01:21:50:WARNING:WU01:FS01:Failed to get assignment from '65.254.110.245:8080': No WUs available for this configuration
01:21:50:WU01:FS01:Connecting to 18.218.241.186:80
01:21:51:WARNING:WU01:FS01:Failed to get assignment from '18.218.241.186:80': No WUs available for this configuration
01:21:51:ERROR:WU01:FS01:Exception: Could not get an assignment
01:21:51:WU01:FS01:Connecting to 65.254.110.245:8080
01:21:52:WU00:FS00:0xa7:Completed 160000 out of 500000 steps (32%)
01:21:52:WARNING:WU01:FS01:Failed to get assignment from '65.254.110.245:8080': No WUs available for this configuration
01:21:52:WU01:FS01:Connecting to 18.218.241.186:80
01:21:53:WARNING:WU01:FS01:Failed to get assignment from '18.218.241.186:80': No WUs available for this configuration
01:21:53:ERROR:WU01:FS01:Exception: Could not get an assignment
01:22:23:WU00:FS00:0xa7:Completed 165000 out of 500000 steps (33%)
01:22:52:WU01:FS01:Connecting to 65.254.110.245:8080
01:22:52:WARNING:WU01:FS01:Failed to get assignment from '65.254.110.245:8080': No WUs available for this configuration
01:22:52:WU01:FS01:Connecting to 18.218.241.186:80
01:22:52:WARNING:WU01:FS01:Failed to get assignment from '18.218.241.186:80': No WUs available for this configuration
01:22:52:ERROR:WU01:FS01:Exception: Could not get an assignment


```

---

### Post by QIII on 2020-04-01
F@H does not apparently work with AMD GPUs right now.  They say this is because AMD drivers do not support OpenCL well.  I think that's balderdash and a cop out.  I think it's simply that they don't have the time and resources to maintain two code bases after developing for AMDGPU.  And that is a legitimate reason.

Because of that, you won't receive any GPU work units.  So you can't really stress your GPS with Folding.  However, along that line, you might see if there is a BOINC project designed for AMD GPUs.

---

### Post by CatKiller on 2020-04-01
> **pqwoerituytrueiwoq said:**
> 
edit i think i got that fixed, but there is the issue i expected, there are no work units to get...
They do show up after a while: they've had a massive increase in users since they started doing corona virus stuff, so there are sometimes delays in getting work units out to people. 

You also need to extract at least something from the proprietary AMD driver to be able to do OpenCL things, as I understand it. I don't know the details, though, since all my GPUs are either Nvidia or Intel. 

As an alternative, the phoronix test suite can run a bunch of benchmarking loads on your GPU without needing a screen to draw to. That should give you the workload that you're after.

---

