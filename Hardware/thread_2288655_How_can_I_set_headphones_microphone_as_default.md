---
title: "How can I set headphones microphone as default?"
date: 2015-07-29
forum: Hardware
---

### Post by mavlutovr on 2015-07-29
I have headphones with microphone. It work good. But when I connect headphones to my laptop, I need to choose Headphones microphone every time. 
[IMG]http://screenshot3.seobit.ru/roma.2015.07.29___09:06:1438149972.png[/IMG]
And some time I forget to do it and make record with laptop microphone with bad quality sound.

I want to set headset microphone automaticaly when I connect it to laptop.

```
pacmd list-sources
```

Part of output:
```
...
analog-input-microphone-internal: Internal Microphone (priority 8900, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-microphone-headset: Headset Microphone (priority 8700, latency offset 0 usec, available: unknown)
...
```

Full output is:

```
roma@romapacmd list-sourcesWelcome to PulseAudio! Use "help" for usage information.
>>> 3 source(s) available.
    index: 0
    name: <alsa_output.pci-0000_00_03.0.hdmi-stereo.monitor>
    driver: <module-alsa-card.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 1950
    volume: 0: 100% 1: 100%
            0: 0,00 dB 1: 0,00 dB
            balance 0,00
    base volume: 100%
                 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max rewind: 0 KiB
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 371,52 ms
    monitor_of: 0
    card: 0 <alsa_card.pci-0000_00_03.0>
    module: 5
    properties:
        device.description = "Monitor of Built-in Audio Digital Stereo (HDMI)"
        device.class = "monitor"
        alsa.card = "0"
        alsa.card_name = "HDA Intel HDMI"
        alsa.long_card_name = "HDA Intel HDMI at 0xf7f14000 irq 63"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:03.0"
        sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "0a0c"
        device.form_factor = "internal"
        device.string = "0"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    index: 1
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo.monitor>
    driver: <module-alsa-card.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 1950
    volume: 0: 100% 1: 100%
            0: 0,00 dB 1: 0,00 dB
            balance 0,00
    base volume: 100%
                 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max rewind: 0 KiB
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 371,52 ms
    monitor_of: 1
    card: 1 <alsa_card.pci-0000_00_1b.0>
    module: 6
    properties:
        device.description = "Monitor of Built-in Audio Analog Stereo"
        device.class = "monitor"
        alsa.card = "1"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xf7f10000 irq 62"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "9c20"
        device.product.name = "Lynx Point-LP HD Audio Controller"
        device.form_factor = "internal"
        device.string = "1"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
  * index: 2
    name: <alsa_input.pci-0000_00_1b.0.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: 
    priority: 9959
    volume: 0:  78% 1:  78%
            0: -6,50 dB 1: -6,50 dB
            balance 0,00
    base volume:  10%
                 -60,00 dB
    volume steps: 65537
    muted: no
    current latency: 2,61 ms
    max rewind: 0 KiB
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 1
    linked by: 1
    configured latency: 20,00 ms; range is 0,50 .. 371,52 ms
    card: 1 <alsa_card.pci-0000_00_1b.0>
    module: 6
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC286 Analog"
        alsa.id = "ALC286 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xf7f10000 irq 62"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "9c20"
        device.product.name = "Lynx Point-LP HD Audio Controller"
        device.form_factor = "internal"
        device.string = "front:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "Realtek ALC286"
        alsa.components = "HDA:10ec0286,104d7100,00100002"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-input-microphone-internal: Internal Microphone (priority 8900, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-microphone-headset: Headset Microphone (priority 8700, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
    active port: <analog-input-microphone-headset>
>>> roma@roma:~$ 



```

---

