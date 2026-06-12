---
title: "no dvb device for pctv 800i"
date: 2012-01-17
forum: Hardware
---

### Post by Mask of Destiny on 2012-01-17
I just purchased a pctv 800i TV tuner card (formerly known as the Pinnacle PCTV 800i). According to the Linux TV wiki this card is supported in the mainline kernel. I've tried it on my HTPC running 11.10 and my desktop which is still on 11.04 with similar results. The card seems to be recognized and entries get created in /dev/ for the analog portion of the card, but not for the ATSC/QAM side (i.e. there's no /dev/dvb).

Here's the relevant portion of the dmesg output:
```
[    4.354293] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded
[    4.364856] cx8800 0000:03:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.365952] cx88[0]: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58,autodetected], frontend(s): 1
[    4.365954] cx88[0]: TV tuner type 76, Radio tuner type -1
[    4.371849] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.8 loaded
[    4.503849] i2c-core: driver [tuner] using legacy suspend method
[    4.503852] i2c-core: driver [tuner] using legacy resume method
[    4.515161] tuner 0-0064: chip found @ 0xc8 (cx88[0])
[    4.564200] xc5000 0-0064: creating new instance
[    4.565315] xc5000: Successfully identified at address 0x64
[    4.565316] xc5000: Firmware has not been loaded previously
[    4.565319] cx88[0]: Calling XC5000 callback
[    4.590020] Registered IR keymap rc-pinnacle-pctv-hd
[    4.590085] input: cx88 IR (Pinnacle PCTV HD 800i) as /devices/pci0000:00/0000:00:14.4/0000:03:06.0/rc/rc0/input6
[    4.590139] rc0: cx88 IR (Pinnacle PCTV HD 800i) as /devices/pci0000:00/0000:00:14.4/0000:03:06.0/rc/rc0
[    4.590205] rc rc0: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 0
[    4.590212] cx88[0]/0: found at 0000:03:06.0, rev: 5, irq: 20, latency: 32, mmio: 0xf9000000
[    4.590273] cx88[0]/0: registered device video0 [v4l2]
[    4.590303] cx88[0]/0: registered device vbi0
[    4.592611] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[    4.595248] xc5000: firmware read 12401 bytes.
[    4.595249] xc5000: firmware uploading...
[    4.595251] cx88[0]: Calling XC5000 callback
[    6.940032] xc5000: firmware upload complete...
[    7.610198] cx88_audio 0000:03:06.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    7.610221] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[    7.611504] cx88[0]/2: cx2388x 8802 Driver Manager
[    7.611513] cx88-mpeg driver manager 0000:03:06.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    7.611522] cx88[0]/2: found at 0000:03:06.2, rev: 5, irq: 20, latency: 32, mmio: 0xfa000000
[    7.612054] cx88[0]: Calling XC5000 callback
[    7.622746] cx88/2: cx2388x dvb driver version 0.0.8 loaded
[    7.622748] cx88/2: registering cx8802 driver, type: dvb access: shared
[    7.622751] cx88[0]/2: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58]
[    7.622752] cx88[0]/2: cx2388x based DVB/ATSC card
[    7.622754] cx8802_alloc_frontends() allocating 1 frontend(s)
[    7.625679] cx88[0]/2: frontend initialization failed
[    7.625681] cx88[0]/2: dvb_register failed (err = -22)
[    7.625683] cx88[0]/2: cx8802 probe failed, err = -22
```

And here's the output of lspci for the card:
```
03:06.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [14f1:8800] (rev 05)
	Subsystem: Pinnacle Systems Inc. Device [11bd:0051]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (5000ns min, 13750ns max), Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [44] Vital Product Data
		Unknown small resource type 00, will not decode more.
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: cx8800
	Kernel modules: cx8800

03:06.1 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] [14f1:8801] (rev 05)
	Subsystem: Pinnacle Systems Inc. Device [11bd:0051]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (1000ns min, 63750ns max), Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: cx88_audio
	Kernel modules: cx88-alsa

03:06.2 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] [14f1:8802] (rev 05)
	Subsystem: Pinnacle Systems Inc. Device [11bd:0051]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (1500ns min, 22000ns max), Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: cx88-mpeg driver manager
	Kernel modules: cx8802
```

I've tested the card under Windows to make sure it's not faulty. Any help getting this working would be greatly appreciated.

---

