---
title: "Firewire soundcard with pulseaudio / add profile"
date: 2018-10-22
forum: Hardware
---

### Post by jl-o on 2018-10-22
Hi Folks,
I am trying to use my Edirol FA-66 with (K)Ubuntu 18.10.
Output or Input work depending on what profile I choose in PulseAudio Volume Control but not at the same time since there is no profile for it.
How do i add a profile and a rule to the system to support Output and Input at the same time.

Thanks,
Joel

card section of pactl list output:
```
Card #1
        Name: alsa_card.firewire-0x0040ab0000c32820
        Driver: module-alsa-card.c
        Owner Module: 8
        Properties:
                alsa.card = "0"
                alsa.card_name = "EDIROL FA-66"
                alsa.long_card_name = "EDIROL EDIROL FA-66 (id:2, rev:1), GUID 0040ab0000c32820 at fw1.0, S400"
                alsa.driver_name = "snd_bebob"
                device.bus_path = "pci-0000:05:00.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1c.0/0000:05:00.0/fw1/fw1.0/sound/card0"
                udev.id = "firewire-0x0040ab0000c32820"
                device.bus = "firewire"
                device.vendor.id = "0040"
                device.vendor.name = "EDIROL"
                device.product.id = "0100"
                device.product.name = "EDIROL FA-66"
                device.serial = "0x0040ab0000c32820"
                device.string = "0"
                device.description = "EDIROL FA-66"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-firewire"
        Profiles:
                input:multichannel-input: Multichannel Input (sinks: 0, sources: 1, priority: 1, available: yes)
                output:multichannel-output: Multichannel Output (sinks: 1, sources: 0, priority: 100, available: yes)
                off: Off (sinks: 0, sources: 0, priority: 0, available: yes)
        Active Profile: output:multichannel-output
        Ports:
                multichannel-input: Multichannel Input (priority: 0, latency offset: 0 usec)
                        Part of profile(s): input:multichannel-input
                multichannel-output: Multichannel Output (priority: 0, latency offset: 0 usec)
                        Part of profile(s): output:multichannel-output

```

---

