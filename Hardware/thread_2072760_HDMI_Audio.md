---
title: "HDMI Audio"
date: 2012-10-18
forum: Hardware
---

### Post by declanb on 2012-10-18
i have a HP Pavilion dv6 running Ubuntu 12.04 TLS 64-bit
i cannot get HDMI audio working
it worked previously until i tried fixing my surround sound

declan@DeclansLaptop:~$  cat /proc/asound/cards
 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xf0344000 irq 52
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf0340000 irq 53


if someone could help that would be great

ps...im a noob so i might need more explanation than most

---

### Post by Time Sheep on 2012-10-18
I'm standing with a really similar problem, only it is another card.

Guides everywhere on the internet suggest I try alsaconf, but this command was removed in 2006 or whatever. So.. Dead end... What I am I supposed to do now?

Info:
# aplay -l
```


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```# aplay -L
```


default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Intel
    HDA Intel, ALC1200 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, HDMI 0
    HDMI Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC1200 Digital
    Direct sample mixing device
dmix:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC1200 Digital
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC1200 Digital
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC1200 Digital
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Hardware device with all software conversions


```# lspci -v
```


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fa000000-febfffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at a800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at a480 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at a400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at f8efec00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f8ef8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f9000000-f9dfffff
    Prefetchable memory behind bridge: 00000000cc000000-00000000cfefffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f9e00000-f9efffff
    Prefetchable memory behind bridge: 00000000cff00000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: f9f00000-f9ffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000c01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at b000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at ac00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at a880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f8eff000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    Memory behind bridge: f8f00000-f8ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
    I/O ports at bc00 [size=8]
    I/O ports at b880 [size=4]
    I/O ports at b800 [size=8]
    I/O ports at b480 [size=4]
    I/O ports at b400 [size=32]
    Memory at f8eff800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Flags: medium devsel, IRQ 11
    Memory at f8eff400 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Flags: bus master, medium devsel, latency 32, IRQ 16
    Memory at f8fff000 (32-bit, non-prefetchable) [size=4K]
    Memory at f8ffe800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

01:04.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02) (prog-if 01)
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at f8ffe400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

01:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Flags: slow devsel, IRQ 10
    Memory at f8ffd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Physical Slot: 0-2
    Flags: bus master, fast devsel, latency 0, IRQ 45
    I/O ports at d800 [size=256]
    Memory at f9eff000 (64-bit, non-prefetchable) [size=4K]
    Memory at cfff0000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at f9ec0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

05:00.0 Network controller: Intel Corporation WiFi Link 5100
    Subsystem: Intel Corporation WiFi Link 5100 AGN
    Physical Slot: 0-3
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f9ffe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

06:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9600M GT] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. Device 7220
    Physical Slot: 0
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at ec00 [size=128]
    [virtual] Expansion ROM at feb80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb


```# cat /proc/asound/cards
```

0 [Intel]: HDA-Intel - HDA Intel
HDA Intel at 0xf8ef8000 irq 47

```# cat /proc/asound/card0/codec#0 | grep Codec
```
Codec: Realtek ALC1200
```# cat /proc/asound/card0/codec#1 | grep Codec
```
Codec: Motorola Si3054
```

---

### Post by marin123 on 2012-10-18
Which driver do you have for your graphics card? Proprietary or open-source?

If you installed driver from Additional drivers app, you have proprietary driver.

If you have open-source driver, you will need to enable audio in grub. Don't worry, it is not complicated :)

---

### Post by Time Sheep on 2012-10-18
> **marin123 said:**
> Which driver do you have for your graphics card? Proprietary or open-source?

If you installed driver from Additional drivers app, you have proprietary driver.

If you have open-source driver, you will need to enable audio in grub. Don't worry, it is not complicated :)

I use the proprietary NVidia driver - version current.
"Additional Drivers" recommended that one.

EDIT: I just noticed something
Under /proc/asound/Intel/ i have a codec#2 as well. If I cat this and grep "Codec" it returns "Codec: Nvidia MCP77/78 HDMI"

EDIT2:
One of my friends told me to do "amixer cset numid=3 3" where the last number was the ID of my HDMI device.
In declanb's case it seems to be 0. So the correct command would be "amixer cset numid=3 0"
Try it and then play a sound, you can just run "speaker-test" in terminal and it should play a purple noise.

---

### Post by declanb on 2012-10-19
proprietary drivers

---

