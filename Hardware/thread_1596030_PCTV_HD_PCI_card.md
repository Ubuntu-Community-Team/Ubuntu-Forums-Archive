---
title: "PCTV HD PCI card"
date: 2010-10-13
forum: Hardware
---

### Post by bowens44 on 2010-10-13
Has anyone been able to get the PCTV HD PCI card to work in lucid or maverick?

I get video but no sound.

---

### Post by bowens44 on 2010-10-13
I found that I can watch digital QAM channels in kaffeine and I have sound.
No sound in tvtime/analog

More info:
lspci -vv

```
05:05.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: Pinnacle Systems Inc. Device 0051
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (5000ns min, 13750ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx8800
	Kernel modules: cx8800

05:05.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
	Subsystem: Pinnacle Systems Inc. Device 0051
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (1000ns min, 63750ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx88_audio
	Kernel modules: cx88-alsa

05:05.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
	Subsystem: Pinnacle Systems Inc. Device 0051
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (1500ns min, 22000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx88-mpeg driver manager
	Kernel modules: cx8802


```


dmesg output

```
[    2.283623] pata_marvell 0000:04:00.0: setting latency timer to 64
[    2.283661] scsi6 : pata_marvell
[    2.283709] scsi7 : pata_marvell
[    2.283730] ata7: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
[    2.283731] ata8: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
[    2.345839] EXT4-fs (sda3): mounted filesystem with ordered data mode
[    2.358325] usb 3-2: configuration #1 chosen from 1 choice
[    2.690859] usb 3-3: new full speed USB device using ohci_hcd and address 3
[    2.873412] usb 3-3: configuration #1 chosen from 1 choice
[    2.880124] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0000297323]
[    2.950114] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[00023c01510ed898]
[    3.330023] usb 5-2: new full speed USB device using ohci_hcd and address 2
[    3.578273] usb 5-2: configuration #1 chosen from 1 choice
[    3.670901] usb 1-5.4: new low speed USB device using ehci_hcd and address 5
[    3.877978] usb 1-5.4: configuration #1 chosen from 1 choice
[   28.643458] udev: starting version 151
[   28.662469] lp: driver loaded but no devices found
[   28.668154] vga16fb: initializing
[   28.668157] vga16fb: mapped to 0xffff8800000a0000
[   28.668201] fb0: VGA16 VGA frame buffer device
[   28.687762] EDAC MC: Ver: 2.1.0 Sep 17 2010
[   28.693692] Adding 9456632k swap on /dev/sda5.  Priority:-1 extents:1 across:9456632k 
[   28.697516] ACPI: resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0x000b00-0x000b0f]
[   28.697519] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   28.735396] nvidia: module license 'NVIDIA' taints kernel.
[   28.735399] Disabling lock debugging due to kernel taint
[   28.758040] type=1505 audit(1287020515.813:2):  operation="profile_load" pid=752 name="/sbin/dhclient3"
[   28.758233] type=1505 audit(1287020515.813:3):  operation="profile_load" pid=752 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   28.758349] type=1505 audit(1287020515.813:4):  operation="profile_load" pid=752 name="/usr/lib/connman/scripts/dhclient-script"
[   28.999635] Linux video capture interface: v2.00
[   29.007528] EDAC amd64_edac:  Ver: 3.2.0 Sep 17 2010
[   29.009235] gameport: EMU10K1 is pci0000:05:06.1/gameport0, io 0xec00, speed 651kHz
[   29.009628] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   29.009634] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   29.009634]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   29.009635]  (Note that use of the override may cause unknown side effects.)
[   29.009644] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   29.011539] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[   29.011995] cx88[0]: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58,autodetected], frontend(s): 1
[   29.011997] cx88[0]: TV tuner type 76, Radio tuner type -1
[   29.013750] usbcore: registered new interface driver hiddev
[   29.018340] Initializing USB Mass Storage driver...
[   29.029069] Bluetooth: Core ver 2.15
[   29.029110] NET: Registered protocol family 31
[   29.029111] Bluetooth: HCI device and connection manager initialized
[   29.029112] Bluetooth: HCI socket layer initialized
[   29.029994] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   29.030057] usbcore: registered new interface driver btusb
[   29.032147] generic-usb 0003:04A9:1095.0002: hiddev96,hidraw0: USB HID v1.10 Device [Canon iP6000D] on usb-0000:00:12.0-3/input2
[   29.033414] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   29.039730] scsi8 : SCSI emulation for USB Mass Storage devices
[   29.039827] usbcore: registered new interface driver usb-storage
[   29.039829] USB Mass Storage support registered.
[   29.043468] usb-storage: device found at 3
[   29.043469] usb-storage: waiting for device to settle before scanning
[   29.046116] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1095
[   29.046128] usbcore: registered new interface driver usblp
[   29.050053] cx2388x alsa driver version 0.0.7 loaded
[   29.061363] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5.4/1-5.4:1.0/input/input3
[   29.061417] generic-usb 0003:046D:C313.0003: input,hidraw1: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:12.2-5.4/input0
[   29.071623] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.124728] kjournald starting.  Commit interval 5 seconds
[   29.124734] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   29.125021] EXT3 FS on sdd1, internal journal
[   29.125023] EXT3-fs: mounted filesystem with ordered data mode.
[   29.133409] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5.4/1-5.4:1.1/input/input4
[   29.133476] generic-usb 0003:046D:C313.0004: input,hiddev97,hidraw2: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:12.2-5.4/input1
[   29.155392] tuner 0-0064: chip found @ 0xc8 (cx88[0])
[   29.157971] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5.4/1-5.4:1.2/input/input5
[   29.158024] generic-usb 0003:046D:C313.0005: input,hidraw3: USB HID v1.10 Mouse [BTC USB Multimedia Keyboard] on usb-0000:00:12.2-5.4/input2
[   29.158040] usbcore: registered new interface driver usbhid
[   29.158041] usbhid: v2.6:USB HID core driver
[   29.196766] Console: switching to colour frame buffer device 80x30
[   29.228817] kjournald starting.  Commit interval 5 seconds
[   29.228831] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   29.229142] EXT3 FS on sdb1, internal journal
[   29.229146] EXT3-fs: mounted filesystem with ordered data mode.
[   29.232133] xc5000 0-0064: creating new instance
[   29.233245] xc5000: Successfully identified at address 0x64
[   29.233247] xc5000: Firmware has not been loaded previously
[   29.233250] cx88[0]: Calling XC5000 callback
[   29.233297] input: cx88 IR (Pinnacle PCTV HD 800i) as /devices/pci0000:00/0000:00:14.4/0000:05:05.2/input/input6
[   29.233336] cx88[0]/2: cx2388x 8802 Driver Manager
[   29.233351]   alloc irq_desc for 20 on node 0
[   29.233352]   alloc kstat_irqs on node 0
[   29.233357] cx88-mpeg driver manager 0000:05:05.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   29.233366] cx88[0]/2: found at 0000:05:05.2, rev: 5, irq: 20, latency: 64, mmio: 0xfb000000
[   29.233371] IRQ 20/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   29.234404] cx8800 0000:05:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   29.234412] cx88[0]/0: found at 0000:05:05.0, rev: 5, irq: 20, latency: 64, mmio: 0xf9000000
[   29.234420] IRQ 20/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   29.234503] cx88[0]/0: registered device video0 [v4l2]
[   29.234550] cx88[0]/0: registered device vbi0
[   29.236954] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[   29.237021] cx88-mpeg driver manager 0000:05:05.2: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[   29.238739] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   29.238745] nvidia 0000:01:00.0: setting latency timer to 64
[   29.238749] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   29.238888] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
[   29.241008] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   29.241010] cx88/2: registering cx8802 driver, type: dvb access: shared
[   29.241012] cx88[0]/2: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58]
[   29.241014] cx88[0]/2: cx2388x based DVB/ATSC card
[   29.241015] cx8802_alloc_frontends() allocating 1 frontend(s)
[   29.256031] EXT4-fs (sdc1): mounted filesystem with ordered data mode
[   29.304325] input: Logitech Logitech Extreme 3D as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input7
[   29.304383] logitech 0003:046D:C215.0001: input,hidraw4: USB HID v1.10 Joystick [Logitech Logitech Extreme 3D] on usb-0000:00:12.0-2/input0
[   29.347856] xc5000: firmware read 12401 bytes.
[   29.347857] xc5000: firmware uploading...
[   29.347859] cx88[0]: Calling XC5000 callback
[   29.465690] xc5000 0-0064: attaching existing instance
[   29.478268] xc5000: Successfully identified at address 0x64
[   29.478269] xc5000: Firmware has not been loaded previously
[   29.490559] cx88[0]: Calling XC5000 callback
[   29.502802] DVB: registering new adapter (cx88[0])
[   29.502804] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   30.264375] r8169: eth0: link up
[   30.264382] r8169: eth0: link up
[   30.384430] type=1505 audit(1287020517.443:5):  operation="profile_load" pid=1067 name="/usr/share/gdm/guest-session/Xsession"
[   30.385219] type=1505 audit(1287020517.443:6):  operation="profile_replace" pid=1068 name="/sbin/dhclient3"
[   30.385381] type=1505 audit(1287020517.443:7):  operation="profile_replace" pid=1068 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   30.385472] type=1505 audit(1287020517.443:8):  operation="profile_replace" pid=1068 name="/usr/lib/connman/scripts/dhclient-script"
[   30.387025] type=1505 audit(1287020517.443:9):  operation="profile_load" pid=1069 name="/usr/bin/evince"
[   30.389108] type=1505 audit(1287020517.443:10):  operation="profile_load" pid=1069 name="/usr/bin/evince-previewer"
[   30.390422] type=1505 audit(1287020517.453:11):  operation="profile_load" pid=1069 name="/usr/bin/evince-thumbnailer"
[   31.720023] xc5000: firmware upload complete...
[   32.360039] cx88_audio 0000:05:05.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   32.360048] IRQ 20/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   32.360062] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   32.362802]   alloc irq_desc for 21 on node 0
[   32.362804]   alloc kstat_irqs on node 0
[   32.362809] EMU10K1_Audigy 0000:05:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   32.369323] Installing spdif_bug patch: SB Audigy 2 ZS [SB0350]
[   32.491319] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   32.491321] vboxdrv: Successfully done.
[   32.491322] vboxdrv: Found 4 processor cores.
[   32.491376] VBoxDrv: dbg - g_abExecMemory=ffffffffa0e6ec80
[   32.491412] vboxdrv: fAsync=0 offMin=0x56b offMax=0x16b3
[   32.491524] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   32.491526] vboxdrv: Successfully loaded version 3.2.8 (interface 0x00140001).
[   32.704953] Bluetooth: L2CAP ver 2.14
[   32.704955] Bluetooth: L2CAP socket layer initialized
[   32.707593] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.707595] Bluetooth: BNEP filters: protocol multicast
[   32.711320] Bridge firewalling registered
[   32.714063] Bluetooth: SCO (Voice Link) ver 0.6
[   32.714065] Bluetooth: SCO socket layer initialized
[   32.719042] ppdev: user-space parallel port driver
[   32.944908] Bluetooth: RFCOMM TTY layer initialized
[   32.944911] Bluetooth: RFCOMM socket layer initialized
[   32.944912] Bluetooth: RFCOMM ver 1.11
[   33.033488] CPU0 attaching NULL sched-domain.
[   33.033492] CPU1 attaching NULL sched-domain.
[   33.033493] CPU2 attaching NULL sched-domain.
[   33.033495] CPU3 attaching NULL sched-domain.
[   33.201743] CPU0 attaching sched-domain:
[   33.201746]  domain 0: span 0-3 level MC
[   33.201748]   groups: 0 1 2 3
[   33.201751] CPU1 attaching sched-domain:
[   33.201752]  domain 0: span 0-3 level MC
[   33.201753]   groups: 1 2 3 0
[   33.201755] CPU2 attaching sched-domain:
[   33.201756]  domain 0: span 0-3 level MC
[   33.201757]   groups: 2 3 0 1
[   33.201759] CPU3 attaching sched-domain:
[   33.201760]  domain 0: span 0-3 level MC
[   33.201761]   groups: 3 0 1 2
[   34.042038] usb-storage: device scan complete
[   34.048027] scsi 8:0:0:0: Direct-Access     Canon    iP6000DStorage   0109 PQ: 0 ANSI: 2
[   34.048331] sd 8:0:0:0: Attached scsi generic sg6 type 0
[   34.078027] sd 8:0:0:0: [sde] Attached SCSI removable disk
[   34.165375] usb 3-3: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   35.888428] CPU0 attaching NULL sched-domain.
[   35.888432] CPU1 attaching NULL sched-domain.
[   35.888434] CPU2 attaching NULL sched-domain.
[   35.888435] CPU3 attaching NULL sched-domain.
[   35.950902] CPU0 attaching sched-domain:
[   35.950904]  domain 0: span 0-3 level MC
[   35.950906]   groups: 0 1 2 3
[   35.950910] CPU1 attaching sched-domain:
[   35.950911]  domain 0: span 0-3 level MC
[   35.950912]   groups: 1 2 3 0
[   35.950915] CPU2 attaching sched-domain:
[   35.950916]  domain 0: span 0-3 level MC
[   35.950917]   groups: 2 3 0 1
[   35.950919] CPU3 attaching sched-domain:
[   35.950920]  domain 0: span 0-3 level MC
[   35.950921]   groups: 3 0 1 2
[   38.024722] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024731] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024738] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024753] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024766] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024779] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024793] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024807] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024820] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024834] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024847] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024860] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024873] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024887] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024900] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024913] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024927] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024940] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024953] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024966] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024979] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.024993] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025006] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025020] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025033] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025046] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025060] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025073] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025086] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025099] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025112] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025126] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025139] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025153] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025160] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025167] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025174] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025181] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025188] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025195] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025202] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025209] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025216] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025223] cx88[0]: irq aud [0x1000] dn_sync*
[   38.025230] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025237] cx88[0]: irq aud [0x1000] dn_sync*
[   38.025243] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025250] cx88[0]: irq aud [0x1000] dn_sync*
[   38.025256] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025263] cx88[0]: irq aud [0x1000] dn_sync*
[   38.025269] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025276] cx88[0]: irq aud [0x1000] dn_sync*
[   38.025283] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025290] cx88[0]: irq aud [0x1000] dn_sync*
[   38.025296] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025303] cx88[0]: irq aud [0x1000] dn_sync*
[   38.025310] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025317] cx88[0]: irq aud [0x1000] dn_sync*
[   38.025323] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025338] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025351] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025365] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025378] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025392] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025405] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.025418] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030022] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030033] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030043] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030052] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030061] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030070] cx88[0]: irq aud [0x1000] dn_sync*
[   38.030080] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030089] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030109] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030119] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030127] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030137] cx88[0]: irq aud [0x1000] dn_sync*
[   38.030147] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030157] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030165] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030172] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030180] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030187] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030193] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030201] cx88[0]: irq aud [0x1000] dn_sync*
[   38.030207] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030214] cx88[0]: irq aud [0x1000] dn_sync*
[   38.030221] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030228] cx88[0]: irq aud [0x1000] dn_sync*
[   38.030234] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030241] cx88[0]: irq aud [0x1000] dn_sync*
[   38.030247] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030256] cx88[0]: irq aud [0x1000] dn_sync*
[   38.030266] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030275] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030290] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030303] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030317] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030330] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030344] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030357] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030371] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030384] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030397] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030411] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030424] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030438] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030451] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030464] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030479] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030492] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030505] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030519] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030532] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030545] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030558] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030572] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030585] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030599] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030612] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030626] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030639] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030653] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030666] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030680] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030693] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030706] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030719] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030733] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030746] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030760] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030773] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030786] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030800] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030813] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030827] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030840] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030853] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030867] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030880] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030894] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030907] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030921] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030934] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030948] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030961] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030974] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.030988] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031002] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031009] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031015] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031023] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031029] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031037] cx88[0]: irq aud [0x1000] dn_sync*
[   38.031043] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031050] cx88[0]: irq aud [0x1000] dn_sync*
[   38.031056] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031064] cx88[0]: irq aud [0x1000] dn_sync*
[   38.031070] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031077] cx88[0]: irq aud [0x1000] dn_sync*
[   38.031083] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031090] cx88[0]: irq aud [0x1000] dn_sync*
[   38.031097] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031104] cx88[0]: irq aud [0x1000] dn_sync*
[   38.031110] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031117] cx88[0]: irq aud [0x1000] dn_sync*
[   38.031123] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031130] cx88[0]: irq aud [0x1000] dn_sync*
[   38.031137] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031144] cx88[0]: irq aud [0x1000] dn_sync*
[   38.031150] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031158] cx88[0]: irq aud [0x1000] dn_sync*
[   38.031164] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031179] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031193] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031206] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031220] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031233] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031246] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031259] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031273] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031286] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031300] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031313] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031326] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031340] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031353] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031366] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031379] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031393] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031407] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031420] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031433] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031446] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031460] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031473] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031487] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031500] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031514] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031526] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031540] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031554] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031567] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031581] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031594] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031607] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031620] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031634] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031647] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031660] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031674] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031687] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031700] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031714] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031728] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031741] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031754] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031768] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031781] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031794] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031808] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031821] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031835] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031848] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031861] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031868] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031875] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031882] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031889] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031897] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031904] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031911] cx88[0]: irq aud [0x1000] dn_sync*
[   38.031917] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031924] cx88[0]: irq aud [0x1000] dn_sync*
[   38.031930] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031937] cx88[0]: irq aud [0x1000] dn_sync*
[   38.031944] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031951] cx88[0]: irq aud [0x1000] dn_sync*
[   38.031957] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031964] cx88[0]: irq aud [0x1000] dn_sync*
[   38.031971] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031977] cx88[0]: irq aud [0x1000] dn_sync*
[   38.031983] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031991] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.031998] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032005] cx88[0]: irq aud [0x1000] dn_sync*
[   38.032011] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032018] cx88[0]: irq aud [0x1000] dn_sync*
[   38.032025] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032032] cx88[0]: irq aud [0x1000] dn_sync*
[   38.032038] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032046] cx88[0]: irq aud [0x1000] dn_sync*
[   38.032052] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032068] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032081] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032095] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032108] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032121] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032135] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032149] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032162] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032176] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032189] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032203] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032216] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032230] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032236] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032244] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032250] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032257] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032263] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032270] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032277] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032285] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032291] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032298] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032305] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032312] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032319] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032327] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032334] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032341] cx88[0]: irq aud [0x1000] dn_sync*
[   38.032347] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032362] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032376] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032389] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032402] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032416] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032429] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032443] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032462] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032470] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032484] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032497] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032519] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032532] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032544] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032556] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032568] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032581] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032593] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032605] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032617] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032629] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032641] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032653] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032660] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032667] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032674] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032681] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032688] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032694] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032702] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032708] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   38.032716] cx88[0]: irq aud [0x1000] dn_sync*
[   38.032738] cx88[0]: irq aud [0x1000] dn_sync*
[   40.500005] eth0: no IPv6 routers present
[   47.412231] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  208.044223] cx88[0]: Calling XC5000 callback
[  278.200828] cx88[0]: Calling XC5000 callback
[  442.794922] lo: Disabled Privacy Extensions

```

---

