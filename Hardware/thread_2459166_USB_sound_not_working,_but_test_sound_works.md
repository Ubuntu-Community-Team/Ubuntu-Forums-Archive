---
title: "USB sound not working, but test sound works"
date: 2021-03-12
forum: Hardware
---

### Post by motophil on 2021-03-12
Hi everybody, 

i have a pretty strange sound problem here. I just bought a "Teufel Cinebar One" which has a USB sound card integrated. It works fine with my business laptop that runs on Windows 10.

Now in Ubuntu 20.04 with Unity desktop, the only thing that works is the "Test Sound" feature in Settings/Sound. But only if there are no other sound sources (i.e. youtube in Google Chrome, or vlc), and only if pavucontrol is not running.

Does anybody have an idea?

I'll attach some info from pulseaudio.

```
>>> list-sink-inputs
1 sink input(s) available.
    index: 58
    driver: <protocol-native.c>
    flags: START_CORKED 
    state: RUNNING
    sink: 11 <alsa_output.usb-2cc2_Teufel_Cinebar_One_ABCDEF0123456789-00.analog-stereo>
    volume: front-left: 65536 / 100% / 0,00 dB,   front-right: 65536 / 100% / 0,00 dB
            balance 0,00
    muted: no
    current latency: 40,27 ms
    requested latency: 23,22 ms
    sample spec: float32le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    resample method: copy
    module: 12
    client: 64 <Google Chrome>
    properties:
        application.icon_name = "google-chrome"
        media.name = "Playback"
        application.name = "Google Chrome"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "33"
        application.process.id = "3820"
        application.process.user = "phil"
        application.process.host = "main"
        application.process.binary = "chrome"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "8264e079a2af472fb6019f39bf24a685"
        module-stream-restore.id = "sink-input-by-application-name:Google Chrome"



```

```
>>> list-sinks
2 sink(s) available.
  * index: 11
    name: <alsa_output.usb-2cc2_Teufel_Cinebar_One_ABCDEF0123456789-00.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 9049
    volume: front-left: 43757 /  67% / -10,53 dB,   front-right: 43757 /  67% / -10,53 dB
            balance 0,00
    base volume: 65536 / 100% / 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 11
    sample spec: s16le 2ch 48000Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 1837,50 ms
    card: 5 <alsa_card.usb-2cc2_Teufel_Cinebar_One_ABCDEF0123456789-00>
    module: 30
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "USB Audio"
        alsa.id = "USB Audio"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "Teufel Cinebar One"
        alsa.long_card_name = "Teufel Cinebar One at usb-0000:00:14.0-13.2.4, full speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:13.2.4:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13.2/1-13.2.4/1-13.2.4:1.0/sound/card1"
        udev.id = "usb-2cc2_Teufel_Cinebar_One_ABCDEF0123456789-00"
        device.bus = "usb"
        device.vendor.id = "2cc2"
        device.vendor.name = "2cc2"
        device.product.id = "0005"
        device.product.name = "Teufel Cinebar One"
        device.serial = "2cc2_Teufel_Cinebar_One_ABCDEF0123456789"
        device.string = "front:1"
        device.buffering.buffer_size = "352800"
        device.buffering.fragment_size = "176400"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Teufel Cinebar One Analog Stereo"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"
    ports:
        analog-output: Analog Output (priority 9900, latency offset 0 usec, available: unknown)
            properties:
                
    active port: <analog-output>
    index: 13
    name: <alsa_output.pci-0000_00_1f.3.hdmi-stereo-extra2>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 9030
    volume: front-left: 65536 / 100% / 0,00 dB,   front-right: 65536 / 100% / 0,00 dB
            balance 0,00
    base volume: 65536 / 100% / 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 13
    sample spec: s16le 2ch 48000Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 341,33 ms
    card: 1 <alsa_card.pci-0000_00_1f.3>
    module: 8
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 2"
        alsa.id = "HDMI 2"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "8"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xdf440000 irq 163"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "a2f0"
        device.product.name = "200 Series PCH HD Audio"
        device.form_factor = "internal"
        device.string = "hdmi:0,2"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo-extra2"
        device.profile.description = "Digital Stereo (HDMI 3)"
        device.description = "Built-in Audio Digital Stereo (HDMI 3)"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "video-display"
                device.product.name = "EV3237"
    active port: <hdmi-output-2>



```

```
>>> list-cards
2 card(s) available.
    index: 1
    name: <alsa_card.pci-0000_00_1f.3>
    driver: <module-alsa-card.c>
    owner module: 8
    properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xdf440000 irq 163"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "a2f0"
        device.product.name = "200 Series PCH HD Audio"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        input:analog-stereo: Analog Stereo Input (priority 65, available: no)
        output:analog-stereo: Analog Stereo Output (priority 6500, available: no)
        output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6565, available: no)
        output:analog-surround-21: Analog Surround 2.1 Output (priority 1300, available: no)
        output:analog-surround-21+input:analog-stereo: Analog Surround 2.1 Output + Analog Stereo Input (priority 1365, available: no)
        output:analog-surround-40: Analog Surround 4.0 Output (priority 1200, available: no)
        output:analog-surround-40+input:analog-stereo: Analog Surround 4.0 Output + Analog Stereo Input (priority 1265, available: no)
        output:analog-surround-41: Analog Surround 4.1 Output (priority 1300, available: no)
        output:analog-surround-41+input:analog-stereo: Analog Surround 4.1 Output + Analog Stereo Input (priority 1365, available: no)
        output:analog-surround-50: Analog Surround 5.0 Output (priority 1200, available: no)
        output:analog-surround-50+input:analog-stereo: Analog Surround 5.0 Output + Analog Stereo Input (priority 1265, available: no)
        output:analog-surround-51: Analog Surround 5.1 Output (priority 1300, available: no)
        output:analog-surround-51+input:analog-stereo: Analog Surround 5.1 Output + Analog Stereo Input (priority 1365, available: no)
        output:iec958-stereo: Digital Stereo (IEC958) Output (priority 5500, available: unknown)
        output:iec958-stereo+input:analog-stereo: Digital Stereo (IEC958) Output + Analog Stereo Input (priority 5565, available: no)
        output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5900, available: no)
        output:hdmi-stereo+input:analog-stereo: Digital Stereo (HDMI) Output + Analog Stereo Input (priority 5965, available: no)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 800, available: no)
        output:hdmi-surround+input:analog-stereo: Digital Surround 5.1 (HDMI) Output + Analog Stereo Input (priority 865, available: no)
        output:hdmi-surround71: Digital Surround 7.1 (HDMI) Output (priority 800, available: no)
        output:hdmi-surround71+input:analog-stereo: Digital Surround 7.1 (HDMI) Output + Analog Stereo Input (priority 865, available: no)
        output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Output (priority 5700, available: no)
        output:hdmi-stereo-extra1+input:analog-stereo: Digital Stereo (HDMI 2) Output + Analog Stereo Input (priority 5765, available: no)
        output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Output (priority 600, available: no)
        output:hdmi-surround-extra1+input:analog-stereo: Digital Surround 5.1 (HDMI 2) Output + Analog Stereo Input (priority 665, available: no)
        output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Output (priority 600, available: no)
        output:hdmi-surround71-extra1+input:analog-stereo: Digital Surround 7.1 (HDMI 2) Output + Analog Stereo Input (priority 665, available: no)
        output:hdmi-stereo-extra2: Digital Stereo (HDMI 3) Output (priority 5700, available: unknown)
        output:hdmi-stereo-extra2+input:analog-stereo: Digital Stereo (HDMI 3) Output + Analog Stereo Input (priority 5765, available: no)
        output:hdmi-stereo-extra3: Digital Stereo (HDMI 4) Output (priority 5700, available: no)
        output:hdmi-stereo-extra3+input:analog-stereo: Digital Stereo (HDMI 4) Output + Analog Stereo Input (priority 5765, available: no)
        output:hdmi-surround-extra3: Digital Surround 5.1 (HDMI 4) Output (priority 600, available: no)
        output:hdmi-surround-extra3+input:analog-stereo: Digital Surround 5.1 (HDMI 4) Output + Analog Stereo Input (priority 665, available: no)
        output:hdmi-surround71-extra3: Digital Surround 7.1 (HDMI 4) Output (priority 600, available: no)
        output:hdmi-surround71-extra3+input:analog-stereo: Digital Surround 7.1 (HDMI 4) Output + Analog Stereo Input (priority 665, available: no)
        output:hdmi-stereo-extra4: Digital Stereo (HDMI 5) Output (priority 5700, available: no)
        output:hdmi-stereo-extra4+input:analog-stereo: Digital Stereo (HDMI 5) Output + Analog Stereo Input (priority 5765, available: no)
        output:hdmi-surround-extra4: Digital Surround 5.1 (HDMI 5) Output (priority 600, available: no)
        output:hdmi-surround-extra4+input:analog-stereo: Digital Surround 5.1 (HDMI 5) Output + Analog Stereo Input (priority 665, available: no)
        output:hdmi-surround71-extra4: Digital Surround 7.1 (HDMI 5) Output (priority 600, available: no)
        output:hdmi-surround71-extra4+input:analog-stereo: Digital Surround 7.1 (HDMI 5) Output + Analog Stereo Input (priority 665, available: no)
        off: Off (priority 0, available: unknown)
    active profile: <output:hdmi-stereo-extra2>
    sinks:
        alsa_output.pci-0000_00_1f.3.hdmi-stereo-extra2/#13: Built-in Audio Digital Stereo (HDMI 3)
    sources:
        alsa_output.pci-0000_00_1f.3.hdmi-stereo-extra2.monitor/#13: Monitor of Built-in Audio Digital Stereo (HDMI 3)
    ports:
        analog-input-front-mic: Front Microphone (priority 8500, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-rear-mic: Rear Microphone (priority 8200, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-linein: Line In (priority 8100, latency offset 0 usec, available: no)
            properties:
                
        analog-output-lineout: Line Out (priority 9000, latency offset 0 usec, available: no)
            properties:
                
        analog-output-headphones: Headphones (priority 9900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
        iec958-stereo-output: Digital Output (S/PDIF) (priority 0, latency offset 0 usec, available: unknown)
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
                device.product.name = "EV3237"
        hdmi-output-3: HDMI / DisplayPort 4 (priority 5600, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-4: HDMI / DisplayPort 5 (priority 5500, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
    index: 5
    name: <alsa_card.usb-2cc2_Teufel_Cinebar_One_ABCDEF0123456789-00>
    driver: <module-alsa-card.c>
    owner module: 30
    properties:
        alsa.card = "1"
        alsa.card_name = "Teufel Cinebar One"
        alsa.long_card_name = "Teufel Cinebar One at usb-0000:00:14.0-13.2.4, full speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:13.2.4:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13.2/1-13.2.4/1-13.2.4:1.0/sound/card1"
        udev.id = "usb-2cc2_Teufel_Cinebar_One_ABCDEF0123456789-00"
        device.bus = "usb"
        device.vendor.id = "2cc2"
        device.vendor.name = "2cc2"
        device.product.id = "0005"
        device.product.name = "Teufel Cinebar One"
        device.serial = "2cc2_Teufel_Cinebar_One_ABCDEF0123456789"
        device.string = "1"
        device.description = "Teufel Cinebar One"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"
    profiles:
        output:analog-stereo: Analog Stereo Output (priority 6500, available: unknown)
        output:iec958-stereo: Digital Stereo (IEC958) Output (priority 5500, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <output:analog-stereo>
    sinks:
        alsa_output.usb-2cc2_Teufel_Cinebar_One_ABCDEF0123456789-00.analog-stereo/#11: Teufel Cinebar One Analog Stereo
    sources:
        alsa_output.usb-2cc2_Teufel_Cinebar_One_ABCDEF0123456789-00.analog-stereo.monitor/#11: Monitor of Teufel Cinebar One Analog Stereo
    ports:
        analog-output: Analog Output (priority 9900, latency offset 0 usec, available: unknown)
            properties:
                
        iec958-stereo-output: Digital Output (S/PDIF) (priority 0, latency offset 0 usec, available: unknown)
            properties:

```                


```
>>> list-clients
10 client(s) logged in.
    index: 0
    driver: <module-systemd-login.c>
    owner module: 18
    properties:
        application.name = "Login Session 1"
        systemd-login.session = "1"
    index: 1
    driver: <protocol-native.c>
    owner module: 12
    properties:
        application.name = "Ubuntu Audio Settings"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "33"
        application.id = "com.canonical.settings.sound"
        application.icon_name = "multimedia-volume-control"
        application.version = "0.1"
        application.process.id = "1791"
        application.process.user = "phil"
        application.process.host = "main"
        application.process.binary = "indicator-sound-service"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "8264e079a2af472fb6019f39bf24a685"
    index: 2
    driver: <protocol-native.c>
    owner module: 12
    properties:
        application.name = "Ubuntu Audio Settings"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "33"
        application.id = "com.canonical.settings.sound"
        application.icon_name = "multimedia-volume-control"
        application.version = "0.1"
        application.process.id = "1791"
        application.process.user = "phil"
        application.process.host = "main"
        application.process.binary = "indicator-sound-service"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "8264e079a2af472fb6019f39bf24a685"
    index: 3
    driver: <protocol-native.c>
    owner module: 12
    properties:
        application.name = "GNOME Volume Control Media Keys"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "33"
        application.id = "org.gnome.VolumeControl"
        application.icon_name = "multimedia-volume-control"
        application.version = "1.0"
        application.process.id = "1795"
        application.process.user = "phil"
        application.process.host = "main"
        application.process.binary = "unity-settings-daemon"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "8264e079a2af472fb6019f39bf24a685"
    index: 7
    driver: <module-x11-xsmp.c>
    owner module: 26
    properties:
        application.name = "XSMP Session on gnome-session as 10e09723b5ff2c6e81161554351310831400000018250059"
        xsmp.vendor = "gnome-session"
        xsmp.client.id = "10e09723b5ff2c6e81161554351310831400000018250059"
    index: 9
    driver: <protocol-native.c>
    owner module: 12
    properties:
        application.name = "Terminal"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "33"
        application.icon_name = "org.gnome.Terminal"
        window.x11.display = ":0"
        window.x11.screen = "0"
        application.process.id = "3208"
        application.process.user = "phil"
        application.process.host = "main"
        application.process.binary = "gnome-terminal-server"
        application.language = "en_US.UTF-8"
        application.process.machine_id = "8264e079a2af472fb6019f39bf24a685"
    index: 12
    driver: <protocol-native.c>
    owner module: 12
    properties:
        application.name = "unity-panel-service"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "33"
        window.x11.display = ":0"
        window.x11.screen = "0"
        application.process.id = "1974"
        application.process.user = "phil"
        application.process.host = "main"
        application.process.binary = "unity-panel-service"
        application.language = "en_US.UTF-8"
        application.process.machine_id = "8264e079a2af472fb6019f39bf24a685"
    index: 22
    driver: <protocol-native.c>
    owner module: 12
    properties:
        application.name = "Google Chrome input"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "33"
        application.process.id = "3820"
        application.process.user = "phil"
        application.process.host = "main"
        application.process.binary = "chrome"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "8264e079a2af472fb6019f39bf24a685"
    index: 58
    driver: <cli.c>
    owner module: 31
    properties:
        application.name = "UNIX socket client"
    index: 59
    driver: <protocol-native.c>
    owner module: 12
    properties:
        application.name = "org.gnome.Nautilus"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "33"
        application.icon_name = "org.gnome.Nautilus"
        window.x11.display = ":0"
        window.x11.screen = "0"
        application.process.id = "7122"
        application.process.user = "phil"
        application.process.host = "main"
        application.process.binary = "nautilus"
        application.language = "en_US.UTF-8"
        application.process.machine_id = "8264e079a2af472fb6019f39bf24a685"

```

---

### Post by motophil on 2021-03-12
[COLOR=#242729]Found it myself. The "Teufel Cinebar One" USB sound seems to only support 48000Hz output. So edit /etc/pulse/daemon.conf, and change the line[/COLOR]

[FONT=Consolas]; default-sample-rate = 44100[/FONT][COLOR=#242729]

to

[FONT=Consolas]default-sample-rate = 48000[/FONT][/COLOR][COLOR=#242729][COLOR=#222222][FONT=Verdana]

[/FONT][/COLOR]then restart pulseaudio:

[/COLOR][FONT=Consolas]pulseaudio -k[/FONT][COLOR=#242729][COLOR=#222222][FONT=Verdana]

[/FONT][/COLOR]This works like a charm :)
[/COLOR]
[COLOR=#242729]Philip[/COLOR]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]
[/FONT]

---

