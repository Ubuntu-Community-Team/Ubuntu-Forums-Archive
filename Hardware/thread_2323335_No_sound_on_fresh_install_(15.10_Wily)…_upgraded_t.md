---
title: "No sound on fresh install (15.10 Wily)… upgraded to (16.04 Xenial) still no sound"
date: 2016-05-04
forum: Hardware
---

### Post by tony118 on 2016-05-04
Just finished installing Ubuntu on this old All-In-One Dell (Inspiron  One 19) and there is no sound coming from it, although there are signs  that suggest it should have sound (volume controls exist).  Some "info  overload" from commands I've seen others posting:  ```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:   xenial

```  -
  ```
$ pacmd
    Welcome to PulseAudio 6.0! Use "help" for usage information.
    >>> list-sinks
    1 sink(s) available.
      * index: 0
        name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
        driver: <module-alsa-card.c>
        flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
        state: RUNNING
        suspend cause: 
        priority: 9959
        volume: front-left: 56821 /  87% / -3.72 dB,   front-right: 56821 /  87% / -3.72 dB
            balance 0.00
        base volume: 65536 / 100% / 0.00 dB
        volume steps: 65537
        muted: no
        current latency: 24.96 ms
        max request: 4 KiB
        max rewind: 64 KiB
        monitor source: 0
        sample spec: s16le 2ch 48000Hz
        channel map: front-left,front-right
                 Stereo
        used by: 1
        linked by: 1
        configured latency: 25.00 ms; range is 0.50 .. 341.33 ms
        card: 0 <alsa_card.pci-0000_00_1b.0>
        module: 6
        properties:
            alsa.resolution_bits = "16"
            device.api = "alsa"
            device.class = "sound"
            alsa.class = "generic"
            alsa.subclass = "generic-mix"
            alsa.name = "CX20582 Analog"
            alsa.id = "CX20582 Analog"
            alsa.subdevice = "0"
            alsa.subdevice_name = "subdevice #0"
            alsa.device = "0"
            alsa.card = "0"
            alsa.card_name = "HDA Intel"
            alsa.long_card_name = "HDA Intel at 0xfe8f8000 irq 29"
            alsa.driver_name = "snd_hda_intel"
            device.bus_path = "pci-0000:00:1b.0"
            sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
            device.bus = "pci"
            device.vendor.id = "8086"
            device.vendor.name = "Intel Corporation"
            device.product.id = "27d8"
            device.product.name = "NM10/ICH7 Family High Definition Audio Controller"
            device.form_factor = "internal"
            device.string = "front:0"
            device.buffering.buffer_size = "65536"
            device.buffering.fragment_size = "32768"
            device.access_mode = "mmap+timer"
            device.profile.name = "analog-stereo"
            device.profile.description = "Analogue Stereo"
            device.description = "Built-in Audio Analogue Stereo"
            alsa.mixer_name = "Conexant CX20582 (Pebble)"
            alsa.components = "HDA:14f15066,10280408,00100301"
            module-udev-detect.discovered = "1"
            device.icon_name = "audio-card-pci"
        ports:
            analog-output-lineout: Line Out (priority 9900, latency offset 0 usec, available: no)
                properties:

            analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: unknown)
                properties:
                    device.icon_name = "audio-speakers"
            analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
                properties:
                    device.icon_name = "audio-headphones"
        active port: <analog-output-speaker>
    >>> exit

```  -
  ```
$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe8f8000 irq 29

```  -
  ```
$ sudo lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3401
01:00.1 Mass storage controller: VIA Technologies, Inc. Device 401a
01:00.2 SD Host controller: VIA Technologies, Inc. Device 401b
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)

```  Installed inxi for this:
  ```
$ inxi -xxA
Audio:     Card Intel NM10/ICH7 Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0 chip-ID: 8086:27d8
           Sound: Advanced Linux Sound Architecture v: k4.4.0-21-generic

```  Not sure if this bit helps but looking through the Xorg log I see this:
  ```
[    24.303] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event7)
[    24.303] (II) No input driver specified, ignoring this device.
[    24.303] (II) This device may have been added with another device file.
[    24.304] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event5)
[    24.304] (II) No input driver specified, ignoring this device.
[    24.304] (II) This device may have been added with another device file.
[    24.304] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event6)
[    24.304] (II) No input driver specified, ignoring this device.
[    24.304] (II) This device may have been added with another device file.
[    24.305] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event2)

```  

Adding this extra info in the hope it reveals something obvious:

```

$ udevadm info -a -p /devices/pci0000:00/0000:00:1b.0/sound/card0 
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1b.0/sound/card0':
    KERNEL=="card0"
    SUBSYSTEM=="sound"
    DRIVER==""
    ATTR{id}=="Intel"
    ATTR{number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1b.0':
    KERNELS=="0000:00:1b.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="snd_hda_intel"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x040300"
    ATTRS{consistent_dma_mask_bits}=="64"
    ATTRS{d3cold_allowed}=="1"
    ATTRS{device}=="0x27d8"
    ATTRS{dma_mask_bits}=="64"
    ATTRS{driver_override}=="(null)"
    ATTRS{enable}=="1"
    ATTRS{irq}=="29"
    ATTRS{local_cpulist}=="0-3"
    ATTRS{local_cpus}=="f"
    ATTRS{msi_bus}=="1"
    ATTRS{subsystem_device}=="0x0408"
    ATTRS{subsystem_vendor}=="0x1028"
    ATTRS{vendor}=="0x8086"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

My alsa-info.sh output is available [here]("http://www.alsa-project.org/db/?f=c4a38093b935ef22cdc330ccbda1e1776eb367ea") :)

I've been through the advice listed here [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS) but it doesnt seem to have helped with this sound issue. Total noob here and not sure what to try.  Any suggestions or further information required would be great to hear.
  TIA


[http://askubuntu.com/questions/767548/no-sound-on-fresh-install-15-10-wily-upgraded-to-16-04-xenial-still-no-so](http://askubuntu.com/questions/767548/no-sound-on-fresh-install-15-10-wily-upgraded-to-16-04-xenial-still-no-so)

---

### Post by tony118 on 2016-05-05
This isn't an Ubuntu issue, as I cant get sound working on another distro...  (puppy)...  time to give up, thanks for reading all this nonsense.

---

