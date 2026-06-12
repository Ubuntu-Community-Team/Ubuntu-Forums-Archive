---
title: "No HDMI audio"
date: 2017-04-13
forum: Hardware
---

### Post by xolott on 2017-04-13
I have no HDMI audio output wit my LG 4K TV as a display (With windows 10 works just fine) I tried multiple fix, guides, how to's, etc, related with this subject but nothing work.


I tried upgrading to the latest 4.11RC6 kernel with no luck. This are my outputs:
```


    jose@desktop:~$ aplay -L
    default
        Playback/recording through the PulseAudio sound server
    null
        Discard all samples (playback) or generate zero samples (capture)
    pulse
        PulseAudio Sound Server
    sysdefault:CARD=PCH
        HDA Intel PCH, ALC1220 Analog
        Default Audio Device
    front:CARD=PCH,DEV=0
        HDA Intel PCH, ALC1220 Analog
        Front speakers
    surround21:CARD=PCH,DEV=0
        HDA Intel PCH, ALC1220 Analog
        2.1 Surround output to Front and Subwoofer speakers
    surround40:CARD=PCH,DEV=0
        HDA Intel PCH, ALC1220 Analog
        4.0 Surround output to Front and Rear speakers
    surround41:CARD=PCH,DEV=0
        HDA Intel PCH, ALC1220 Analog
        4.1 Surround output to Front, Rear and Subwoofer speakers
    surround50:CARD=PCH,DEV=0
        HDA Intel PCH, ALC1220 Analog
        5.0 Surround output to Front, Center and Rear speakers
    surround51:CARD=PCH,DEV=0
        HDA Intel PCH, ALC1220 Analog
        5.1 Surround output to Front, Center, Rear and Subwoofer speakers
    surround71:CARD=PCH,DEV=0
        HDA Intel PCH, ALC1220 Analog
        7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
    iec958:CARD=PCH,DEV=0
        HDA Intel PCH, ALC1220 Digital
        IEC958 (S/PDIF) Digital Audio Output
    hdmi:CARD=PCH,DEV=0
        HDA Intel PCH, HDMI 0
        HDMI Audio Output
    hdmi:CARD=PCH,DEV=1
        HDA Intel PCH, HDMI 1
        HDMI Audio Output
    hdmi:CARD=PCH,DEV=2
        HDA Intel PCH, HDMI 2
        HDMI Audio Output
    hdmi:CARD=PCH,DEV=3
        HDA Intel PCH, HDMI 3
        HDMI Audio Output
    hdmi:CARD=PCH,DEV=4
        HDA Intel PCH, HDMI 4
        HDMI Audio Output
    dmix:CARD=PCH,DEV=0
        HDA Intel PCH, ALC1220 Analog
        Direct sample mixing device
    dmix:CARD=PCH,DEV=1
        HDA Intel PCH, ALC1220 Digital
        Direct sample mixing device
    dmix:CARD=PCH,DEV=3
        HDA Intel PCH, HDMI 0
        Direct sample mixing device
    dmix:CARD=PCH,DEV=7
        HDA Intel PCH, HDMI 1
        Direct sample mixing device
    dmix:CARD=PCH,DEV=8
        HDA Intel PCH, HDMI 2
        Direct sample mixing device
    dmix:CARD=PCH,DEV=9
        HDA Intel PCH, HDMI 3
        Direct sample mixing device
    dmix:CARD=PCH,DEV=10
        HDA Intel PCH, HDMI 4
        Direct sample mixing device
    dsnoop:CARD=PCH,DEV=0
        HDA Intel PCH, ALC1220 Analog
        Direct sample snooping device
    dsnoop:CARD=PCH,DEV=1
        HDA Intel PCH, ALC1220 Digital
        Direct sample snooping device
    dsnoop:CARD=PCH,DEV=3
        HDA Intel PCH, HDMI 0
        Direct sample snooping device
    dsnoop:CARD=PCH,DEV=7
        HDA Intel PCH, HDMI 1
        Direct sample snooping device
    dsnoop:CARD=PCH,DEV=8
        HDA Intel PCH, HDMI 2
        Direct sample snooping device
    dsnoop:CARD=PCH,DEV=9
        HDA Intel PCH, HDMI 3
        Direct sample snooping device
    dsnoop:CARD=PCH,DEV=10
        HDA Intel PCH, HDMI 4
        Direct sample snooping device
    hw:CARD=PCH,DEV=0
        HDA Intel PCH, ALC1220 Analog
        Direct hardware device without any conversions
    hw:CARD=PCH,DEV=1
        HDA Intel PCH, ALC1220 Digital
        Direct hardware device without any conversions
    hw:CARD=PCH,DEV=3
        HDA Intel PCH, HDMI 0
        Direct hardware device without any conversions
    hw:CARD=PCH,DEV=7
        HDA Intel PCH, HDMI 1
        Direct hardware device without any conversions
    hw:CARD=PCH,DEV=8
        HDA Intel PCH, HDMI 2
        Direct hardware device without any conversions
    hw:CARD=PCH,DEV=9
        HDA Intel PCH, HDMI 3
        Direct hardware device without any conversions
    hw:CARD=PCH,DEV=10
        HDA Intel PCH, HDMI 4
        Direct hardware device without any conversions
    plughw:CARD=PCH,DEV=0
        HDA Intel PCH, ALC1220 Analog
        Hardware device with all software conversions
    plughw:CARD=PCH,DEV=1
        HDA Intel PCH, ALC1220 Digital
        Hardware device with all software conversions
    plughw:CARD=PCH,DEV=3
        HDA Intel PCH, HDMI 0
        Hardware device with all software conversions
    plughw:CARD=PCH,DEV=7
        HDA Intel PCH, HDMI 1
        Hardware device with all software conversions
    plughw:CARD=PCH,DEV=8
        HDA Intel PCH, HDMI 2
        Hardware device with all software conversions
    plughw:CARD=PCH,DEV=9
        HDA Intel PCH, HDMI 3
        Hardware device with all software conversions
    plughw:CARD=PCH,DEV=10
        HDA Intel PCH, HDMI 4
        Hardware device with all software conversions



```With pacmd I get:
```


    jose@desktop:~$ pacmd list-cards 
    1 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_00_1f.3>
    driver: <module-alsa-card.c>
    owner module: 6
    properties:
        alsa.card = "1"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xdf140000 irq 132"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card1"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "a2f0"
        device.form_factor = "internal"
        device.string = "1"
        device.description = "Audio Interno"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        input:analog-stereo: Estéreo analógico Entrada (priority 60, available: unknown)
        output:analog-stereo: Estéreo analógico Salida (priority 6000, available: unknown)
        output:analog-stereo+input:analog-stereo: Estéreo Analógico Dúplex (priority 6060, available: unknown)
        output:analog-surround-21: Análogico envolvente 2.1 Salida (priority 800, available: unknown)
        output:analog-surround-21+input:analog-stereo: Análogico envolvente 2.1 Salida + Estéreo analógico Entrada (priority 860, available: unknown)
        output:analog-surround-40: Analógico envolvente 4.0 Salida (priority 700, available: unknown)
        output:analog-surround-40+input:analog-stereo: Analógico envolvente 4.0 Salida + Estéreo analógico Entrada (priority 760, available: unknown)
        output:analog-surround-41: Analógico envolvente 4.1 Salida (priority 800, available: unknown)
        output:analog-surround-41+input:analog-stereo: Analógico envolvente 4.1 Salida + Estéreo analógico Entrada (priority 860, available: unknown)
        output:analog-surround-50: Analógico envolvente 5.0 Salida (priority 700, available: unknown)
        output:analog-surround-50+input:analog-stereo: Analógico envolvente 5.0 Salida + Estéreo analógico Entrada (priority 760, available: unknown)
        output:analog-surround-51: Analógico envolvente 5.1 Salida (priority 800, available: unknown)
        output:analog-surround-51+input:analog-stereo: Analógico envolvente 5.1 Salida + Estéreo analógico Entrada (priority 860, available: unknown)
        output:analog-surround-71: Analog Surround 7.1 Salida (priority 700, available: unknown)
        output:analog-surround-71+input:analog-stereo: Analog Surround 7.1 Salida + Estéreo analógico Entrada (priority 760, available: unknown)
        output:iec958-stereo: Estéreo Digital (IEC958) Salida (priority 5500, available: unknown)
        output:iec958-stereo+input:analog-stereo: Estéreo Digital (IEC958) Salida + Estéreo analógico Entrada (priority 5560, available: unknown)
        output:hdmi-stereo: Digital Stereo (HDMI) Salida (priority 5400, available: unknown)
        output:hdmi-stereo+input:analog-stereo: Digital Stereo (HDMI) Salida + Estéreo analógico Entrada (priority 5460, available: unknown)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Salida (priority 300, available: unknown)
        output:hdmi-surround+input:analog-stereo: Digital Surround 5.1 (HDMI) Salida + Estéreo analógico Entrada (priority 360, available: unknown)
        output:hdmi-surround71: Digital Surround 7.1 (HDMI) Salida (priority 300, available: unknown)
        output:hdmi-surround71+input:analog-stereo: Digital Surround 7.1 (HDMI) Salida + Estéreo analógico Entrada (priority 360, available: unknown)
        output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Salida (priority 5200, available: unknown)
        output:hdmi-stereo-extra1+input:analog-stereo: Digital Stereo (HDMI 2) Salida + Estéreo analógico Entrada (priority 5260, available: unknown)
        output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Salida (priority 100, available: unknown)
        output:hdmi-surround-extra1+input:analog-stereo: Digital Surround 5.1 (HDMI 2) Salida + Estéreo analógico Entrada (priority 160, available: unknown)
        output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Salida (priority 100, available: unknown)
        output:hdmi-surround71-extra1+input:analog-stereo: Digital Surround 7.1 (HDMI 2) Salida + Estéreo analógico Entrada (priority 160, available: unknown)
        output:hdmi-stereo-extra2: Digital Stereo (HDMI 3) Salida (priority 5200, available: unknown)
        output:hdmi-stereo-extra2+input:analog-stereo: Digital Stereo (HDMI 3) Salida + Estéreo analógico Entrada (priority 5260, available: unknown)
        output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI 3) Salida (priority 100, available: unknown)
        output:hdmi-surround-extra2+input:analog-stereo: Digital Surround 5.1 (HDMI 3) Salida + Estéreo analógico Entrada (priority 160, available: unknown)
        output:hdmi-stereo-extra3: Digital Stereo (HDMI 4) Salida (priority 5200, available: unknown)
        output:hdmi-stereo-extra3+input:analog-stereo: Digital Stereo (HDMI 4) Salida + Estéreo analógico Entrada (priority 5260, available: unknown)
        output:hdmi-surround-extra3: Digital Surround 5.1 (HDMI 4) Salida (priority 100, available: unknown)
        output:hdmi-surround-extra3+input:analog-stereo: Digital Surround 5.1 (HDMI 4) Salida + Estéreo analógico Entrada (priority 160, available: unknown)
        output:hdmi-surround71-extra3: Digital Surround 7.1 (HDMI 4) Salida (priority 100, available: unknown)
        output:hdmi-surround71-extra3+input:analog-stereo: Digital Surround 7.1 (HDMI 4) Salida + Estéreo analógico Entrada (priority 160, available: unknown)
        output:hdmi-stereo-extra4: Digital Stereo (HDMI 5) Salida (priority 5200, available: unknown)
        output:hdmi-stereo-extra4+input:analog-stereo: Digital Stereo (HDMI 5) Salida + Estéreo analógico Entrada (priority 5260, available: unknown)
        output:hdmi-surround-extra4: Digital Surround 5.1 (HDMI 5) Salida (priority 100, available: unknown)
        output:hdmi-surround-extra4+input:analog-stereo: Digital Surround 5.1 (HDMI 5) Salida + Estéreo analógico Entrada (priority 160, available: unknown)
        output:hdmi-surround71-extra4: Digital Surround 7.1 (HDMI 5) Salida (priority 100, available: unknown)
        output:hdmi-surround71-extra4+input:analog-stereo: Digital Surround 7.1 (HDMI 5) Salida + Estéreo analógico Entrada (priority 160, available: unknown)
        off: Apagado (priority 0, available: unknown)
    active profile: <output:hdmi-stereo-extra2>
    sinks:
        alsa_output.pci-0000_00_1f.3.hdmi-stereo-extra2/#0: Audio Interno Digital Stereo (HDMI 3)
    sources:
        alsa_output.pci-0000_00_1f.3.hdmi-stereo-extra2.monitor/#0: Monitor of Audio Interno Digital Stereo (HDMI 3)
    ports:
        analog-input-front-mic: Micrófono frontal (priority 8500, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-rear-mic: Micrófono trasero (priority 8200, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-linein: En línea (priority 8100, latency offset 0 usec, available: no)
            properties:
                
        analog-output-lineout: Línea de salida (priority 9900, latency offset 0 usec, available: no)
            properties:
                
        analog-output-headphones: Auriculares analógicos (priority 9000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
        iec958-stereo-output: Salida digital (S/PDIF) (priority 0, latency offset 0 usec, available: unknown)
            properties:
                
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "video-display"
                device.product.name = "LG TV"
        hdmi-output-3: HDMI / DisplayPort 4 (priority 5600, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-4: HDMI / DisplayPort 5 (priority 5500, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"

```

I installed pavucontrol, and I can see and select the HDMI audio output, but still no luck.

[IMG]https://i.stack.imgur.com/UmVD1.png[/IMG]



I tried reinstalling Ubuntu (16.04 and 16.10), same result. Just now, I will install the recent 17.04 version.


Just to clarify, I have only 1 HDMI output port and 1 DisplayPort output port.


Any hint on what can I do to solve this issue?

---

