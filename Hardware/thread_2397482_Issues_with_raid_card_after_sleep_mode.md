---
title: "Issues with raid card after sleep mode"
date: 2018-07-30
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2018-07-30
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic
Kernel:   4.15.0-29-generic

```
*No raid configuration is in use 
I picked up a raid card cause i was trying to rule out (or bypass if need be) a issue with my onboard controller (like bad wires, bad ports, or maybe the entire controller)
```
05:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9230 PCIe SATA 6Gb/s Controller (rev 11) (prog-if 01 [AHCI 1.0])
    Subsystem: Marvell Technology Group Ltd. 88SE9230 PCIe SATA 6Gb/s Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 28
    Region 0: I/O ports at d050 [size=8]
    Region 1: I/O ports at d040 [size=4]
    Region 2: I/O ports at d030 [size=8]
    Region 3: I/O ports at d020 [size=4]
    Region 4: I/O ports at d000 [size=32]
    Region 5: Memory at ef240000 (32-bit, non-prefetchable) [size=2K]
    Expansion ROM at ef200000 [disabled] [size=256K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Address: fee01004  Data: 4022
    Capabilities: [70] Express (v2) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 512 bytes, PhantFunc 0, Latency L0s <1us, L1 <8us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 5GT/s, Width x2, ASPM L0s L1, Exit Latency L0s <512ns, L1 <64us
            ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s, Width x2, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis+, LTR-, OBFF Not Supported
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
        LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [e0] SATA HBA v0.0 BAR4 Offset=00000004
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
    Kernel driver in use: ahci
    Kernel modules: ahci

```
Product page: [http://www.sybausa.com/index.php?route=product/product&product_id=183](http://www.sybausa.com/index.php?route=product/product&product_id=183)
when i wake from sleep mode the system hangs up and eventually unlocks in read only mode
dmesg output: [https://pastebin.com/VYnCXm0c](https://pastebin.com/VYnCXm0c)
```
[  351.631187] PM: suspend entry (deep)
[  351.631188] PM: Syncing filesystems ... done.
[  352.368897] Freezing user space processes ... (elapsed 1.283 seconds) done.
[  353.652435] OOM killer disabled.
[  353.652436] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[  353.653884] Suspending console(s) (use no_console_suspend to debug)
[  353.658032] serial 00:06: disabled
[  353.660311] e1000e: EEE TX LPI TIMER: 00000000
[  353.675973] sd 1:0:0:0: [sda] Synchronizing SCSI cache
[  353.676006] sd 6:0:0:0: [sdc] Synchronizing SCSI cache
[  353.676048] sd 2:0:0:0: [sdb] Synchronizing SCSI cache
[  353.676060] sd 1:0:0:0: [sda] Stopping disk
[  353.676177] sd 2:0:0:0: [sdb] Stopping disk
[  353.677411] sd 6:0:0:0: [sdc] Stopping disk
[  354.522513] ACPI: Preparing to enter system sleep state S3
[  354.936167] PM: Saving platform NVS memory
[  354.936182] Disabling non-boot CPUs ...
[  354.952248] IRQ 16: no longer affine to CPU1
[  354.952252] IRQ 33: no longer affine to CPU1
[  354.953269] smpboot: CPU 1 is now offline
[  354.976319] IRQ 24: no longer affine to CPU2
[  354.977351] smpboot: CPU 2 is now offline
[  354.997477] smpboot: CPU 3 is now offline
[  354.999326] ACPI: Low-level resume complete
[  354.999372] PM: Restoring platform NVS memory
[  354.999676] Enabling non-boot CPUs ...
[  354.999705] x86: Booting SMP configuration:
[  354.999706] smpboot: Booting Node 0 Processor 1 APIC 0x2
[  355.000045]  cache: parent cpu1 should not be sleeping
[  355.000169] CPU1 is up
[  355.000188] smpboot: Booting Node 0 Processor 2 APIC 0x4
[  355.000522]  cache: parent cpu2 should not be sleeping
[  355.000655] CPU2 is up
[  355.000672] smpboot: Booting Node 0 Processor 3 APIC 0x6
[  355.001009]  cache: parent cpu3 should not be sleeping
[  355.001154] CPU3 is up
[  355.003641] ACPI: Waking up from system sleep state S3
[  355.009756] snd_hda_intel 0000:01:00.1: spurious response 0x40:0x0, last cmd=0x5f0900
[  355.009761] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f0900
[  355.009765] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f0900
[  355.009769] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f0900
[  355.009773] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f0900
[  355.009777] snd_hda_intel 0000:01:00.1: spurious response 0x1:0x0, last cmd=0x5f0900
[  355.009781] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f0900
[  355.009784] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f0900
[  355.009788] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f0900
[  355.009792] snd_hda_intel 0000:01:00.1: spurious response 0x0:0x0, last cmd=0x5f0900
[  355.043199] rtc_cmos 00:02: Alarms can be up to one month in the future
[  355.044632] serial 00:06: activated
[  355.055901] sd 1:0:0:0: [sda] Starting disk
[  355.055936] sd 2:0:0:0: [sdb] Starting disk
[  355.172029] e1000e 0000:06:00.0 enp6s0: MAC Wakeup cause - Magic Packet
[  355.221863] ACPI Error: [D1F0] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[  355.221874] No Local Variables are initialized for Method [_L09]
[  355.221877] No Arguments are initialized for method [_L09]
[  355.221879] ACPI Error: Method parse/execution failed \_GPE._L09, AE_NOT_FOUND (20170831/psparse-550)
[  355.221890] ACPI Exception: AE_NOT_FOUND, while evaluating GPE method [_L09] (20170831/evgpe-646)
[  356.041787] ahci 0000:05:00.0: controller reset failed (0x80000001)
[  356.041801] dpm_run_callback(): pci_pm_resume+0x0/0xb0 returns -5
[  356.041828] PM: Device 0000:05:00.0 failed to resume async: error -5
[  356.041921] sd 6:0:0:0: [sdc] Starting disk
[  356.073743] OOM killer enabled.
[  356.073743] Restarting tasks ... 
[  356.073905] pci_bus 0000:04: Allocating resources
[  356.073918] pci 0000:03:00.0: bridge window [io  0x1000-0x0fff] to [bus 04] add_size 1000
[  356.073920] pci 0000:03:00.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000 add_align 100000
[  356.073921] pci 0000:03:00.0: bridge window [mem 0x00100000-0x000fffff] to [bus 04] add_size 200000 add_align 100000
[  356.073926] pci 0000:03:00.0: BAR 14: assigned [mem 0xea000000-0xea1fffff]
[  356.073930] pci 0000:03:00.0: BAR 15: assigned [mem 0xea200000-0xea3fffff 64bit pref]
[  356.073933] pci 0000:03:00.0: BAR 13: assigned [io  0x2000-0x2fff]
[  356.073934] pci 0000:03:00.0: PCI bridge to [bus 04]
[  356.073936] pci 0000:03:00.0:   bridge window [io  0x2000-0x2fff]
[  356.073942] pci 0000:03:00.0:   bridge window [mem 0xea000000-0xea1fffff]
[  356.073946] pci 0000:03:00.0:   bridge window [mem 0xea200000-0xea3fffff 64bit pref]
[  356.074690] done.
[  356.074722] PM: suspend exit
[  356.121756] snd_hda_codec_hdmi hdaudioC2D0: HDMI: invalid ELD data byte 77
[  357.130826] e1000e: enp6s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[  358.453819] ata8: SATA link down (SStatus 0 SControl 310)
[  358.457837] ata9: SATA link down (SStatus 0 SControl 310)
[  358.457870] ata5: SATA link down (SStatus 0 SControl 310)
[  358.465814] ata6: SATA link down (SStatus 0 SControl 310)
[  358.465846] ata11: SATA link down (SStatus 0 SControl 310)
[  358.469831] ata10: SATA link down (SStatus 0 SControl 310)
[  358.469864] ata12: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  358.469896] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  358.969802] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  359.075177] ata2.00: configured for UDMA/133
[  360.417826] ata3: link is slow to respond, please be patient (ready=0)
[  361.797794] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  362.347214] ata3.00: configured for UDMA/133
[  363.493826] ata7.00: qc timeout (cmd 0xec)
[  363.494927] ata7.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  363.494930] ata7.00: revalidation failed (errno=-5)
[  363.497833] ata12.00: qc timeout (cmd 0xa1)
[  363.501133] ata12.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  363.501136] ata12.00: revalidation failed (errno=-5)
[  363.808854] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  363.816775] ata12: SATA link up 1.5 Gbps (SStatus 113 SControl 300)

```

*no freeze up if my drives are not on the controller
any drive connected to the controller is not accessible after waking from sleep mode

---

