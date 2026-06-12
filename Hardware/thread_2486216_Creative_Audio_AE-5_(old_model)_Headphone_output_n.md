---
title: "Creative Audio AE-5 (old model) Headphone output not working."
date: 2023-04-23
forum: Hardware
---

### Post by lepeletie on 2023-04-23
Hi Team,

This is my first post here. So, sorry for any inconvenience.

I just installed Ubuntu 22.04.2 LTS and faced a problem with my Creative Audio sound card AE-5. The card itself is definitely working. I use its headphone output. However, in Ubuntu I hear nothing from it. It is just plain silent. What I tried so far:

In alsamixer I enabled "HP/Speakers Auto Detect" and set Output as "Headphon".
[IMG]https://drive.google.com/file/d/1lo0fkQ21cXIr14GwbF6pzVHbo0aKSpTC/view?usp=sharing[/IMG]
[IMG]https://drive.google.com/file/d/1lo0fkQ21cXIr14GwbF6pzVHbo0aKSpTC/view?usp=sharing[/IMG]
[https://drive.google.com/file/d/1lo0fkQ21cXIr14GwbF6pzVHbo0aKSpTC/view?usp=sharing](https://drive.google.com/file/d/1lo0fkQ21cXIr14GwbF6pzVHbo0aKSpTC/view?usp=sharing)

I tried reinstalling pulseaudio a few times with and without my USB Creative SB Live card connected

I installed libcanberra-pulse as it was suggested in some posts

I tried different audio outs in pavucontrol
[https://drive.google.com/file/d/1iM9JslsJIkwFLzvJeBegEGWZ5mqplAI7/view?usp=sharing](https://drive.google.com/file/d/1iM9JslsJIkwFLzvJeBegEGWZ5mqplAI7/view?usp=sharing)
[https://drive.google.com/file/d/1W4Im2tw-PcloZ0EzygearvtmfnNBkmfK/view?usp=sharing](https://drive.google.com/file/d/1W4Im2tw-PcloZ0EzygearvtmfnNBkmfK/view?usp=sharing)

I selected the Headphones on AE-5 as a default output device in System Audio Settings
[https://drive.google.com/file/d/1efiDtlycBhIW2UKv6WPiT3IvLsMDCSyd/view?usp=share_link](https://drive.google.com/file/d/1efiDtlycBhIW2UKv6WPiT3IvLsMDCSyd/view?usp=share_link)

Even though I can clearly see that the headphones are detected and active, there is no sound
[https://drive.google.com/file/d/1w-E6TFSLQSpHN66QcQFxhEyvVSWHC7li/view?usp=share_link](https://drive.google.com/file/d/1w-E6TFSLQSpHN66QcQFxhEyvVSWHC7li/view?usp=share_link)

Everything looks fine but no sound.

Here is some of my logs:
alsa-info: [http://alsa-project.org/db/?f=9d1142637e3727d2a0abba95f77ea6d83c88c70e](http://alsa-project.org/db/?f=9d1142637e3727d2a0abba95f77ea6d83c88c70e)
```
~$ lspci | grep 'Audio'
05:00.0 Audio device: Creative Labs Sound Core3D [Sound Blaster Recon3D / Z-Series] (rev 01)
0f:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Navi 10 HDMI Audio



```


```
~$ aplay -Lnull
    Discard all samples (playback) or generate zero samples (capture)
default
    Playback/recording through the PulseAudio sound server
samplerate
    Rate Converter Plugin Using Samplerate Library
speexrate
    Rate Converter Plugin Using Speex Resampler
jack
    JACK Audio Connection Kit
oss
    Open Sound System
pulse
    PulseAudio Sound Server
upmix
    Plugin for channel upmix (4,6,8)
vdownmix
    Plugin for channel downmix (stereo) with a simple spacialization
hw:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    Direct hardware device without any conversions
hw:CARD=Creative,DEV=1
    HDA Creative, CA0132 Digital
    Direct hardware device without any conversions
plughw:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    Hardware device with all software conversions
plughw:CARD=Creative,DEV=1
    HDA Creative, CA0132 Digital
    Hardware device with all software conversions
sysdefault:CARD=Creative
    HDA Creative, CA0132 Analog
    Default Audio Device
front:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    Front output / input
surround21:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Creative,DEV=0
    HDA Creative, CA0132 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Creative,DEV=0
    HDA Creative, CA0132 Analog
    Direct sample mixing device
dmix:CARD=Creative,DEV=1
    HDA Creative, CA0132 Digital
    Direct sample mixing device
usbstream:CARD=Creative
    HDA Creative
    USB Stream Output
hw:CARD=Pro,DEV=0
    SB X-Fi Surround 5.1 Pro, USB Audio
    Direct hardware device without any conversions
hw:CARD=Pro,DEV=1
    SB X-Fi Surround 5.1 Pro, USB Audio #1
    Direct hardware device without any conversions
plughw:CARD=Pro,DEV=0
    SB X-Fi Surround 5.1 Pro, USB Audio
    Hardware device with all software conversions
plughw:CARD=Pro,DEV=1
    SB X-Fi Surround 5.1 Pro, USB Audio #1
    Hardware device with all software conversions
sysdefault:CARD=Pro
    SB X-Fi Surround 5.1 Pro, USB Audio
    Default Audio Device
front:CARD=Pro,DEV=0
    SB X-Fi Surround 5.1 Pro, USB Audio
    Front output / input
surround21:CARD=Pro,DEV=0
    SB X-Fi Surround 5.1 Pro, USB Audio
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=Pro,DEV=0
    SB X-Fi Surround 5.1 Pro, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Pro,DEV=0
    SB X-Fi Surround 5.1 Pro, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Pro,DEV=0
    SB X-Fi Surround 5.1 Pro, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Pro,DEV=0
    SB X-Fi Surround 5.1 Pro, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Pro,DEV=0
    SB X-Fi Surround 5.1 Pro, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Pro,DEV=0
    SB X-Fi Surround 5.1 Pro, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
iec958:CARD=Pro,DEV=1
    SB X-Fi Surround 5.1 Pro, USB Audio #1
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Pro,DEV=0
    SB X-Fi Surround 5.1 Pro, USB Audio
    Direct sample mixing device
dmix:CARD=Pro,DEV=1
    SB X-Fi Surround 5.1 Pro, USB Audio #1
    Direct sample mixing device
usbstream:CARD=Pro
    SB X-Fi Surround 5.1 Pro
    USB Stream Output
hw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=7
    HDA ATI HDMI, HDMI 1
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=8
    HDA ATI HDMI, HDMI 2
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=9
    HDA ATI HDMI, HDMI 3
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=10
    HDA ATI HDMI, HDMI 4
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=11
    HDA ATI HDMI, HDMI 5
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=7
    HDA ATI HDMI, HDMI 1
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=8
    HDA ATI HDMI, HDMI 2
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=9
    HDA ATI HDMI, HDMI 3
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=10
    HDA ATI HDMI, HDMI 4
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=11
    HDA ATI HDMI, HDMI 5
    Hardware device with all software conversions
hdmi:CARD=HDMI,DEV=0
    HDA ATI HDMI, HDMI 0
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=1
    HDA ATI HDMI, HDMI 1
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=2
    HDA ATI HDMI, HDMI 2
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 3
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=4
    HDA ATI HDMI, HDMI 4
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=5
    HDA ATI HDMI, HDMI 5
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample mixing device
dmix:CARD=HDMI,DEV=7
    HDA ATI HDMI, HDMI 1
    Direct sample mixing device
dmix:CARD=HDMI,DEV=8
    HDA ATI HDMI, HDMI 2
    Direct sample mixing device
dmix:CARD=HDMI,DEV=9
    HDA ATI HDMI, HDMI 3
    Direct sample mixing device
dmix:CARD=HDMI,DEV=10
    HDA ATI HDMI, HDMI 4
    Direct sample mixing device
dmix:CARD=HDMI,DEV=11
    HDA ATI HDMI, HDMI 5
    Direct sample mixing device
usbstream:CARD=HDMI
    HDA ATI HDMI
    USB Stream Output
usbstream:CARD=StudioTM
    Microsoft® LifeCam Studio(TM)
    USB Stream Output



```

```
~$ pacmd list-cards4 card(s) available.
    index: 0
    name: <alsa_card.usb-Creative_Technology_Ltd_SB_X-Fi_Surround_5.1_Pro_0000045Y-00>
    driver: <module-alsa-card.c>
    owner module: 19
    properties:
        alsa.card = "1"
        alsa.card_name = "SB X-Fi Surround 5.1 Pro"
        alsa.long_card_name = "Creative Technology Ltd SB X-Fi Surround 5.1 Pro at usb-0000:0a:00.1-3.1, full"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:0a:00.1-usb-0:3.1:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:0a:00.1/usb3/3-3/3-3.1/3-3.1:1.0/sound/card1"
        udev.id = "usb-Creative_Technology_Ltd_SB_X-Fi_Surround_5.1_Pro_0000045Y-00"
        device.bus = "usb"
        device.vendor.id = "041e"
        device.vendor.name = "Creative Technology, Ltd"
        device.product.id = "30df"
        device.product.name = "SB X-Fi Surround 5.1 Pro"
        device.serial = "Creative_Technology_Ltd_SB_X-Fi_Surround_5.1_Pro_0000045Y"
        device.string = "1"
        device.description = "SB X-Fi Surround 5.1 Pro"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"
    profiles:
        input:analog-stereo: Analog Stereo Input (priority 65, available: unknown)
        input:iec958-stereo: Digital Stereo (IEC958) Input (priority 55, available: unknown)
        output:analog-stereo: Analog Stereo Output (priority 6500, available: unknown)
        output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6565, available: unknown)
        output:analog-stereo+input:iec958-stereo: Analog Stereo Output + Digital Stereo (IEC958) Input (priority 6555, available: unknown)
        output:analog-surround-21: Analog Surround 2.1 Output (priority 1300, available: unknown)
        output:analog-surround-21+input:analog-stereo: Analog Surround 2.1 Output + Analog Stereo Input (priority 1365, available: unknown)
        output:analog-surround-21+input:iec958-stereo: Analog Surround 2.1 Output + Digital Stereo (IEC958) Input (priority 1355, available: unknown)
        output:analog-surround-41: Analog Surround 4.1 Output (priority 1300, available: unknown)
        output:analog-surround-41+input:analog-stereo: Analog Surround 4.1 Output + Analog Stereo Input (priority 1365, available: unknown)
        output:analog-surround-41+input:iec958-stereo: Analog Surround 4.1 Output + Digital Stereo (IEC958) Input (priority 1355, available: unknown)
        output:analog-surround-50: Analog Surround 5.0 Output (priority 1200, available: unknown)
        output:analog-surround-50+input:analog-stereo: Analog Surround 5.0 Output + Analog Stereo Input (priority 1265, available: unknown)
        output:analog-surround-50+input:iec958-stereo: Analog Surround 5.0 Output + Digital Stereo (IEC958) Input (priority 1255, available: unknown)
        output:analog-surround-51: Analog Surround 5.1 Output (priority 1300, available: unknown)
        output:analog-surround-51+input:analog-stereo: Analog Surround 5.1 Output + Analog Stereo Input (priority 1365, available: unknown)
        output:analog-surround-51+input:iec958-stereo: Analog Surround 5.1 Output + Digital Stereo (IEC958) Input (priority 1355, available: unknown)
        output:iec958-stereo: Digital Stereo (IEC958) Output (priority 5500, available: unknown)
        output:iec958-stereo+input:analog-stereo: Digital Stereo (IEC958) Output + Analog Stereo Input (priority 5565, available: unknown)
        output:iec958-stereo+input:iec958-stereo: Digital Stereo Duplex (IEC958) (priority 5555, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <output:analog-stereo+input:analog-stereo>
    sinks:
        alsa_output.usb-Creative_Technology_Ltd_SB_X-Fi_Surround_5.1_Pro_0000045Y-00.analog-stereo/#1: SB X-Fi Surround 5.1 Pro Analog Stereo
    sources:
        alsa_output.usb-Creative_Technology_Ltd_SB_X-Fi_Surround_5.1_Pro_0000045Y-00.analog-stereo.monitor/#1: Monitor of SB X-Fi Surround 5.1 Pro Analog Stereo
        alsa_input.usb-Creative_Technology_Ltd_SB_X-Fi_Surround_5.1_Pro_0000045Y-00.analog-stereo/#2: SB X-Fi Surround 5.1 Pro Analog Stereo
    ports:
        analog-input: Analog Input (priority 10000, latency offset 0 usec, available: unknown)
            properties:
                
        iec958-stereo-input: Digital Input (S/PDIF) (priority 0, latency offset 0 usec, available: unknown)
            properties:
                
        analog-output: Analog Output (priority 9900, latency offset 0 usec, available: unknown)
            properties:
                
        iec958-stereo-output: Digital Output (S/PDIF) (priority 0, latency offset 0 usec, available: unknown)
            properties:
                
    index: 1
    name: <alsa_card.pci-0000_05_00.0>
    driver: <module-alsa-card.c>
    owner module: 20
    properties:
        alsa.card = "0"
        alsa.card_name = "HDA Creative"
        alsa.long_card_name = "HDA Creative at 0xfc804000 irq 41"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:05:00.0"
        sysfs.path = "/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:01.0/0000:05:00.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "1102"
        device.vendor.name = "Creative Labs"
        device.product.id = "0012"
        device.product.name = "Sound Core3D [Sound Blaster Recon3D / Z-Series]"
        device.string = "0"
        device.description = "Sound Core3D [Sound Blaster Recon3D / Z-Series]"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        input:analog-stereo: Analog Stereo Input (priority 32833, available: unknown)
        output:analog-stereo: Analog Stereo Output (priority 39268, available: unknown)
        output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 39333, available: unknown)
        output:analog-surround-21: Analog Surround 2.1 Output (priority 1300, available: no)
        output:analog-surround-21+input:analog-stereo: Analog Surround 2.1 Output + Analog Stereo Input (priority 1365, available: unknown)
        output:analog-surround-40: Analog Surround 4.0 Output (priority 1200, available: no)
        output:analog-surround-40+input:analog-stereo: Analog Surround 4.0 Output + Analog Stereo Input (priority 1265, available: unknown)
        output:analog-surround-41: Analog Surround 4.1 Output (priority 1300, available: no)
        output:analog-surround-41+input:analog-stereo: Analog Surround 4.1 Output + Analog Stereo Input (priority 1365, available: unknown)
        output:analog-surround-50: Analog Surround 5.0 Output (priority 1200, available: no)
        output:analog-surround-50+input:analog-stereo: Analog Surround 5.0 Output + Analog Stereo Input (priority 1265, available: unknown)
        output:analog-surround-51: Analog Surround 5.1 Output (priority 1300, available: no)
        output:analog-surround-51+input:analog-stereo: Analog Surround 5.1 Output + Analog Stereo Input (priority 1365, available: unknown)
        output:iec958-stereo: Digital Stereo (IEC958) Output (priority 38268, available: unknown)
        output:iec958-stereo+input:analog-stereo: Digital Stereo (IEC958) Output + Analog Stereo Input (priority 38333, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <output:analog-stereo+input:analog-stereo>
    sinks:
        alsa_output.pci-0000_05_00.0.analog-stereo/#2: Sound Core3D [Sound Blaster Recon3D / Z-Series] Analog Stereo
    sources:
        alsa_output.pci-0000_05_00.0.analog-stereo.monitor/#3: Monitor of Sound Core3D [Sound Blaster Recon3D / Z-Series] Analog Stereo
        alsa_input.pci-0000_05_00.0.analog-stereo/#4: Sound Core3D [Sound Blaster Recon3D / Z-Series] Analog Stereo
    ports:
        analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-linein: Line In (priority 8100, latency offset 0 usec, available: unknown)
            properties:
                
        analog-output-lineout: Line Out (priority 9000, latency offset 0 usec, available: no)
            properties:
                
        analog-output-headphones: Headphones (priority 9900, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "audio-headphones"
        iec958-stereo-output: Digital Output (S/PDIF) (priority 0, latency offset 0 usec, available: unknown)
            properties:
                
    index: 2
    name: <alsa_card.usb-Microsoft_Microsoft___LifeCam_Studio_TM_-02>
    driver: <module-alsa-card.c>
    owner module: 21
    properties:
        alsa.card = "3"
        alsa.card_name = "Microsoft® LifeCam Studio(TM)"
        alsa.long_card_name = "Microsoft Microsoft® LifeCam Studio(TM) at usb-0000:0a:00.1-3.3, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:0a:00.1-usb-0:3.3:1.2"
        sysfs.path = "/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:0a:00.1/usb3/3-3/3-3.3/3-3.3:1.2/sound/card3"
        udev.id = "usb-Microsoft_Microsoft®_LifeCam_Studio_TM_-02"
        device.bus = "usb"
        device.vendor.id = "045e"
        device.vendor.name = "Microsoft Corp."
        device.product.id = "0811"
        device.product.name = "Microsoft® LifeCam Studio(TM)"
        device.serial = "Microsoft_Microsoft®_LifeCam_Studio_TM_"
        device.form_factor = "webcam"
        device.string = "3"
        device.description = "Microsoft® LifeCam Studio(TM)"
        module-udev-detect.discovered = "1"
        device.icon_name = "camera-web-usb"
    profiles:
        input:mono-fallback: Mono Input (priority 1, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <input:mono-fallback>
    sources:
        alsa_input.usb-Microsoft_Microsoft___LifeCam_Studio_TM_-02.mono-fallback/#5: Microsoft® LifeCam Studio(TM) Mono
    ports:
        analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
    index: 3
    name: <alsa_card.pci-0000_0f_00.1>
    driver: <module-alsa-card.c>
    owner module: 22
    properties:
        alsa.card = "2"
        alsa.card_name = "HDA ATI HDMI"
        alsa.long_card_name = "HDA ATI HDMI at 0xfcda0000 irq 191"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:0f:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:03.1/0000:0d:00.0/0000:0e:00.0/0000:0f:00.1/sound/card2"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "ab38"
        device.product.name = "Navi 10 HDMI Audio"
        device.string = "2"
        device.description = "Navi 10 HDMI Audio"
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
        output:hdmi-stereo-extra3: Digital Stereo (HDMI 4) Output (priority 38468, available: unknown)
        output:hdmi-stereo-extra4: Digital Stereo (HDMI 5) Output (priority 5700, available: no)
        output:hdmi-surround-extra4: Digital Surround 5.1 (HDMI 5) Output (priority 600, available: no)
        output:hdmi-surround71-extra4: Digital Surround 7.1 (HDMI 5) Output (priority 600, available: no)
        output:hdmi-stereo-extra5: Digital Stereo (HDMI 6) Output (priority 5700, available: no)
        output:hdmi-surround-extra5: Digital Surround 5.1 (HDMI 6) Output (priority 600, available: no)
        output:hdmi-surround71-extra5: Digital Surround 7.1 (HDMI 6) Output (priority 600, available: no)
        off: Off (priority 0, available: unknown)
    active profile: <output:hdmi-stereo-extra3>
    sinks:
        alsa_output.pci-0000_0f_00.1.hdmi-stereo-extra3/#4: Navi 10 HDMI Audio Digital Stereo (HDMI 4)
    sources:
        alsa_output.pci-0000_0f_00.1.hdmi-stereo-extra3.monitor/#7: Monitor of Navi 10 HDMI Audio Digital Stereo (HDMI 4)
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
        hdmi-output-3: HDMI / DisplayPort 4 (priority 5600, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "video-display"
                device.product.name = "VZ27A"
        hdmi-output-4: HDMI / DisplayPort 5 (priority 5500, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-5: HDMI / DisplayPort 6 (priority 5400, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"



```
[IMG]https://drive.google.com/file/d/1iM9JslsJIkwFLzvJeBegEGWZ5mqplAI7/view?usp=sharing[/IMG]

---

