---
title: "Low Graphics Mode on Vaio"
date: 2008-05-17
forum: Hardware
---

### Post by davisford on 2008-05-17
Hi, I have a Sony Vaio PCG-VX88P.  I used to have Xubuntu 7.04 installed and I recall having this same problem, and I really don't know how I fixed it.  Today, I wiped the disk, and installed Xubuntu 8.04 fresh.  

X will only display at 800x600.  This causes the desktop to have a large black border around it -- as it is not filling up the entire screen.

I have tried 

```
sudo dpgk-reconfigure -phigh xserver-xorg
```

It does not change anything.  It seems to not detect any of my hw, so defaults to generic drivers / monitors.  The relevant sections of xorg.conf are like this:

```

Section "Device"
 Identifier "Configured Video Device"
EndSection

Section "Monitor"
 Identifier "Configured Monitor"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
EndSection

```

I have tried entering my own settings in there to no avail -- usually, I have to do safe boot and restore xorg.conf.

lspci shows this for the graphics controller:

```

00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)

```

Sometimes, after editing xorg.conf, and restarting X, it would say that X is in "Low Graphics Mode" and give me the option to configure via a GUI.  I tried that.  I even tried picking my video card driver (for the Intel 815), and when I apply, it says it will test it -- the screen goes black forever, and I have to do a hard reset, and restore xorg.conf.

The monitor is an XGA 14.1" TFT that supports 1024x768.  I think I also can put safe values in there for H/V sync.  

What else can I try to get this to work?  How can I launch that X configuration manually (the GUI that loads when low graphics mode is detected) -- and any idea why it fails to revert after testing a failed configuration?

Thanks in advance!

Regards,
Davis

---

### Post by davisford on 2008-05-18
As a follow up, I tried the 915resolution tool, but got the following error:

davis@vaio:/etc/X11$ sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.3

Intel chipset detected.  However, 915resolution was unable to
determine the chipset type.
Chipset Id: 11308086
Please report this problem to [email]xxxxxx@yahoo.com[/email]

I sent an email to the address listed (x'd out)

I reconfigured xorg.conf as:

```

Section "Device"
  Identifier "Configured Video Device"
# The i810 driver causes X to fail with blank screen
# Driver "i810"
  Driver "intel"
  BusID "PCI:0:2:0"
EndSection

Section "Monitor"
  Identifier "Configured Monitor"
  DisplaySize 360 270
# These cause X to fail with blank screen
# HorizSync 31.5-90
# VertRefresh 59-75
EndSection

Section "Screen"
  Identifier "Default Screen"
  Monitor "Configured Monitor"
  DefaultDepth 16
  SubSection "Display"
    Depth 1
    Modes "1024x768" "800x600" "640x480"
  EndSubSection
  SubSection "Display"
    Depth 4
    Modes "1024x768" "800x600" "640x480"
  EndSubSection
  SubSection "Display"
    Depth 8
    Modes "1024x768" "800x600" "640x480"
  EndSubSection
  SubSection "Display"
    Depth 16
    Modes "1024x768" "800x600" "640x480"
  EndSubSection
  Device "Configured Video Device"
EndSection

```

From the comments above -- I tried the i810 driver, and it fails with a blank screen.  So I switched it to the "intel" driver.  Oddly enough, this loads X (desktop still too small for screen), but if I do an lsmod, it shows the i810 driver is loaded:

```

davis@vaio:/etc/X11$ lsmod
Module                  Size  Used by
ipv6                  267780  8
af_packet              23812  2
i810                   19968  2
drm                    82580  3 i810
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
sonypi                 23192  0
ppdev                  10372  0
speedstep_ich           6288  0
speedstep_lib           6532  1 speedstep_ich
cpufreq_powersave       2688  0
cpufreq_userspace       5284  0
cpufreq_conservative     8712  0
cpufreq_stats           7104  0
cpufreq_ondemand        9740  1
freq_table              5536  3 speedstep_ich,cpufreq_stats,cpufreq_ondemand
dock                   11280  0
container               5632  0
sbs                    15112  0
sbshc                   7680  1 sbs
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0
parport_pc             36260  0
lp                     12324  0
parport                37832  3 ppdev,parport_pc,lp
loop                   18948  0
wlan_scan_sta          14720  1
ath_rate_sample        14336  1
orinoco_cs             16396  1
orinoco                42772  1 orinoco_cs
hermes                  8448  2 orinoco_cs,orinoco
ath_pci               101024  0
joydev                 13120  0
wlan                  207728  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci
pcmcia                 40876  1 orinoco_cs
snd_intel8x0           35356  1
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0
evdev                  13056  7
battery                14212  0
ac                      6916  0
psmouse                40336  0
serio_raw               7940  0
sony_laptop            35292  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
yenta_socket           27276  5
rsrc_nonstatic         13696  1 yenta_socket
video                  19856  0
output                  4736  1 video
pcmcia_core            40596  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6
snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5
snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0
snd                    56996  13
snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
pcspkr                  4224  0
i2c_i810                5636  0
iTCO_wdt               13092  0
iTCO_vendor_support     4868  1 iTCO_wdt
i2c_algo_bit            7300  1 i2c_i810
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
i2c_core               24832  2 i2c_i810,i2c_algo_bit
intel_agp              25492  1
agpgart                34760  3 drm,intel_agp
ext3                  136712  1
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usb_storage            73664  0
libusual               19108  1 usb_storage
sg                     36880  0
sd_mod                 30720  3
ohci1394               33584  0
pata_acpi               8320  0
e100                   37388  0
mii                     6400  1 e100
ata_generic             8324  0
ieee1394               93752  2 sbp2,ohci1394
uhci_hcd               27024  0
ata_piix               19588  2
usbcore               146028  4 usb_storage,libusual,uhci_hcd
libata                159344  3 pata_acpi,ata_generic,ata_piix
scsi_mod              151436  5 sbp2,usb_storage,sg,sd_mod,libata
thermal                16796  0
processor              36872  2 thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1

```

Here is the full dump of lspci:

```

davis@vaio:/etc/X11$ sudo lspci -vv
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge
and Memory Controller Hub (rev 11)
       Subsystem: Sony Corporation Unknown device 8111
       Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR+ FastB2B-
       Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort+ >SERR- <PERR-
       Latency: 0
       Capabilities: [88] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset
Graphics Controller (CGC) (rev 11) (prog-if 00 [VGA controller])
       Subsystem: Sony Corporation Unknown device 8111
       Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR- FastB2B-
       Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
       Latency: 0
       Interrupt: pin A routed to IRQ 9
       Region 0: Memory at f8000000 (32-bit, prefetchable) [size=64M]
       Region 1: Memory at f4000000 (32-bit, non-prefetchable) [size=512K]
       Capabilities: [dc] Power Management version 2
               Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
               Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
(prog-if 00 [Normal decode])
       Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR+ FastB2B-
       Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
       Latency: 0
       Bus: primary=00, secondary=01, subordinate=09, sec-latency=64
       I/O behind bridge: 00003000-00003fff
       Memory behind bridge: f4100000-f41fffff
       Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- <SERR- <PERR-
       BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-

00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
       Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr-
Stepping- SERR- FastB2B-
       Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
       Latency: 0

00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller
(rev 03) (prog-if 80 [Master])
       Subsystem: Sony Corporation Unknown device 8111
       Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR- FastB2B-
       Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
       Latency: 0
       Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable)
[disabled] [size=8]
       Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable)
[disabled] [size=1]
       Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable)
[disabled] [size=8]
       Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable)
[disabled] [size=1]
       Region 4: I/O ports at 1800 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller
#1 (rev 03) (prog-if 00 [UHCI])
       Subsystem: Sony Corporation Unknown device 8111
       Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR- FastB2B-
       Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
       Latency: 0
       Interrupt: pin D routed to IRQ 9
       Region 4: I/O ports at 1820 [size=32]

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 03)
       Subsystem: Sony Corporation Unknown device 8111
       Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR- FastB2B-
       Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
       Interrupt: pin B routed to IRQ 9
       Region 4: I/O ports at 1810 [size=16]

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller
#1 (rev 03) (prog-if 00 [UHCI])
       Subsystem: Sony Corporation Unknown device 8111
       Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR- FastB2B-
       Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
       Latency: 0
       Interrupt: pin C routed to IRQ 9
       Region 4: I/O ports at 1840 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM
AC'97 Audio Controller (rev 03)
       Subsystem: Sony Corporation Unknown device 8111
       Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR- FastB2B-
       Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
       Latency: 0
       Interrupt: pin B routed to IRQ 9
       Region 0: I/O ports at 1c00 [size=256]
       Region 1: I/O ports at 1880 [size=64]

00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller
(rev 03) (prog-if 00 [Generic])
       Subsystem: Sony Corporation Unknown device 8111
       Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR- FastB2B-
       Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
       Interrupt: pin B routed to IRQ 9
       Region 0: I/O ports at 2400 [size=256]
       Region 1: I/O ports at 2000 [size=128]

01:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A
IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
       Subsystem: Sony Corporation Unknown device 8111
       Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr-
Stepping- SERR+ FastB2B-
       Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
       Latency: 64 (750ns min, 1000ns max), Cache Line Size: 32 bytes
       Interrupt: pin A routed to IRQ 9
       Region 0: Memory at f4105000 (32-bit, non-prefetchable) [size=2K]
       Region 1: Memory at f4100000 (32-bit, non-prefetchable) [size=16K]
       Capabilities: [44] Power Management version 2
               Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
               Status: D0 PME-Enable- DSel=0 DScale=0 PME+

01:02.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 80)
       Subsystem: Sony Corporation Unknown device 8111
       Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR- FastB2B-
       Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
       Latency: 168
       Interrupt: pin A routed to IRQ 9
       Region 0: Memory at f4106000 (32-bit, non-prefetchable) [size=4K]
       Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
       Memory window 0: 20000000-23fff000 (prefetchable)
       Memory window 1: 24000000-27fff000
       I/O window 0: 00003400-000034ff
       I/O window 1: 00003800-000038ff
       BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt- PostWrite+
       16-bit legacy interface ports at 0001

01:05.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus
Controller (rev 01)
       Subsystem: Lucent Technologies Unknown device ab01
       Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR- FastB2B-
       Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
       Latency: 168, Cache Line Size: 128 bytes
       Interrupt: pin A routed to IRQ 9
       Region 0: Memory at f4107000 (32-bit, non-prefetchable) [size=4K]
       Bus: primary=01, secondary=06, subordinate=09, sec-latency=176
       Memory window 0: 28000000-2bfff000 (prefetchable)
       Memory window 1: 2c000000-2ffff000
       I/O window 0: 00003c00-00003cff
       I/O window 1: 00001400-000014ff
       BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt- PostWrite+
       16-bit legacy interface ports at 0001

01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM
Ethernet Controller (rev 03)
       Subsystem: Sony Corporation Unknown device 8111
       Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr-
Stepping- SERR+ FastB2B-
       Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
       Latency: 66 (2000ns min, 14000ns max), Cache Line Size: 32 bytes
       Interrupt: pin A routed to IRQ 9
       Region 0: Memory at f4104000 (32-bit, non-prefetchable) [size=4K]
       Region 1: I/O ports at 3000 [size=64]
       Capabilities: [dc] Power Management version 2
               Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
               Status: D0 PME-Enable- DSel=0 DScale=2 PME-

02:00.0 Ethernet controller: Atheros Communications Inc. AR2413
802.11bg NIC (rev 01)
       Subsystem: Atheros Communications Inc. TP-Link TL-WN510G Wireless
CardBus Adapter
       Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR- FastB2B-
       Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR-
       Latency: 168 (2500ns min, 7000ns max), Cache Line Size: 128 bytes
       Interrupt: pin A routed to IRQ 9
       Region 0: Memory at 24000000 (32-bit, non-prefetchable) [size=64K]
       Capabilities: [44] Power Management version 2
               Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
               Status: D0 PME-Enable- DSel=0 DScale=2 PME-

```

Anyone have an idea on what I could try next?

Any time I issue:

```
sudo dpkg-reconfigure xserver-xorg
```

It does nothing but create a blank xorg.conf file -- it doesn't even ask me questions about my video driver and monitor...it only asks about the keyboard type.

---

### Post by galiel on 2009-01-10
you might want to try running:
```
$ sudo displayconfig-gtk
```
see <[this thread]("http://ubuntuforums.org/archive/index.php/t-791820.html")> for more context.
I had a problem where ubuntu identified my monitor as PnP and allowed only up to 800x600.
When I connected another monitor some other resolutions were available. So I tried to see if there is a way to impose the (actual) capabilities of my monitor and so in displayconfig-gtk I chose generic monitor 1024x768. This added a bunch of extra stuff in xorg.conf under Monitor and Screen and it solved the problem.

good luck...

---

