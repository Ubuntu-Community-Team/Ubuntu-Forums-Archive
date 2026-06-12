---
title: "CX23880 Tuner settings"
date: 2008-06-30
forum: Hardware
---

### Post by kessaris on 2008-06-30
Hello dear community members!

I've managed to wrestle a japanese laptop from the grips of windows XP home, but now I'm still trying to configure a few of the loose ends.

Now that the touchpad is finally working, it's time to tackle the TV tuner!

Is it is now, the tuner SORT OF WORKS.. I get static basically.. but it seems like the driver is loaded.  I understand I'll need to insert some options into modprobe, but before I start trying everything at random, I'd love to hear what everyone has to say about it!  

Your help is greatly appreciated.  Here are some relevant portions of hwinfo.

```
37: udi = '/org/freedesktop/Hal/devices/pci_14f1_8800_video4linux_0'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/video4linux/video0'
  info.parent = '/org/freedesktop/Hal/devices/pci_14f1_8800'
  info.product = 'UNKNOWN/GENERIC'
  info.udi = '/org/freedesktop/Hal/devices/pci_14f1_8800_video4linux_0'
  video4linux.device = '/dev/video0'
  info.category = 'video4linux'
  linux.hotplug_type = 2 (0x2)
  video4linux.version = '1'
  info.capabilities = { 'video4linux', 'video4linux.video_capture', 'access_control' }
  linux.subsystem = 'video4linux'
  access_control.file = '/dev/video0'
  access_control.type = 'video4linux'
  linux.device_file = '/dev/video0'
  info.callouts.remove = { 'hal-acl-tool --remove-device' }

  38: udi = '/org/freedesktop/Hal/devices/pci_14f1_8800_video4linux'
  info.callouts.add = { 'hal-acl-tool --add-device' }
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/video4linux/vbi0'
  info.parent = '/org/freedesktop/Hal/devices/pci_14f1_8800'
  info.product = 'UNKNOWN/GENERIC'
  info.udi = '/org/freedesktop/Hal/devices/pci_14f1_8800_video4linux'
  video4linux.device = '/dev/vbi0'
  info.category = 'video4linux'
  linux.hotplug_type = 2 (0x2)
  video4linux.version = '1'
  info.capabilities = { 'video4linux', 'video4linux.video_capture', 'access_control' }
  linux.subsystem = 'video4linux'
  access_control.file = '/dev/vbi0'
  access_control.type = 'video4linux'
  linux.device_file = '/dev/vbi0'
  info.callouts.remove = { 'hal-acl-tool --remove-device' }

  85: udi = '/org/freedesktop/Hal/devices/pci_14f1_8800'
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0'
  info.subsystem = 'pci'
  pci.vendor = 'Conexant'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.vendor = 'Conexant'
  info.product = 'CX23880/1/2/3 PCI Video and Audio Decoder'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0'
  pci.product = 'CX23880/1/2/3 PCI Video and Audio Decoder'
  info.udi = '/org/freedesktop/Hal/devices/pci_14f1_8800'
  info.linux.driver = 'cx8800'
  pci.subsys_vendor = 'Sharp corporation'
  pci.product_id = 34816 (0x8800)
  linux.hotplug_type = 2 (0x2)
  pci.vendor_id = 5361 (0x14f1)
  linux.subsystem = 'pci'
  pci.subsys_product_id = 4150 (0x1036)
  pci.subsys_vendor_id = 5053 (0x13bd)
  pci.device_class = 4 (0x4)

 <6>EXT3-fs: mounted filesystem with ordered data mode.
  <6>Linux agpgart interface v0.103
  <6>agpgart: Detected VIA Apollo Pro266 chipset
  <6>agpgart: AGP aperture is 64M @ 0xa0000000
  <6>Yenta: CardBus bridge found at 0000:00:09.0 [13bd:1036]
  <6>Yenta: Using CSCINT to route CSC interrupts to PCI
  <6>Yenta: Routing CardBus interrupts to PCI
  <6>Yenta TI: socket 0000:00:09.0, mfunc 0x010c1202, devctl 0x44
  <6>Linux video capture interface: v2.00
  <6>input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
  <6>ACPI: Power Button (FF) [PWRF]
  <6>input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
  <6>ACPI: Sleep Button (CM) [SBTN]
  <6>input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
  <6>ACPI: Lid Switch [LID]
  <6>cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
  <6>Yenta: ISA IRQ mask 0x0040, PCI irq 10
  <6>Socket status: 30000006
  <6>ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
  <4>cx88[0]: Your board isn't known (yet) to the driver.  You can
  <4>cx88[0]: try to pick one of the existing card configs via
  <4>cx88[0]: card=<n> insmod option.  Updating to the latest
  <4>cx88[0]: version might help as well.
  <4>cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
  <4>cx88[0]:    card=0 -> UNKNOWN/GENERIC
  <4>cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
  <4>cx88[0]:    card=2 -> GDI Black Gold
  <4>cx88[0]:    card=3 -> PixelView
  <4>cx88[0]:    card=4 -> ATI TV Wonder Pro
  <4>cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
  <4>cx88[0]:    card=6 -> AverTV Studio 303 (M126)
  <4>cx88[0]:    card=7 -> MSI TV-@nywhere Master
  <4>cx88[0]:    card=8 -> Leadtek Winfast DV2000
  <4>cx88[0]:    card=9 -> Leadtek PVR 2000
  <4>cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
  <4>cx88[0]:    card=11 -> Prolink PlayTV PVR
  <4>cx88[0]:    card=12 -> ASUS PVR-416
  <4>cx88[0]:    card=13 -> MSI TV-@nywhere
  <4>cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
  <4>cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
  <4>cx88[0]:    card=16 -> KWorld LTV883RF
  <4>cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
  <4>cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
  <4>cx88[0]:    card=19 -> Conexant DVB-T reference design
  <4>cx88[0]:    card=20 -> Provideo PV259
  <4>cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
  <4>cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
  <4>cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
  <4>cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
  <4>cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
  <4>cx88[0]:    card=26 -> IODATA GV/BCTV7E
  <4>cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
  <4>cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
  <4>cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
  <4>cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
  <4>cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
  <4>cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
  <4>cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
  <4>cx88[0]:    card=34 -> ATI HDTV Wonder
  <4>cx88[0]:    card=35 -> WinFast DTV1000-T
  <4>cx88[0]:    card=36 -> AVerTV 303 (M126)
  <4>cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
  <4>cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
  <4>cx88[0]:    card=39 -> KWorld DVB-S 100
  <4>cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
  <4>cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
  <4>cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
  <4>cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
  <4>cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
  <4>cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
  <4>cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
  <4>cx88[0]:    card=47 -> pcHDTV HD5500 HDTV
  <4>cx88[0]:    card=48 -> Kworld MCE 200 Deluxe
  <4>cx88[0]:    card=49 -> PixelView PlayTV P7000
  <4>cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10
  <4>cx88[0]:    card=51 -> WinFast DTV2000 H
  <4>cx88[0]:    card=52 -> Geniatech DVB-S
  <4>cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
  <4>cx88[0]:    card=54 -> Norwood Micro TV Tuner
  <4>cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
  <4>cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
  <4>cx88[0]:    card=57 -> ADS Tech Instant Video PCI
  <4>cx88[0]:    card=58 -> Pinnacle PCTV HD 800i
  <6>cx88[0]: subsystem: 13bd:1036, board: UNKNOWN/GENERIC [card=0,autodetected]
  <6>cx88[0]: TV tuner type -1, Radio tuner type -1

snd_via82xx,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer, Live 0xee9d6000
  video 16016 0 - Live 0xee9a0000
  output 2560 1 video, Live 0xee9c4000
  tuner 34656 0 - Live 0xee9e3000
  tea5767 5828 1 tuner, Live 0xee967000
  tda8290 12036 1 tuner, Live 0xee9d2000
  tuner_xc2028 18896 1 tuner, Live 0xee9cc000
  tda9887 8772 1 tuner, Live 0xee9b5000
  tuner_simple 8328 1 tuner, Live 0xee9b9000
  via_ircc 23316 0 - Live 0xee9bd000
  mt20xx 11592 1 tuner, Live 0xee97d000
  tea5761 4420 1 tuner, Live 0xee99d000
  irda 174076 1 via_ircc, Live 0xefa01000
  crc_ccitt 1728 1 irda, Live 0xee992000
  i2c_prosavage 3200 0 - Live 0xee995000
  battery 9860 0 - Live 0xee997000
  cx8800 27828 0 - Live 0xee981000
  cx88xx 58344 1 cx8800, Live 0xee9a5000
  ac 3908 0 - Live 0xee96a000
  ir_common 32068 1 cx88xx, Live 0xee989000
  i2c_viapro 7380 0 - Live 0xee97a000
  i2c_algo_bit 5508 2 i2c_prosavage,cx88xx, Live 0xee96d000
  button 5776 0 - Live 0xee91b000
  tveeprom 14032 1 cx88xx, Live 0xee94e000
  videodev 30464 3 tuner,cx8800,cx88xx, Live 0xee971000
  v4l1_compat 13316 1 videodev, Live 0xee95b000
  compat_ioctl32 960 1 cx8800, Live 0xee92f000
  v4l2_common 9600 2 tuner,cx8800, Live 0xee957000
  yenta_socket 22412 1 - Live 0xee960000
  rsrc_nonstatic 10496 1 yenta_socket, Live 0xee953000
  via_agp 7872 1 - Live 0xee918000
  agpgart 26416 2 drm,via_agp, Live 0xee927000
  i2c_core 18448 14 tuner,tea5767,tda8290,tuner_xc2028,tda9887,tuner_simple,mt20xx,tea5761,i2c_prosavage,cx88xx,i2c_viapro,i2c_algo_bit,tveeprom,v4l2_common, Live 0xee876000
  pcmcia_core 31440 3 pcmcia,yenta_socket,rsrc_nonstatic, Live 0xee91e000
  videobuf_dma_sg 9988 2 cx8800,cx88xx, Live 0xee90f000
  videobuf_core 14340 3 cx8800,cx88xx,videobuf_dma_sg, Live 0xee8c4000
  btcx_risc 3848 2 cx8800,cx88xx, Live 0xee840000
  ext3 111304 3 - Live 0xee931000
  jbd 33876 1 ext3, Live 0xee8fb000
  mbcache 5888 1 ext3, Live 0xee816000
  sg 29552 0 - Live 0xee906000
  sr_mod 13476 0 - Live 0xee87c000
  cdrom 33120 1 sr_mod, Live 0xee8f1000
  sd_mod 24080 5 - Live 0xee8ea000
  pata_acpi 4480 0 - Live 0xee837000
  ata_generic 5060 0 - Live 0xee834000
  pata_via 8260 4 - Live 0xee872000
  via_rhine 19592 0 - Live 0xee85e000
  mii 4416 1 via_rhine, Live 0xee85b000
  libata 136836 3 pata_acpi,ata_generic,pata_via, Live 0xee8a1000
  scsi_mod 126092 5 sbp2,sg,sr_mod,sd_mod,libata, Live 0xee8ca000
  dock 7308 1 libata, Live 0xee842000
  ehci_hcd 30732 0 - Live 0xee865000
  uhci_hcd 20300 0 - Live 0xee83a000
  usbcore 123504 4 usbhid,ehci_hcd,uhci_hcd, Live 0xee881000
  ohci1394 27632 0 - Live 0xee81b000
  ieee1394 75448 2 sbp2,ohci1394, Live 0xee847000
  thermal 14684 0 - Live 0xee82a000
  processor 21664 2 thermal, Live 0xee823000
  fan 3844 0 - Live 0xee819000
----- /proc/modules end -----
  used irqs: 0,1,2,5,7,8,9,10,11,12,14,15

23: PCI 08.0: 11200 TV Card
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_14f1_8800
  Unique ID: RE4e.VYe4YDjmeKA
  SysFS ID: /devices/pci0000:00/0000:00:08.0
  SysFS BusID: 0000:00:08.0
  Hardware Class: tv card
  Model: "Sharp CX23880/1/2/3 PCI Video and Audio Decoder"
  Vendor: pci 0x14f1 "Conexant"
  Device: pci 0x8800 "CX23880/1/2/3 PCI Video and Audio Decoder"
  SubVendor: pci 0x13bd "Sharp corporation"
  SubDevice: pci 0x1036 
  Revision: 0x05
  Driver: "cx8800"
  Driver Modules: "cx8800"
  Memory Range: 0xf1000000-0xf1ffffff (rw,non-prefetchable)
  IRQ: 5 (246203 events)
  Module Alias: "pci:v000014F1d00008800sv000013BDsd00001036bc04sc00i00"
  Driver Info #0:
    Driver Status: cx8800 is active
    Driver Activation Cmd: "modprobe cx8800"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

This laptop is a SHARP PC-XV70G, a beautiful little piece of Ubuntu hardware, save for the memory card reader, but it would be sweet if the TV tuner could work!

Presently, as I said, it's getting static in the image and no audio.  The inputs are all listed as 'composite' and channel scanning does not work.

Much obliged, and thanks in advance for any suggestions!  It's a great pleasure to be part of this wonderful ubuntu community!

---

### Post by kessaris on 2008-07-01
OK, well a major update but a remaining minor annoyance!

This is a CX23880 card.. when in doubt, use the TV wonder driver! 

That should be the first sentence in the video4linux documentation.

To get the video working on an unsupported card, why don't you try 

```
echo "options cx88xx card=4" >> /etc/modules.conf
``` 

or

```
echo "options cx88xx card=4" >> /etc/modprobe.d/options
``` 

inserting this option directly into your modprobe.d settings.

It seems to work like a charm, but unfortunately, the sound still doesn't work.

I'll post an lspci once I get back to Linux, but any suggestions would be incredibly well appreciated!

---

### Post by Pizbit on 2008-11-06
You sir. Are a god.

THANK YOU FOR SHOWING ON GOOGLE :D

---

### Post by kessaris on 2008-11-06
So I guess you have a CX23880 tuner?
..

Yea, CX23880 is the new standard I guess.
but how about your audio?  is it recognized by the kernel?
What happens when you do lspci?

---

### Post by tanis143 on 2009-01-15
I have the same issue. I have an v-stream xpert 2000pro video capture card (no tuner, just a a/v input). I get video fine through XawTV and TVTime, but no audio. The input on the card is a dongle that has an s-video, coaxial video right and left coaxial audio and a audio cord that connects to the line in on the sound card. I've hooked my speakers directly to the line out of the vid cap card and I get no audio. I know the card works because before I switched to linux I recorded some stuff off a vcr.

 01:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (5000ns min, 13750ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: cx8800
	Kernel modules: cx8800

Any suggestions?

---

### Post by Astinsan on 2009-04-10
see if it shows up when you type ```
lspci -v | grep -i audio
```

should be the only conexant cx238800 series

---

### Post by kessaris on 2009-04-12
There's just no audio device showing up at all.
The video works OK though.

---

### Post by wingnux on 2009-04-13
Here's mine:
> 
wingnux@wingnux-desktop:~$ lspci -v | grep -i audio
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
01:05.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)

EDIT: Problem solved!

On the terminal I've typed "sudo gedit /etc/modprobe.d/plTV" and then entered the following line "options cx88xx card=27 tuner=65 i2c_scan=1", saved, rebooted and the card started working just fine with tvtime! =)

Note that the card and tuner values may change for your card, mine's a Pixelview PlayTV Pro Ultra.

---

### Post by bravebug on 2010-03-13
Hi, guys. I have Pinnacle PCTV pro card on cx23880 chip. It work after install xc3028-firware. But no sound. I use ArchLinux, not Ubuntu, but I want to have help.
What I should to do to have sound work?
```

lspci | grep CX23880
04:00.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
04:00.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
04:00.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

```

---

### Post by Gerard08 on 2010-03-20
I have the same TV card, running 9.10. If you have Gnome Alsa Mixer installed you can check off the IEC 958 default PCM, and make sure none of the inputs are muted. Also make sure the C88x playback is turned up and capture is checked. Don;t forget to check the "Sound" admin.in System.

---

### Post by markkingfw on 2010-04-15
I have a cx23885 tuner and I can't get it to work under 9.10, I see alot of great information here but its over my head. Is there a step by step way someone could walk me through to install of drivers and setting up/edting. Its the only thing I can not get working under ubuntu 9.10 and I seriously want out from under windows.

thanks

markkingfw

---

