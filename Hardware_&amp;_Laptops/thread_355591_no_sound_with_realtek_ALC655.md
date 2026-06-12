---
title: "no sound with realtek ALC655"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by toketin on 2007-02-07
hi, i have a great problem with my new pc, i have a sound card the "realtek alc655" i've downloaded and compiled the drivers but when i try to run alsamixer to high the volume the shell ansewr this "alsamixer: function snd_ctl_open failed for default: No such file or directory" how can i resolve this problem??

---

### Post by chepotenza on 2008-02-27
I have the same problem, but I suspect no drivers are installed yet on my system. Where did you get the drivers from? I can't find them on the web.Thanks

---

### Post by superprash2003 on 2008-02-29
try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by Yellow Pasque on 2008-02-29
> **chepotenza said:**
> I have the same problem, but I suspect no drivers are installed yet on my system. Where did you get the drivers from? I can't find them on the web.Thanks
Use these scripts:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by sabbath06 on 2008-03-17
I have the same problem. I have an ALC655 onboard sound chip. I installed ubuntu gutsy and have no sound at all. I've followed several guides that people have recommended to no avail. I've also included these listings

Are there some settings that need to be changed in alsamixer perhaps?

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [e0] HyperTransport: MSI Mapping

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0ca8
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0ca8
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0ca8
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0ca8
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0ca8
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] #00 [00fe]
        Capabilities: [fc] #00 [0000]

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0ca8
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0ca8
        Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fe300000-fe3fffff
        Prefetchable memory behind bridge: 00000000fea00000-00000000feafffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fe900000-fe9fffff
        Prefetchable memory behind bridge: 00000000fe800000-00000000fe8fffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fe500000-fe5fffff
        Prefetchable memory behind bridge: 00000000fe400000-00000000fe4fffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2) (prog-if 00 [VGA])
        Subsystem: Foxconn International, Inc. Unknown device 0ca8
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fd000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 30000000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0ca8
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [e0] HyperTransport: MSI Mapping

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0ca8
        Flags: 66MHz, fast devsel, IRQ 7
        I/O ports at fc00 [size=64]
        I/O ports at f800 [size=64]
        Capabilities: [44] Power Management version 2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0ca8
        Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at febff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at febfe000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] Debug port
        Capabilities: [80] Power Management version 2

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f400 [size=16]
        Capabilities: [44] Power Management version 2

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
        Subsystem: Foxconn International, Inc. Unknown device 0ca8
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at e000 [size=16]
        Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fe700000-fe7fffff
        Prefetchable memory behind bridge: fe600000-fe6fffff
        Capabilities: [b8] Subsystem: Gammagraphx, Inc. Unknown device 0000
        Capabilities: [8c] HyperTransport: MSI Mapping

00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0ca8
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        I/O ports at dc00 [size=256]
        I/O ports at d800 [size=256]
        Memory at febfc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
        Subsystem: Foxconn International, Inc. Unknown device 0ca8
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at d400 [size=8]
        Capabilities: [44] Power Management version 2

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel


```

---

### Post by chepotenza on 2008-04-11
Unfortunatly there is no change: I used the scripts advertised in:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)
but nothing happens. Linux doesn't even see any card!

So I'll detail more my situation.

I've got this motherboard:
[http://www.ieiworld.com/en/Product_IPC.asp?model=KINO-690AM2#top](http://www.ieiworld.com/en/Product_IPC.asp?model=KINO-690AM2#top)
which has Realtek ALC655 with AC'97 codec.
This coded is enabled at BIOS.

I run Ubuntu 8.04 with the latest updates and alsa-drivers, alsa-utils and alsa-lib at version 1.0.16 (the latest)

I also tried to both modprobe the modules (either of the two):
```

snd-atiixp
snd-hda-intel

```
because in ubuntu forums they suggest to use the second.
However, when I downloaded the realtek packages (=latest alsa packages + some shell scripts) from this page:
[ftp://66.104.77.130/pc/audio/realtek-linux-audiopack-4.06a.tar.bz2](ftp://66.104.77.130/pc/audio/realtek-linux-audiopack-4.06a.tar.bz2)
they sugegsted to modprobe the atiixp module if the chipset is ATI (ant I think it is) or to modprobe the hda-intel module if the chipset is INTEL.
Nothing happens:

Please help!

Some more info:

alsamixer
```

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

aplay -v
```


ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:564: audio open error: No such file or directory


```

lspci
```

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc SB600 AC97 Audio
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

```

so the Southbridge sees the audio controller, and

lsmod
```

af_packet              23812  2
radeon                124192  0
drm                    82580  1 radeon
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0
ipv6                  267780  16
powernow_k8            16704  1
cpufreq_conservative     8712  0
cpufreq_powersave       2688  0
cpufreq_stats           7104  0
cpufreq_ondemand        9740  1
freq_table              5536  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0
sbs                    15112  0
dock                   11280  0
container               5632  0
sbshc                   7680  1 sbs
video                  19856  0
output                  4736  1 video
battery                14212  0
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0
parport_pc             36260  0
lp                     12324  0
parport                37832  3 ppdev,parport_pc,lp
serio_raw               7940  0
psmouse                40336  0
k8temp                  6656  0
pcspkr                  4224  0
sr_mod                 17956  0
cdrom                  37408  1 sr_mod
evdev                  13056  5
atiixp                  5648  0 [permanent]
i2c_piix4               9612  0
ide_core              113996  1 atiixp
i2c_core               24832  1 i2c_piix4
button                  9232  0
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
ati_agp                 9996  0
agpgart                34760  2 drm,ati_agp
ext3                  136712  1
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0
sd_mod                 30720  3
pata_atiixp             8960  0
pata_acpi               8320  0
usbhid                 31872  0
hid                    38784  1 usbhid
ata_generic             8324  0
ahci                   28420  2
ehci_hcd               37900  0
libata                159344  4 pata_atiixp,pata_acpi,ata_generic,ahci
ohci_hcd               25348  0
scsi_mod              151436  4 sr_mod,sg,sd_mod,libata
usbcore               146028  4 usbhid,ehci_hcd,ohci_hcd
tg3                   116228  0
thermal                16796  0
processor              36872  2 powernow_k8,thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3

```

---

### Post by papaya74 on 2008-05-21
Hello, 

i have 100% the same problem with 100% identical setup: Hardy & mainboard !

Do you have any solution for that problem ?

Best regards, 

Harry

---

### Post by ApUUbunU on 2008-05-26
Me too! (or four...)
I have the same problem in configuring my Realtek ALC655, however, I haven't tried any options, yet, but I will be in the near future :)

Are there any advantages to using a driver for a sound card, as I can currently hear sound. Possibly performance or quality advantages? Perhaps even extra functionality of a sound card?

---

### Post by steveb-uuser on 2008-06-07
Hi, I the same problem, Tried lots of alsamixer settings - no sound at all.
Has anyone fixed this one?
Thanks

---

### Post by 50below on 2008-07-02
same problemo ere :(

---

