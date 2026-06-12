---
title: "Sound not working | Ubuntu 22.10 Tiger Lake-LP Smart Sound"
date: 2023-02-09
forum: Hardware
---

### Post by aahmetdurmaz on 2023-02-09
Hello everyone. I just bought my laptop and I want to use Ubuntu. I was using 20.04 before. After I bought my new computer, I started having problems with sound. I can get sound from the laptop with Windows 11, but I could not get any sound at all despite trying Ubuntu 22.10, 22.04, 20.04 versions. I searched all over the internet but I could not find a solution.
Strangely, my microphone is active even though the sound is not working.

inxi output:
```

Audio:
  Device-1: Intel Tiger Lake-LP Smart Sound Audio vendor: IP3 Tech
    driver: sof-audio-pci-intel-tgl bus-ID: 3-4:3
  Device-2: BKX-Usb2.0 2MP Camera type: USB driver: snd-usb-audio,uvcvideo
  Sound Server-1: ALSA v: k5.19.0-21-generic running: yes
  Sound Server-2: PulseAudio v: 16.1 running: no
  Sound Server-3: PipeWire v: 0.3.58 running: yes

```

lspci output:
```
00:1f.3 Multimedia audio controller: Intel Corporation Tiger Lake-LP Smart Sound Technology Audio Controller (rev 20)
```

pactl list cards:
```
Card #48
    Name: alsa_card.pci-0000_00_1f.3-platform-sof-essx8336
    Driver: alsa
    Owner Module: n/a
    Properties:
        api.acp.auto-port = "false"
        api.acp.auto-profile = "false"
        api.alsa.card = "0"
        api.alsa.card.longname = "Monster-HumaH5V3.1-V10"
        api.alsa.card.name = "sof-essx8336"
        api.alsa.path = "hw:0"
        api.alsa.use-acp = "true"
        api.dbus.ReserveDevice1 = "Audio0"
        device.api = "alsa"
        device.bus = "pci"
        device.bus_path = "pci-0000:00:1f.3-platform-sof-essx8336"
        device.description = "Tiger Lake-LP Smart Sound Technology Audio Controller"
        device.enum.api = "udev"
        device.icon_name = "audio-card-analog-pci"
        device.name = "alsa_card.pci-0000_00_1f.3-platform-sof-essx8336"
        device.nick = "sof-essx8336"
        device.plugged.usec = "6510820"
        device.product.id = "0xa0c8"
        device.product.name = "Tiger Lake-LP Smart Sound Technology Audio Controller"
        device.subsystem = "sound"
        sysfs.path = "/sys/devices/pci0000:00/0000:00:1f.3/sof-essx8336/sound/card0"
        device.vendor.id = "0x8086"
        device.vendor.name = "Intel Corporation"
        media.class = "Audio/Device"
        factory.id = "14"
        client.id = "34"
        object.id = "47"
        object.serial = "48"
        object.path = "alsa:pcm:0"
        alsa.card = "0"
        alsa.card_name = "sof-essx8336"
        alsa.long_card_name = "Monster-HumaH5V3.1-V10"
        alsa.driver_name = "snd_soc_sof_es8336"
        device.string = "0"
    Profiles:
        off: Off (sinks: 0, sources: 0, priority: 0, available: yes)
        output:stereo-fallback+input:stereo-fallback: Stereo Output + Stereo Input (sinks: 1, sources: 1, priority: 5151, available: no)
        output:stereo-fallback: Stereo Output (sinks: 1, sources: 0, priority: 5100, available: yes)
        input:stereo-fallback: Stereo Input (sinks: 0, sources: 1, priority: 51, available: no)
        pro-audio: Pro Audio (sinks: 4, sources: 1, priority: 1, available: yes)
    Active Profile: output:stereo-fallback
    Ports:
        analog-input-headset-mic: Headset Microphone (type: Headset, priority: 8800, latency offset: 0 usec, availability group: Legacy 1, not available)
            Properties:
                port.type = "headset"
                port.availability-group = "Legacy 1"
                device.icon_name = "audio-input-microphone"
                card.profile.port = "0"
            Part of profile(s): input:stereo-fallback, output:stereo-fallback+input:stereo-fallback
        analog-output-speaker: Speakers (type: Speaker, priority: 10000, latency offset: 0 usec, availability unknown)
            Properties:
                port.type = "speaker"
                device.icon_name = "audio-speakers"
                card.profile.port = "1"
            Part of profile(s): output:stereo-fallback, output:stereo-fallback+input:stereo-fallback
        analog-output-headphones: Headphones (type: Headphones, priority: 9900, latency offset: 0 usec, availability group: Legacy 1, not available)
            Properties:
                port.type = "headphones"
                port.availability-group = "Legacy 1"
                device.icon_name = "audio-headphones"
                card.profile.port = "2"
            Part of profile(s): output:stereo-fallback, output:stereo-fallback+input:stereo-fallback

Card #49
    Name: alsa_card.usb-BKX-Usb2.0_2MP_Camera_BKX-Usb2.0_2MP_Camera-02
    Driver: alsa
    Owner Module: n/a
    Properties:
        api.acp.auto-port = "false"
        api.acp.auto-profile = "false"
        api.alsa.card = "1"
        api.alsa.card.longname = "BKX-Usb2.0 2MP Camera BKX-Usb2.0 2MP Camera at usb-0000:00:14.0-4, high speed"
        api.alsa.card.name = "BKX-Usb2.0 2MP Camera"
        api.alsa.path = "hw:1"
        api.alsa.use-acp = "true"
        api.dbus.ReserveDevice1 = "Audio1"
        device.api = "alsa"
        device.bus = "usb"
        device.bus-id = "usb-BKX-Usb2.0_2MP_Camera_BKX-Usb2.0_2MP_Camera-02"
        device.bus_path = "pci-0000:00:14.0-usb-0:4:1.2"
        device.description = "BKX-Usb2.0 2MP Camera"
        device.enum.api = "udev"
        device.form_factor = "webcam"
        device.icon_name = "camera-web-analog-usb"
        device.name = "alsa_card.usb-BKX-Usb2.0_2MP_Camera_BKX-Usb2.0_2MP_Camera-02"
        device.nick = "BKX-Usb2.0 2MP Camera"
        device.plugged.usec = "4212254"
        device.product.id = "0xb182"
        device.product.name = "BKX-Usb2.0 2MP Camera"
        device.serial = "BKX-Usb2.0_2MP_Camera_BKX-Usb2.0_2MP_Camera"
        device.subsystem = "sound"
        sysfs.path = "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.2/sound/card1"
        device.vendor.id = "0xb349"
        device.vendor.name = "BKX-Usb2.0 2MP Camera"
        media.class = "Audio/Device"
        factory.id = "14"
        client.id = "34"
        object.id = "48"
        object.serial = "49"
        object.path = "alsa:pcm:1"
        alsa.card = "1"
        alsa.card_name = "BKX-Usb2.0 2MP Camera"
        alsa.long_card_name = "BKX-Usb2.0 2MP Camera BKX-Usb2.0 2MP Camera at usb-0000:00:14.0-4, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.string = "1"
    Profiles:
        off: Off (sinks: 0, sources: 0, priority: 0, available: yes)
        input:analog-stereo: Analog Stereo Input (sinks: 0, sources: 1, priority: 65, available: yes)
        input:iec958-stereo: Digital Stereo (IEC958) Input (sinks: 0, sources: 1, priority: 55, available: yes)
        pro-audio: Pro Audio (sinks: 0, sources: 1, priority: 1, available: yes)
    Active Profile: input:analog-stereo
    Ports:
        analog-input-mic: Microphone (type: Mic, priority: 8700, latency offset: 0 usec, availability unknown)
            Properties:
                port.type = "mic"
                device.icon_name = "audio-input-microphone"
                card.profile.port = "0"
            Part of profile(s): input:analog-stereo
        iec958-stereo-input: Digital Input (S/PDIF) (type: SPDIF, priority: 0, latency offset: 0 usec, availability unknown)
            Properties:
                port.type = "spdif"
                card.profile.port = "1"
            Part of profile(s): input:iec958-stereo

```

pactl list sinks:
```
Sink #52
    State: IDLE
    Name: alsa_output.pci-0000_00_1f.3-platform-sof-essx8336.stereo-fallback
    Description: Tiger Lake-LP Smart Sound Technology Audio Controller Stereo
    Driver: PipeWire
    Sample Specification: s32le 2ch 48000Hz
    Channel Map: front-left,front-right
    Owner Module: 4294967295
    Mute: no
    Volume: front-left: 42843 /  65% / -11,08 dB,   front-right: 42843 /  65% / -11,08 dB
            balance 0,00
    Base Volume: 65536 / 100% / 0,00 dB
    Monitor Source: alsa_output.pci-0000_00_1f.3-platform-sof-essx8336.stereo-fallback.monitor
    Latency: 0 usec, configured 0 usec
    Flags: HARDWARE HW_MUTE_CTRL DECIBEL_VOLUME LATENCY 
    Properties:
        alsa.card = "0"
        alsa.card_name = "sof-essx8336"
        alsa.class = "generic"
        alsa.device = "0"
        alsa.driver_name = "snd_soc_sof_es8336"
        alsa.id = "ES8336 (*)"
        alsa.long_card_name = "Monster-HumaH5V3.1-V10"
        alsa.name = ""
        alsa.resolution_bits = "16"
        alsa.subclass = "generic-mix"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        api.alsa.card.longname = "Monster-HumaH5V3.1-V10"
        api.alsa.card.name = "sof-essx8336"
        api.alsa.path = "hw:0"
        api.alsa.pcm.card = "0"
        api.alsa.pcm.stream = "playback"
        audio.channels = "2"
        audio.position = "FL,FR"
        card.profile.device = "6"
        device.api = "alsa"
        device.class = "sound"
        device.id = "47"
        device.profile.description = "Stereo"
        device.profile.name = "stereo-fallback"
        device.routes = "2"
        factory.name = "api.alsa.pcm.sink"
        media.class = "Audio/Sink"
        device.description = "Tiger Lake-LP Smart Sound Technology Audio Controller"
        node.name = "alsa_output.pci-0000_00_1f.3-platform-sof-essx8336.stereo-fallback"
        node.nick = "Stereo"
        node.pause-on-idle = "false"
        object.path = "alsa:pcm:0:hw:0:playback"
        priority.driver = "1000"
        priority.session = "1000"
        factory.id = "18"
        clock.quantum-limit = "8192"
        client.id = "34"
        node.driver = "true"
        factory.mode = "merge"
        audio.adapt.follower = ""
        library.name = "audioconvert/libspa-audioconvert"
        object.id = "51"
        object.serial = "52"
        node.max-latency = "4096/48000"
        api.alsa.period-size = "1024"
        api.alsa.period-num = "8"
        api.alsa.headroom = "0"
        api.acp.auto-port = "false"
        api.acp.auto-profile = "false"
        api.alsa.card = "0"
        api.alsa.use-acp = "true"
        api.dbus.ReserveDevice1 = "Audio0"
        device.bus = "pci"
        device.bus_path = "pci-0000:00:1f.3-platform-sof-essx8336"
        device.enum.api = "udev"
        device.icon_name = "audio-card-analog-pci"
        device.name = "alsa_card.pci-0000_00_1f.3-platform-sof-essx8336"
        device.nick = "sof-essx8336"
        device.plugged.usec = "6510820"
        device.product.id = "0xa0c8"
        device.product.name = "Tiger Lake-LP Smart Sound Technology Audio Controller"
        device.subsystem = "sound"
        sysfs.path = "/sys/devices/pci0000:00/0000:00:1f.3/sof-essx8336/sound/card0"
        device.vendor.id = "0x8086"
        device.vendor.name = "Intel Corporation"
        device.string = "0"
    Ports:
        analog-output-speaker: Speakers (type: Speaker, priority: 10000, availability unknown)
        analog-output-headphones: Headphones (type: Headphones, priority: 9900, availability group: Legacy 1, not available)
    Active Port: analog-output-speaker
    Formats:
        pcm

```


[IMG]https://i.hizliresim.com/djgv85p.jpg[/IMG]

pavucontrol:
[IMG]https://i.hizliresim.com/jovgde2.jpg[/IMG]

---

### Post by #&amp;thj^% on 2023-02-09
please show this:
```
pipewire status
```

---

### Post by him610 on 2023-02-09
> Sound Server-2: PulseAudio v: 16.1 running: no
Maybe this should be running - just a thought.

---

### Post by aahmetdurmaz on 2023-02-10
Pipewire Status:
```
[E][00097.954145] mod.protocol-native | [module-protocol-:  728 lock_socket()] server 0x55a7e68c95c0: unable to lock lockfile '/run/user/1000/pipewire-0.lock': Resource temporarily unavailable (maybe another daemon is running)
[E][00097.954392] pw.conf      | [          conf.c:  594 load_module()] 0x55a7e68ae250: could not load mandatory module "libpipewire-module-protocol-native": Resource temporarily unavailable
[E][00097.954566] default      | [      pipewire.c:  125 main()] failed to create context: Resource temporarily unavailable

```

if it helps i also get dmesg error messages.

sudo dmesg -l=err:
```
[    0.447448] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20220331/psargs-330)
[    0.447471] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS01._PLD due to previous error (AE_NOT_FOUND) (20220331/psparse-529)
[    0.483108] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20220331/psargs-330)
[    0.483123] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS01._PLD due to previous error (AE_NOT_FOUND) (20220331/psparse-529)
[    0.635014] pci 0000:00:07.0: DPC: RP PIO log size 0 is invalid
[    1.625260] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20220331/psargs-330)
[    1.625299] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS01._PLD due to previous error (AE_NOT_FOUND) (20220331/psparse-529)
[    1.625338] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20220331/psargs-330)
[    1.625364] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS01._PLD due to previous error (AE_NOT_FOUND) (20220331/psparse-529)
[    1.633833] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20220331/psargs-330)
[    1.633901] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS01._PLD due to previous error (AE_NOT_FOUND) (20220331/psparse-529)
[    1.633990] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20220331/psargs-330)
[    1.634020] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS01._PLD due to previous error (AE_NOT_FOUND) (20220331/psparse-529)
[    7.684516] Dev loop1: unable to read RDB block 8
[    9.150023] Dev loop8: unable to read RDB block 8
[   10.401152] Bluetooth: hci0: Malformed MSFT vendor event: 0x02

```

---

### Post by aahmetdurmaz on 2023-02-10
> **him610 said:**
> Maybe this should be running - just a thought.
I tried, but when I turn on pulseaudio the system crashes and I have to fully reinstall ubuntu.

---

### Post by #&amp;thj^% on 2023-02-10
yep forget pulseaudio, it's on it's way out.
will you please try this, and post back the results please!
```
 systemctl --user status pipewire pipewire-pulse wireplumber pulseaudio
```
This may take a little hunt and seek, so please be aware.
EDIT:
```
>> systemctl --user status pipewire pipewire-pulse wireplumber pulseaudio
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; preset: e>
     Active: active (running) since Fri 2023-02-10 09:03:14 MST; 9h ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 252521 (pipewire)
      Tasks: 2 (limit: 9226)
     Memory: 6.1M
        CPU: 14.955s
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewi>
             &#9492;&#9472;252521 /usr/bin/pipewire

Feb 10 09:03:14 zfs-root systemd[4555]: Started PipeWire Multimedia Service.

&#9679; pipewire-pulse.service - PipeWire PulseAudio
     Loaded: loaded (/usr/lib/systemd/user/pipewire-pulse.service; enabled; pre>
     Active: active (running) since Fri 2023-02-10 07:51:57 MST; 10h ago
TriggeredBy: &#9679; pipewire-pulse.socket
   Main PID: 4567 (pipewire-pulse)
      Tasks: 2 (limit: 9226)
     Memory: 3.4M
        CPU: 21.410s
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewi>
             &#9492;&#9472;4567 /usr/bin/pipewire-pulse

Feb 10 07:51:57 zfs-root systemd[4555]: Started PipeWire PulseAudio.
Feb 10 07:51:57 zfs-root pipewire-pulse[4567]: mod.rt: Can't find org.freedeskt>
Feb 10 07:51:57 zfs-root pipewire-pulse[4567]: mod.rt: found session bus but no>

&#9679; wireplumber.service - Multimedia Service Session Manager
     Loaded: loaded (/usr/lib/systemd/user/wireplumber.service; enabled; preset>
     Active: active (running) since Fri 2023-02-10 09:03:14 MST; 9h ago
   Main PID: 252523 (wireplumber)
      Tasks: 4 (limit: 9226)
     Memory: 9.7M
        CPU: 778ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/wirepl>
             &#9492;&#9472;252523 /usr/bin/wireplumber

Feb 10 09:03:14 zfs-root systemd[4555]: Started Multimedia Service Session Mana>
Feb 10 09:03:24 zfs-root wireplumber[252523]: Failed to set scheduler settings:>
Feb 10 09:03:24 zfs-root wireplumber[252523]: SPA handle 'api.libcamera.enum.ma>
Feb 10 09:03:24 zfs-root wireplumber[252523]: PipeWire's libcamera SPA missing >
Feb 10 09:03:25 zfs-root wireplumber[252523]: Trying to use legacy bluez5 API f>
Feb 10 09:03:25 zfs-root wireplumber[252523]: <WpPortalPermissionStorePlugin:0x>

&#9675; pulseaudio.service
     Loaded: masked (Reason: Unit pulseaudio.service is masked.)
     Active: inactive (dead)

```

---

### Post by aahmetdurmaz on 2023-02-11
> **1fallen said:**
> yep forget pulseaudio, it's on it's way out.
will you please try this, and post back the results please!
```
 systemctl --user status pipewire pipewire-pulse wireplumber pulseaudio
```
This may take a little hunt and seek, so please be aware.
EDIT:
```
>> systemctl --user status pipewire pipewire-pulse wireplumber pulseaudio
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; preset: e>
     Active: active (running) since Fri 2023-02-10 09:03:14 MST; 9h ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 252521 (pipewire)
      Tasks: 2 (limit: 9226)
     Memory: 6.1M
        CPU: 14.955s
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewi>
             &#9492;&#9472;252521 /usr/bin/pipewire

Feb 10 09:03:14 zfs-root systemd[4555]: Started PipeWire Multimedia Service.

&#9679; pipewire-pulse.service - PipeWire PulseAudio
     Loaded: loaded (/usr/lib/systemd/user/pipewire-pulse.service; enabled; pre>
     Active: active (running) since Fri 2023-02-10 07:51:57 MST; 10h ago
TriggeredBy: &#9679; pipewire-pulse.socket
   Main PID: 4567 (pipewire-pulse)
      Tasks: 2 (limit: 9226)
     Memory: 3.4M
        CPU: 21.410s
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewi>
             &#9492;&#9472;4567 /usr/bin/pipewire-pulse

Feb 10 07:51:57 zfs-root systemd[4555]: Started PipeWire PulseAudio.
Feb 10 07:51:57 zfs-root pipewire-pulse[4567]: mod.rt: Can't find org.freedeskt>
Feb 10 07:51:57 zfs-root pipewire-pulse[4567]: mod.rt: found session bus but no>

&#9679; wireplumber.service - Multimedia Service Session Manager
     Loaded: loaded (/usr/lib/systemd/user/wireplumber.service; enabled; preset>
     Active: active (running) since Fri 2023-02-10 09:03:14 MST; 9h ago
   Main PID: 252523 (wireplumber)
      Tasks: 4 (limit: 9226)
     Memory: 9.7M
        CPU: 778ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/wirepl>
             &#9492;&#9472;252523 /usr/bin/wireplumber

Feb 10 09:03:14 zfs-root systemd[4555]: Started Multimedia Service Session Mana>
Feb 10 09:03:24 zfs-root wireplumber[252523]: Failed to set scheduler settings:>
Feb 10 09:03:24 zfs-root wireplumber[252523]: SPA handle 'api.libcamera.enum.ma>
Feb 10 09:03:24 zfs-root wireplumber[252523]: PipeWire's libcamera SPA missing >
Feb 10 09:03:25 zfs-root wireplumber[252523]: Trying to use legacy bluez5 API f>
Feb 10 09:03:25 zfs-root wireplumber[252523]: <WpPortalPermissionStorePlugin:0x>

&#9675; pulseaudio.service
     Loaded: masked (Reason: Unit pulseaudio.service is masked.)
     Active: inactive (dead)

```

It's great that he is learning new things here. I hope we can solve the bug.
```
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; preset: enabled)
     Active: active (running) since Sat 2023-02-11 12:09:26 +03; 57s ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 1586 (pipewire)
      Tasks: 2 (limit: 18870)
     Memory: 6.2M
        CPU: 194ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire.service
             &#9492;&#9472;1586 /usr/bin/pipewire

&#350;ub 11 12:09:26 ark systemd[1579]: Started PipeWire Multimedia Service.
&#350;ub 11 12:09:26 ark pipewire[1586]: mod.rt: Can't find xdg-portal: (null)
&#350;ub 11 12:09:26 ark pipewire[1586]: mod.rt: found session bus but no portal

&#9679; pipewire-pulse.service - PipeWire PulseAudio
     Loaded: loaded (/usr/lib/systemd/user/pipewire-pulse.service; enabled; preset: enabled)
     Active: active (running) since Sat 2023-02-11 12:09:26 +03; 57s ago
TriggeredBy: &#9679; pipewire-pulse.socket
   Main PID: 1590 (pipewire-pulse)
      Tasks: 2 (limit: 18870)
     Memory: 3.9M
        CPU: 97ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire-pulse.service
             &#9492;&#9472;1590 /usr/bin/pipewire-pulse

&#350;ub 11 12:09:26 ark systemd[1579]: Started PipeWire PulseAudio.
&#350;ub 11 12:09:26 ark pipewire-pulse[1590]: mod.rt: Can't find xdg-portal: (null)
&#350;ub 11 12:09:26 ark pipewire-pulse[1590]: mod.rt: found session bus but no portal
&#350;ub 11 12:09:26 ark pipewire-pulse[1662]: 536870912

&#9679; wireplumber.service - Multimedia Service Session Manager
     Loaded: loaded (/usr/lib/systemd/user/wireplumber.service; enabled; preset: enabled)
     Active: active (running) since Sat 2023-02-11 12:09:26 +03; 57s ago
   Main PID: 1589 (wireplumber)
      Tasks: 4 (limit: 18870)
     Memory: 8.6M
        CPU: 209ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/wireplumber.service
             &#9492;&#9472;1589 /usr/bin/wireplumber

&#350;ub 11 12:09:26 ark systemd[1579]: Started Multimedia Service Session Manager.
&#350;ub 11 12:09:26 ark wireplumber[1589]: Can't find xdg-portal: (null)
&#350;ub 11 12:09:26 ark wireplumber[1589]: found session bus but no portal
&#350;ub 11 12:09:26 ark wireplumber[1589]: Failed to set scheduler settings: Operation not permitted
&#350;ub 11 12:09:26 ark wireplumber[1589]: SPA handle 'api.libcamera.enum.manager' could not be loaded; is it installed?
&#350;ub 11 12:09:26 ark wireplumber[1589]: PipeWire's libcamera SPA missing or broken. libcamera not supported.

&#9675; pulseaudio.service - Sound Service
     Loaded: loaded (/usr/lib/systemd/user/pulseaudio.service; enabled; preset: enabled)
     Active: inactive (dead)
TriggeredBy: &#9675; pulseaudio.socket


```

After this, i masked the pulseaudio.service. Still same.
After masking:
```

&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; preset: enabled)
     Active: active (running) since Sat 2023-02-11 12:52:49 +03; 50s ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 1550 (pipewire)
      Tasks: 2 (limit: 18870)
     Memory: 10.4M
        CPU: 803ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire.service
             &#9492;&#9472;1550 /usr/bin/pipewire

&#350;ub 11 12:52:49 ark systemd[1543]: Started PipeWire Multimedia Service.
&#350;ub 11 12:52:49 ark pipewire[1550]: mod.rt: Can't find xdg-portal: (null)
&#350;ub 11 12:52:49 ark pipewire[1550]: mod.rt: found session bus but no portal

&#9679; pipewire-pulse.service - PipeWire PulseAudio
     Loaded: loaded (/usr/lib/systemd/user/pipewire-pulse.service; enabled; preset: enabled)
     Active: active (running) since Sat 2023-02-11 12:52:49 +03; 50s ago
TriggeredBy: &#9679; pipewire-pulse.socket
   Main PID: 1554 (pipewire-pulse)
      Tasks: 2 (limit: 18870)
     Memory: 24.8M
        CPU: 999ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire-pulse.service
             &#9492;&#9472;1554 /usr/bin/pipewire-pulse

&#350;ub 11 12:52:49 ark systemd[1543]: Started PipeWire PulseAudio.
&#350;ub 11 12:52:49 ark pipewire-pulse[1554]: mod.rt: Can't find xdg-portal: (null)
&#350;ub 11 12:52:49 ark pipewire-pulse[1554]: mod.rt: found session bus but no portal
&#350;ub 11 12:52:49 ark pipewire-pulse[1618]: 536870912

&#9679; wireplumber.service - Multimedia Service Session Manager
     Loaded: loaded (/usr/lib/systemd/user/wireplumber.service; enabled; preset: enabled)
     Active: active (running) since Sat 2023-02-11 12:52:49 +03; 50s ago
   Main PID: 1553 (wireplumber)
      Tasks: 4 (limit: 18870)
     Memory: 8.6M
        CPU: 1.092s
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/wireplumber.service
             &#9492;&#9472;1553 /usr/bin/wireplumber

&#350;ub 11 12:52:49 ark systemd[1543]: Started Multimedia Service Session Manager.
&#350;ub 11 12:52:49 ark wireplumber[1553]: Can't find xdg-portal: (null)
&#350;ub 11 12:52:49 ark wireplumber[1553]: found session bus but no portal
&#350;ub 11 12:52:49 ark wireplumber[1553]: Failed to set scheduler settings: Operation not permitted
&#350;ub 11 12:52:49 ark wireplumber[1553]: SPA handle 'api.libcamera.enum.manager' could not be loaded; is it installed?
&#350;ub 11 12:52:49 ark wireplumber[1553]: PipeWire's libcamera SPA missing or broken. libcamera not supported.

&#9675; pulseaudio.service
     Loaded: masked (Reason: Unit pulseaudio.service is masked.)
     Active: inactive (dead)
TriggeredBy: &#9675; pulseaudio.socket



```

I think our communication takes a long time because of the time difference. If you agree, I can open an SSH connection for you. If we can overcome the error, we can explain what we did one by one here. If you have some free time, could you contact me?

---

### Post by #&amp;thj^% on 2023-02-11
> **aahmetdurmaz said:**
> 
I think our communication takes a long time because of the time difference. If you agree, I can open an SSH connection for you. If we can overcome the error, we can explain what we did one by one here. If you have some free time, could you contact me?

Here in UF we try to do things in the public eye, for all to gain.
I work, and always on call > so time is what it is sorry, "anyone" else can step in here to you as well. ;)
For now please try:
```
sudo alsa force-reload
```
and change output devices, example change from speakers to HDMI and back, while something is playing.
If no joy still, run this, and check sound again:
```
systemctl --user start pipewire-pulse.service

```
Before you follow or try the below please try this first:
```
sudo nano /etc/default/grub
```
and add this to " **GRUB_CMDLINE_LINUX_DEFAULT**"
```
snd_intel_dspcfg.dsp_driver=1
```
now update grub to make the change for your next reboot:
```
sudo update-grub
```
next reboot.....any better? if not follow the below with *caution*

I had to dump the kernel -V 5.15 it just wasn't up to snuff for my needs, I'm now using "Kernel: 5.19.0-21-generic" (**Warning 5.19 is on hold for this point in time use at your own risk) it still has a couple of weeks before they release it again.
which by happenstance fixed my sound on my X1 carbon which has a card similar to yours Comet Lake HD Audio.
```
inxi -Alsa -P
Audio:
  Device-1: NVIDIA driver: snd_hda_intel v: kernel bus-ID: 4-1.2.1:5 pcie:
    gen: 1 chip-ID: 17e9:4307 class-ID: 0a00 speed: 2.5 GT/s lanes: 8
    serial: 4307293310436 link-max: gen: 3 speed: 8 GT/s lanes: 16
    bus-ID: 01:00.1 chip-ID: 10de:10fa class-ID: 0403
  Device-2: AMD ACP/ACP3X/ACP6x Audio Coprocessor vendor: Lenovo driver: N/A
    alternate: snd_pci_acp3x, snd_rn_pci_acp3x, snd_pci_acp5x, snd_pci_acp6x,
    snd_acp_pci, snd_pci_ps, snd_sof_amd_renoir pcie: gen: 4 speed: 16 GT/s
    lanes: 16 bus-ID: 06:00.5 chip-ID: 1022:15e2 class-ID: 0480
  Device-3: AMD Family 17h/19h HD Audio vendor: Lenovo driver: snd_hda_intel
    v: kernel pcie: gen: 4 speed: 16 GT/s lanes: 16 bus-ID: 06:00.6
    chip-ID: 1022:15e3 class-ID: 0403
  Device-4: DisplayLink UOEOS Laptop Dock type: USB
    driver: cdc_ncm,snd-usb-audio
  Sound API: ALSA v: k5.19.0-21-generic running: yes
  Sound Server-1: PulseAudio v: 16.1 running: no
  Sound Server-2: PipeWire v: 0.3.65 running: yes
Partition:
  ID-1: / raw-size: N/A size: 177.86 GiB used: 5.82 GiB (3.3%) fs: zfs
    logical: rpool/ROOT/ubuntu_eo0rsx
  ID-2: /boot raw-size: N/A size: 1.63 GiB used: 352.5 MiB (21.2%) fs: zfs
    logical: bpool/BOOT/ubuntu_eo0rsx
  ID-3: /boot/efi raw-size: 512 MiB size: 511 MiB (99.80%)
    used: 12.2 MiB (2.4%) fs: vfat dev: /dev/nvme0n1p1 maj-min: 259:6 label: N/A
  ID-4: /var/log raw-size: N/A size: 172.15 GiB used: 114.1 MiB (0.1%)
    fs: zfs logical: rpool/ROOT/ubuntu_eo0rsx/var/log
  ID-5: swap-1 size: 2 GiB used: 286.2 MiB (14.0%) fs: swap
    swappiness: 60 (default) cache-pressure: 100 (default) priority: -2
    dev: /dev/nvme1n1p2 maj-min: 259:2 label: N/A
Sensors:
  System Temperatures: cpu: 47.4 C mobo: N/A gpu: nvidia temp: 37 C
  Fan Speeds (RPM): N/A


```
Good Luck and I'll check back....
EDIT:
```
 wpctl status
PipeWire 'pipewire-0' [0.3.65, me@zfs-root, cookie:2157182323]
 &#9492;&#9472; Clients:
        31. pipewire                            [0.3.65, me@zfs-root, pid:3904]
        33. WirePlumber                         [0.3.65, me@zfs-root, pid:3903]
        34. WirePlumber [export]                [0.3.65, me@zfs-root, pid:3903]
        65. xfce4-pulseaudio-plugin             [0.3.65, me@zfs-root, pid:4241]
        66. xdg-desktop-portal                  [0.3.65, me@zfs-root, pid:4726]
        67. easyeffects                         [0.3.65, me@zfs-root, pid:4514]
       183. wpctl                               [0.3.65, me@zfs-root, pid:10599]
       227. Strawberry                          [0.3.65, me@zfs-root, pid:7086]
       228. Strawberry device finder            [0.3.65, me@zfs-root, pid:7086]

Audio
 &#9500;&#9472; Devices:
 &#9474;      42. HDA NVidia                          [alsa]
 &#9474;      43. UOEOS Laptop Dock                   [alsa]
 &#9474;      44. Family 17h/19h HD Audio Controller  [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;      32. Family 17h/19h HD Audio Controller Pro [vol: 1.25]
 &#9474;  *   51. UOEOS Laptop Dock Analog Surround 4.1 [vol: 0.69]
 &#9474;      68. Easy Effects Sink                   [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   50. Family 17h/19h HD Audio Controller Pro [vol: 0.00 MUTED]
 &#9474;      69. Easy Effects Source                 [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:
       212. Strawberry                                                  
            190. output_FR       > Easy Effects Sink:playback_FR	[active]
            213. output_FL       > Easy Effects Sink:playback_FL	[active]

Video
 &#9500;&#9472; Devices:
 &#9474;      40. Integrated Camera                   [v4l2]
 &#9474;      41. Integrated Camera                   [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   45. Integrated Camera (V4L2)           
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-surround-41
         1. Audio/Source  alsa_input.pci-0000_06_00.6.pro-input-0


```

---

### Post by aahmetdurmaz on 2023-02-11
I tried all the steps but unfortunately the result is still the same. As for the kernel version, I have tested 5 or 6 different kernel versions since morning. I can't get any results. Among the ones I tested are the 5.19 and 6.1.11 you mentioned. I guess I'm not gonna get lucky this time. Thank you for your help, though. Let me know if there are other methods I can try. I'm in love with Linux but I think we're going to part ways for a while :(.

If that helps:
```

wpctl status
PipeWire 'pipewire-0' [0.3.58, ahmet@ark, cookie:2391554768]
 &#9492;&#9472; Clients:
        32. pipewire                            [0.3.58, ahmet@ark, pid:1585]
        33. WirePlumber                         [0.3.58, ahmet@ark, pid:1584]
        34. WirePlumber [export]                [0.3.58, ahmet@ark, pid:1584]
        48. GNOME Shell Volume Control          [0.3.58, ahmet@ark, pid:1806]
        54. GNOME Volume Control Media Keys     [0.3.58, ahmet@ark, pid:1937]
        55. xdg-desktop-portal                  [0.3.58, ahmet@ark, pid:2113]
        56. gnome-shell                         [0.3.58, ahmet@ark, pid:1806]
        57. wpctl                               [0.3.58, ahmet@ark, pid:7372]
        63. Firefox                             [0.3.58, ahmet@ark, pid:5949]
        71. Mutter                              [0.3.58, ahmet@ark, pid:1806]

Audio
 &#9500;&#9472; Devices:
 &#9474;      46. Tiger Lake-LP Smart Sound Technology Audio Controller [alsa]
 &#9474;      47. BKX-Usb2.0 2MP Camera               [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  *   51. Tiger Lake-LP Smart Sound Technology Audio Controller Stereo [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   52. BKX-Usb2.0 2MP Camera Analog Stereo [vol: 0.49]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Video
 &#9500;&#9472; Devices:
 &#9474;      41. BKX-Usb2.0 2MP Camera               [v4l2]
 &#9474;      42. BKX-Usb2.0 2MP Camera               [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   49. BKX-Usb2.0 2MP Camera (V4L2)       
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    auto_null



```

and

```

inxi -Alsa -P
Audio:
  Device-1: Intel Tiger Lake-LP Smart Sound Audio vendor: IP3 Tech
    driver: sof-audio-pci-intel-tgl bus-ID: 3-4:2
    alternate: snd_hda_intel,snd_sof_pci_intel_tgl chip-ID: b349:b182
    bus-ID: 00:1f.3 class-ID: 0102 chip-ID: 8086:a0c8 class-ID: 0401
  Device-2: BKX-Usb2.0 2MP Camera type: USB driver: snd-usb-audio,uvcvideo
  Sound Server-1: ALSA v: k6.1.11-060111-generic running: yes
  Sound Server-2: PulseAudio v: 16.1 running: no
  Sound Server-3: PipeWire v: 0.3.58 running: yes
Partition:
  ID-1: / raw-size: 93.84 GiB size: 91.81 GiB (97.83%) used: 9.72 GiB (10.6%)
    fs: ext4 dev: /dev/nvme0n1p6 maj-min: 259:6 label: N/A
  ID-2: /boot/efi raw-size: 100 MiB size: 96 MiB (96.00%) used: 33.9 MiB
    (35.4%) fs: vfat dev: /dev/nvme0n1p1 maj-min: 259:1 label: N/A
  ID-3: swap-1 size: 3.81 GiB used: 0 KiB (0.0%) fs: swap
    swappiness: 60 (default) cache-pressure: 100 (default) priority: -2
    dev: /dev/nvme0n1p5 maj-min: 259:5 label: N/A
Sensors:
  System Temperatures: cpu: 38.0 C mobo: N/A
  Fan Speeds (RPM): N/A

```

---

### Post by #&amp;thj^% on 2023-02-11
Just for info only, you are aware 22.10 is point release and supported for 9 months only.
22.04 is a LTS and supported for 5 years and better stability, just wondering if you gave 22.04 a shot yet?
Your having the typical point release flaws IE:
```
Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    auto_null
```

---

### Post by aahmetdurmaz on 2023-02-12
Yes. As i told before, i tried 22.04 still same

---

