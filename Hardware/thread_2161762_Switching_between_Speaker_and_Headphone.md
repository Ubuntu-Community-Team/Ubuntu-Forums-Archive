---
title: "Switching between Speaker and Headphone"
date: 2013-07-11
forum: Hardware
---

### Post by bizhat on 2013-07-11
Hi,

I am using Ubuntu 13.04

I want to switch between Speaker and Headphone with out disconnecting headphone (This work in Windows 7).

My sound device is

```

$ cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ALC892
$ 

```


```

boby@hon-1:~/Desktop$ pacmd list-sinks
Welcome to PulseAudio! Use "help" for usage information.
>>> 2 sink(s) available.
    index: 0
    name: <alsa_output.pci-0000_04_00.1.hdmi-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9050
    volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 96.00 .. 371.52 ms
    card: 0 <alsa_card.pci-0000_04_00.1>
    module: 4
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 0"
        alsa.id = "HDMI 0"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "3"
        alsa.card = "1"
        alsa.card_name = "HD-Audio Generic"
        alsa.long_card_name = "HD-Audio Generic at 0xfbcfc000 irq 76"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:04:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:07.0/0000:04:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices [AMD] nee ATI"
        device.product.name = "Redwood HDMI Audio [Radeon HD 5000 Series]"
        device.string = "hdmi:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo"
        device.profile.description = "Digital Stereo (HDMI)"
        device.description = "Redwood HDMI Audio [Radeon HD 5000 Series] Digital Stereo (HDMI)"
        alsa.mixer_name = "ATI R6xx HDMI"
        alsa.components = "HDA:1002aa01,00aa0100,00100200"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
    active port: <hdmi-output-0>
  * index: 3
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: 
    priority: 9959
    volume: 0:  43% 1:  43%
            0: -22.08 dB 1: -22.08 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 6.11 ms
    max request: 1 KiB
    max rewind: 64 KiB
    monitor source: 4
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 4
    linked by: 4
    configured latency: 8.00 ms; range is 8.00 .. 371.52 ms
    card: 1 <alsa_card.pci-0000_00_1b.0>
    module: 5
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC892 Analog"
        alsa.id = "ALC892 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA Intel"
        alsa.long_card_name = "HDA Intel at 0xfb9f8000 irq 75"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.name = "82801JI (ICH10 Family) HD Audio Controller"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "Realtek ALC892"
        alsa.components = "HDA:10ec0892,10438436,00100302"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output: Analog Output (priority 9900, latency offset 0 usec, available: unknown)
            properties:
                
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "audio-headphones"
    active port: <analog-output>
>>> boby@hon-1:~/Desktop$ 

```

Currently i get sound in Speaker when i unplug Headphone.

Switching output device in sound settings is not working.

[IMG]http://flashweb.in/fpimg/sound_device.png[/IMG]

Anyway i can get sound in Speaker with out disconnecting Headphone ?

Thanks,

Boby

---

