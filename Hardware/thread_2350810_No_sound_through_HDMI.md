---
title: "No sound through HDMI"
date: 2017-01-28
forum: Hardware
---

### Post by tigerjack89 on 2017-01-28
As the title suggests, I'm not able to reproduce any sound on my external TV through the HDMI cable.
To note that starting using the same notebook with Windows does not give any kind of problem.

I've tried all the solution found so far on the web, namely
[LIST=1]
[*]```
speaker-test -c 2 -r 48000 -D hw:0,3
``` 
and/or 
```
speaker-test -D hdmi:CARD=PCH,DEV=0 -c 2
``` 
[*]Upgrading alsa driver to the latest version (now I have oem-audio-hda-daily-dkms:amd64 0.201701260732~ubuntu14.04.1 installed) 
[*]Use pulseaudio, alsamixer or the default sound manager to switch to the HDMI output port 
[*]pulseaudio -k to restart the pulseaudio daemon 
[*]adding my user to various groups with ```
sudo usermod -a -G audio,pulse,pulse-access,video,voice $USER
``` 
[/LIST]
but, as said, nothing changed.

Here is some useful output
```

>dpkg -l | grep alsa
ii  alsa-base                                                   1.0.25+dfsg-0ubuntu4                                all          ALSA driver configuration files
ii  alsa-utils                                                  1.0.27.2-1ubuntu2                                   amd64        Utilities for configuring and using ALSA
ii  bluez-alsa:amd64                                            4.101-0ubuntu13.1                                   amd64        Bluetooth ALSA support
ii  gnome-alsamixer                                             0.9.7~cvs.20060916.ds.1-5                           amd64        ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa:amd64                                    0.10.36-1.1ubuntu2                                  amd64        GStreamer plugin for ALSA
ii  libsox-fmt-alsa:amd64                                       14.4.1-3ubuntu1                                     amd64        SoX alsa format I/O library

```

```

>lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)

```

```

>sudo lshw | grep -A9 "Audio"
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:47 memory:f1610000-f1613fff

```

```

>aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: 92HD91BXX Analog [92HD91BXX Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: Generic Digital [Generic Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
N.B.: I don't know if it can be an issue, but I have two subdevices: 1/1.

```

>pacmd list-cards
Welcome to PulseAudio! Use "help" for usage information.
>>> 1 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_00_1b.0>
    driver: <module-alsa-card.c>
    owner module: 5
    properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xf1610000 irq 47"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "1e20"
        device.product.name = "7 Series/C210 Series Chipset Family High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        input:analog-stereo: Analogue Stereo Input (priority 60, available: unknown)
        output:analog-stereo: Analogue Stereo Output (priority 6000, available: unknown)
        output:analog-stereo+input:analog-stereo: Analogue Stereo Duplex (priority 6060, available: unknown)
        output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400, available: unknown)
        output:hdmi-stereo+input:analog-stereo: Digital Stereo (HDMI) Output + Analogue Stereo Input (priority 5460, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <output:hdmi-stereo+input:analog-stereo>
    sinks:
        alsa_output.pci-0000_00_1b.0.hdmi-stereo/#0: Built-in Audio Digital Stereo (HDMI)
    sources:
        alsa_output.pci-0000_00_1b.0.hdmi-stereo.monitor/#0: Monitor of Built-in Audio Digital Stereo (HDMI)
        alsa_input.pci-0000_00_1b.0.analog-stereo/#1: Built-in Audio Analogue Stereo
    ports:
        analog-input-microphone-internal: Internal Microphone (priority 8900, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-microphone: Microphone (priority 8700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-speakers"
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "video-display"

```



Some images from PulseAudio Volume Control ...
[http://tinypic.com/usermedia.php?uo=XaTRJmVkC3cScUTnUtfPsYh4l5k2TGxc](http://tinypic.com/usermedia.php?uo=XaTRJmVkC3cScUTnUtfPsYh4l5k2TGxc)
[http://tinypic.com/usermedia.php?uo=XaTRJmVkC3cDTBJPccOp%2FYh4l5k2TGxc](http://tinypic.com/usermedia.php?uo=XaTRJmVkC3cDTBJPccOp%2FYh4l5k2TGxc)

... Gnome Alsa mixer ...
[http://tinypic.com/usermedia.php?uo=XaTRJmVkC3de26q8uf0cQYh4l5k2TGxc](http://tinypic.com/usermedia.php?uo=XaTRJmVkC3de26q8uf0cQYh4l5k2TGxc)

... and the dafault sound manager
[http://tinypic.com/usermedia.php?uo=XaTRJmVkC3dvzSy87mAtPYh4l5k2TGxc](http://tinypic.com/usermedia.php?uo=XaTRJmVkC3dvzSy87mAtPYh4l5k2TGxc)

I don't know what else to try and any help is really appreciated.

Thanks in advance.

---

### Post by Bucky Ball on 2017-01-28
Please attach large pics using 'Adv Reply' or 'Go Advanced' and the paperclip icon rather than using a heap of space inserting them in the text. Think of potential helpers with slow internet connections or vision issues. ;) 

Go to the 'Configuration' tab in Pulseaudio and make sure the correct HDMI profile is selected in the top drop-down selection box. A lot of them will say 'Disconnected' but there should be one that says 'Connected'. Use that. Any luck?

Stick with tweaking Pulse for now. If you start screwing about with ALSA and experimenting you may cause more issues than you started with.

---

### Post by tigerjack89 on 2017-01-28
> **Bucky Ball said:**
> Please attach large pics using 'Adv Reply' or 'Go Advanced' and the paperclip icon rather than using a heap of space inserting them in the text. Think of potential helpers with slow internet connections or vision issues. ;) 

Go to the 'Configuration' tab in Pulseaudio and make sure the correct HDMI profile is selected in the top drop-down selection box. A lot of them will say 'Disconnected' but there should be one that says 'Connected'. Use that. Any luck?

Stick with tweaking Pulse for now. If you start screwing about with ALSA and experimenting you may cause more issues than you started with.
Thanks for your help, I've just modified them with a link to the image.
Btw I already tried all the profiles listed in the menu, without any luck.

---

