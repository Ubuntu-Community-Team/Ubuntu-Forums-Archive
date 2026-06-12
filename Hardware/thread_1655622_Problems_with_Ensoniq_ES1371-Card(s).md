---
title: "Problems with Ensoniq ES1371-Card(s)"
date: 2010-12-29
forum: Hardware
---

### Post by Stef9 on 2010-12-29
Hi all,

i´m new here; my Name is Stefan from Germany and i encounter some mixer problems with these type of cards running under Ubuntu Studio (10.10, the same under 10.04) running kernel 2.6.35-22 (and for testing issues 2.6.35-24). I´ve bought four of them, all new and the same brand. They have all exactly the same Chipset (ES1373=>ES1371) and overall type of card. I do the "el-cheapo"-Trick to merge them all with JackD and a modified .asoundrc ,including the hardware-mod (connecting all cards to one Crystal-Source), but this won´t work correctly, not because of the merging overall, it´s more about the Alsamixer. 

One Card of them is recoginzed as "Ensoniq Audio PCI" with Chipset "CS4299" and there does the un-mute of line-in work correctly; i also can record from its line-in withut ptoblems. All other cards are recognized also as "Ensoniq AudioPCI", but with Chipset "CS4297" and there i cannot mute/unmute "line-in" or record from them; also some few mixer entrys are missing compared to the CS4299. Switching to other sources (Aux, Mic) does not affect anything, except using "mix Mono", but there is the base recording level too high and raise/lower the level of "Capture" affects gain in a wrong manner (it acts more like a hard compressor rather than adjusting the recording level). As i said, all cards are optical and technical the same.

Compiling Alsa 1.0.23 SVN from scratch incuding the latest JackD won´t help; so the cards (except that one which works) are not correctly recognized. Is this issue "mute/unmute won´t work" on this type of card known? Is there any way to tell the System/Alsa to recognize the Chipsets as 4299 for all cards, instead of one 4299 and three 4297?

Greetings
Stefan

---

### Post by cascade9 on 2010-12-30
> **Stef9 said:**
> Compiling Alsa 1.0.23 SVN from scratch incuding the latest JackD won´t help; so the cards (except that one which works) are not correctly recognized. Is this issue "mute/unmute won´t work" on this type of card known? Is there any way to tell the System/Alsa to recognize the Chipsets as 4299 for all cards, instead of one 4299 and three 4297?


Not as far as I know.

those 1373/1371 cards were some of the worst I've ever had the displeasure of using. Why on earth did yom get 4 of them? SBlive cards should be almost as cheap, and they are better cards (mind you, thanks to creative there are multipule chipsets for them as well......annoying). 

Sorry this didnt help much, think of this post as a 'free bump' ;)

---

### Post by Stef9 on 2010-12-30
Well, it was the only way to get four of them at once; sure i've also taken look at SBLive and Audigys, but they were simply too expensive in a bundle, cause there was noone, which sold them for a affordable price. Nevermind, I had SBPCI64V/128 also running on earlier times under OpenSuSE (afair under 10.3 or earlier) with the same construct and had no problems at all, but there was also the OpenSoundSystem, which let me enable/disable in/outs where Alsamixer did not anything or vice versa.

One thing i found out so far is that adding "options snd_ens1371 spdif=1 lineio=1" at etc/modprobe.d/alsabase.conf let me set/unset IEC958 and Line in=>rear out; options in Alsamixer, which were not present before, but that does not affect anything. That additional entry in alsabase.conf also affects only one of that four cards and not all of them. I removed now for testing purposes one of them, so there are at the moment only three listed. Swapping to different PCI-Slots ( i have 5 on that boarD) does also not affect anything.


Here is lspci -v:

```

00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 0300
    Flags: bus master, 66MHz, fast devsel, latency 0
    Memory at <ignored> (32-bit, prefetchable)
    Capabilities: [44] HyperTransport: Slave or Primary Interface
    Capabilities: [c0] AGP version 3.0
    Kernel driver in use: agpgart-amd64

00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
    Subsystem: Micro-Star International Co., Ltd. Device 0300
    Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 0300
    Flags: 66MHz, fast devsel, IRQ 3
    I/O ports at e100 [size=32]
    I/O ports at 4c00 [size=64]
    I/O ports at 4c40 [size=64]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 0300
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at ea003000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 0300
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at ea004000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci_hcd

00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 0300
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at ea000000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port: BAR=1 offset=0098
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ehci_hcd

00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
    Subsystem: Micro-Star International Co., Ltd. Device 0300
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at ea001000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at d200 [size=8]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2) (prog-if 8a [Master SecP PriP])
    Subsystem: Micro-Star International Co., Ltd. Device 0300
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at f000 [size=16]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: pata_amd
    Kernel modules: pata_amd

00:09.0 IDE interface: nVidia Corporation nForce3 Serial ATA Controller 2 (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: Micro-Star International Co., Ltd. Device 0300
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at 09e0 [size=8]
    I/O ports at 0be0 [size=4]
    I/O ports at 0960 [size=8]
    I/O ports at 0b60 [size=4]
    I/O ports at d900 [size=16]
    I/O ports at da00 [size=128]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:0a.0 IDE interface: nVidia Corporation nForce3 Serial ATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: Micro-Star International Co., Ltd. Device 0300
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at df00 [size=16]
    I/O ports at e000 [size=128]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 16
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
    Memory behind bridge: e8000000-e9ffffff
    Prefetchable memory behind bridge: e0000000-e7ffffff
    Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
    I/O behind bridge: 0000c000-0000cfff
    Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600XT] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. V9560XT/TD
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (32-bit, prefetchable) [size=128M]
    [virtual] Expansion ROM at e9000000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
    Capabilities: [44] AGP version 3.0
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb

02:07.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 04)
    Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
    Flags: bus master, slow devsel, latency 32, IRQ 17
    I/O ports at c000 [size=64]
    Capabilities: [dc] Power Management version 1
    Kernel driver in use: ENS1371
    Kernel modules: snd-ens1371

02:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 04)
    Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
    Flags: bus master, slow devsel, latency 32, IRQ 19
    I/O ports at c100 [size=64]
    Capabilities: [dc] Power Management version 1
    Kernel driver in use: ENS1371
    Kernel modules: snd-ens1371

02:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 04)
    Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
    Flags: bus master, slow devsel, latency 32, IRQ 17
    I/O ports at c200 [size=64]
    Capabilities: [dc] Power Management version 1
    Kernel driver in use: ENS1371
    Kernel modules: snd-ens1371


```lsmod:

```

Module                  Size  Used by
snd_ens1371            23974  13 
gameport               11460  1 snd_ens1371
snd_ac97_codec        125009  1 snd_ens1371
nouveau               578605  2 
ac97_bus                1442  1 snd_ac97_codec
snd_pcm                91964  8 snd_ens1371,snd_ac97_codec
ttm                    66976  1 nouveau
snd_seq_midi            5914  0 
snd_rawmidi            21856  2 snd_ens1371,snd_seq_midi
drm_kms_helper         34518  1 nouveau
snd_seq_midi_event      7195  1 snd_seq_midi
snd_seq                57128  4 snd_seq_midi,snd_seq_midi_event
drm                   219952  4 nouveau,ttm,drm_kms_helper
snd_timer              24248  2 snd_pcm,snd_seq
snd_seq_device          6816  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    64310  29 snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd
snd_page_alloc          8740  1 snd_pcm
ppdev                   6575  0 
i2c_algo_bit            5870  1 nouveau
video                  24034  1 nouveau
psmouse                60584  0 
output                  2463  1 video
shpchp                 28930  0 
serio_raw               4990  0 
lp                     10280  0 
parport_pc             32098  1 
k8temp                  4297  0 
edac_core              48393  0 
i2c_nforce2             6054  0 
edac_mce_amd            9471  0 
parport                39060  3 ppdev,lp,parport_pc
pata_amd               11954  0 
forcedeth              58613  0 
sata_nv                24396  2 
floppy                 65584  0 


```

And lspci-vv for that three cards:

```


02:07.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 04)
    Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort+ <MAbort+ >SERR- <PERR- INTx-
    Latency: 32 (3000ns min, 32000ns max)
    Interrupt: pin A routed to IRQ 17
    Region 0: I/O ports at c000 [size=64]
    Capabilities: [dc] Power Management version 1
        Flags: PMEClk- DSI+ D1- D2+ AuxCurrent=0mA PME(D0+,D1-,D2+,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: ENS1371
    Kernel modules: snd-ens1371

02:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 04)
    Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort+ <MAbort+ >SERR- <PERR- INTx-
    Latency: 32 (3000ns min, 32000ns max)
    Interrupt: pin A routed to IRQ 19
    Region 0: I/O ports at c100 [size=64]
    Capabilities: [dc] Power Management version 1
        Flags: PMEClk- DSI+ D1- D2+ AuxCurrent=0mA PME(D0+,D1-,D2+,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: ENS1371
    Kernel modules: snd-ens1371

02:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 04)
    Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort+ <MAbort+ >SERR- <PERR- INTx-
    Latency: 32 (3000ns min, 32000ns max)
    Interrupt: pin A routed to IRQ 17
    Region 0: I/O ports at c200 [size=64]
    Capabilities: [dc] Power Management version 1
        Flags: PMEClk- DSI+ D1- D2+ AuxCurrent=0mA PME(D0+,D1-,D2+,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: ENS1371
    Kernel modules: snd-ens1371

```

Kernel is at the Moment 2.6.36.

Greetings & thanks for bump
Stefan

---

### Post by Stef9 on 2010-12-30
Seems to be a Hardware fault. Installed Win2K and XP for testing purposes; tried with N-Track Studio what´s happening an there is exactly the same fault regarding the Inputs. Also N-Track Studio complains that the devices have incompatible buffers.

=>Trash.

Greetings
Stef

---

