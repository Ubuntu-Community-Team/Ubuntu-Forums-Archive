---
title: "Displayport Audio not working on HP Thunderbolt dock"
date: 2018-06-20
forum: Hardware
---

### Post by stefan39 on 2018-06-20
Hello,
 
 
 I‘m using the Thunderbolt 3 docking station HP 1DT93AA with my HP Elite x2 1012 G1 (see [https://ubuntuforums.org/showthread.php?t=2313988](https://ubuntuforums.org/showthread.php?t=2313988)) on Ubuntu 18.04. Everything works well, except I don‘t get audio through the Displayports of the dock (I connected a Displayport to HDMI adapter on the Displayport). This active Displayport to HDMI adapter is working on another machine (Ubuntu 18.04). In the sound settings, I can choose the adapter as HDMI/Displayport – Built-in Audio.  

I get the following output with **pacmd list-sinks**:

 
```
  * index: 37
    name: <alsa_output.pci-0000_00_1f.3.hdmi-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: 
    priority: 9030
    volume: front-left: 51049 /  78% / -6,51 dB,   front-right: 51049 /  78% / -6,51 dB
            balance 0,00
    base volume: 65536 / 100% / 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 4,26 ms
    max request: 0 KiB
    max rewind: 64 KiB
    monitor source: 39
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 3
    linked by: 3
    configured latency: 4,00 ms; range is 4,00 .. 371,52 ms
    card: 1 <alsa_card.pci-0000_00_1f.3>
    module: 8
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
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xdc53c000 irq 184"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "9d70"
        device.product.name = "Sunrise Point-LP HD Audio"
        device.form_factor = "internal"
        device.string = "hdmi:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo"
        device.profile.description = "Digital Stereo (HDMI)"
        device.description = "Built-in Audio Digital Stereo (HDMI)"
        alsa.mixer_name = "Conexant CX20724"
        alsa.components = "HDA:14f150f4,103c80fc,00100101 HDA:80862809,80860101,00100000"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "video-display"
                device.product.name = "DENON-AVAMP"
    active port: <hdmi-output-0>


```

---

