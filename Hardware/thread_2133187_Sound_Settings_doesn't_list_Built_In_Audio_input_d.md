---
title: "Sound Settings doesn't list Built In Audio input device (but pavucontrol does)"
date: 2013-04-07
forum: Hardware
---

### Post by bitterjug on 2013-04-07
Ubuntu (12.10) thinks I don't have any input audio devices.  When I open Sound Settings and pick the 'Input' tab, there is nothing in the 'Record sound from' box. I can't record my voice or make skype calls, etc.

This is a Fujitsu T5010 laptop with stereo mics built in. 
```
$ uname -a
Linux fuji 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:18:20 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

Pulse audio knows about the card, and its input ports:
```
Welcome to PulseAudio! Use "help" for usage information.
>>> list-cards
1 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_00_1b.0>
    driver: <module-alsa-card.c>
    owner module: 4
    properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel"
        alsa.long_card_name = "HDA Intel at 0xf2720000 irq 47"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.name = "82801I (ICH9 Family) HD Audio Controller"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        output:analog-stereo: Analogue Stereo Output (priority 6000)
        output:analog-stereo+input:analog-stereo: Analogue Stereo Duplex (priority 6060)
        output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400)
        output:hdmi-stereo+input:analog-stereo: Digital Stereo (HDMI) Output + Analogue Stereo Input (priority 5460)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 300)
        output:hdmi-surround+input:analog-stereo: Digital Surround 5.1 (HDMI) Output + Analogue Stereo Input (priority 360)
        input:analog-stereo: Analogue Stereo Input (priority 60)
        off: Off (priority 0)
    active profile: <output:analog-stereo+input:analog-stereo>
    sinks:
        alsa_output.pci-0000_00_1b.0.analog-stereo/#0: Built-in Audio Analogue Stereo
    sources:
        alsa_output.pci-0000_00_1b.0.analog-stereo.monitor/#0: Monitor of Built-in Audio Analogue Stereo
        alsa_input.pci-0000_00_1b.0.analog-stereo/#1: Built-in Audio Analogue Stereo
    ports:
        analog-output-speaker: Speakers (priority 10000, available: unknown)
            properties:
                
        analog-output-headphones: Headphones (priority 9000, available: no)
            properties:
                
        analog-input-microphone-dock: Dock Microphone (priority 7800, available: no)
            properties:
                
        analog-input-microphone: Microphone (priority 8700, available: no)
            properties:
                
        hdmi-output-0: HDMI / DisplayPort (priority 5900, available: no)
            properties:
                
>>> 
```

And if I run pavucontrol, my built-in microphone is listed under Input Devices; and I can tell by watching the levels that it can hear sounds in the room.

Since Pulse Audio knows about my sound card and Mic, I'm guessing I can make it show up in the Ubuntu sound settings with a configuration change, but I have no idea how to make that change. Can anyone advise?
Thanks

---

