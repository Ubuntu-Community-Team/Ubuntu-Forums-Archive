---
title: "Fixing audio on Ubuntu 20.04 | ASUS VIA VT1708S"
date: 2020-08-11
forum: Hardware
---

### Post by mscofield2 on 2020-08-11
I'm trying to fix my damn sound on Ubuntu for a week now and I can't find good resource that is new, everything I find is a decade old.

Problem is my Intel HD Audio isn't being used for some reason, Ubuntu recognizes it, as evident from:

```

bloo@mscofield:~$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: VT1708S Alt Analog [VT1708S Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Alsamixer also recognizes it, as evident from:
[IMG]https://media.discordapp.net/attachments/471740270036385824/742852718116339833/unknown.png[/IMG]


How come my sound settings don't recognize it and let me use it?

The post with the old links is: [URL="https://doc.ubuntu-fr.org/audio_intel_hda"]https://doc.ubuntu-fr.org/audio_intel_hda
[/URL]under the VIA VT1708S section: [http://ubuntuforums.org/showthread.php?t=1204735](http://ubuntuforums.org/showthread.php?t=1204735)

---

### Post by Yellow Pasque on 2020-08-11
Swearing and duplicating threads will not get your problem fixed faster. [https://ubuntuforums.org/showthread.php?t=2448359&p=13978131](https://ubuntuforums.org/showthread.php?t=2448359&p=13978131)

Now that you have reinstalled, get a new copy of the alsa info.
EDIT: Also, give output of:
```
pacmd list-sinks
```

---

### Post by mscofield2 on 2020-08-12
That is the new copy of alsa info.

Here is the output from pacmd

```
1 sink(s) available.
  * index: 3
    name: <alsa_output.pci-0000_01_00.1.hdmi-stereo-extra1>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: (none)
    priority: 9030
    volume: front-left: 65536 / 100% / 0,00 dB,   front-right: 65536 / 100% / 0,00 dB
            balance 0,00
    base volume: 65536 / 100% / 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 7,85 ms
    max request: 1 KiB
    max rewind: 1 KiB
    monitor source: 3
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 3
    linked by: 3
    configured latency: 8,00 ms; range is 8,00 .. 371,52 ms
    card: 0 <alsa_card.pci-0000_01_00.1>
    module: 23
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 1"
        alsa.id = "HDMI 1"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "7"
        alsa.card = "1"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xf7080000 irq 17"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:01:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "NVIDIA Corporation"
        device.product.id = "10f1"
        device.product.name = "GP106 High Definition Audio Controller"
        device.string = "hdmi:1,1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo-extra1"
        device.profile.description = "Digital Stereo (HDMI 2)"
        device.description = "GP106 High Definition Audio Controller Digital Stereo (HDMI 2)"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "video-display"
    active port: <hdmi-output-1>
```

---

### Post by Yellow Pasque on 2020-08-12
> **mscofield2 said:**
> That is the new copy of alsa info.
What is? I only see one link to alsa info in your old thread.

---

### Post by mscofield2 on 2020-08-13
Oh, I apologize, I thought alsa info meant the alsamixer screenshot, I forgot.

Here's the new alsa-info:
[http://alsa-project.org/db/?f=7e93f5a11f8c75909bc5c899cdcd1546a1b2acfd](http://alsa-project.org/db/?f=7e93f5a11f8c75909bc5c899cdcd1546a1b2acfd)

And thank you for helping me.

---

### Post by Yellow Pasque on 2020-08-14
> **mscofield2 said:**
> Here's the new alsa-info

That looks better. In fact, everything looks fine to me in that log. But for some reason, pulseaudio is not happy.
I think the next step is to get a log for pulseaudio: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)
You may want to file a bug on this since it happens on clean install (and include the pulseaudio log).
```
ubuntu-bug audio
```

---

### Post by mscofield2 on 2020-08-14
So here is the pulseaudio log:
```
(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
(   0.000|   0.000) D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
(   0.005|   0.005) D: [pulseaudio] core-util.c: RealtimeKit worked.
(   0.005|   0.000) I: [pulseaudio] core-util.c: Successfully gained nice level -11.
(   0.005|   0.000) I: [pulseaudio] main.c: This is PulseAudio 13.99.1
(   0.005|   0.000) D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
(   0.005|   0.000) D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fdebug-prefix-map=/build/pulseaudio-EPqXvV/pulseaudio-13.99.1=. -fstack-protector-strong -Wformat -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -fno-common -fdiagnostics-show-option -fdiagnostics-color=auto
(   0.005|   0.000) D: [pulseaudio] main.c: Running on host: Linux x86_64 5.4.0-42-generic #46-Ubuntu SMP Fri Jul 10 00:24:02 UTC 2020
(   0.006|   0.000) D: [pulseaudio] main.c: Found 4 CPUs.
(   0.006|   0.000) I: [pulseaudio] main.c: Page size is 4096 bytes
(   0.006|   0.000) D: [pulseaudio] main.c: Compiled with Valgrind support: no
(   0.006|   0.000) D: [pulseaudio] main.c: Running in valgrind mode: no
(   0.006|   0.000) D: [pulseaudio] main.c: Running in VM: no
(   0.006|   0.000) D: [pulseaudio] main.c: Running from build tree: no
(   0.006|   0.000) D: [pulseaudio] main.c: Optimized build: yes
(   0.006|   0.000) D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
(   0.006|   0.000) I: [pulseaudio] main.c: Machine ID is 21d1b364ec0f449392b27ba7f25b430a.
(   0.006|   0.000) I: [pulseaudio] main.c: Using runtime directory /run/user/1000/pulse.
(   0.006|   0.000) I: [pulseaudio] main.c: Using state directory /home/bloo/.config/pulse.
(   0.006|   0.000) I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-13.99.1/modules.
(   0.006|   0.000) I: [pulseaudio] main.c: Running in system mode: no
(   0.006|   0.000) E: [pulseaudio] pid.c: Daemon already running.
(   0.006|   0.000) E: [pulseaudio] main.c: pa_pid_file_create() failed.
```

I also noticed something interesting when I ran the bug report command.
[IMG]https://media.discordapp.net/attachments/471740270036385824/743931638282715146/unknown.png[/IMG]

so I installed pavucontrol via `sudo apt install pavucontrol`
I ran it and in the `Configuration` tab it says that the Built-in audio is all "unplugged".

Also when it played sounds to the outputs, I did actually hear sound from my headphones!
The bug report link is: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1891715](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1891715)

---

### Post by Yellow Pasque on 2020-08-15
Other than playing with "Auto-Mute" and "Independent HP" controls in alsamixer (spacebar to toggle), I don't have any suggestions. :\

---

### Post by mscofield2 on 2020-08-16
Just tried and it restarted. Sadly it didn't fix it. :(

---

