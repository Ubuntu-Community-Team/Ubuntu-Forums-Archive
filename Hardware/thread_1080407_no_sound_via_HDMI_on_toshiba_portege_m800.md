---
title: "no sound via HDMI on toshiba portege m800"
date: 2009-02-25
forum: Hardware
---

### Post by crashedster on 2009-02-25
Hi!

I tried to plug TV via HDMI on my laptop Toshiba Portege m800 and as a result I see video but audio goes thru my laptop's speakers. I tried to play with different settings in gnome-volume-control but nothing helped.


```

#uname -a
Linux epbyminw1962h 2.6.28-8-server #24-Ubuntu SMP Wed Feb 18 19:58:05 UTC 2009 i686 GNU/Linux

```

```

# lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
08:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```

```

# cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf4800000 irq 22

```

```

# aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, Conexant Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

```

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

# cat /proc/asound/card0/codec#1
Codec: Generic 8086 ID 2802
Address: 1
Vendor Id: 0x80862802
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6211: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
Node 0x03 [Pin Complex] wcaps 0x40739d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x80]
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02

```

```

modinfo snd-hda-intel
filename:       /lib/modules/2.6.28-8-server/kernel/sound/pci/hda/snd-hda-intel.ko
description:    Intel HDA driver
license:        GPL
srcversion:     4CF64AD36F111DD0142FC2E
alias:          pci:v00001002d*sv*sd*bc04sc03i00*
alias:          pci:v00006549d00001200sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000BD7sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000BD6sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000BD5sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000BD4sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AC3sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AC2sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AC1sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AC0sv*sd*bc*sc*i*
alias:          pci:v000010DEd000007FDsv*sd*bc*sc*i*
alias:          pci:v000010DEd000007FCsv*sd*bc*sc*i*
alias:          pci:v000010DEd00000777sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000776sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000775sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000774sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Dsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Csv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Bsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Asv*sd*bc*sc*i*
alias:          pci:v000010DEd000003F0sv*sd*bc*sc*i*
alias:          pci:v000010DEd000003E4sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000371sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000026Csv*sd*bc*sc*i*
alias:          pci:v000010B9d00005461sv*sd*bc*sc*i*
alias:          pci:v00001039d00007502sv*sd*bc*sc*i*
alias:          pci:v00001106d00003288sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA48sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA40sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA38sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA30sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA28sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA20sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA18sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA10sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA08sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA00sv*sd*bc*sc*i*
alias:          pci:v00001002d0000970Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000960Fsv*sd*bc*sc*i*
alias:          pci:v00001002d00007919sv*sd*bc*sc*i*
alias:          pci:v00001002d0000793Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00004383sv*sd*bc*sc*i*
alias:          pci:v00001002d0000437Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000811Bsv*sd*bc*sc*i*
alias:          pci:v00008086d00003B56sv*sd*bc*sc*i*
alias:          pci:v00008086d00003A6Esv*sd*bc*sc*i*
alias:          pci:v00008086d00003A3Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Esv*sd*bc*sc*i*
alias:          pci:v00008086d00002911sv*sd*bc*sc*i*
alias:          pci:v00008086d0000284Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000269Asv*sd*bc*sc*i*
alias:          pci:v00008086d000027D8sv*sd*bc*sc*i*
alias:          pci:v00008086d00002668sv*sd*bc*sc*i*
depends:        snd-pcm,snd-page-alloc,snd
vermagic:       2.6.28-8-server SMP mod_unload modversions 686 
parm:           power_save:Automatic power-saving timeout (in second, 0 = disable). (int)
parm:           index:Index value for Intel HD audio interface. (array of int)
parm:           id:ID string for Intel HD audio interface. (array of charp)
parm:           enable:Enable Intel HD audio interface. (array of bool)
parm:           model:Use the given board model. (array of charp)
parm:           position_fix:Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF). (array of int)
parm:           bdl_pos_adj:BDL position adjustment offset. (array of int)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (array of int)
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm:           enable_msi:Enable Message Signaled Interrupt (MSI) (int)
parm:           power_save_controller:Reset controller in power save mode. (bool)

```

Please help me!
Thanks in advance.

---

### Post by Fintan on 2009-06-20
Hello crashedster,
I know this way off topic and I am sorry I cannot help you with that issue.

I just got the same laptop and have a network (wired / wlan) problem that you may be able to help me with.
[http://kubuntuforums.net/forums/index.php?topic=3104627.msg185502#new]("http://http://kubuntuforums.net/forums/index.php?topic=3104627.msg185502#new")

That is me talking to myself and any help would be greatly appreciated.

again sorry I cannot be of assistance.

Thanky in advance

---

