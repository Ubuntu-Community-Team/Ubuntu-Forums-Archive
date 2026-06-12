---
title: "ieee1394 of my VIA EPIA MII-10000 and ubuntu 7.04"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by renzos on 2007-10-23
I have a problem installing a stereo firewire camera head (made for robots from Videre Design) on my ubuntu 7.04

Following the linux drivers installation instructions, the section that speaks about the ieee1394 controller is here:

[http://www.videredesign.com/vision/linux_drivers.htm](http://www.videredesign.com/vision/linux_drivers.htm)

and I encounter problems when I do:

**$cat /proc/bus/ieee1394/devices | grep Root**

in fact, reading the output: [B]cat: /proc/bus/ieee1394/devices: No file or directory
[/B]
could you help me?

This is the output of some commands that could be helpful for you:

**$ lspci**
00:00.0 Host bridge: VIA Technologies, Inc. VT8623 [Apollo CLE266]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
00:0a.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
00:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03)
02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
[B]
$ dmesg |grep ieee1394[/B]
[   24.144986] ieee1394: Initialized config rom entry `ip1394'
[    9.936000] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0001687300012565]
[    9.936000] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[00406350000134d8]
[   29.304000] ieee1394: raw1394: /dev/raw1394 device initialized
[ 2273.960000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[ 2273.960000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0001687300012565]
[ 2276.444000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[0001687300012565]
[ 2276.444000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023

**$ lsmod**
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
vmnet                  39076  13 
vmmon                 113420  0 
vboxdrv                44552  0 
ipv6                  268704  10 
ppdev                  10116  0 
via                    44160  2 
drm                    81044  3 via
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
ac                      6020  0 
video                  16388  0 
dock                   10268  0 
button                  8720  0 
container               5248  0 
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
af_packet              23816  0 
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  0 
acx                    98564  0 
pcmcia                 39212  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
serio_raw               7940  0 
pcspkr                  4224  0 
via_ircc               27540  0 
psmouse                38920  0 
irda                  201276  1 via_ircc
crc_ccitt               3072  1 irda
i2c_viapro             10132  0 
via_agp                11264  1 
agpgart                35400  2 drm,via_agp
i2c_core               22784  2 i2c_ec,i2c_viapro
yenta_socket           27532  3 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
raw1394                30328  0 
video1394              19672  0 
evdev                  11008  3 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  2 sbp2,libata
generic                 5124  0 [permanent]
floppy                 59524  0 
via82cxxx              10372  0 [permanent]
ehci_hcd               34188  0 
ohci1394               36528  1 video1394
ieee1394              299448  4 sbp2,raw1394,video1394,ohci1394
uhci_hcd               25360  0 
usbcore               134280  4 acx,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

**$ lspci -vvx**
00:00.0 Host bridge: VIA Technologies, Inc. VT8623 [Apollo CLE266]
        Subsystem: VIA Technologies, Inc. Unknown device aa01
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 8
        Region 0: Memory at e6000000 (32-bit, prefetchable) [size=16M]
        Capabilities: <access denied>
00: 06 11 23 31 06 00 30 22 00 00 00 06 00 08 00 00
10: 08 00 00 e6 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 06 11 01 aa
30: 00 00 00 00 a0 00 00 00 00 00 00 00 00 00 00 00

00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP] (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR+
        Latency: 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: e4000000-e5ffffff
        Prefetchable memory behind bridge: e0000000-e3ffffff
        Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR+
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <access denied>
00: 06 11 91 b0 07 01 30 a2 00 00 04 06 00 00 01 00
10: 00 00 00 00 00 00 00 00 00 01 01 00 f0 00 20 a2
20: 00 e4 f0 e5 00 e0 f0 e3 00 00 00 00 00 00 00 00
30: 00 00 00 00 80 00 00 00 00 00 00 00 00 00 0c 00

00:0a.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
        Subsystem: VIA Technologies, Inc. Unknown device aa01
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at e7000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20000000-23fff000 (prefetchable)
        Memory window 1: 24000000-27fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt- PostWrite+
        16-bit legacy interface ports at 0001
00: 80 11 76 04 07 00 10 02 80 00 07 06 00 a8 82 00
10: 00 00 00 e7 dc 00 00 02 00 02 05 b0 00 00 00 20
20: 00 f0 ff 23 00 00 00 24 00 f0 ff 27 00 10 00 00
30: fc 10 00 00 00 14 00 00 fc 14 00 00 05 01 00 05
40: 06 11 01 aa 01 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:0a.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
        Subsystem: VIA Technologies, Inc. Unknown device aa01
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168
        Interrupt: pin B routed to IRQ 5
        Region 0: Memory at e7005000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 28000000-2bfff000 (prefetchable)
        Memory window 1: 2c000000-2ffff000
        I/O window 0: 00001800-000018ff
        I/O window 1: 00001c00-00001cff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001
00: 80 11 76 04 07 00 10 02 80 00 07 06 00 a8 82 00
10: 00 50 00 e7 dc 00 00 02 00 06 09 b0 00 00 00 28
20: 00 f0 ff 2b 00 00 00 2c 00 f0 ff 2f 00 18 00 00
30: fc 18 00 00 00 1c 00 00 fc 1c 00 00 09 02 80 05
40: 06 11 01 aa 01 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Unknown device 3044:df03
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (8000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at e700a000 (32-bit, non-prefetchable) [size=2K]
        Region 1: I/O ports at b000 [size=128]
        Capabilities: <access denied>
00: 06 11 44 30 07 00 10 02 80 10 00 0c 08 20 00 00
10: 00 a0 00 e7 01 b0 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 44 30 03 df
30: 00 00 00 00 50 00 00 00 00 00 00 00 09 01 00 20

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. Unknown device aa01
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 5
        Region 4: I/O ports at b400 [size=32]
        Capabilities: <access denied>
00: 06 11 38 30 07 00 10 02 80 00 03 0c 08 20 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 01 b4 00 00 00 00 00 00 00 00 00 00 06 11 01 aa
30: 00 00 00 00 80 00 00 00 00 00 00 00 05 01 00 00

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. Unknown device aa01
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin B routed to IRQ 5
        Region 4: I/O ports at b800 [size=32]
        Capabilities: <access denied>
00: 06 11 38 30 07 00 10 02 80 00 03 0c 08 20 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 01 b8 00 00 00 00 00 00 00 00 00 00 06 11 01 aa
30: 00 00 00 00 80 00 00 00 00 00 00 00 05 02 00 00

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. Unknown device aa01
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin C routed to IRQ 5
        Region 4: I/O ports at bc00 [size=32]
        Capabilities: <access denied>
00: 06 11 38 30 07 00 10 02 80 00 03 0c 08 20 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 01 bc 00 00 00 00 00 00 00 00 00 00 06 11 01 aa
30: 00 00 00 00 80 00 00 00 00 00 00 00 05 03 00 00

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin D routed to IRQ 5
        Region 0: Memory at e700b000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
00: 06 11 04 31 17 00 10 02 82 20 03 0c 08 20 00 00
10: 00 b0 00 e7 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 06 11 04 31
30: 00 00 00 00 80 00 00 00 00 00 00 00 05 04 00 00

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
        Subsystem: VIA Technologies, Inc. Unknown device aa01
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>
00: 06 11 77 31 87 00 10 02 00 00 01 06 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 06 11 01 aa
30: 00 00 00 00 c0 00 00 00 00 00 00 00 00 00 00 00

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: VIA Technologies, Inc. Unknown device aa01
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 5
        Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        Region 4: I/O ports at c000 [size=16]
        Capabilities: <access denied>
00: 06 11 71 05 07 00 90 02 06 8a 01 01 00 20 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 01 c0 00 00 00 00 00 00 00 00 00 00 06 11 01 aa
30: 00 00 00 00 c0 00 00 00 00 00 00 00 ff 01 00 00

01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03) (prog-if 00 [VGA])
        Subsystem: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min)
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Region 1: Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at e5000000 [disabled] [size=64K]
        Capabilities: <access denied>
00: 06 11 22 31 07 00 30 02 03 00 00 03 00 20 00 00
10: 08 00 00 e0 00 00 00 e4 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 06 11 22 31
30: 00 00 00 00 60 00 00 00 00 00 00 00 05 01 02 00

02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
        Subsystem: D-Link System Inc DWL-G650+ AirPlusG+ CardBus Wireless LAN
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at 24020000 (32-bit, non-prefetchable) [size=8K]
        Region 1: Memory at 24000000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: <access denied>
00: 4c 10 66 90 06 00 10 02 00 00 80 02 00 40 00 00
10: 00 00 02 24 00 00 00 24 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 02 1c 00 00 86 11 05 3b
30: 00 00 00 00 40 00 00 00 00 00 00 00 05 01 00 00

---

