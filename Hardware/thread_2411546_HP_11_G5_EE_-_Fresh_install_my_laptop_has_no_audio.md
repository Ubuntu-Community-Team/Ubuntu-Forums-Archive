---
title: "HP 11 G5 EE - Fresh install: my laptop has no audio - Ubuntu 18.04"
date: 2019-01-31
forum: Hardware
---

### Post by manexdomeinuak on 2019-01-31
Hello,

I was given a new HP 11 G5 EE chromebook and after some use I realised it was not going to do it for me, so I decided to format it and install Ubuntu instead. I have installed it and managed to get all the software I normally use without trouble, but I have realised that it does not play any audio. When using ChromeOS it did work.

If I look in the settings, there is no input device detected and the output is just "Dummy output":
[ATTACH=CONFIG]282365[/ATTACH][ATTACH=CONFIG]282366[/ATTACH]

I have tried by following some solutions in this forum and in AskUbuntu, but I could not solve it. Do you know what the problem may be?

Here is the output of some commands, I hope it is helpful:
```
**pacmd list-cards**
1 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_00_1b.0>
    driver: <module-alsa-card.c>
    owner module: 7
    properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xd1314000 irq 314"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "2284"
        device.product.name = "Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400, available: no)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 300, available: no)
        output:hdmi-surround71: Digital Surround 7.1 (HDMI) Output (priority 300, available: no)
        output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Output (priority 5200, available: no)
        output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Output (priority 100, available: no)
        output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Output (priority 100, available: no)
        output:hdmi-stereo-extra2: Digital Stereo (HDMI 3) Output (priority 5200, available: no)
        output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI 3) Output (priority 100, available: no)
        output:hdmi-surround71-extra2: Digital Surround 7.1 (HDMI 3) Output (priority 100, available: no)
        off: Off (priority 0, available: unknown)
    active profile: <off>
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"

```

```
**hwinfo --short**
cpu:                                                            
                       Intel(R) Celeron(R) CPU  N3060  @ 1.60GHz, 2075 MHz
                       Intel(R) Celeron(R) CPU  N3060  @ 1.60GHz, 2166 MHz
keyboard:
  /dev/input/event5    Maxxter Wireless Receiver
  /dev/input/event3    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Maxxter Wireless Receiver
  /dev/input/mice      Elan Touchpad
monitor:
                       LCD Monitor
graphics card:
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller
sound:
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller
network:
  wlp2s0               Intel Dual Band Wireless-AC 7265
network interface:
  lo                   Loopback network interface
  wlp2s0               Ethernet network interface
disk:
  /dev/mmcblk0         Disk
  /dev/mmcblk0boot0    Disk
  /dev/mmcblk0boot1    Disk
partition:
  /dev/mmcblk0p1       Partition
usb controller:
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller
bios:
                       BIOS
bridge:
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #3
hub:
                       Linux Foundation 2.0 root hub
                       Linux Foundation 3.0 root hub
memory:
                       Main Memory
bluetooth:
                       Intel Bluetooth Device
unknown:
                       FPU
                       DMA controller
                       PIC
                       Keyboard controller
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller
                       Serial controller
                       Quanta Chromebook HD Camera
```

Thank you very much for your help! :)

Manex

---

### Post by theone29 on 2019-02-10
I'm in the same situation with a Samsung CB3, your HP11 has the same Intel 3060 chip. I spent a good day or two researching for a solution but without luck. Hopefully someone will help us with this issue. 

1 card(s) available.
    index: 0
	name: <alsa_card.pci-0000_00_1b.0>
	driver: <module-alsa-card.c>
	owner module: 7
	properties:
		alsa.card = "0"
		alsa.card_name = "HDA Intel PCH"
		alsa.long_card_name = "HDA Intel PCH at 0xd1314000 irq 314"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "2284"
		device.product.name = "Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller"
		device.form_factor = "internal"
		device.string = "0"
		device.description = "Built-in Audio"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	profiles:
		output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5900, available: no)
		output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 800, available: no)
		output:hdmi-surround71: Digital Surround 7.1 (HDMI) Output (priority 800, available: no)
		output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Output (priority 5700, available: no)
		output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Output (priority 600, available: no)
		output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Output (priority 600, available: no)
		output:hdmi-stereo-extra2: Digital Stereo (HDMI 3) Output (priority 5700, available: no)
		output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI 3) Output (priority 600, available: no)
		output:hdmi-surround71-extra2: Digital Surround 7.1 (HDMI 3) Output (priority 600, available: no)
		off: Off (priority 0, available: unknown)
	active profile: <off>
	ports:
		hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "video-display"
		hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "video-display"
		hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "video-display"

cpu:                                                            
                       Intel(R) Celeron(R) CPU  N3060  @ 1.60GHz, 1840 MHz#######......]                          Intel(R) Celeron(R) CPU  N3060  @ 1.60GHz, 2356 MHz
keyboard:
                       Logitech Unifying Receiver
  /dev/input/event2    AT Translated Set 2 keyboard
mouse:
                       Logitech Unifying Receiver
  /dev/input/mice      Atmel maXTouch Touchpad
monitor:
                       AUO LCD Monitor
graphics card:
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller
sound:
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller
network:
  wlp2s0               Intel Dual Band Wireless-AC 7265
network interface:
  lo                   Loopback network interface
  wlp2s0               Ethernet network interface
disk:
  /dev/mmcblk0         Disk
  /dev/mmcblk1         Disk
partition:
  /dev/mmcblk0p1       Partition
  /dev/mmcblk0p2       Partition
  /dev/mmcblk1p1       Partition
usb controller:
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller
bios:
                       BIOS
bridge:
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #3
hub:
                       Linux Foundation 2.0 root hub
                       Linux Foundation 3.0 root hub
memory:
                       Main Memory
unknown:
                       FPU
                       DMA controller
                       PIC
                       Keyboard controller
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series MMC Controller
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SD Controller
                       Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller
                       Serial controller
                       Logitech Unifying Receiver
  /dev/input/event6    Chicony Electronics 720p HD Camera

---

### Post by pmaff on 2019-02-12
Short search:
 [https://forums.linuxmint.com/viewtopic.php?t=274487](https://forums.linuxmint.com/viewtopic.php?t=274487) ?   

 [https://ubuntuforums.org/showthread.php?t=2391606](https://ubuntuforums.org/showthread.php?t=2391606)  ?    

But I did not test this as I have different hardware.

---

