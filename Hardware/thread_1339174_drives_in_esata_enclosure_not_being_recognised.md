---
title: "drives in esata enclosure not being recognised"
date: 2009-11-27
forum: Hardware
---

### Post by shanigans on 2009-11-27
Hi, 

I've just bought some esata enclosures for my system, but my system cannot seem to fully detect the drives. When I connect or power-on the drives, dmesg shows me that its receiving a signal and the system tries to connect the drives, but it just never manages to actually do it.
Any help would be greatly appreciated. (I've been at this for days and I have many HDD's sitting idle)

Following is every tidbit of information I can think of which might be useful. Let me know if there is anything else I can do to help.

**Various information about my system**
MB: Asus P5K Deluxe 

> 
$cat /etc/issue
Ubuntu 9.10

$uname -r
2.6.31-15-generic

$lspci -vv -k
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02) (prog-if 01)
        Subsystem: ASUSTeK Computer Inc. Device 8277
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin B routed to IRQ 28
        Region 0: I/O ports at 9c00 [size=8]
        Region 1: I/O ports at 9880 [size=4]
        Region 2: I/O ports at 9800 [size=8]
        Region 3: I/O ports at 9480 [size=4]
        Region 4: I/O ports at 9400 [size=32]
        Region 5: Memory at f9ffe800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 Enable+
                Address: fee0300c  Data: 4181
        Capabilities: [70] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [a8] SATA HBA <?>
        Capabilities: [b0] Vendor Specific Information <?>
        Kernel driver in use: ahci

03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03) (prog-if 01)
        Subsystem: ASUSTeK Computer Inc. Device 824f
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 16
        Region 5: Memory at feafe000 (32-bit, non-prefetchable) [size=8K]
        Expansion ROM at feae0000 [disabled] [size=64K]
        Capabilities: [68] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] Express (v1) Legacy Endpoint, MSI 01
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
                LnkCap: Port #1, Speed 2.5GT/s, Width x1, ASPM L0s, Latency L0 <1us, L1 <16us
                        ClockPM- Suprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Kernel driver in use: ahci

03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Device 824f
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin B routed to IRQ 17
        Region 0: I/O ports at dc00 [size=8]
        Region 1: I/O ports at d880 [size=4]
        Region 2: I/O ports at d800 [size=8]
        Region 3: I/O ports at d480 [size=4]
        Region 4: I/O ports at d400 [size=16]
        Capabilities: [68] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: pata_jmicron

$lsmod
Module                  Size  Used by
aes_i586                8124  1 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
ppdev                   6688  0 
arc4                    1660  2 
ecb                     2524  2 
snd_hda_codec_analog    59292  1 
rtl8187                50624  0 
snd_hda_intel          26920  4 
snd_hda_codec          75708  2 snd_hda_codec_analog,snd_hda_intel
mac80211              181236  1 rtl8187
led_class               4096  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
snd_hwdep               7200  1 snd_hda_codec
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
lp                      8964  0 
serio_raw               5280  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  19 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
parport                35340  2 ppdev,lp
cfg80211               93052  2 rtl8187,mac80211
x_tables               16544  1 ip_tables
asus_atk0110            8252  0 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usbhid                 38208  0 
floppy                 54916  0 
r8169                  32064  0 
mii                     5212  1 r8169
ohci1394               29900  0 
sky2                   46560  0 
ieee1394               86596  1 ohci1394
intel_agp              27484  0 
agpgart                34988  1 intel_agp



**Various diagnostic information:**

BIOS: 
BIOS is set to AHCI for all sata ports.
BIOS recognises first drive connected via the port multipliers at post (I have confirmed this is correct behaviour)

Actual port multipliers/enclosures:
I'm afraid I cannot find any real information on the hardware the esata enclosures use. Let me know if there are any linux commands I can run to find details.

**dmesg (all cables connected, powering on the esata enclosure, connected to and Intel ich9 sata port)**
> 
[16165.773246] ata3: exception Emask 0x10 SAct 0x0 SErr 0x4050002 action 0xe frozen
[16165.773252] ata3: irq_stat 0x00400040, connection status changed
[16165.773256] ata3: SError: { RecovComm PHYRdyChg CommWake DevExch }
[16165.773265] ata3: hard resetting link
[16175.788012] ata3: softreset failed (device not ready)
[16175.788018] ata3: hard resetting link
[16182.668555] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[16182.668847] ata3.15: Port Multiplier 1.1, 0x197b:0x2352 r0, 2 ports, feat 0x0/0x0
[16182.668851] ata3.15: Asynchronous notification not supported, hotplug won't
[16182.668852]          work on fan-out ports. Use warm-plug instead.
[16182.668998] ata3.15: applying bridge limits
[16182.669048] ata3.00: hard resetting link
[16183.152274] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[16183.152317] ata3.01: hard resetting link
[16183.636765] ata3.01: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[16213.636515] ata3.00: qc timeout (cmd 0xec)
[16213.636524] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[16213.636532] ata3.15: hard resetting link
[16214.400540] ata3.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[16214.400837] ata3.00: hard resetting link
[16214.884271] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[16214.884314] ata3.01: hard resetting link
[16215.368766] ata3.01: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[16245.368516] ata3.00: qc timeout (cmd 0xec)
[16245.368526] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[16245.368534] ata3.15: hard resetting link
[16246.132520] ata3.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[16246.132823] ata3.00: hard resetting link
[16249.132519] ata3.15: qc timeout (cmd 0xe4)
[16249.132528] ata3.00: failed to read SCR 2 (Emask=0x4)
[16249.132531] ata3.00: COMRESET failed (errno=-5)
[16249.132536] ata3.00: failed to read SCR 0 (Emask=0x40)
[16249.132539] ata3.00: reset failed, giving up
[16249.132542] ata3.00: failed to recover link after 3 tries, disabling
[16249.132548] ata3.15: hard resetting link
[16254.656523] ata3.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[16254.976634] ata3.00: failed to read SCR 0 (Emask=0x100)
[16254.976639] ata3.00: failed to write SCR 1 (Emask=0x40)
[16254.976643] ata3.00: failed to clear SError.N (errno=-5)
[16254.976649] ata3.15: hard resetting link
[16260.476521] ata3.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[16260.796640] ata3.00: failed to read SCR 0 (Emask=0x100)
[16260.796645] ata3.00: failed to write SCR 1 (Emask=0x40)
[16260.796648] ata3.00: failed to clear SError.N (errno=-5)
[16260.796655] ata3.15: hard resetting link
[16266.320523] ata3.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[16266.644139] ata3.00: failed to read SCR 0 (Emask=0x100)
[16266.644144] ata3.00: failed to write SCR 1 (Emask=0x40)
[16266.644147] ata3.00: failed to clear SError.N (errno=-5)
[16266.644153] ata3.15: hard resetting link
[16272.168025] ata3.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[16272.488134] ata3.00: failed to read SCR 0 (Emask=0x100)
[16272.488139] ata3.00: failed to write SCR 1 (Emask=0x40)
[16272.488142] ata3.00: failed to clear SError.N (errno=-5)
[16272.488146] ata3: failed to recover PMP after 5 tries, giving up
[16272.488149] ata3.15: Port Multiplier detaching
[16272.488189] ata3.00: disabled
[16272.488197] ata3: exception Emask 0x2 SAct 0x0 SErr 0x0 action 0x6 frozen t4
[16272.488201] ata3: irq_stat 0x00800000, incorrect PMP
[16272.488207] ata3: hard resetting link
[16272.975351] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[16272.975366] ata3: EH complete


**dmesg (all cables connected, powering on the esata enclosure, connected to and JMicron esata port)**
> 
[16383.696381] ata8: exception Emask 0x10 SAct 0x0 SErr 0x4050000 action 0xe frozen
[16383.696387] ata8: irq_stat 0x00400040, connection status changed
[16383.696391] ata8: SError: { PHYRdyChg CommWake DevExch }
[16383.696400] ata8: hard resetting link
[16384.420032] ata8: SATA link down (SStatus 0 SControl 300)
[16384.420045] ata8: EH complete
[16386.252042] ata8: exception Emask 0x10 SAct 0x0 SErr 0x4050000 action 0xe frozen
[16386.252046] ata8: irq_stat 0x00000040, connection status changed
[16386.252049] ata8: SError: { PHYRdyChg CommWake DevExch }
[16386.252056] ata8: hard resetting link
[16396.272015] ata8: softreset failed (device not ready)
[16396.272022] ata8: hard resetting link
[16403.156027] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[16403.156393] ata8.15: Port Multiplier 1.1, 0x197b:0x2352 r0, 2 ports, feat 0x0/0x0
[16403.156396] ata8.15: Asynchronous notification not supported, hotplug won't
[16403.156398]          work on fan-out ports. Use warm-plug instead.
[16403.156562] ata8.15: applying bridge limits
[16403.156625] ata8.00: hard resetting link
[16403.640329] ata8.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[16403.640381] ata8.01: hard resetting link
[16404.124328] ata8.01: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[16409.124521] ata8.00: qc timeout (cmd 0xec)
[16409.124537] ata8.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[16409.124544] ata8.15: hard resetting link
[16409.608531] ata8.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[16409.608910] ata8.00: hard resetting link
[16412.932020] ata8.15: qc timeout (cmd 0xe8)
[16412.932035] ata8.00: failed to write SCR 1 (Emask=0x4)
[16412.932039] ata8.00: COMRESET failed (errno=-5)
[16412.932044] ata8.00: failed to read SCR 0 (Emask=0x40)
[16412.932046] ata8.00: reset failed, giving up
[16412.932052] ata8.15: hard resetting link
[16413.416026] ata8.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[16414.612015] ata8.00: hard resetting link
[16415.096326] ata8.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[16415.096378] ata8.01: hard resetting link
[16415.584327] ata8.01: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[16425.584014] ata8.00: qc timeout (cmd 0xec)
[16425.584029] ata8.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[16425.584034] ata8.00: failed to recover link after 3 tries, disabling
[16425.584041] ata8.15: hard resetting link
[16426.348026] ata8.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[16426.668737] ata8.01: hard resetting link
[16427.152827] ata8.01: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[16432.152028] ata8.01: qc timeout (cmd 0xec)
[16432.152043] ata8.01: failed to IDENTIFY (I/O error, err_mask=0x4)
[16432.152051] ata8.15: hard resetting link
[16432.692031] ata8.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[16433.012232] ata8.01: hard resetting link
[16433.496334] ata8.01: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[16443.496519] ata8.01: qc timeout (cmd 0xec)
[16443.496539] ata8.01: failed to IDENTIFY (I/O error, err_mask=0x4)
[16443.496546] ata8.15: hard resetting link
[16444.372526] ata8.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[16444.692236] ata8.01: hard resetting link
[16445.176333] ata8.01: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[16475.180022] ata8.01: qc timeout (cmd 0xec)
[16475.180037] ata8.01: failed to IDENTIFY (I/O error, err_mask=0x4)
[16475.180042] ata8.01: failed to recover link after 3 tries, disabling
[16475.180048] ata8.15: hard resetting link
[16476.056028] ata8.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[16477.344787] ata8: EH complete


If there is any other information I could provide which would be useful, please let me know. I am going bananas trying to figure this out!

- shanigans

---

### Post by roman.romaniuk on 2009-12-26
Any luck in getting this resolved? I appear to be in the exact same boat ...

-Roman

---

### Post by shanigans on 2009-12-27
No luck yet I'm afraid. I'm concerned that the linux kernel may need to support the chipset inside the actual enclosure too.
That being said, there are a fair few port-multiplier related fixes/additions in one of the newer linux builds (not yet released in ubuntu), so fingers crossed that will solve it. Otherwise, I guess I've got 10 drives being accessed via USB. Hazaa :-/

---

### Post by idallen on 2010-12-06
I get the same "Asynchronous notification not supported" using a Thermaltake BlacX Duet ST0014U 2-drive eSATA docking station under Ubuntu 10.10 x86_64. Resetting the port doesn't help:

echo '- - -' > /sys/class/scsi_host/host4/scan

My Vantec NexStar Dual Bay 2-drive eSATA docking station doesn't generate that error and works fine.

Themaltake (not working) says:

Port Multiplier 1.1, 0x197b:0x2352 r0, 2 ports, feat 0x0/0x0

Vantec (works fine) says:

Port Multiplier 1.1, 0x1095:0x5744 r33, 3 ports, feat 0x1/0x9

---

### Post by aonikenk on 2011-01-21
Any good news on this? I am in the same exactly boat (Thermaltake BlacX Duet ST0014U 2-drive eSATA docking station under Ubuntu 10.10 x86_64). The enclosure  will recognize one drive but fails when inserting the second. I have AHCI enabled and the first drive inserted hotplugs correctly.

---

### Post by shmore on 2011-09-16
This is definitely coming down to the hot-plugging support. I have the same unit as the others here, the Thermaltake BlacX Duet ST0014U, and experience an identical stream of kernel messages.

> Asynchronous notification not supported, hotplug won't
[16182.668852] work on fan-out ports. Use warm-plug instead.

A restart with the drives on during boot up works fine, both drives are recognised.

---

