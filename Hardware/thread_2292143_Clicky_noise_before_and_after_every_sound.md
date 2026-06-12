---
title: "Clicky noise before and after every sound"
date: 2015-08-25
forum: Hardware
---

### Post by DJDBgr on 2015-08-25
[COLOR=#111111][FONT=Ubuntu]Hello. I'm getting a click/pop (like something is powering on/off) before and after every sound (or modification of the volume via the software) on my system. I'm using a Behringer UCA222, connected via an optical audio cable with my speakers.

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Any idea what's wrong?
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks in advance.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This is my inxi -Fx ouput:
[/FONT][/COLOR]
```
System:    Host: djdblinux Kernel: 3.19.0-26-generic x86_64 (64 bit gcc: 4.9.2)
           Desktop: Unity 7.3.2 (Gtk 3.14.13-0ubuntu1)
           Distro: Ubuntu 15.04 vivid
Machine:   Mobo: ASRock model: Z97 Extreme4
           Bios: American Megatrends v: P1.30 date: 05/23/2014
CPU:       Quad core Intel Core i5-4690K (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 27992
           clock speeds: max: 3900 MHz 1: 3896 MHz 2: 3496 MHz 3: 2793 MHz
           4: 2716 MHz
Graphics:  Card: NVIDIA GK104 [GeForce GTX 770] bus-ID: 01:00.0
           Display Server: X.Org 1.17.1 driver: nvidia
           Resolution: 1600x900@60.0hz, 1920x1080@60.0hz
           GLX Renderer: GeForce GTX 770/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 352.30 Direct Rendering: Yes
Audio:     Card-1 NVIDIA GK104 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Texas Instruments PCM2902C Audio CODEC
           driver: USB Audio usb-ID: 001-008
           Sound: Advanced Linux Sound Architecture v: k3.19.0-26-generic
Network:   Card: Intel Ethernet Connection (2) I218-V
           driver: e1000e v: 2.3.2-k port: f040 bus-ID: 00:19.0
           IF: eth0 state: up speed: 100 Mbps duplex: full
           mac: d0:50:99:28:ed:16
Drives:    HDD Total Size: 1128.3GB (29.0% used)
           ID-1: /dev/sda model: INTEL_SSDSC2CW12 size: 120.0GB
           ID-2: /dev/sdb model: WDC_WD10EZEX size: 1000.2GB
           ID-3: USB /dev/sdc model: v165w size: 8.0GB
Partition: ID-1: / size: 102G used: 17G (18%) fs: ext4 dev: /dev/sda2
           ID-2: swap-1 size: 8.53GB used: 0.00GB (0%) fs: swap dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 55.0C mobo: N/A gpu: 0.0:60C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 267 Uptime: 3:58 Memory: 3264.5/7932.9MB
           Init: systemd runlevel: 5 Gcc sys: 4.9.2
           Client: Shell (bash 4.3.301) inxi: 2.2.16 

```

---

### Post by DJDBgr on 2015-08-25
So, after a lot of searching and experimenting, i solved this on my own. I have found a workaround and not a fix, since this is a bug that affects Behringer uca222, [with an unsolved LaunchPad bug report from 3 years back]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/995090").

To make all the crackling noises disappear, you have to install PulseAudio Volume Control and just... run it. To install it, just fire up a terminal and run

```
sudo apt-get install pavucontrol
```

That's it. I don't really know why, but after running Volume Control, all the crackling is fixed. This means that if you close the app you'll have to face the same cracks/pops, so just leave it running minimized.

If you want to run pavucontrol on boot **and have it automatically minimized**, add it as a startup application.

[[IMG]http://i.imgur.com/ZmxuJGmb.jpg[/IMG]]("http://imgur.com/ZmxuJGm")

Then, install gDevilsPie using

```
sudo apt-get install gdevilspie
```

Open gdevilspieand add a new rule, using the following conditions and actions:

[[IMG]http://i.imgur.com/X2sEYXib.jpg[/IMG]]("http://imgur.com/X2sEYXi") [[IMG]http://i.imgur.com/fWIGTo8b.jpg[/IMG]]("http://imgur.com/fWIGTo8")

Save, set gdevilspie to run on boot and you're done.

---

### Post by DJDBgr on 2015-08-27
kudos to Reddit user /u/solen-skiner, i think that there is a better solution/workaround. Check [here]("https://www.reddit.com/r/linux/comments/3idb1h/clicky_noise_before_and_after_every_sound/cug3x5u") and [here]("https://www.reddit.com/r/linux/comments/3idb1h/clicky_noise_before_and_after_every_sound/cui06gk").

---

### Post by Yellow Pasque on 2015-08-28
> I wish PA would ship with a blacklist of known "bad" hardware, and intelligently disable that plugin... Users shouldn't have to deal with problems like this.

What you're doing is a hacky workaround. If your audio device clicks when changing power states, the best solution is to try and fix it at the kernel/driver level. After all, the card would probably exhibit the same symptom(s) if you use a distro that doesn't use pulseaudio.

> an unsolved LaunchPad bug report from 3 years back.
It seems like that report complains of crackling/static in the middle of watching video.  That's a bit different than what you're experiencing.
If you want to file a bug report, you'd probably have more luck using the kernel bugzilla: [https://bugzilla.kernel.org/](https://bugzilla.kernel.org/)
I'd suggest installing a vanilla 4.2 kernel before making a report:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-rc8-unstable/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-rc8-unstable/)

---

