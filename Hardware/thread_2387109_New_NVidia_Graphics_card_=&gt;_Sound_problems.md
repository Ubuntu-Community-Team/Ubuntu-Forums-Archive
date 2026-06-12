---
title: "New NVidia Graphics card =&gt; Sound problems"
date: 2018-03-14
forum: Hardware
---

### Post by subject117 on 2018-03-14
I just installed a new NVidia Geforce GTX 1080 TI graphics card in an ubuntu machine. I installed the Ubuntu driver and the card works great. The only problem is the sound is not working.

The sound is not going through the graphics card. However I see the card listed here:

```

jim@htpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I also see it here:

```

jim@htpc:~$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xfbff4000 irq 31
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfaffc000 irq 17

```

However when I run the pavucontrol command I only see S/PDIF digital output as the only possible audio option. I tried reinstalling puseaudio but it still doesn't work. What should I try next?

---

### Post by subject117 on 2018-03-14
I made some progress.

In pavucontrol I went to the Configuration tab and set the Built-in audio Profile to Off and set the GM200 High Definition Audio Profile to Digital Stereo (HDMI) Output (unplugged). Unfortunately all of the options are "unplugged" and I can't figure out how to change that. I am using one of the DisplayPort ports to connect my computer to my TV via an HDMI cable.

When I go into the Settings Control Panel and go to the Sound section I only see the Built-in Audio as a sound option. The graphics card is nowhere to be found.

Whn I use the `pacmd list-cards` command I see the profiles but they are all not available:

```
    index: 1
        name: <alsa_card.pci-0000_01_00.1>
        driver: <module-alsa-card.c>
        owner module: 7
        properties:
                alsa.card = "1"
                alsa.card_name = "HDA NVidia"
                alsa.long_card_name = "HDA NVidia at 0xfaffc000 irq 17"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:01:00.1"
                sysfs.path = "/devices/pci0000:00/0000:00:1c.0/0000:01:00.1/sound/card1"
                device.bus = "pci"
                device.vendor.id = "10de"
                device.vendor.name = "NVIDIA Corporation"
                device.product.id = "0fb0"
                device.product.name = "GM200 High Definition Audio"
                device.string = "1"
                device.description = "GM200 High Definition Audio"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        profiles:
                output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400, available: no)
                output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 300, available: no)
                output:hdmi-surround71: Digital Surround 7.1 (HDMI) Output (priority 300, available: no)
                output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Output (priority 5200, available: no)
                output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Output (priority 100, available: no)
                output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Output (priority 100, available: no)
                output:hdmi-stereo-extra2: Digital Stereo (HDMI 3) Output (priority 5200, available: no)
                output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI 3) Output (priority 100, available: no)
                output:hdmi-surround71-extra2: Digital Surround 7.1 (HDMI 3) Output (priority 100, available: no)
                output:hdmi-stereo-extra3: Digital Stereo (HDMI 4) Output (priority 5200, available: no)
                output:hdmi-surround-extra3: Digital Surround 5.1 (HDMI 4) Output (priority 100, available: no)
                output:hdmi-surround71-extra3: Digital Surround 7.1 (HDMI 4) Output (priority 100, available: no)
                off: Off (priority 0, available: unknown)
        active profile: <output:hdmi-stereo>
        sinks:
                alsa_output.pci-0000_01_00.1.hdmi-stereo/#0: GM200 High Definition Audio Digital Stereo (HDMI)
        sources:
                alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor/#0: Monitor of GM200 High Definition Audio Digital Stereo (HDMI)
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
                hdmi-output-3: HDMI / DisplayPort 4 (priority 5600, latency offset 0 usec, available: no)
                        properties:
                                device.icon_name = "video-display"
```

Now what? Any help would be appreciated.

---

### Post by Autodave on 2018-03-15
What driver did you install and where did you get it from?

---

### Post by subject117 on 2018-03-15
I installed this one:

[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-384](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-384)

NVidia Driver Version: 384.111

---

