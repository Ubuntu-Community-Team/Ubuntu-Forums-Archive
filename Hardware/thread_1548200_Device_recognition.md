---
title: "Device recognition"
date: 2010-08-08
forum: Hardware
---

### Post by genoskill on 2010-08-08
I want to put music on a mp3 device, but ubuntu doesnt recognize it. so I did this: [http://ubuntuforums.org/showpost.php?p=3299667&postcount=2]("http://ubuntuforums.org/showpost.php?p=3299667&postcount=2")

[SIZE="1"]Aug  7 11:46:42 genoskill-compaq kernel: [   16.591520] ppdev: user-space parallel port driver
Aug  7 11:46:42 genoskill-compaq kernel: [   16.606622] cfg80211: World regulatory domain updated:
Aug  7 11:46:42 genoskill-compaq kernel: [   16.606630] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug  7 11:46:42 genoskill-compaq kernel: [   16.606634] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  7 11:46:42 genoskill-compaq kernel: [   16.606638] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug  7 11:46:42 genoskill-compaq kernel: [   16.606642] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug  7 11:46:42 genoskill-compaq kernel: [   16.606645] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  7 11:46:42 genoskill-compaq kernel: [   16.606648] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  7 11:46:42 genoskill-compaq kernel: [   16.632557] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x0038, PCI irq 11
Aug  7 11:46:42 genoskill-compaq kernel: [   16.632565] yenta_cardbus 0000:00:0a.0: Socket status: 30000007
Aug  7 11:46:42 genoskill-compaq kernel: [   16.752748] b43legacy-phy0: Broadcom 4306 WLAN found
Aug  7 11:46:42 genoskill-compaq kernel: [   17.013735] Broadcom 43xx-legacy driver loaded [ Features: PLID, Firmware-ID: FW10 ]
Aug  7 11:46:42 genoskill-compaq kernel: [   17.099695] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
Aug  7 11:46:42 genoskill-compaq kernel: [   17.102078] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
Aug  7 11:46:42 genoskill-compaq kernel: [   17.102980] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Aug  7 11:46:42 genoskill-compaq kernel: [   17.103799] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Aug  7 11:46:42 genoskill-compaq kernel: [   17.107528] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Aug  7 11:46:42 genoskill-compaq kernel: [   17.157284] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x2348b3, caps: 0x904713/0x10008
Aug  7 11:46:42 genoskill-compaq kernel: [   17.192541] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
Aug  7 11:46:42 genoskill-compaq kernel: [   17.274609] ALI 5451 0000:00:06.0: enabling device (0005 -> 0007)
Aug  7 11:46:42 genoskill-compaq kernel: [   17.274962] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 5
Aug  7 11:46:42 genoskill-compaq kernel: [   17.274973] ALI 5451 0000:00:06.0: PCI INT A -> Link[LNK7] -> GSI 5 (level, low) -> IRQ 5
Aug  7 11:46:42 genoskill-compaq kernel: [   17.314197] EXT4-fs (sda4): mounted filesystem with ordered data mode
Aug  7 11:46:42 genoskill-compaq kernel: [   17.372449] EXT4-fs (sda6): mounted filesystem with ordered data mode
Aug  7 11:46:43 genoskill-compaq kernel: [   18.332143] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
Aug  7 11:46:43 genoskill-compaq kernel: [   18.408376] eth0: DSPCFG accepted after 0 usec.
Aug  7 11:46:43 genoskill-compaq kernel: [   18.408388] eth0: link up.
Aug  7 11:46:43 genoskill-compaq kernel: [   18.408400] eth0: Setting full-duplex based on negotiated link capability.
Aug  7 11:46:44 genoskill-compaq kernel: [   19.036238] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
Aug  7 11:46:45 genoskill-compaq kernel: [   20.136138] AC'97 1 does not respond - RESET
Aug  7 11:46:52 genoskill-compaq pulseaudio[1248]: ratelimit.c: 18 events suppressed
Aug  7 11:50:28 genoskill-compaq nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Aug  7 11:50:29 genoskill-compaq nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Aug  7 11:50:29 genoskill-compaq pulseaudio[1519]: ratelimit.c: 18 events suppressed
Aug  7 11:50:32 genoskill-compaq kernel: [  246.924843] UDF-fs: No anchor found
Aug  7 11:50:32 genoskill-compaq kernel: [  246.924851] UDF-fs: Rescanning with blocksize 2048
Aug  7 11:50:32 genoskill-compaq kernel: [  246.933357] UDF-fs: Partition marked readonly; forcing readonly mount
Aug  7 11:50:32 genoskill-compaq kernel: [  246.933850] UDF-fs INFO UDF: Mounting volume 'ARCH_201005', timestamp 2010/05/16 09:54 (1f10)
Aug  7 12:15:53 genoskill-compaq pulseaudio[1519]: ratelimit.c: 54 events suppressed
Aug  7 12:16:14 genoskill-compaq pulseaudio[1519]: ratelimit.c: 58 events suppressed
Aug  7 12:16:44 genoskill-compaq pulseaudio[1519]: last message repeated 2 times
Aug  7 12:17:39 genoskill-compaq pulseaudio[1519]: ratelimit.c: 58 events suppressed
Aug  7 12:18:05 genoskill-compaq pulseaudio[1519]: ratelimit.c: 58 events suppressed
Aug  7 12:19:14 genoskill-compaq pulseaudio[1519]: last message repeated 3 times
Aug  7 12:25:26 genoskill-compaq rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="741" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Aug  7 12:28:42 genoskill-compaq pulseaudio[1519]: ratelimit.c: 112 events suppressed
Aug  7 12:28:56 genoskill-compaq pulseaudio[1519]: ratelimit.c: 54 events suppressed
Aug  7 13:07:02 genoskill-compaq pulseaudio[1519]: ratelimit.c: 58 events suppressed
Aug  7 13:07:23 genoskill-compaq pulseaudio[1519]: ratelimit.c: 54 events suppressed
Aug  7 13:25:33 genoskill-compaq pulseaudio[2953]: ratelimit.c: 18 events suppressed
Aug  7 13:25:42 genoskill-compaq nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Aug  7 13:25:43 genoskill-compaq pulseaudio[3057]: ratelimit.c: 18 events suppressed
Aug  7 13:25:44 genoskill-compaq nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Aug  7 18:36:34 genoskill-compaq kernel: [24609.352003] plugin-containe[4465] general protection ip:7c14df sp:ff13cc38 error:0 in libc-2.11.1.so[797000+153000]
Aug  7 21:51:36 genoskill-compaq gnome-screensaver-dialog: pam_sm_authenticate: Called
Aug  7 21:51:36 genoskill-compaq gnome-screensaver-dialog: pam_sm_authenticate: username = [genoskill]
Aug  7 22:45:37 genoskill-compaq kernel: [39552.256112] usb 1-3: new high speed USB device using ehci_hcd and address 4
Aug  7 22:45:37 genoskill-compaq kernel: [39552.748101] usb 1-3: new high speed USB device using ehci_hcd and address 6
Aug  7 22:45:38 genoskill-compaq kernel: [39553.056112] usb 1-3: new high speed USB device using ehci_hcd and address 7
Aug  7 22:45:38 genoskill-compaq kernel: [39553.366588] usb 1-3: new high speed USB device using ehci_hcd and address 8
Aug  7 22:45:38 genoskill-compaq kernel: [39553.672080] usb 1-3: new high speed USB device using ehci_hcd and address 9
Aug  7 22:45:39 genoskill-compaq kernel: [39553.980153] usb 1-3: new high speed USB device using ehci_hcd and address 10
Aug  7 22:47:04 genoskill-compaq kernel: [39638.976907] usb 1-2: USB disconnect, address 2
Aug  7 22:47:42 genoskill-compaq kernel: [39677.688099] usb 3-2: USB disconnect, address 2
Aug  7 22:47:50 genoskill-compaq kernel: [39685.624100] usb 2-2: new low speed USB device using uhci_hcd and address 2
Aug  7 22:47:51 genoskill-compaq kernel: [39685.799405] usb 2-2: configuration #1 chosen from 1 choice
Aug  7 22:47:51 genoskill-compaq kernel: [39685.834929] input: Genius 4D Scroll Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2:1.0/input/input8
Aug  7 22:47:51 genoskill-compaq kernel: [39685.835336] generic-usb 0003:0458:0056.0002: input,hidraw0: USB HID v1.10 Mouse [Genius 4D Scroll Mouse] on usb-0000:00:0b.0-2/input0
Aug  7 22:48:01 genoskill-compaq kernel: [39696.120148] usb 1-4: new high speed USB device using ehci_hcd and address 12
Aug  7 22:48:01 genoskill-compaq kernel: [39696.428099] usb 1-4: new high speed USB device using ehci_hcd and address 13
Aug  7 22:48:01 genoskill-compaq kernel: [39696.736149] usb 1-4: new high speed USB device using ehci_hcd and address 14
Aug  7 22:48:02 genoskill-compaq kernel: [39697.044109] usb 1-4: new high speed USB device using ehci_hcd and address 15
Aug  7 22:48:02 genoskill-compaq kernel: [39697.352121] usb 1-4: new high speed USB device using ehci_hcd and address 16
Aug  7 22:48:02 genoskill-compaq kernel: [39697.660089] usb 1-4: new high speed USB device using ehci_hcd and address 17
Aug  7 23:39:50 genoskill-compaq kernel: [42805.296122] usb 1-4: new high speed USB device using ehci_hcd and address 18
Aug  7 23:39:50 genoskill-compaq kernel: [42805.604126] usb 1-4: new high speed USB device using ehci_hcd and address 19
Aug  7 23:39:51 genoskill-compaq kernel: [42805.912097] usb 1-4: new high speed USB device using ehci_hcd and address 20
Aug  7 23:39:51 genoskill-compaq kernel: [42806.220114] usb 1-4: new high speed USB device using ehci_hcd and address 21
Aug  7 23:39:51 genoskill-compaq kernel: [42806.528155] usb 1-4: new high speed USB device using ehci_hcd and address 22
Aug  7 23:39:52 genoskill-compaq kernel: [42806.836123] usb 1-4: new high speed USB device using ehci_hcd and address 23
Aug  7 23:42:27 genoskill-compaq kernel: [42962.118455] plugin-containe[4669]: segfault at 0 ip 0243d911 sp b771e5c0 error 4 in libflashplayer.so[1d5e000+b04000]
Aug  7 23:44:41 genoskill-compaq kernel: [43096.168086] usb 1-4: new high speed USB device using ehci_hcd and address 24
Aug  7 23:44:41 genoskill-compaq kernel: [43096.476092] usb 1-4: new high speed USB device using ehci_hcd and address 25
Aug  7 23:44:41 genoskill-compaq kernel: [43096.784107] usb 1-4: new high speed USB device using ehci_hcd and address 26
Aug  7 23:44:42 genoskill-compaq kernel: [43097.092093] usb 1-4: new high speed USB device using ehci_hcd and address 27
Aug  7 23:44:42 genoskill-compaq kernel: [43097.400092] usb 1-4: new high speed USB device using ehci_hcd and address 28
Aug  7 23:44:42 genoskill-compaq kernel: [43097.708100] usb 1-4: new high speed USB device using ehci_hcd and address 29
Aug  7 23:48:34 genoskill-compaq kernel: [43329.236071] usb 1-4: new high speed USB device using ehci_hcd and address 32
Aug  7 23:48:34 genoskill-compaq kernel: [43329.728081] usb 1-4: new high speed USB device using ehci_hcd and address 34
Aug  7 23:48:35 genoskill-compaq kernel: [43330.220132] usb 1-4: new high speed USB device using ehci_hcd and address 36
Aug  7 23:48:35 genoskill-compaq kernel: [43330.528086] usb 1-4: new high speed USB device using ehci_hcd and address 37
Aug  7 23:51:11 genoskill-compaq kernel: [43485.828082] usb 1-4: new high speed USB device using ehci_hcd and address 38
Aug  7 23:51:11 genoskill-compaq kernel: [43486.140080] usb 1-4: new high speed USB device using ehci_hcd and address 39
Aug  7 23:51:12 genoskill-compaq kernel: [43486.816097] usb 1-4: new high speed USB device using ehci_hcd and address 42
Aug  7 23:51:12 genoskill-compaq kernel: [43487.124154] usb 1-4: new high speed USB device using ehci_hcd and address 43
Aug  7 23:52:30 genoskill-compaq kernel: [43565.444095] usb 1-4: new high speed USB device using ehci_hcd and address 46
Aug  7 23:52:31 genoskill-compaq kernel: [43565.936096] usb 1-4: new high speed USB device using ehci_hcd and address 48
Aug  7 23:52:31 genoskill-compaq kernel: [43566.244110] usb 1-4: new high speed USB device using ehci_hcd and address 49
Aug  7 23:52:31 genoskill-compaq kernel: [43566.552100] usb 1-4: new high speed USB device using ehci_hcd and address 50
Aug  7 23:52:32 genoskill-compaq kernel: [43567.044185] usb 1-4: new high speed USB device using ehci_hcd and address 52
[/SIZE]

What could be the problem?
thanks

---

