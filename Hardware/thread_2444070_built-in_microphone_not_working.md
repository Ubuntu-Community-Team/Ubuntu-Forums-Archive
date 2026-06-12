---
title: "built-in microphone not working"
date: 2020-05-24
forum: Hardware
---

### Post by Sadi58 on 2020-05-24
I've looked at some similar threads but they seem related to specific hardware and/or kernel which doesn't apply to me, so I'd be very grateful if I could use some help here to get my built-in microphone working (which works under the pre-installed Windows 10 by the way). I've never used microphone on this computer that I bought several years ago, so I don't know if the problem emerged recently or has been there all through previous versions of Ubuntu (with different DEs). I've just become aware of it when I tried using Zoom the other day due to the Coronavirus situation.

This is an **ASUS 2-in-1 Q325UA** laptop running K**ubuntu 20.04** with **kernel 5.4.0-31-generic**.
And below are some relevant terminal outputs (no problem with speakers/audio output).

**INXI**
```
Audio: Device-1: Intel Sunrise Point-LP HD Audio vendor: ASUSTeK driver: snd_hda_intel 
           v: kernel bus ID: 00:1f.3 
           Sound Server: ALSA v: k5.4.0-31-generic

```
**DMESG | GREP SND**
```
[    4.132629] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    4.133713] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    4.163992] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC295: line_outs=1 (0x17/0x0/0x0/0x0/0x0) type:speaker
[    4.163994] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    4.163995] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    4.163996] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    4.163996] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    4.163997] snd_hda_codec_realtek hdaudioC0D0:      Headset Mic=0x19
[    4.163998] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12

```**AMIXER**
```
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Headset Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 1 [33%] [10.00dB]
  Front Right: 1 [33%] [10.00dB]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.00dB]
  Front Right: 3 [100%] [30.00dB]

```
**PACMD LIST-SOURCES**
```
2 source(s) available.
    index: 0
        name: <alsa_output.pci-0000_00_1f.3.analog-stereo.monitor>
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
        max rewind: 7 KiB
        sample spec: s16le 2ch 48000Hz
        channel map: front-left,front-right
                     Stereo
        used by: 1
        linked by: 1
        configured latency: 40.00 ms; range is 0.50 .. 341.33 ms
        monitor_of: 0
        card: 0 <alsa_card.pci-0000_00_1f.3>
        module: 7
        properties:
                device.description = "Monitor of Built-in Audio Analog Stereo"
                device.class = "monitor"
                alsa.card = "0"
                alsa.card_name = "HDA Intel PCH"
                alsa.long_card_name = "HDA Intel PCH at 0xef128000 irq 133"
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
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
  * index: 1
        name: <alsa_input.pci-0000_00_1f.3.analog-stereo>
        driver: <module-alsa-card.c>
        flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
        state: RUNNING
        suspend cause: (none)
        priority: 9039
        volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
                balance 0.00
        base volume: 6554 /  10% / -60.00 dB
        volume steps: 65537
        muted: no
        current latency: 0.54 ms
        max rewind: 0 KiB
        sample spec: s16le 2ch 44100Hz
        channel map: front-left,front-right
                     Stereo
        used by: 1
        linked by: 1
        configured latency: 40.00 ms; range is 1.00 .. 371.52 ms
        card: 0 <alsa_card.pci-0000_00_1f.3>
        module: 7
        properties:
                alsa.resolution_bits = "16"
                device.api = "alsa"
                device.class = "sound"
                alsa.class = "generic"
                alsa.subclass = "generic-mix"
                alsa.name = "ALC295 Analog"
                alsa.id = "ALC295 Analog"
                alsa.subdevice = "0"
                alsa.subdevice_name = "subdevice #0"
                alsa.device = "0"
                alsa.card = "0"
                alsa.card_name = "HDA Intel PCH"
                alsa.long_card_name = "HDA Intel PCH at 0xef128000 irq 133"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1f.3"
                sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "9d71"
                device.product.name = "Sunrise Point-LP HD Audio"
                device.form_factor = "internal"
                device.string = "front:0"
                device.buffering.buffer_size = "65536"
                device.buffering.fragment_size = "32768"
                device.access_mode = "mmap+timer"
                device.profile.name = "analog-stereo"
                device.profile.description = "Analog Stereo"
                device.description = "Built-in Audio Analog Stereo"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        ports:
                analog-input-internal-mic: Internal Microphone (priority 8900, latency offset 0 usec, available: yes)
                        properties:
                                device.icon_name = "audio-input-microphone"
                analog-input-headset-mic: Headset Microphone (priority 8800, latency offset 0 usec, available: yes)
                        properties:
                                device.icon_name = "audio-input-microphone"
        active port: <analog-input-internal-mic>

```

---

### Post by TheFu on 2020-05-24
I'm not an expert, but ... a monitor isn't a microphone.

Run :
```
$ pacmd list-sources | grep input
        name: <**alsa_input.usb-046d_HD_Pro_Webcam_C920_76B4D93F-02.analog-stereo.2**>
                analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: unknown)
                                device.icon_name = "audio-input-microphone"
        active port: <analog-input-mic>
        name: <**alsa_input.usb-Samson_Technologies_Samson_GoMic-00.analog-stereo**>
                analog-input-mic: Microphone (priority 8700, latency offset -20000 usec, available: unknown)
                                device.icon_name = "audio-input-microphone"
        active port: <analog-input-mic>
```

See the **name:** lines? Take the one you want to use and and set the default input ...
```
$ pacmd set-default-source alsa_input.usb-046d_HD_Pro_Webcam_C920_76B4D93F-02.analog-stereo.2
```
or
```
$ pacmd set-default-source alsa_input.usb-Samson_Technologies_Samson_GoMic-00.analog-stereo
```

If you don't have a _name:_, then I haven't a clue besides to ensure the microphone is enabled in the far-right tab of **pavucontrol**.

---

### Post by Sadi58 on 2020-05-24
[SIZE=3]_[FONT=century gothic]Finally solved after adding[/FONT]_[/SIZE]
[SIZE=3][FONT=lucida console]**options snd-hda-intel model=thinkpad**[/FONT][/SIZE]
[SIZE=3][FONT=century gothic]_at the end of_[/FONT][/SIZE]
 [SIZE=3][FONT=lucida console]**/etc/modprobe.d/alsa-base.conf**[/FONT][/SIZE]
[SIZE=3][FONT=century gothic]and restarting the computer. [/FONT][/SIZE];)

---

### Post by Sadi58 on 2020-05-24
Thanks TheFu!
I have no idea what that source 0 is for, but probably my built-in mic is source 1.
I have no other hardware problems (sound output etc.); source 0 might have something to do with external monitor which might have (or not) speakers, just a wild guess as I'm not an expert either. ;-)

---

### Post by TheFu on 2020-05-24
Telling an Asus system that it is a thinkpad probably isn't really the best answer.

---

### Post by Sadi58 on 2020-05-24
> **TheFu said:**
> Telling an Asus system that it is a thinkpad probably isn't really the best answer.

I know, it sounds kind of funny, but I think it's not important (looking at similar threads replied by experts), it works, that's what counts. :-)

---

