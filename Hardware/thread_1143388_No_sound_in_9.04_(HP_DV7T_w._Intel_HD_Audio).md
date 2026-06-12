---
title: "No sound in 9.04 (HP DV7T w. Intel HD Audio)"
date: 2009-04-29
forum: Hardware
---

### Post by MadJester on 2009-04-29
I'm new to Ubuntu, but not new to Linux.  I have a new laptop w. a new 9.04 installation.  The sound has not worked since installation.  

I have tried various suggestions:
disable pulse audio 
adding various entries to /etc/modprobe.d/alsa-base.conf
--options snd-hda-intel model=3stack-dig
--options snd-hda-intel enable_msi=1
--options snd-hda-intel single_cmd=1
--#options snd-hda-intel model=hp-m4 enable_msi=1
--options snd slots=snd-hda-intel
--# u1Nb.Jqboh86TqAC:82801I (ICH9 Family) HD Audio Controller
--alias snd-card-0 snd-hda-intel
--#
--#options snd-hda-intel position_fix=1 model=3stack

No sound so far.  Volume is all the way up, and not muted.

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

# lspci -vv
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 3624
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 2295
        Region 0: Memory at da100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
                Address: 00000000fee0300c  Data: 41c9
        Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag- RBE- FLReset+
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
                LnkCap: Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
                        ClockPM- Suprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; Disabled- Retrain- CommClk-
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
        Subsystem: Hewlett-Packard Company Device 3624
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 2294
        Region 0: Memory at da010000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
                        ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <64ns, L1 <1us
                        ClockPM- Suprise- LLActRep- BwNot-
                LnkCtl: ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
                Address: 00000000fee0300c  Data: 41d1
        Capabilities: [100] Vendor Specific Information <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

From syslog:
Apr 27 18:21:57 singularity kernel: [   12.016736] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr 27 18:21:57 singularity kernel: [   12.016821] HDA Intel 0000:00:1b.0: irq 2295 for MSI/MSI-X
Apr 27 18:21:57 singularity kernel: [   12.016855] HDA Intel 0000:00:1b.0: setting latency timer to 64
Apr 27 18:21:57 singularity kernel: [   12.050628] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input12
Apr 27 18:21:57 singularity kernel: [   12.149524] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 27 18:21:57 singularity kernel: [   12.149604] HDA Intel 0000:01:00.1: irq 2294 for MSI/MSI-X
Apr 27 18:21:57 singularity kernel: [   12.149641] HDA Intel 0000:01:00.1: setting latency timer to 64


What should I look at next?

---

### Post by MadJester on 2009-04-30
Fixed via this thread:
[http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090)

Bug in the driver.  Needed to compile the newest version of the alsa-driver.

:)

---

### Post by andhradon on 2009-07-26
Hi, i have had the same problem for a while, and i found a solution and it worked like magic.... :D

type the following line from recovery mode as root and reboot

echo "options snd-hda-intel enable_msi=1" >> /etc/modprobe.d/alsa-base.conf

---

