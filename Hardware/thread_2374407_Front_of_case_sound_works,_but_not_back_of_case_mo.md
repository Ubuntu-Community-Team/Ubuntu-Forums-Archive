---
title: "Front of case sound works, but not back of case motherboard sound."
date: 2017-10-15
forum: Hardware
---

### Post by macksfield on 2017-10-15
I'm having an issue where the front of case sound is working [headphones], but the back of case sound, direct from the motherboard, is not working. [speakers]

When I go to Sound Settings, I see my headphones listed, and 'Digital Output (S/PDIF).' Unplugging my headphones registers in this list of output devices, but unplugging speakers does not. My speakers are currently plugged into an analog jack, no the S/PDIF jack.   
  
I believe this may be a routing issue, or perhaps the speakers are not being recognized?

```

macksfield@MORTIS:~$ pacmd list-sinks
2 sink(s) available.
    index: 0
    name: <alsa_output.pci-0000_01_00.1.hdmi-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9050
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
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
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 0 <alsa_card.pci-0000_01_00.1>
    module: 6
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
        alsa.card_name = "HDA ATI HDMI"
        alsa.long_card_name = "HDA ATI HDMI at 0xdfe60000 irq 323"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:01:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "aac8"
        device.product.name = "Hawaii HDMI Audio"
        device.string = "hdmi:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo"
        device.profile.description = "Digital Stereo (HDMI)"
        device.description = "Hawaii HDMI Audio Digital Stereo (HDMI)"
        alsa.mixer_name = "ATI R6xx HDMI"
        alsa.components = "HDA:1002aa01,00aa0100,00100500"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
    active port: <hdmi-output-0>
  * index: 1
    name: <alsa_output.pci-0000_00_1f.3.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9959
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 3
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 1
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 3 <alsa_card.pci-0000_00_1f.3>
    module: 9
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC1150 Analog"
        alsa.id = "ALC1150 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xdff20000 irq 322"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "a170"
        device.product.name = "Sunrise Point-H HD Audio"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "Realtek ALC1150"
        alsa.components = "HDA:10ec0900,1462d977,00100001"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output-lineout: Line Out (priority 9900, latency offset 0 usec, available: no)
            properties:
                
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "audio-headphones"
    active port: <analog-output-headphones>


```

---

### Post by macksfield on 2017-10-15
Some additional info:
```

macksfield@MORTIS:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC1150 Analog [ALC1150 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC1150 Digital [ALC1150 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````

macksfield@MORTIS:~$ lspci | grep -i audio
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii HDMI Audio

```

---

### Post by Autodave on 2017-10-16
What version of ?buntu have you installed?

---

### Post by macksfield on 2017-10-16
> **Autodave said:**
> What version of ?buntu have you installed?

Using 16.04, but the issue was present on 17.04 as well.

I have made some strides to correct this issue, but am not quite there yet.
Using alsamixer I am able to unmute the line-out option, and if I also disable auto auto-muting -> I am able to get sound output from speakers and headphones **simultaneously**. 

The only way to get Line-Out to show up in my system settings by itself is to unplug my headphones, at which point it shows. So the question becomes, how do I get Line-Out *and *Headphones to show up so that I can easily switch between them without unplugging things or mucking with the terminal.

---

### Post by macksfield on 2017-10-16
Issue is VERY similar to this: [https://superuser.com/questions/1047943/pavucontrol-shows-line-out-as-unplugged-when-headphones-are-plugged-in](https://superuser.com/questions/1047943/pavucontrol-shows-line-out-as-unplugged-when-headphones-are-plugged-in)'

---

