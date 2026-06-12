---
title: "Flashing screen - graphical issues with HP pavillion dv"
date: 2015-10-27
forum: Hardware
---

### Post by alexander_M_clarke on 2015-10-27
Hey :)
Newbie to ubuntu here. Used it a few years ago but stopped after my laptop broke.

Just installed ubuntu  15.10 over a copy of W10 on a dell pavillion Dv6 (trying to find the full laptop ID now), which I was also having driver troubles with

The CCC on W10 was reporting an error every time I logged in. I can't remember the whole message, but it was something along the lines of "drivers malfunctioning"
It also reported a C++ runtime error every time I plugged in or unplugged my laptop (atibtmon.exe terminated in an usual way, or something similar), and the brightness buttons didn't wor

Here on ubuntu 15.10, now and then (it does it for a while, stops for a bit, and does it again) it'll have a phase where every few seconds, everything (including the cursor) will freeze for a moment, then the active window will flash white for a frame or two, then go back to normal.
I'm not sure, but I don't think performance is 100% as good as I remembered it used to be, but coming from W10 I'm not really sure.

I'm taking a look at both the open source and proprietary drivers now.
I'm reading [this guide]("https://help.ubuntu.com/community/RadeonDriver") right now.

I think this command is reporting errors (correct me if I'm wrong):

```
lspci -vvnn | grep VGA


    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250] [1002:9712] (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470] [1002:68e0] (rev ff) (prog-if ff)
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
```

Thank you in advance for any help.

Fun update:

Each time the screen freezes, this is entered into the syslog:
```
Oct 27 18:10:51 ***-HP-Pavilion-dv6-Notebook-PC kernel: [  753.507299] [drm] ring test on 0 succeeded in 1 usecs
Oct 27 18:10:51 ***-HP-Pavilion-dv6-Notebook-PC kernel: [  753.507309] [drm] ring test on 3 succeeded in 2 usecs
Oct 27 18:10:52 ***-HP-Pavilion-dv6-Notebook-PC kernel: [  753.694088] [drm] ring test on 5 succeeded in 1 usecs
Oct 27 18:10:52 ***-HP-Pavilion-dv6-Notebook-PC kernel: [  753.694104] [drm] UVD initialized successfully.
Oct 27 18:10:52 ***-HP-Pavilion-dv6-Notebook-PC kernel: [  753.694163] [drm] ib test on ring 0 succeeded in 0 usecs
Oct 27 18:10:52 ***-HP-Pavilion-dv6-Notebook-PC kernel: [  753.694223] [drm] ib test on ring 3 succeeded in 0 usecs
Oct 27 18:10:52 ***-HP-Pavilion-dv6-Notebook-PC kernel: [  753.865375] [drm] ib test on ring 5 succeeded
Oct 27 18:10:58 ***-HP-Pavilion-dv6-Notebook-PC kernel: [  760.498528] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
Oct 27 18:10:58 ***-HP-Pavilion-dv6-Notebook-PC kernel: [  760.502397] [drm] PCIE GART of 512M enabled (table at 0x000000000025E000).
Oct 27 18:10:58 ***-HP-Pavilion-dv6-Notebook-PC kernel: [  760.502495] radeon 0000:02:00.0: WB enabled
Oct 27 18:10:58 ***-HP-Pavilion-dv6-Notebook-PC kernel: [  760.502507] radeon 0000:02:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff8800cd2a7c00
Oct 27 18:10:58 ***-HP-Pavilion-dv6-Notebook-PC kernel: [  760.502516] radeon 0000:02:00.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff8800cd2a7c0c
Oct 27 18:10:58 ***-HP-Pavilion-dv6-Notebook-PC kernel: [  760.503332] radeon 0000:02:00.0: fence driver on ring 5 use gpu addr 0x000000000005c418 and cpu addr 0xffffc90001c1c418
```

this is entered in the xorg log, each freeze:

```
[   464.481] (II) RADEON(0): Modeline "1366x768"x0.0   69.30  1366 1382 1416 1466  768 770 776 788 -hsync -vsync (47.3 kHz eP)
[   464.492] (II) RADEON(0): EDID vendor "CMO", prod id 5522
```

Can anyone explain what these mean, and exactly why this would be happening over and over?

bump. I think it's worth noting that if I'm fullscreen on youtube, the 'you're fullscreen, press escape to exit fullscreen' message will reappaear each time the screen flashes.

Is the screen being reinitialised each time it flashes?

---

