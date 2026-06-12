---
title: "Amcrest Webcam microphone does not work on start up."
date: 2021-02-10
forum: Hardware
---

### Post by onesixtyfourth on 2021-02-10
Hi all, I have just purchased a [webcam]("https://www.amazon.co.uk/gp/product/B089M6SXK2/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1") for online meetings and it works great once ubuntu recognises it. To get it to work I have to unplug and then replug the usb cable into my computer. I do have a fairly convoluted sound set up and I have also installed ubuntu studio meta packages. I have a Yamaha THR10C amplifier which acts as an audio interface plugged in through usb (2.0) and a Behringer UMC204HD plugged in (2.0) to capture another amp I use. Both of these are plugged into a usb 2.0 expansion back plate utilising usb 2.0 ports on the motherboard. I also use the Yamaha as output.

After replugging the cable for the webcam I can make messenger calls, Microsoft Teams calls & Cheese also works all with sound. When I restart the computer the input section in Settings -> Sound is always set to the Yamaha and simply selecting the correct device does not make it work. This is probably some kind of loading order that needs correcting but what do I need to do so that the correct device is used from initial start up?

Thank you.

[ATTACH=CONFIG]287938[/ATTACH]

On Startup:
```
~$ pacmd list-sources7 source(s) available.
    index: 0
    name: <alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor>
    driver: <module-alsa-card.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 1030
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: yes
    current latency: 0.00 ms
    max rewind: 0 KiB
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 1999.82 ms
    monitor_of: 0
    card: 0 <alsa_card.pci-0000_01_00.1>
    module: 7
    properties:
        device.description = "Monitor of GP108 High Definition Audio Controller Digital Stereo (HDMI)"
        device.class = "monitor"
        alsa.card = "1"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xdf080000 irq 17"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:01:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "NVIDIA Corporation"
        device.product.id = "0fb8"
        device.product.name = "GP108 High Definition Audio Controller"
        device.string = "1"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
  * index: 1
    name: <alsa_input.usb-USB_Camera_USB_Camera_SN0001-02.mono-fallback>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: (none)
    priority: 9040
    volume: mono: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max rewind: 0 KiB
    sample spec: s16le 1ch 44100Hz
    channel map: mono
                 Mono
    used by: 1
    linked by: 1
    configured latency: 40.00 ms; range is 0.50 .. 2000.00 ms
    card: 1 <alsa_card.usb-USB_Camera_USB_Camera_SN0001-02>
    module: 8
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "USB Audio"
        alsa.id = "USB Audio"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "3"
        alsa.card_name = "USB Camera"
        alsa.long_card_name = "USB Camera USB Camera at usb-0000:00:14.0-10, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:10:1.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.2/sound/card3"
        udev.id = "usb-USB_Camera_USB_Camera_SN0001-02"
        device.bus = "usb"
        device.vendor.id = "0c45"
        device.vendor.name = "Microdia"
        device.product.id = "6366"
        device.product.name = "USB Camera"
        device.serial = "USB_Camera_USB_Camera_SN0001"
        device.form_factor = "webcam"
        device.string = "hw:3"
        device.buffering.buffer_size = "176400"
        device.buffering.fragment_size = "88200"
        device.access_mode = "mmap+timer"
        device.profile.name = "mono-fallback"
        device.profile.description = "Mono"
        device.description = "USB Camera Mono"
        module-udev-detect.discovered = "1"
        device.icon_name = "camera-web-usb"
    ports:
        analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
    active port: <analog-input-mic>
    index: 2
    name: <alsa_output.usb-BEHRINGER_UMC204HD_192k-00.analog-surround-40.monitor>
    driver: <module-alsa-card.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: (none)
    priority: 1040
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB,   rear-left: 65536 / 100% / 0.00 dB,   rear-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: yes
    current latency: 0.00 ms
    max rewind: 13 KiB
    sample spec: s16le 4ch 44100Hz
    channel map: front-left,front-right,rear-left,rear-right
                 Surround 4.0
    used by: 1
    linked by: 1
    configured latency: 40.00 ms; range is 0.50 .. 2000.00 ms
    monitor_of: 1
    card: 2 <alsa_card.usb-BEHRINGER_UMC204HD_192k-00>
    module: 9
    properties:
        device.description = "Monitor of UMC204HD 192k Analogue Surround 4.0"
        device.class = "monitor"
        alsa.card = "4"
        alsa.card_name = "UMC204HD 192k"
        alsa.long_card_name = "BEHRINGER UMC204HD 192k at usb-0000:00:14.0-13, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:13:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13:1.0/sound/card4"
        udev.id = "usb-BEHRINGER_UMC204HD_192k-00"
        device.bus = "usb"
        device.vendor.id = "1397"
        device.vendor.name = "BEHRINGER International GmbH"
        device.product.id = "0508"
        device.product.name = "UMC204HD 192k"
        device.serial = "BEHRINGER_UMC204HD_192k"
        device.string = "4"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"
    index: 3
    name: <alsa_input.usb-BEHRINGER_UMC204HD_192k-00.iec958-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 9048
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: yes
    current latency: 0.00 ms
    max rewind: 0 KiB
    sample spec: s32le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
    card: 2 <alsa_card.usb-BEHRINGER_UMC204HD_192k-00>
    module: 9
    properties:
        alsa.resolution_bits = "32"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "USB Audio"
        alsa.id = "USB Audio"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "4"
        alsa.card_name = "UMC204HD 192k"
        alsa.long_card_name = "BEHRINGER UMC204HD 192k at usb-0000:00:14.0-13, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:13:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13:1.0/sound/card4"
        udev.id = "usb-BEHRINGER_UMC204HD_192k-00"
        device.bus = "usb"
        device.vendor.id = "1397"
        device.vendor.name = "BEHRINGER International GmbH"
        device.product.id = "0508"
        device.product.name = "UMC204HD 192k"
        device.serial = "BEHRINGER_UMC204HD_192k"
        device.string = "iec958:4"
        device.buffering.buffer_size = "705600"
        device.buffering.fragment_size = "352800"
        device.access_mode = "mmap+timer"
        device.profile.name = "iec958-stereo"
        device.profile.description = "Digital Stereo (IEC958)"
        device.description = "UMC204HD 192k Digital Stereo (IEC958)"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"
    ports:
        iec958-stereo-input: Digital Input (S/PDIF) (priority 0, latency offset 0 usec, available: unknown)
            properties:
                
    active port: <iec958-stereo-input>
    index: 4
    name: <alsa_output.usb-Yamaha_Corporation_THR10C-00.analog-stereo.monitor>
    driver: <module-alsa-card.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 1040
    volume: front-left: 55705 /  85% / -4.24 dB,   front-right: 55705 /  85% / -4.24 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max rewind: 0 KiB
    sample spec: s24le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
    monitor_of: 2
    card: 3 <alsa_card.usb-Yamaha_Corporation_THR10C-00>
    module: 10
    properties:
        device.description = "Monitor of THR10C Analogue Stereo"
        device.class = "monitor"
        alsa.card = "2"
        alsa.card_name = "THR10C"
        alsa.long_card_name = "Yamaha Corporation THR10C at usb-0000:00:14.0-2, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:2:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/sound/card2"
        udev.id = "usb-Yamaha_Corporation_THR10C-00"
        device.bus = "usb"
        device.vendor.id = "0499"
        device.vendor.name = "Yamaha Corp."
        device.product.id = "150c"
        device.product.name = "THR10C"
        device.serial = "Yamaha_Corporation_THR10C"
        device.string = "2"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"
    index: 5
    name: <alsa_input.usb-Yamaha_Corporation_THR10C-00.multichannel-input>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 9040
    volume: front-left: 70896 / 108% / 2.05 dB,   front-right: 70896 / 108% / 2.05 dB,   rear-left: 70896 / 108% / 2.05 dB,   rear-right: 70896 / 108% / 2.05 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max rewind: 0 KiB
    sample spec: s24le 4ch 44100Hz
    channel map: front-left,front-right,rear-left,rear-right
                 Surround 4.0
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 1981.43 ms
    card: 3 <alsa_card.usb-Yamaha_Corporation_THR10C-00>
    module: 10
    properties:
        alsa.resolution_bits = "24"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "USB Audio"
        alsa.id = "USB Audio"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "2"
        alsa.card_name = "THR10C"
        alsa.long_card_name = "Yamaha Corporation THR10C at usb-0000:00:14.0-2, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:2:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/sound/card2"
        udev.id = "usb-Yamaha_Corporation_THR10C-00"
        device.bus = "usb"
        device.vendor.id = "0499"
        device.vendor.name = "Yamaha Corp."
        device.product.id = "150c"
        device.product.name = "THR10C"
        device.serial = "Yamaha_Corporation_THR10C"
        device.string = "hw:2"
        device.buffering.buffer_size = "1048572"
        device.buffering.fragment_size = "524280"
        device.access_mode = "mmap+timer"
        device.profile.name = "multichannel-input"
        device.profile.description = "Multichannel"
        device.description = "THR10C Multichannel"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"
    ports:
        multichannel-input: Multichannel Input (priority 0, latency offset 0 usec, available: unknown)
            properties:
                
    active port: <multichannel-input>
    index: 6
    name: <alsa_output.pci-0000_00_1f.3.analog-stereo.monitor>
    driver: <module-alsa-card.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 1030
    volume: front-left: 85192 / 130% / 6.84 dB,   front-right: 85192 / 130% / 6.84 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: yes
    current latency: 0.00 ms
    max rewind: 0 KiB
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
    monitor_of: 3
    card: 4 <alsa_card.pci-0000_00_1f.3>
    module: 11
    properties:
        device.description = "Monitor of Built-in Audio Analogue Stereo"
        device.class = "monitor"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xdf220000 irq 127"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "a2f0"
        device.product.name = "200 Series PCH HD Audio"
        device.form_factor = "internal"
        device.string = "0"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"



```


After replugging (webcam on different index):
```
$ pacmd list-sources7 source(s) available.
    index: 0
    name: <alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor>
    driver: <module-alsa-card.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: (none)
    priority: 1030
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max rewind: 6 KiB
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 1
    linked by: 1
    configured latency: 40.00 ms; range is 0.50 .. 1999.82 ms
    monitor_of: 0
    card: 0 <alsa_card.pci-0000_01_00.1>
    module: 7
    properties:
        device.description = "Monitor of GP108 High Definition Audio Controller Digital Stereo (HDMI)"
        device.class = "monitor"
        alsa.card = "1"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xdf080000 irq 17"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:01:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "NVIDIA Corporation"
        device.product.id = "0fb8"
        device.product.name = "GP108 High Definition Audio Controller"
        device.string = "1"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    index: 2
    name: <alsa_output.usb-BEHRINGER_UMC204HD_192k-00.analog-surround-40.monitor>
    driver: <module-alsa-card.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: (none)
    priority: 1040
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB,   rear-left: 65536 / 100% / 0.00 dB,   rear-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max rewind: 13 KiB
    sample spec: s16le 4ch 44100Hz
    channel map: front-left,front-right,rear-left,rear-right
                 Surround 4.0
    used by: 2
    linked by: 2
    configured latency: 40.00 ms; range is 0.50 .. 2000.00 ms
    monitor_of: 1
    card: 2 <alsa_card.usb-BEHRINGER_UMC204HD_192k-00>
    module: 9
    properties:
        device.description = "Monitor of UMC204HD 192k Analogue Surround 4.0"
        device.class = "monitor"
        alsa.card = "4"
        alsa.card_name = "UMC204HD 192k"
        alsa.long_card_name = "BEHRINGER UMC204HD 192k at usb-0000:00:14.0-13, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:13:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13:1.0/sound/card4"
        udev.id = "usb-BEHRINGER_UMC204HD_192k-00"
        device.bus = "usb"
        device.vendor.id = "1397"
        device.vendor.name = "BEHRINGER International GmbH"
        device.product.id = "0508"
        device.product.name = "UMC204HD 192k"
        device.serial = "BEHRINGER_UMC204HD_192k"
        device.string = "4"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"
    index: 3
    name: <alsa_input.usb-BEHRINGER_UMC204HD_192k-00.iec958-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: (none)
    priority: 9048
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.79 ms
    max rewind: 0 KiB
    sample spec: s32le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 1
    linked by: 1
    configured latency: 40.00 ms; range is 0.50 .. 2000.00 ms
    card: 2 <alsa_card.usb-BEHRINGER_UMC204HD_192k-00>
    module: 9
    properties:
        alsa.resolution_bits = "32"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "USB Audio"
        alsa.id = "USB Audio"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "4"
        alsa.card_name = "UMC204HD 192k"
        alsa.long_card_name = "BEHRINGER UMC204HD 192k at usb-0000:00:14.0-13, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:13:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13:1.0/sound/card4"
        udev.id = "usb-BEHRINGER_UMC204HD_192k-00"
        device.bus = "usb"
        device.vendor.id = "1397"
        device.vendor.name = "BEHRINGER International GmbH"
        device.product.id = "0508"
        device.product.name = "UMC204HD 192k"
        device.serial = "BEHRINGER_UMC204HD_192k"
        device.string = "iec958:4"
        device.buffering.buffer_size = "705600"
        device.buffering.fragment_size = "352800"
        device.access_mode = "mmap+timer"
        device.profile.name = "iec958-stereo"
        device.profile.description = "Digital Stereo (IEC958)"
        device.description = "UMC204HD 192k Digital Stereo (IEC958)"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"
    ports:
        iec958-stereo-input: Digital Input (S/PDIF) (priority 0, latency offset 0 usec, available: unknown)
            properties:
                
    active port: <iec958-stereo-input>
    index: 4
    name: <alsa_output.usb-Yamaha_Corporation_THR10C-00.analog-stereo.monitor>
    driver: <module-alsa-card.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: (none)
    priority: 1040
    volume: front-left: 58975 /  90% / -2.75 dB,   front-right: 58975 /  90% / -2.75 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max rewind: 10 KiB
    sample spec: s24le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 1
    linked by: 1
    configured latency: 40.00 ms; range is 0.50 .. 2000.00 ms
    monitor_of: 2
    card: 3 <alsa_card.usb-Yamaha_Corporation_THR10C-00>
    module: 10
    properties:
        device.description = "Monitor of THR10C Analogue Stereo"
        device.class = "monitor"
        alsa.card = "2"
        alsa.card_name = "THR10C"
        alsa.long_card_name = "Yamaha Corporation THR10C at usb-0000:00:14.0-2, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:2:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/sound/card2"
        udev.id = "usb-Yamaha_Corporation_THR10C-00"
        device.bus = "usb"
        device.vendor.id = "0499"
        device.vendor.name = "Yamaha Corp."
        device.product.id = "150c"
        device.product.name = "THR10C"
        device.serial = "Yamaha_Corporation_THR10C"
        device.string = "2"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"
    index: 5
    name: <alsa_input.usb-Yamaha_Corporation_THR10C-00.multichannel-input>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: (none)
    priority: 9040
    volume: front-left: 51234 /  78% / -6.42 dB,   front-right: 51234 /  78% / -6.42 dB,   rear-left: 51234 /  78% / -6.42 dB,   rear-right: 51234 /  78% / -6.42 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.58 ms
    max rewind: 0 KiB
    sample spec: s24le 4ch 44100Hz
    channel map: front-left,front-right,rear-left,rear-right
                 Surround 4.0
    used by: 1
    linked by: 1
    configured latency: 40.00 ms; range is 0.50 .. 1981.43 ms
    card: 3 <alsa_card.usb-Yamaha_Corporation_THR10C-00>
    module: 10
    properties:
        alsa.resolution_bits = "24"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "USB Audio"
        alsa.id = "USB Audio"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "2"
        alsa.card_name = "THR10C"
        alsa.long_card_name = "Yamaha Corporation THR10C at usb-0000:00:14.0-2, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:2:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/sound/card2"
        udev.id = "usb-Yamaha_Corporation_THR10C-00"
        device.bus = "usb"
        device.vendor.id = "0499"
        device.vendor.name = "Yamaha Corp."
        device.product.id = "150c"
        device.product.name = "THR10C"
        device.serial = "Yamaha_Corporation_THR10C"
        device.string = "hw:2"
        device.buffering.buffer_size = "1048572"
        device.buffering.fragment_size = "524280"
        device.access_mode = "mmap+timer"
        device.profile.name = "multichannel-input"
        device.profile.description = "Multichannel"
        device.description = "THR10C Multichannel"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"
    ports:
        multichannel-input: Multichannel Input (priority 0, latency offset 0 usec, available: unknown)
            properties:
                
    active port: <multichannel-input>
    index: 6
    name: <alsa_output.pci-0000_00_1f.3.analog-stereo.monitor>
    driver: <module-alsa-card.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: (none)
    priority: 1030
    volume: front-left: 85192 / 130% / 6.84 dB,   front-right: 85192 / 130% / 6.84 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max rewind: 6 KiB
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 1
    linked by: 1
    configured latency: 40.00 ms; range is 0.50 .. 2000.00 ms
    monitor_of: 3
    card: 4 <alsa_card.pci-0000_00_1f.3>
    module: 11
    properties:
        device.description = "Monitor of Built-in Audio Analogue Stereo"
        device.class = "monitor"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xdf220000 irq 127"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "a2f0"
        device.product.name = "200 Series PCH HD Audio"
        device.form_factor = "internal"
        device.string = "0"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
  * index: 7
    name: <alsa_input.usb-USB_Camera_USB_Camera_SN0001-02.mono-fallback>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: (none)
    priority: 9040
    volume: mono: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.65 ms
    max rewind: 0 KiB
    sample spec: s16le 1ch 44100Hz
    channel map: mono
                 Mono
    used by: 2
    linked by: 2
    configured latency: 40.00 ms; range is 0.50 .. 2000.00 ms
    card: 5 <alsa_card.usb-USB_Camera_USB_Camera_SN0001-02>
    module: 29
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "USB Audio"
        alsa.id = "USB Audio"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "3"
        alsa.card_name = "USB Camera"
        alsa.long_card_name = "USB Camera USB Camera at usb-0000:00:14.0-10, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:10:1.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.2/sound/card3"
        udev.id = "usb-USB_Camera_USB_Camera_SN0001-02"
        device.bus = "usb"
        device.vendor.id = "0c45"
        device.vendor.name = "Microdia"
        device.product.id = "6366"
        device.product.name = "USB Camera"
        device.serial = "USB_Camera_USB_Camera_SN0001"
        device.form_factor = "webcam"
        device.string = "hw:3"
        device.buffering.buffer_size = "176400"
        device.buffering.fragment_size = "88200"
        device.access_mode = "mmap+timer"
        device.profile.name = "mono-fallback"
        device.profile.description = "Mono"
        device.description = "USB Camera Mono"
        module-udev-detect.discovered = "1"
        device.icon_name = "camera-web-usb"
    ports:
        analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
    active port: <analog-input-mic>



```

[Edit]
This seems to be related to pulseaudio as running ```
pulseaudio -k
``` resets back to what I have when I boot. If I then replug the webcam it all works. What is that?

---

