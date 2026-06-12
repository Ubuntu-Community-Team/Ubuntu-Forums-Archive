---
title: "pulse won't load"
date: 2009-12-03
forum: Hardware
---

### Post by LutraMan on 2009-12-03
I seem to have a problem with pulseaudio.
I can't get it started.

here is the verbose code:
```
tom@tom-desktop:~$ pulseaudio -v
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Failed to acquire high-priority scheduling: No such file or directory
I: main.c: This is PulseAudio 0.9.19
I: main.c: Page size is 4096 bytes
I: main.c: Machine ID is 1034af32e50519c628a5e26a4afeccc9.
I: main.c: Session ID is 1034af32e50519c628a5e26a4afeccc9-1259873066.366102-586355925.
I: main.c: Using runtime directory /home/tom/.pulse/1034af32e50519c628a5e26a4afeccc9-runtime.
I: main.c: Using state directory /home/tom/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.19/modules.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: cpu-x86.c: CPU flags: MMX SSE SSE2 SSE3 SSSE3 
I: svolume_mmx.c: Initialising MMX optimized functions.
I: remap_mmx.c: Initialising MMX optimized remappers.
I: svolume_sse.c: Initialising SSE2 optimized functions.
I: remap_sse.c: Initialising SSE2 optimized remappers.
I: sconv_sse.c: Initialising SSE2 optimized conversions.
I: module-device-restore.c: Sucessfully opened database file '/home/tom/.pulse/1034af32e50519c628a5e26a4afeccc9-device-volumes'.
I: module.c: Loaded "module-device-restore" (index: #0; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/tom/.pulse/1034af32e50519c628a5e26a4afeccc9-stream-volumes'.
I: module.c: Loaded "module-stream-restore" (index: #1; argument: "").
I: module-card-restore.c: Sucessfully opened database file '/home/tom/.pulse/1034af32e50519c628a5e26a4afeccc9-card-database'.
I: module.c: Loaded "module-card-restore" (index: #2; argument: "").
I: module.c: Loaded "module-augment-properties" (index: #3; argument: "").
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D3p failed
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
I: card.c: Created 0 "alsa_card.pci-0000_00_1b.0"
I: alsa-sink.c: Successfully opened device front:0.
I: alsa-sink.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-mixer.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-mixer.c: Successfully attached to mixer 'hw:0'
I: sink.c: Created sink 0 "alsa_output.pci-0000_00_1b.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     alsa.resolution_bits = "16"
I: sink.c:     device.api = "alsa"
I: sink.c:     device.class = "sound"
I: sink.c:     alsa.class = "generic"
I: sink.c:     alsa.subclass = "generic-mix"
I: sink.c:     alsa.name = "ALC889A Analog"
I: sink.c:     alsa.id = "ALC889A Analog"
I: sink.c:     alsa.subdevice = "0"
I: sink.c:     alsa.subdevice_name = "subdevice #0"
I: sink.c:     alsa.device = "0"
I: sink.c:     alsa.card = "0"
I: sink.c:     alsa.card_name = "HDA Intel"
I: sink.c:     alsa.long_card_name = "HDA Intel at 0xfa100000 irq 22"
I: sink.c:     alsa.driver_name = "snd_hda_intel"
I: sink.c:     device.bus_path = "pci-0000:00:1b.0"
I: sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: sink.c:     device.bus = "pci"
I: sink.c:     device.vendor.id = "8086"
I: sink.c:     device.vendor.name = "Intel Corporation"
I: sink.c:     device.product.id = "293e"
I: sink.c:     device.product.name = "82801I (ICH9 Family) HD Audio Controller"
I: sink.c:     device.form_factor = "internal"
I: sink.c:     device.string = "front:0"
I: sink.c:     device.buffering.buffer_size = "65536"
I: sink.c:     device.buffering.fragment_size = "32768"
I: sink.c:     device.access_mode = "mmap+timer"
I: sink.c:     device.profile.name = "analog-stereo"
I: sink.c:     device.profile.description = "Analog Stereo"
I: sink.c:     device.description = "Internal Audio Analog Stereo"
I: sink.c:     alsa.mixer_name = "Realtek ALC889A"
I: sink.c:     alsa.components = "HDA:10ec0885,1458a002,00100101"
I: sink.c:     module-udev-detect.discovered = "1"
I: sink.c:     device.icon_name = "audio-card-pci"
I: source.c: Created source 0 "alsa_output.pci-0000_00_1b.0.analog-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of Internal Audio Analog Stereo"
I: source.c:     device.class = "monitor"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA Intel"
I: source.c:     alsa.long_card_name = "HDA Intel at 0xfa100000 irq 22"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:00:1b.0"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "8086"
I: source.c:     device.vendor.name = "Intel Corporation"
I: source.c:     device.product.id = "293e"
I: source.c:     device.product.name = "82801I (ICH9 Family) HD Audio Controller"
I: source.c:     device.form_factor = "internal"
I: source.c:     device.string = "0"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-sink.c: Using 2.0 fragments of size 32768 bytes (185.76ms), buffer size is 65536 bytes (371.52ms)
I: alsa-sink.c: Time scheduling watermark is 20.00ms
I: alsa-sink.c: Hardware volume ranges from -179.00 dB to 0.00 dB.
I: alsa-sink.c: No particular base volume set, fixing to 0 dB
I: alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-sink.c: Using hardware mute control.
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 4, which is lower than the requested 5.
I: alsa-sink.c: Starting playback.
I: alsa-source.c: Successfully opened device front:0.
I: alsa-source.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: alsa-source.c: Successfully enabled mmap() mode.
I: alsa-source.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-mixer.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-mixer.c: Successfully attached to mixer 'hw:0'
I: source.c: Created source 1 "alsa_input.pci-0000_00_1b.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     alsa.resolution_bits = "16"
I: source.c:     device.api = "alsa"
I: source.c:     device.class = "sound"
I: source.c:     alsa.class = "generic"
I: source.c:     alsa.subclass = "generic-mix"
I: source.c:     alsa.name = "ALC889A Analog"
I: source.c:     alsa.id = "ALC889A Analog"
I: source.c:     alsa.subdevice = "0"
I: source.c:     alsa.subdevice_name = "subdevice #0"
I: source.c:     alsa.device = "0"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA Intel"
I: source.c:     alsa.long_card_name = "HDA Intel at 0xfa100000 irq 22"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:00:1b.0"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "8086"
I: source.c:     device.vendor.name = "Intel Corporation"
I: source.c:     device.product.id = "293e"
I: source.c:     device.product.name = "82801I (ICH9 Family) HD Audio Controller"
I: source.c:     device.form_factor = "internal"
I: source.c:     device.string = "front:0"
I: source.c:     device.buffering.buffer_size = "65536"
I: source.c:     device.buffering.fragment_size = "32768"
I: source.c:     device.access_mode = "mmap+timer"
I: source.c:     device.profile.name = "analog-stereo"
I: source.c:     device.profile.description = "Analog Stereo"
I: source.c:     device.description = "Internal Audio Analog Stereo"
I: source.c:     alsa.mixer_name = "Realtek ALC889A"
I: source.c:     alsa.components = "HDA:10ec0885,1458a002,00100101"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-source.c: Using 2.0 fragments of size 32768 bytes (185.76ms), buffer size is 65536 bytes (371.52ms)
I: alsa-source.c: Time scheduling watermark is 20.00ms
I: alsa-source.c: Hardware volume ranges from -16.00 dB to 30.00 dB.
I: alsa-source.c: Fixing base volume to -30.00 dB
I: alsa-source.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-source.c: Using hardware mute control.
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 4, which is lower than the requested 5.
I: module.c: Loaded "module-alsa-card" (index: #4; argument: "device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"").
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:1b.0/sound/card0 (alsa_card.pci-0000_00_1b.0) module loaded.
I: module-udev-detect.c: Found 1 cards.
I: module.c: Loaded "module-udev-detect" (index: #5; argument: "").
I: module.c: Loaded "module-bluetooth-discover" (index: #6; argument: "").
E: socket-server.c: **bind(): Address already in use**
E: module.c: **Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.**
E: main.c: **Module load failed.**
E: main.c: **Failed to initialize daemon.**
I: module.c: Unloading "module-device-restore" (index: #0).
I: module.c: Unloaded "module-device-restore" (index: #0).
I: module.c: Unloading "module-stream-restore" (index: #1).
I: module.c: Unloaded "module-stream-restore" (index: #1).
I: module.c: Unloading "module-card-restore" (index: #2).
I: module.c: Unloaded "module-card-restore" (index: #2).
I: module.c: Unloading "module-augment-properties" (index: #3).
I: module.c: Unloaded "module-augment-properties" (index: #3).
I: module.c: Unloading "module-alsa-card" (index: #4).
I: sink.c: Freeing sink 0 "alsa_output.pci-0000_00_1b.0.analog-stereo"
I: source.c: Freeing source 0 "alsa_output.pci-0000_00_1b.0.analog-stereo.monitor"
I: source.c: Freeing source 1 "alsa_input.pci-0000_00_1b.0.analog-stereo"
I: card.c: Freed 0 "alsa_card.pci-0000_00_1b.0"
I: module.c: Unloaded "module-alsa-card" (index: #4).
I: module.c: Unloading "module-udev-detect" (index: #5).
I: module.c: Unloaded "module-udev-detect" (index: #5).
I: module.c: Unloading "module-bluetooth-discover" (index: #6).
I: module.c: Unloaded "module-bluetooth-discover" (index: #6).
I: main.c: Daemon terminated.

```

I've looked and all I could find in forums are very similar problems but not one with a working solution for me.

any kind of help would be very appreciated.

---

### Post by LutraMan on 2009-12-03
Something new.

Pulse loads now, but it tries to load a blue-tooth module (witch is unnecessary since I don't have a bt on my computer) and loads it with errors, witch later causes wine programs to fail to load with this output message:
```
bt_audio_service_open: connect() failed: Connection refused (111)

```

any idea how I stop it from loading bt?

---

### Post by LutraMan on 2009-12-04
anyone??? plz...

---

