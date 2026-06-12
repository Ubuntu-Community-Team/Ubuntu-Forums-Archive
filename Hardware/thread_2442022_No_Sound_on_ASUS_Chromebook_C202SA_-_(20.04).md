---
title: "No Sound on ASUS Chromebook C202SA - (20.04)"
date: 2020-04-28
forum: Hardware
---

### Post by fedemw on 2020-04-28
Hello Ubuntu/Gallium Community!

Thank you for helping me with this audio issue (speaker & mic) on my kid's Chromebook laptop. 

[B]**Hardware**:
[/B]ASUS Chromebook C202SA (TERRA, 2016, Intel Braswell).

[B]**Firmware**: 
[/B]Updated to: Full Firmware [UEFI] (all) / RW_LEGACY (all)). Source: [https://wiki.galliumos.org/Firmware](https://wiki.galliumos.org/Firmware).

[B]**OS**: 
[/B]UBUNTU MATE 20.04 (ISO install).

[B]**Issue**: 
[/B]Sound works well on Gallium OS. 
With Ubuntu Mate, everything seems to be working fine on my system except audio. The system doesn't appear to see my sound card. The only interface I have is Dummy Audio. 

[B]**Terminal Outputs:**
[/B]
[B]**brylen@terra:~$ pulseaudio**
[/B]```
>     E: [pulseaudio] pid.c: Daemon already running.
>     E: [pulseaudio] main.c: pa_pid_file_create() failed.

```

[B]**brylen@terra:~$ arecord -l**
[/B]```
>     **** List of CAPTURE Hardware Devices ****
>     card 1: chtrt5650 [chtrt5650], device 0: Audio (*) []
>       Subdevices: 1/1
>       Subdevice #0: subdevice #0

```

[B]**brylen@terra:~$ aplay -l**
[/B] ```
 >   **** List of PLAYBACK Hardware Devices ****
>     card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
>       Subdevices: 1/1
>       Subdevice #0: subdevice #0
>     card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
>       Subdevices: 1/1
>       Subdevice #0: subdevice #0
>     card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
>       Subdevices: 1/1
>       Subdevice #0: subdevice #0
>     card 1: chtrt5650 [chtrt5650], device 0: Audio (*) []
>       Subdevices: 1/1
>       Subdevice #0: subdevice #0
>     card 1: chtrt5650 [chtrt5650], device 1: Deep-Buffer Audio (*) []
>       Subdevices: 1/1
>       Subdevice #0: subdevice #0
```

**brylen@terra:~$ pacmd list-cards**
 ```
   > 1 card(s) available.
>         index: 0
>         name: <alsa_card.pci-0000_00_1b.0>
>         driver: <module-alsa-card.c>
>         owner module: 7
>         properties:
>             alsa.card = "0"
>             alsa.card_name = "HDA Intel PCH"
>             alsa.long_card_name = "HDA Intel PCH at 0xd1314000 irq 314"
>             alsa.driver_name = "snd_hda_intel"
>             device.bus_path = "pci-0000:00:1b.0"
>             sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
>             device.bus = "pci"
>             device.vendor.id = "8086"
>             device.vendor.name = "Intel Corporation"
>             device.product.id = "2284"
>             device.product.name = "Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller"
>             device.form_factor = "internal"
>             device.string = "0"
>             device.description = "Built-in Audio"
>             module-udev-detect.discovered = "1"
>             device.icon_name = "audio-card-pci"
>         profiles:
>             output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5900, available: no)
>             output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 800, available: no)
>             output:hdmi-surround71: Digital Surround 7.1 (HDMI) Output (priority 800, available: no)
>             output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Output (priority 5700, available: no)
>             output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Output (priority 600, available: no)
>             output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Output (priority 600, available: no)
>             output:hdmi-stereo-extra2: Digital Stereo (HDMI 3) Output (priority 5700, available: no)
>             output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI 3) Output (priority 600, available: no)
>             output:hdmi-surround71-extra2: Digital Surround 7.1 (HDMI 3) Output (priority 600, available: no)
>             off: Off (priority 0, available: unknown)
>         active profile: <off>
>         ports:
>             hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
>                 properties:
>                     device.icon_name = "video-display"
>             hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
>                 properties:
>                     device.icon_name = "video-display"
>             hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, latency offset 0 usec, available: no)
>                 properties:
>                     device.icon_name = "video-display"
```

[B]**We have done this:**
[/B][https://github.com/bliutwo/dummy-sound-fix-ubuntu](https://github.com/bliutwo/dummy-sound-fix-ubuntu). But we have had no luck! :-(

We are looking forward to your help!

Thanks in advance!

A desperate Linux fan!

[ATTACH=CONFIG]285657[/ATTACH][ATTACH=CONFIG]285658[/ATTACH][ATTACH=CONFIG]285659[/ATTACH][ATTACH=CONFIG]285661[/ATTACH][ATTACH=CONFIG]285662[/ATTACH]

---

