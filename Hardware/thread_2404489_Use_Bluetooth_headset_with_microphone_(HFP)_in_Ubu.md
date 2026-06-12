---
title: "Use Bluetooth headset with microphone (HFP) in Ubuntu 18.04"
date: 2018-10-24
forum: Hardware
---

### Post by amitmo81 on 2018-10-24
[COLOR=#242729][FONT=Arial]My Bluetooth headset (IFROGZ Toxix Wireless) supports the Headset Head Unit profile (headset_head_unit or HSP/HFP) and the audio playback profile (a2dp_sink). It pairs and connects successfully with my Ubuntu 18.04 laptop. However, when connected, in the Settings > Sound menu, it is only listed under Output and not under Input (i.e. the mic is not recognized).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Therefore, I can only use it for playback, and not as a headset for video meetings, which poses a big problem for me as all my work is done on this computer.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I found that this is a known bug:[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1768625](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1768625)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Are there any workarounds / pathces / solutions for this?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial](been using Ubunu for years but very much a noob here when it comes to the inner workings)

---
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]*bluetoothctl* output (note it supports Handsfree HFP but not Headset HSP)[/FONT][/COLOR]
```
Device 61:21:34:24:4F:20 (public)
Name: IFROGZ Toxix Wireless
Alias: IFROGZ Toxix Wireless
Class: 0x00240404
Icon: audio-card
Paired: yes
Trusted: yes
Blocked: no
Connected: yes
LegacyPairing: no
UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb) UUID: Handsfree                 (0000111e-0000-1000-8000-00805f9b34fb)
```

*pacmd list-cards*[COLOR=#242729][FONT=Arial] output (note at the end that headset-input has[/FONT][/COLOR]*available: no*[COLOR=#242729][FONT=Arial]):

[/FONT][/COLOR]```
$ pacmd list-cards
2 card(s) available.
index: 0
name: <alsa_card.pci-0000_00_1f.3>
driver: <module-alsa-card.c>
owner module: 7
properties:
    alsa.card = "0"
    alsa.card_name = "HDA Intel PCH"
    alsa.long_card_name = "HDA Intel PCH at 0xb1328000 irq 134"
    alsa.driver_name = "snd_hda_intel"
    device.bus_path = "pci-0000:00:1f.3"
    sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
    device.bus = "pci"
    device.vendor.id = "8086"
    device.vendor.name = "Intel Corporation"
    device.product.id = "9d71"
    device.product.name = "Sunrise Point-LP HD Audio"
    device.form_factor = "internal"
    device.string = "0"
    device.description = "Built-in Audio"
    module-udev-detect.discovered = "1"
    device.icon_name = "audio-card-pci"
profiles:
    input:analog-stereo: Analog Stereo Input (priority 60, available: unknown)
    output:analog-stereo: Analog Stereo Output (priority 6000, available: unknown)
    output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060, available: unknown)
    output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400, available: unknown)
    output:hdmi-stereo+input:analog-stereo: Digital Stereo (HDMI) Output + Analog Stereo Input (priority 5460, available: unknown)
    output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Output (priority 5200, available: no)
    output:hdmi-stereo-extra1+input:analog-stereo: Digital Stereo (HDMI 2) Output + Analog Stereo Input (priority 5260, available: unknown)
    output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Output (priority 100, available: no)
    output:hdmi-surround-extra1+input:analog-stereo: Digital Surround 5.1 (HDMI 2) Output + Analog Stereo Input (priority 160, available: unknown)
    output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Output (priority 100, available: no)
    output:hdmi-surround71-extra1+input:analog-stereo: Digital Surround 7.1 (HDMI 2) Output + Analog Stereo Input (priority 160, available: unknown)
    output:hdmi-stereo-extra2: Digital Stereo (HDMI 3) Output (priority 5200, available: no)
    output:hdmi-stereo-extra2+input:analog-stereo: Digital Stereo (HDMI 3) Output + Analog Stereo Input (priority 5260, available: unknown)
    output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI 3) Output (priority 100, available: no)
    output:hdmi-surround-extra2+input:analog-stereo: Digital Surround 5.1 (HDMI 3) Output + Analog Stereo Input (priority 160, available: unknown)
    output:hdmi-surround71-extra2: Digital Surround 7.1 (HDMI 3) Output (priority 100, available: no)
    output:hdmi-surround71-extra2+input:analog-stereo: Digital Surround 7.1 (HDMI 3) Output + Analog Stereo Input (priority 160, available: unknown)
    output:hdmi-stereo-extra3: Digital Stereo (HDMI 4) Output (priority 5200, available: no)
    output:hdmi-stereo-extra3+input:analog-stereo: Digital Stereo (HDMI 4) Output + Analog Stereo Input (priority 5260, available: unknown)
    output:hdmi-surround-extra3: Digital Surround 5.1 (HDMI 4) Output (priority 100, available: no)
    output:hdmi-surround-extra3+input:analog-stereo: Digital Surround 5.1 (HDMI 4) Output + Analog Stereo Input (priority 160, available: unknown)
    output:hdmi-surround71-extra3: Digital Surround 7.1 (HDMI 4) Output (priority 100, available: no)
    output:hdmi-surround71-extra3+input:analog-stereo: Digital Surround 7.1 (HDMI 4) Output + Analog Stereo Input (priority 160, available: unknown)
    output:hdmi-stereo-extra4: Digital Stereo (HDMI 5) Output (priority 5200, available: no)
    output:hdmi-stereo-extra4+input:analog-stereo: Digital Stereo (HDMI 5) Output + Analog Stereo Input (priority 5260, available: unknown)
    output:hdmi-surround-extra4: Digital Surround 5.1 (HDMI 5) Output (priority 100, available: no)
    output:hdmi-surround-extra4+input:analog-stereo: Digital Surround 5.1 (HDMI 5) Output + Analog Stereo Input (priority 160, available: unknown)
    output:hdmi-surround71-extra4: Digital Surround 7.1 (HDMI 5) Output (priority 100, available: no)
    output:hdmi-surround71-extra4+input:analog-stereo: Digital Surround 7.1 (HDMI 5) Output + Analog Stereo Input (priority 160, available: unknown)
    off: Off (priority 0, available: unknown)
active profile: <output:analog-stereo+input:analog-stereo>
sinks:
    alsa_output.pci-0000_00_1f.3.analog-stereo/#0: Built-in Audio Analog Stereo
sources:
    alsa_output.pci-0000_00_1f.3.analog-stereo.monitor/#0: Monitor of Built-in Audio Analog Stereo
    alsa_input.pci-0000_00_1f.3.analog-stereo/#1: Built-in Audio Analog Stereo
ports:
    analog-input-internal-mic: Internal Microphone (priority 8900, latency offset 0 usec, available: unknown)
        properties:
            device.icon_name = "audio-input-microphone"
    analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: no)
        properties:
            device.icon_name = "audio-input-microphone"
    analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: unknown)
        properties:
            device.icon_name = "audio-speakers"
    analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
        properties:
            device.icon_name = "audio-headphones"
    hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: yes)
        properties:
            device.icon_name = "video-display"
            device.product.name = "2429W"
    hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
        properties:
            device.icon_name = "video-display"
    hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, latency offset 0 usec, available: no)
        properties:
            device.icon_name = "video-display"
    hdmi-output-3: HDMI / DisplayPort 4 (priority 5600, latency offset 0 usec, available: no)
        properties:
            device.icon_name = "video-display"
    hdmi-output-4: HDMI / DisplayPort 5 (priority 5500, latency offset 0 usec, available: no)
        properties:
            device.icon_name = "video-display"
index: 1
name: <bluez_card.61_21_34_24_4F_20>
driver: <module-bluez5-device.c>
owner module: 24
properties:
    device.description = "IFROGZ Toxix Wireless"
    device.string = "61:21:34:24:4F:20"
    device.api = "bluez"
    device.class = "sound"
    device.bus = "bluetooth"
    device.form_factor = "headset"
    bluez.path = "/org/bluez/hci0/dev_61_21_34_24_4F_20"
    bluez.class = "0x240404"
    bluez.alias = "IFROGZ Toxix Wireless"
    device.icon_name = "audio-headset-bluetooth"
    device.intended_roles = "phone"
profiles:
    a2dp_sink: High Fidelity Playback (A2DP Sink) (priority 40, available: unknown)
    headset_head_unit: Headset Head Unit (HSP/HFP) (priority 30, available: no)
    off: Off (priority 0, available: yes)
active profile: <a2dp_sink>
sinks:
    bluez_sink.61_21_34_24_4F_20.a2dp_sink/#1: IFROGZ Toxix Wireless
sources:
    bluez_sink.61_21_34_24_4F_20.a2dp_sink.monitor/#2: Monitor of IFROGZ Toxix Wireless
ports:
    headset-output: Headset (priority 0, latency offset 0 usec, available: unknown)
        properties:

    headset-input: Headset (priority 0, latency offset 0 usec, available: no)         properties:
```[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]

---

