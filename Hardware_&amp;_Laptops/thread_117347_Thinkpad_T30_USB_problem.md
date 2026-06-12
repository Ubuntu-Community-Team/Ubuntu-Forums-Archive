---
title: "Thinkpad T30 USB problem"
date: 2006-01-14
forum: Hardware &amp; Laptops
---

### Post by mikebern on 2006-01-14
I am trying to setup a thinkpad using breezy

The problem I am having is with the usb ports and a printer. The printer is HP P1100.

The thinkpad is connected to a docking station and the usb ports are on the back of the docking station. I get the follow when trying to connect a device to the usb ports.

usb 1-1: new full speed USB device using uhci_hcd and address 6[4297088.284000] usb 1-1: device descriptor read/64, error -71
[4297088.457000] usb 1-1: device descriptor read/64, error -71
[4297088.620000] usb 1-1: new full speed USB device using uhci_hcd and address 7[4297088.693000] usb 1-1: device descriptor read/64, error -71
[4297088.867000] usb 1-1: device descriptor read/64, error -71
[4297089.030000] usb 1-1: new full speed USB device using uhci_hcd and address 8[4297089.438000] usb 1-1: device not accepting address 8, error -71
[4297089.500000] usb 1-1: new full speed USB device using uhci_hcd and address 9[4297089.908000] usb 1-1: device not accepting address 9, error -71

lsusb shows:
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

dmesg for usb section:
[4294677.696000] swsusp: Suspend partition has wrong signature?
[4294677.728000] usbcore: registered new driver usbfs
[4294677.728000] usbcore: registered new driver hub
[4294677.729000] USB Universal Host Controller Interface driver v2.2
[4294677.730000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294677.730000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294677.730000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294677.730000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801CA/CAM USB (Hub #1)
[4294677.792000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294677.792000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[4294677.792000] hub 1-0:1.0: USB hub found
[4294677.792000] hub 1-0:1.0: 2 ports detected
[4294677.795000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294677.795000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294677.795000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294677.795000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801CA/CAM USB (Hub #2)
[4294677.857000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294677.857000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[4294677.857000] hub 2-0:1.0: USB hub found
[4294677.857000] hub 2-0:1.0: 2 ports detected
[4294677.860000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294677.860000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294677.860000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801CA/CAM USB (Hub #3)
[4294677.922000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294677.922000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[4294677.922000] hub 3-0:1.0: USB hub found
[4294677.922000] hub 3-0:1.0: 2 ports detected
[4294677.998000] usb 1-1: new full speed USB device using uhci_hcd and address 2[4294678.062000] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI


lspci:
0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 96
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: e8000000-efffffff

0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02) (prog-if 00 [UHCI])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1800 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #2) (rev 02) (prog-if 00 [UHCI])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1820 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #3) (rev 02) (prog-if 00 [UHCI])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1840 [size=32]

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=0f, sec-latency=64
        I/O behind bridge: 00004000-00009fff
        Memory behind bridge: d0200000-dfffffff
        Prefetchable memory behind bridge: f0000000-f80fffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at 1860 [size=16]
        Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.3 SMBus: Intel Corp. 82801CA/CAM SMBus Controller (rev 02)
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: medium devsel, IRQ 11
        I/O ports at 1880 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)
        Subsystem: IBM ThinkPad T30
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]

0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: medium devsel, IRQ 11
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] (prog-if 00 [VGA])
        Subsystem: IBM ThinkPad T30
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 3000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

0000:02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
        Subsystem: IBM ThinkPad T30/T40
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=12, subordinate=15, sec-latency=176
        Memory window 0: 20400000-207ff000 (prefetchable)
        Memory window 1: 20800000-20bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
        Subsystem: IBM ThinkPad T30/T40
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 51000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=16, subordinate=19, sec-latency=176
        Memory window 0: 20c00000-20fff000 (prefetchable)
        Memory window 1: 21000000-213ff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        16-bit legacy interface ports at 0001

0000:02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
        Subsystem: Intel Corp. Wireless 802.11b MiniPCI Adapter
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f8000000 (32-bit, prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:02:03.0 PCI bridge: Texas Instruments PCI2032 PCI Docking Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, medium devsel, latency 64
        Bus: primary=02, secondary=09, subordinate=0f, sec-latency=68
        I/O behind bridge: 00000000-00000fff
        Memory behind bridge: 00000000-000fffff
        Prefetchable memory behind bridge: 00000000-000fffff
        Capabilities: <available only to root>

0000:02:08.0 Ethernet controller: Intel Corp. 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at d0200000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 8000 [size=64]
        Capabilities: <available only to root>

0000:09:01.0 IDE interface: Silicon Image, Inc. (formerly CMD Technology Inc) PCI0648 (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Silicon Image, Inc. (formerly CMD Technology Inc) PCI0648
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 9020 [size=8]
        I/O ports at 9014 [size=4]
        I/O ports at 9018 [size=8]
        I/O ports at 9010 [size=4]
        I/O ports at 9000 [size=16]
        Capabilities: <available only to root>

0000:09:02.0 CardBus bridge: Texas Instruments PCI1420
        Subsystem: IBM: Unknown device 0148
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 52000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=09, secondary=0a, subordinate=0d, sec-latency=176
        Memory window 0: 21400000-217ff000 (prefetchable)
        Memory window 1: 21800000-21bff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

0000:09:02.1 CardBus bridge: Texas Instruments PCI1420
        Subsystem: IBM: Unknown device 0148
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 53000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=09, secondary=0e, subordinate=11, sec-latency=176
        Memory window 0: 21c00000-21fff000 (prefetchable)
        Memory window 1: 22000000-223ff000
        I/O window 0: 00005800-000058ff
        I/O window 1: 00005c00-00005cff
        16-bit legacy interface ports at 0001

lsmod
Module                  Size  Used by
nfs                   208008  1
lockd                  63784  1 nfs
sunrpc                137796  3 nfs,lockd
vmnet                  32068  15
vmmon                 178316  3
rfcomm                 38460  0
l2cap                  24740  5 rfcomm
bluetooth              48356  4 rfcomm,l2cap
speedstep_ich           5164  0
speedstep_lib           4228  1 speedstep_ich
cpufreq_userspace       4316  1
cpufreq_stats           5252  0
freq_table              4388  2 speedstep_ich,cpufreq_stats
cpufreq_powersave       1696  0
cpufreq_ondemand        6044  0
cpufreq_conservative     6948  0
pcmcia                 26568  8
radeon                 78080  1
drm                    64884  2 radeon
video                  15748  0
tc1100_wmi              6692  0
sony_acpi               5324  0
pcc_acpi               11104  0
ibm_acpi               17684  0
hotkey                  9284  0
dev_acpi               11108  0
i2c_acpi_ec             5472  0
i2c_core               21200  1 i2c_acpi_ec
button                  6480  0
battery                 9348  0
container               4384  0
ac                      4708  0
ipv6                  251232  6
af_packet              21768  2
irtty_sir               8512  0
sir_dev                18444  1 irtty_sir
irda                  187612  2 irtty_sir,sir_dev
crc_ccitt               1984  1 irda
floppy                 59124  0
rtc                    12344  0
pcspkr                  3396  0
hostap_pci             54768  0
hostap                118408  1 hostap_pci
orinoco_pci             7008  0
orinoco                39820  1 orinoco_pci
hermes                  7264  2 orinoco_pci,orinoco
yenta_socket           25292  4
rsrc_nonstatic         13376  1 yenta_socket
pcmcia_core            49348  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           33248  2
snd_ac97_codec         83932  1 snd_intel8x0
snd_pcm_oss            52704  0
snd_mixer_oss          19296  2 snd_pcm_oss
snd_pcm                88840  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  1 snd_pcm
snd                    54884  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9600  2 snd
snd_page_alloc         10600  2 snd_intel8x0,snd_pcm
tpm_atmel               5536  0
tpm_nsc                 6656  0
tpm                     9888  2 tpm_atmel,tpm_nsc
hw_random               5172  0
shpchp                 96996  0
pci_hotplug            27508  1 shpchp
intel_agp              23164  1
agpgart                34792  2 drm,intel_agp
dm_mod                 57692  1
tsdev                   7776  0
evdev                   9664  0
psmouse                30116  0
mousedev               11616  2
parport_pc             35236  1
lp                     12292  0
parport                35912  2 parport_pc,lp
md                     45584  0
ext3                  136264  1
jbd                    54776  1 ext3
mbcache                 9252  1 ext3
thermal                13000  0
processor              22812  1 thermal
fan                     4484  0
e100                   34976  0
mii                     5696  1 e100
uhci_hcd               31184  0
usbcore               118044  2 uhci_hcd
ide_cd                 41572  1
cdrom                  39616  1 ide_cd
ide_disk               18464  3
ide_generic             1376  0
cmd64x                 11964  1
piix                   10372  1
ide_core              138772  5 ide_cd,ide_disk,ide_generic,cmd64x,piix
unix                   26896  632
vesafb                  7992  0
capability              4712  0
commoncap               6816  1 capability
vga16fb                12584  1
vgastate                9664  1 vga16fb
softcursor              2272  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3872  2 vesafb,vga16fb
cfbcopyarea             4608  2 vesafb,vga16fb
fbcon                  38496  73
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon

---

### Post by 23meg on 2006-01-15
What exactly is your problem; are the USB devices that you plug in not recognized? Do you have USB ports on the laptop itself, and if so, do those work?

---

### Post by mikebern on 2006-01-17
No devices are usable on the usb ports. 

The ports are on the back of the docking station. I can not get to the ports on the back of the laptop. Will try sometime this weekend when I can take the laptop of the docking station.

---

### Post by Lambert on 2006-01-17
Look through these links.

[http://thinkwiki.org/wiki/Docking_Solutions](http://thinkwiki.org/wiki/Docking_Solutions)

[http://thinkwiki.org/wiki/Problem_with_Dock_USB_Ports](http://thinkwiki.org/wiki/Problem_with_Dock_USB_Ports)

---

### Post by mikebern on 2006-01-26
Since this look to be a common problem I install a ehci_hcd pci card into the docking station (type 2631) and now things work from the docking station. This looks to be the best way around the problem.

This still leaves me a system that can be removed from the docking station without
having wire attached to the thinkpad. It does cost the PCI slot in the docking station but I have no other use for the slot.

Problem worked around but not fixed.
The usb ports on the docking station are useless but the pci card allow me have usb port while docked and not wire to the thinkpad.

---

### Post by dunder on 2007-09-24
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/144210](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/144210)

---

### Post by rybu on 2007-09-24
I've got two thinkpad t30's running Ubuntu 7.04 and everything runs fine there, although I don't have a docking station.  A docking station should arrive for my t61p soon... looking forward to seeing if that works.

---

### Post by dunder on 2007-09-25
Without docking station Ubuntu works perfectly with IBM Thinkpads. I've resolved dock PCI problem, but still got some crappy errors from yenta_socket module when PCMCIA USB card is connected to dock slots.

0e:00.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0e:00.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0e:00.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
0e:00.4 FireWire (IEEE 1394): ALi Corporation M5253 P1394 OHCI 1.1 Controller

it sometimes works and sometimes shows errors like:

Sep 22 13:11:48 dunder kernel: [   20.380000] handlers:
Sep 22 13:11:48 dunder kernel: [   20.380000] [acpi_irq+0/20] (acpi_irq+0x0/0x14)
Sep 22 13:11:48 dunder kernel: [   20.380000] [<f8baef00>] (usb_hcd_irq+0x0/0x60 [usbcore])
Sep 22 13:11:48 dunder kernel: [   20.380000] [<f8ddc570>] (ath_intr+0x0/0xc40 [ath_pci])
Sep 22 13:11:48 dunder kernel: [   20.380000] [<f8cc88b0>] (yenta_interrupt+0x0/0xe0 [yenta_socket])
Sep 22 13:11:48 dunder kernel: [   20.380000] [<f8cc88b0>] (yenta_interrupt+0x0/0xe0 [yenta_socket])
Sep 22 13:11:48 dunder kernel: [   20.380000] Disabling IRQ #9

---

