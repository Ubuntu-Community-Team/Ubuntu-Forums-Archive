---
title: "No sound on new computer"
date: 2016-03-27
forum: Hardware
---

### Post by josh171 on 2016-03-27
I just put together a computer with an MSI z170A PC MATE mobo and I'm using my old hard drive in it, with Ubuntu and i3.
No sound plays through my usb speaker, whether I plug it into the headphones port on the front or the port on the back.
I see sound playing in pavucontrol under the Built In Audio Analog Stereo device.
Here's the aplay and pacmd list-sinks results:
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
josh$ pacmd list-sinks
Welcome to PulseAudio! Use "help" for usage information.
>>> 2 sink(s) available.
    index: 0
    name: <alsa_output.pci-0000_01_00.1.hdmi-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: IDLE
    suspend cause: 
    priority: 9050
    volume: 0: 115% 1: 115%
            0: 3.62 dB 1: 3.62 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 371.30 ms
    max request: 64 KiB
    max rewind: 64 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 371.52 ms; range is 0.50 .. 371.52 ms
    card: 0 <alsa_card.pci-0000_01_00.1>
    module: 5
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 0"
        alsa.id = "HDMI 0"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "3"
        alsa.card = "1"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xdf080000 irq 17"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:01:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "NVIDIA Corporation"
        device.product.id = "0bea"
        device.product.name = "GF108 High Definition Audio Controller"
        device.string = "hdmi:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo"
        device.profile.description = "Digital Stereo (HDMI)"
        device.description = "GF108 High Definition Audio Controller Digital Stereo (HDMI)"
        alsa.mixer_name = "Nvidia GPU 14 HDMI/DP"
        alsa.components = "HDA:10de0014,10de0101,00100100"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
    active port: <hdmi-output-0>
  * index: 1
    name: <alsa_output.pci-0000_00_1f.3.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: 
    priority: 9959
    volume: 0: 106% 1: 106%
            0: 1.52 dB 1: 1.52 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 165.13 ms
    max request: 63 KiB
    max rewind: 64 KiB
    monitor source: 1
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 1
    linked by: 1
    configured latency: 371.52 ms; range is 371.52 .. 371.52 ms
    card: 1 <alsa_card.pci-0000_00_1f.3>
    module: 6
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC887-VD Analog"
        alsa.id = "ALC887-VD Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA Intel"
        alsa.long_card_name = "HDA Intel at 0xdf320000 irq 145"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "a170"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "Realtek ALC887-VD"
        alsa.components = "HDA:10ec0887,1462f971,00100302"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output: Analog Output (priority 9900, latency offset 0 usec, available: unknown)
            properties:
                
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
    active port: <analog-output>
```

Thanks

---

### Post by Yellow Pasque on 2016-03-29
```
analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
```

Not available? Hmm. Try getting more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by josh171 on 2016-03-29
Here it is: [http://www.alsa-project.org/db/?f=79cf086d4cd5dfd65acd757eec3e68d6bf53a227](http://www.alsa-project.org/db/?f=79cf086d4cd5dfd65acd757eec3e68d6bf53a227)

Thank you

---

### Post by Yellow Pasque on 2016-03-29
Okay. Did you gather the info with the speaker plugged in? I'm a bit confused by your speaker. You say it's USB, but it sounds like you're plugging it into regular 3.5mm audio jacks. Please clarify

---

### Post by josh171 on 2016-03-29
Yes, it was plugged in.  Sorry, but it's plugged into the headphones or maybe the audio jack in the back.  It's merely powered by the USB, afaik.  Thanks

---

### Post by Yellow Pasque on 2016-03-29
This little utility might help you see whether it's recognizing the device being plugged in: [http://ubuntuforums.org/showthread.php?t=2282532&p=13305397#post13305397](http://ubuntuforums.org/showthread.php?t=2282532&p=13305397#post13305397)

---

### Post by Yellow Pasque on 2016-03-29
Also, if it's not too much trouble (i.e. you have bandwidth and a USB stick), you could test a LiveUSB of Ubuntu 16.04 to see if it's a bug that got corrected. [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by josh171 on 2016-03-31
That doesn't make the sound work.

---

### Post by josh171 on 2016-03-31
I have a lot of problems with conflicts when trying to install that package.
I downloaded and try to install snd-hda-tools_0.20130207+trusty1_amd64.deb


```

Reading package lists...
Building dependency tree...
Reading state information...
acl is already the newest version.
...
scala is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 389-ds-base : Conflicts: slapd but 2.4.31-1+nmu2ubuntu8.2 is to be installed
 adobe-flashplugin : Conflicts: flashplugin-downloader
                     Conflicts: flashplugin-downloader:i386 but 11.2.202.577ubuntu0.14.04.1 is to be installed
                     Conflicts: flashplugin-installer
                     Conflicts: flashplugin-installer:i386
 aide : Conflicts: aide-dynamic but 0.16~a2.git20130520-2ubuntu0.1 is to be installed
        Conflicts: aide-xen but 0.16~a2.git20130520-2ubuntu0.1 is to be installed
 aide-dynamic : Conflicts: aide but 0.16~a2.git20130520-2ubuntu0.1 is to be installed
                Conflicts: aide-xen but 0.16~a2.git20130520-2ubuntu0.1 is to be installed
 aide-xen : Conflicts: aide but 0.16~a2.git20130520-2ubuntu0.1 is to be installed
            Conflicts: aide-dynamic but 0.16~a2.git20130520-2ubuntu0.1 is to be installed
 amule-adunanza : Conflicts: amule but 2.3.1-11 is to be installed
                  Conflicts: amule-common but 2.3.1-11 is to be installed
 amule-adunanza-daemon : Conflicts: amule-common but 2.3.1-11 is to be installed
                         Conflicts: amule-daemon but 2.3.1-11 is to be installed
 amule-adunanza-utils : Conflicts: amule-utils but 2.3.1-11 is to be installed
 amule-adunanza-utils-gui : Conflicts: amule-utils-gui but 2.3.1-11 is to be installed
 anthy-el : Conflicts: xemacs21-nomule but 21.4.22-4ubuntu3 is to be installed
 apache2.2-bin : Breaks: gnome-user-share (< 3.8.0-2~) but 3.0.4-0ubuntu1 is to be installed
 apcupsd : Conflicts: ups-monitor
 apsfilter : Conflicts: magicfilter but 1.2-64 is to be installed
 arping : Conflicts: iputils-arping but 3:20121221-4ubuntu1.1 is to be installed
 asterisk-prompt-es-co : Conflicts: asterisk-prompt-es
 asterisk-prompt-fr-armelle : Conflicts: asterisk-prompt-fr
 asterisk-prompt-fr-proformatique : Conflicts: asterisk-prompt-fr
 asterisk-voicemail : Conflicts: asterisk-voicemail-storage
 asterisk-voicemail-imapstorage : Conflicts: asterisk-voicemail-storage
 asterisk-voicemail-odbcstorage : Conflicts: asterisk-voicemail-storage
 atftpd : Conflicts: tftpd but 0.17-18ubuntu2 is to be installed
 aumix : Conflicts: aumix-gtk but 2.9.1-2 is to be installed
 aumix-gtk : Conflicts: aumix
 babel-1.4.0 : Conflicts: openbabel but 2.3.2+dfsg-1.1 is to be installed
 bacula-common-mysql : Conflicts: bacula-common-pgsql but 5.2.6+dfsg-9.1ubuntu3 is to be installed
                       Conflicts: bacula-common-sqlite3 but 5.2.6+dfsg-9.1ubuntu3 is to be installed
 bacula-common-mysql-dbg : Conflicts: bacula-common-pgsql-dbg but 5.2.6+dfsg-9.1ubuntu3 is to be installed
                           Conflicts: bacula-common-sqlite3-dbg but 5.2.6+dfsg-9.1ubuntu3 is to be installed
 bacula-common-pgsql : Conflicts: bacula-common-mysql but 5.2.6+dfsg-9.1ubuntu3 is to be installed
                       Conflicts: bacula-common-sqlite3 but 5.2.6+dfsg-9.1ubuntu3 is to be installed
...

```

---

### Post by Yellow Pasque on 2016-03-31
> **josh171 said:**
> That doesn't make the sound work.

What doesn't make the sound work? You tried the LiveUSB?

> I have a lot of problems with conflicts when trying to install that package

Given the amount of conflicts and the packages involved, I'm guessing your apt problems go deeper than the snd-hda-tools. If you do a simple system update, do you also get conflicts?
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by josh171 on 2016-03-31
> **Temüjin said:**
> What doesn't make the sound work? You tried the LiveUSB?

Given the amount of conflicts and the packages involved, I'm guessing your apt problems go deeper than the snd-hda-tools. If you do a simple system update, do you also get conflicts?
```
sudo apt-get update
sudo apt-get dist-upgrade
```

I installed via the liveusb onto my new ssd and still no sound.  The apt-get update and dist-upgrade work fine, but then I try sudo apt-get install . to install snd-hda-tools and I still get tons of conflicts.

---

