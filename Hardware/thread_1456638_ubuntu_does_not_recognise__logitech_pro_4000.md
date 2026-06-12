---
title: "ubuntu does not recognise  logitech pro 4000"
date: 2010-04-17
forum: Hardware
---

### Post by kaisoor on 2010-04-17
Hi all

hera what i get when type lsusb in terminal 


Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 15d9:0a4c Dexon 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I think my webcam isn't recognised at all ....

and hera what i get when i type dmesg

[    0.991953] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    1.167356] usb 2-1: configuration #1 chosen from 1 choice
[    1.178400] usbcore: registered new interface driver hiddev
[    1.192466] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input4
[    1.192543] generic-usb 0003:15D9:0A4C.0001: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:1d.0-1/input0
[    1.192559] usbcore: registered new interface driver usbhid
[    1.192561] usbhid: v2.6:USB HID core driver
[    1.293701] kjournald starting.  Commit interval 5 seconds
[    1.293709] EXT3-fs: mounted filesystem with ordered data mode.
[    1.408018] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    1.528009] usb 3-2: device descriptor read/64, error -71
[    1.752009] usb 3-2: device descriptor read/64, error -71
[    1.968014] usb 3-2: new full speed USB device using uhci_hcd and address 3
[    2.088010] usb 3-2: device descriptor read/64, error -71
[    2.312011] usb 3-2: device descriptor read/64, error -71
[    2.528019] usb 3-2: new full speed USB device using uhci_hcd and address 4
[    2.936013] usb 3-2: device not accepting address 4, error -71
[    3.048018] usb 3-2: new full speed USB device using uhci_hcd and address 5
[    3.456011] usb 3-2: device not accepting address 5, error -71
[    3.456027] hub 3-0:1.0: unable to enumerate USB device on port 2
[   14.605290] udev: starting version 151
[   14.613520] Adding 1992020k swap on /dev/sda5.  Priority:-1 extents:1 across:1992020k 
[   14.685581] Linux agpgart interface v0.103
[   14.720601] agpgart-intel 0000:00:00.0: Intel G41 Chipset
[   14.721187] agpgart-intel 0000:00:00.0: detected 131068K stolen memory
[   14.808759] type=1505 audit(1271521579.932:2):  operation="profile_load" pid=586 name="/sbin/dhclient3"
[   14.809308] type=1505 audit(1271521579.932:3):  operation="profile_load" pid=586 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.809601] type=1505 audit(1271521579.932:4):  operation="profile_load" pid=586 name="/usr/lib/connman/scripts/dhclient-script"
[   14.843298] parport_pc 00:06: reported by Plug and Play ACPI
[   14.843353] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   14.852144] [drm] Initialized drm 1.1.0 20060810
[   14.854597] Linux video capture interface: v2.00
[   14.858207] intel_rng: FWH not detected
[   14.860437] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   14.867843] EXT3 FS on sda6, internal journal
[   14.882775] lp: driver loaded but no devices found
[   14.893891] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.893896] i915 0000:00:02.0: setting latency timer to 64
[   14.897127] ppdev: user-space parallel port driver
[   14.899345]   alloc irq_desc for 27 on node -1
[   14.899348]   alloc kstat_irqs on node -1
[   14.899357] i915 0000:00:02.0: irq 27 for MSI/MSI-X
[   14.899365] [drm] set up 127M of stolen space
[   14.911456] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   14.911591] cx8800 0000:03:02.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   14.911764] cx88[0]: Your board isn't known (yet) to the driver.  You can
[   14.911765] cx88[0]: try to pick one of the existing card configs via
[   14.911765] cx88[0]: card=<n> insmod option.  Updating to the latest
[   14.911766] cx88[0]: version might help as well.
[   14.911922] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   14.911966] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   14.912032] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   14.912069] cx88[0]:    card=2 -> GDI Black Gold
[   14.912100] cx88[0]:    card=3 -> PixelView
[   14.912131] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   14.912163] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[   14.912198] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[   14.912232] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[   14.912265] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[   14.912299] cx88[0]:    card=9 -> Leadtek PVR 2000
[   14.912331] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[   14.912364] cx88[0]:    card=11 -> Prolink PlayTV PVR
[   14.912396] cx88[0]:    card=12 -> ASUS PVR-416
[   14.912428] cx88[0]:    card=13 -> MSI TV-@nywhere
[   14.912460] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   14.912494] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   14.912533] cx88[0]:    card=16 -> KWorld LTV883RF
[   14.912565] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[   14.912600] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   14.912651] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   14.912703] cx88[0]:    card=20 -> Provideo PV259
[   14.912753] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   14.912804] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[   14.912854] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   14.912905] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[   14.912959] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[   14.913032] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[   14.913082] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[   14.913135] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
[   14.913186] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   14.913238] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   14.913289] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
[   14.913340] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
[   14.913395] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
[   14.913446] cx88[0]:    card=34 -> ATI HDTV Wonder
[   14.913495] cx88[0]:    card=35 -> WinFast DTV1000-T
[   14.913544] cx88[0]:    card=36 -> AVerTV 303 (M126)
[   14.913594] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   14.913646] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   14.913696] cx88[0]:    card=39 -> KWorld DVB-S 100
[   14.913746] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   14.913800] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[   14.913873] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   14.913933] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   14.913998] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   14.914059] cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
[   14.914116] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   14.914175] cx88[0]:    card=47 -> pcHDTV HD5500 HDTV
[   14.914234] cx88[0]:    card=48 -> Kworld MCE 200 Deluxe
[   14.914291] cx88[0]:    card=49 -> PixelView PlayTV P7000
[   14.914347] cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10
[   14.914403] cx88[0]:    card=51 -> WinFast DTV2000 H
[   14.914460] cx88[0]:    card=52 -> Geniatech DVB-S
[   14.914494] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[   14.914515] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   14.914593] cx88[0]:    card=54 -> Norwood Micro TV Tuner
[   14.914645] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
[   14.914721] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   14.914798] cx88[0]:    card=57 -> ADS Tech Instant Video PCI
[   14.914850] cx88[0]:    card=58 -> Pinnacle PCTV HD 800i
[   14.914904] cx88[0]:    card=59 -> DViCO FusionHDTV 5 PCI nano
[   14.914958] cx88[0]:    card=60 -> Pinnacle Hybrid PCTV
[   14.915009] cx88[0]:    card=61 -> Leadtek TV2000 XP Global
[   14.915061] cx88[0]:    card=62 -> PowerColor RA330
[   14.915111] cx88[0]:    card=63 -> Geniatech X8000-MT DVBT
[   14.915163] cx88[0]:    card=64 -> DViCO FusionHDTV DVB-T PRO
[   14.915258] cx88[0]:    card=65 -> DViCO FusionHDTV 7 Gold
[   14.915324] cx88[0]:    card=66 -> Prolink Pixelview MPEG 8000GT
[   14.915383] cx88[0]:    card=67 -> Kworld PlusTV HD PCI 120 (ATSC 120)
[   14.915441] cx88[0]:    card=68 -> Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid
[   14.915500] cx88[0]:    card=69 -> Hauppauge WinTV-HVR4000(Lite) DVB-S/S2
[   14.915558] cx88[0]:    card=70 -> TeVii S460 DVB-S/S2
[   14.915616] cx88[0]:    card=71 -> Omicom SS4 DVB-S/S2 PCI
[   14.915678] cx88[0]:    card=72 -> TBS 8920 DVB-S/S2
[   14.915736] cx88[0]:    card=73 -> TeVii S420 DVB-S
[   14.915788] cx88[0]:    card=74 -> Prolink Pixelview Global Extreme
[   14.915847] cx88[0]:    card=75 -> PROF 7300 DVB-S/S2
[   14.915897] cx88[0]:    card=76 -> SATTRADE ST4200 DVB-S/S2
[   14.915949] cx88[0]:    card=77 -> TBS 8910 DVB-S
[   14.916021] cx88[0]:    card=78 -> Prof 6200 DVB-S
[   14.916070] cx88[0]:    card=79 -> Terratec Cinergy HT PCI MKII
[   14.916122] cx88[0]:    card=80 -> Hauppauge WinTV-IR Only
[   14.916172] cx88[0]:    card=81 -> Leadtek WinFast DTV1800 Hybrid
[   14.916225] cx88[0]:    card=82 -> WinFast DTV2000 H rev. J
[   14.916277] cx88[0]: subsystem: 153b:117a, board: UNKNOWN/GENERIC [card=0,autodetected], frontend(s): 0
[   14.916279] cx88[0]: TV tuner type -1, Radio tuner type -1
[   14.944684] lp0: using parport0 (interrupt-driven).
[   15.071973] fb0: inteldrmfb frame buffer device
[   15.071975] registered panic notifier
[   15.072077] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.072114] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.072129] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.074353] vga16fb: initializing
[   15.074355] vga16fb: mapped to 0xc00a0000
[   15.074358] vga16fb: not registering due to another framebuffer present
[   15.095833] cx88[0]/0: found at 0000:03:02.0, rev: 5, irq: 23, latency: 32, mmio: 0xfb000000
[   15.095845] IRQ 23/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   15.096053] cx88[0]/0: registered device video0 [v4l2]
[   15.096130] cx88[0]/0: registered device vbi0
[   15.097559] cx88[0]/2: cx2388x 8802 Driver Manager
[   15.144145] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   15.178709] Console: switching to colour frame buffer device 128x48
[   15.406020] r8169: eth0: link up
[   15.406027] r8169: eth0: link up
[   15.412811] type=1505 audit(1271521580.536:5):  operation="profile_load" pid=837 name="/usr/share/gdm/guest-session/Xsession"
[   15.414203] type=1505 audit(1271521580.536:6):  operation="profile_replace" pid=838 name="/sbin/dhclient3"
[   15.414758] type=1505 audit(1271521580.536:7):  operation="profile_replace" pid=838 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.415056] type=1505 audit(1271521580.536:8):  operation="profile_replace" pid=838 name="/usr/lib/connman/scripts/dhclient-script"
[   15.418189] type=1505 audit(1271521580.540:9):  operation="profile_load" pid=839 name="/usr/bin/evince"
[   15.426993] type=1505 audit(1271521580.548:10):  operation="profile_load" pid=839 name="/usr/bin/evince-previewer"
[   15.431447] type=1505 audit(1271521580.552:11):  operation="profile_load" pid=839 name="/usr/bin/evince-thumbnailer"
[   16.160361] CPU0 attaching NULL sched-domain.
[   16.160366] CPU1 attaching NULL sched-domain.
[   16.184553] CPU0 attaching sched-domain:
[   16.184556]  domain 0: span 0-1 level MC
[   16.184558]   groups: 0 1
[   16.184562] CPU1 attaching sched-domain:
[   16.184564]  domain 0: span 0-1 level MC
[   16.184566]   groups: 1 0
[   17.632515] usb 3-2: new full speed USB device using uhci_hcd and address 6
[   17.756023] usb 3-2: device descriptor read/64, error -71
[   17.984015] usb 3-2: device descriptor read/64, error -71
[   18.200009] usb 3-2: new full speed USB device using uhci_hcd and address 7
[   18.320007] usb 3-2: device descriptor read/64, error -71
[   18.544009] usb 3-2: device descriptor read/64, error -71
[   18.760008] usb 3-2: new full speed USB device using uhci_hcd and address 8
[   19.168016] usb 3-2: device not accepting address 8, error -71
[   19.280014] usb 3-2: new full speed USB device using uhci_hcd and address 9
[   19.688009] usb 3-2: device not accepting address 9, error -71
[   19.688016] hub 3-0:1.0: unable to enumerate USB device on port 2
[   19.799659] CPU0 attaching NULL sched-domain.
[   19.799664] CPU1 attaching NULL sched-domain.
[   19.812564] CPU0 attaching sched-domain:
[   19.812568]  domain 0: span 0-1 level MC
[   19.812570]   groups: 0 1
[   19.812575] CPU1 attaching sched-domain:
[   19.812576]  domain 0: span 0-1 level MC
[   19.812578]   groups: 1 0
[   26.068028] eth0: no IPv6 routers present
[  344.724033] usb 3-2: new full speed USB device using uhci_hcd and address 10
[  344.844028] usb 3-2: device descriptor read/64, error -71
[  345.068033] usb 3-2: device descriptor read/64, error -71
[  345.284024] usb 3-2: new full speed USB device using uhci_hcd and address 11
[  345.404024] usb 3-2: device descriptor read/64, error -71
[  345.628038] usb 3-2: device descriptor read/64, error -71
[  345.844032] usb 3-2: new full speed USB device using uhci_hcd and address 12
[  346.252028] usb 3-2: device not accepting address 12, error -71
[  346.364032] usb 3-2: new full speed USB device using uhci_hcd and address 13
[  346.772028] usb 3-2: device not accepting address 13, error -71
[  346.772050] hub 3-0:1.0: unable to enumerate USB device on port 2
[  367.208045] usb 2-1: USB disconnect, address 2
[  370.520032] usb 2-1: new low speed USB device using uhci_hcd and address 3
[  370.695271] usb 2-1: configuration #1 chosen from 1 choice
[  370.714518] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input6
[  370.714679] generic-usb 0003:15D9:0A4C.0002: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:1d.0-1/input0
[  370.932025] usb 3-2: new full speed USB device using uhci_hcd and address 14
[  371.052014] usb 3-2: device descriptor read/64, error -71
[  371.276039] usb 3-2: device descriptor read/64, error -71
[  371.492024] usb 3-2: new full speed USB device using uhci_hcd and address 15
[  371.612036] usb 3-2: device descriptor read/64, error -71
[  371.836029] usb 3-2: device descriptor read/64, error -71
[  372.052036] usb 3-2: new full speed USB device using uhci_hcd and address 16
[  372.460029] usb 3-2: device not accepting address 16, error -71
[  372.572046] usb 3-2: new full speed USB device using uhci_hcd and address 17
[  372.980033] usb 3-2: device not accepting address 17, error -71
[  372.980050] hub 3-0:1.0: unable to enumerate USB device on port 2
[  785.131936] ISO 9660 Extensions: Microsoft Joliet Level 3
[  785.160994] ISO 9660 Extensions: RRIP_1991A
[ 1017.641525] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1017.641560] ISO 9660 Extensions: RRIP_1991A
[ 3780.468033] usbcore: registered new interface driver uvcvideo
[ 3780.468038] USB Video Class driver (v0.1.0)
[ 3822.152039] usb 3-2: new full speed USB device using uhci_hcd and address 18
[ 3822.272035] usb 3-2: device descriptor read/64, error -71
[ 3822.496031] usb 3-2: device descriptor read/64, error -71
[ 3822.712028] usb 3-2: new full speed USB device using uhci_hcd and address 19
[ 3822.832027] usb 3-2: device descriptor read/64, error -71
[ 3823.056028] usb 3-2: device descriptor read/64, error -71
[ 3823.272038] usb 3-2: new full speed USB device using uhci_hcd and address 20
[ 3823.684019] usb 3-2: device not accepting address 20, error -71
[ 3823.796027] usb 3-2: new full speed USB device using uhci_hcd and address 21
[ 3824.204528] usb 3-2: device not accepting address 21, error -71
[ 3824.204552] hub 3-0:1.0: unable to enumerate USB device on port 2
[ 4070.420524] usb 3-2: new full speed USB device using uhci_hcd and address 22
[ 4070.540025] usb 3-2: device descriptor read/64, error -71
[ 4070.764034] usb 3-2: device descriptor read/64, error -71
[ 4070.980024] usb 3-2: new full speed USB device using uhci_hcd and address 23
[ 4071.100022] usb 3-2: device descriptor read/64, error -71
[ 4071.324038] usb 3-2: device descriptor read/64, error -71
[ 4071.540041] usb 3-2: new full speed USB device using uhci_hcd and address 24
[ 4071.948022] usb 3-2: device not accepting address 24, error -71
[ 4072.060027] usb 3-2: new full speed USB device using uhci_hcd and address 25
[ 4072.468031] usb 3-2: device not accepting address 25, error -71
[ 4072.468054] hub 3-0:1.0: unable to enumerate USB device on port 2


any help ????????

---

### Post by kaisoor on 2010-04-18
i forget to say that i am uing ubuntu 10.04

---

### Post by wilee-nilee on 2010-04-18
So Looking on Google with logitech pro 4000 ubuntu these hits come up. There is only one other UF thread shown on the first page and is a little old but might be worth looking at, to understand what is going on.
[http://www.google.com/#hl=en&q=+logitech+pro+4000+Ubuntu&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=bcdf8cbbf06dc4f](http://www.google.com/#hl=en&q=+logitech+pro+4000+Ubuntu&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=bcdf8cbbf06dc4f)

Sorry that is the best I can do.

---

### Post by kaisoor on 2010-04-18
thanks wilee-nilee .. your help is appreciated 

I looked for all old threads about this webcam but no solution worked for me ...

thanks again

---

### Post by kaisoor on 2010-04-19
up !!

---

### Post by kaisoor on 2010-04-19
up again

---

### Post by Mark Phelps on 2010-04-19
Quite bumping every few hours -- it's rude!

---

### Post by kaisoor on 2010-04-21
> **Mark Phelps said:**
> Quite bumping every few hours -- it's rude!

I am bumping so that who never see my topic could see it ..

thanks for your useful and ( not rude ) reply ...

---

### Post by nicola76b on 2010-05-06
Hi, 
sorry if I speak also if I can't help with your probelm, but I have a question..
Have you got also hauppauge hvr-3000? Does it works?
I've setting all and spend a lot of time.. My board seems recognized but I can find (w_scan) any channel, so I can't use it..
in ubuntu 9.10 it worked!
Regards,
  Nicola

---

