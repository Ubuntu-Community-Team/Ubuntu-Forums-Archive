---
title: "setting sound from 3.5 MM jack instead of HDMI"
date: 2021-06-12
forum: Hardware
---

### Post by ejbiow on 2021-06-12
I have the same issue. I installed Kubuntu 21.04 Hirsute Hippo and I could never get the analog sound to be recognized (though it works fine in Windows, which came with the computer, but is not my daily driver). I used tasksel to install Ubuntu-Desktop (gnome 3), hoping that would work, but it didn't. HDMI sound works fine through my TV speakers, and I can use bluetooth to my Bluetooth devices, but I just bought a nice Klipsch ProMedia 2.1 set of speakers and I'd like to annoy the neighborhood. 

I tried a bunch of stuff that sometimes helps:


[LIST]
[*][I]removing timidity
[/I] 
[*][I] [FONT=monospace][COLOR=#000000]pactl load-module module-detect[/COLOR][/FONT]
[/I] 
[*][I] [FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]killall pulseaudio; pulseaudio -k  ; rm -r ~/.config/pulse/* ; rm -r ~/.pulse*
[/COLOR][/FONT][/COLOR][/FONT][/I] 
[*][I][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000] removing the pipewire packages, which removed Plasma & Gnome but didn't help the sound issue, so I reinstalled them and kubuntu-desktop
[/COLOR][/FONT][/COLOR][/FONT][/I] 
[*][I][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]sudo alsa force-reload (this command didn't even kill the Mozart I was listening to with audacious)[/COLOR]
[/FONT][/COLOR][/FONT][/COLOR][/FONT][/I] 
[*][I][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000][FONT=monospace] I added "[/FONT][/COLOR][/FONT][/COLOR][/FONT][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000][FONT=monospace][FONT=monospace][COLOR=#000000]options snd-hda-intel model=auto[/COLOR][/FONT]" to [/FONT][/COLOR][/FONT][/COLOR][/FONT][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000][FONT=monospace][FONT=monospace][COLOR=#000000]/etc/modprobe.d/alsa-base.conf & rebooted
[/COLOR][/FONT][/FONT][/COLOR][/FONT][/COLOR][/FONT][/I] 
[*][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000][FONT=monospace][FONT=monospace][FONT=monospace][I][COLOR=#000000]sudo setfacl -m u:$USER:rw /dev/snd/*[/COLOR]
[/I][/FONT][/FONT][/FONT][/COLOR][/FONT][/COLOR][/FONT] 
[*][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000][FONT=monospace][FONT=monospace][FONT=monospace]* Pavucontrol didn't help, it only saw my HDMI interface. (same with alsamixer)*
[/FONT][/FONT][/FONT][/COLOR][/FONT][/COLOR][/FONT] 
[/LIST]
[FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000][FONT=monospace][FONT=monospace][FONT=monospace]Same story with the systemsettings5 & Gnome-settings sound modules, just HDMI.
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

[/FONT][/FONT][/FONT]My hardware doesn't look too exotic.

```
lspci -nn | grep -i audio
00:0e.0 Multimedia audio controller [0401]: Intel Corporation Celeron/Pentium Silver Processor High Definition Audio [8086:3198] (rev 06)

inxi -Ax
Audio:     Device-1: Intel Celeron/Pentium Silver Processor High Definition Audio
           driver: snd_hda_intel v: kernel bus ID: 00:0e.0
           Sound Server: ALSA v: k5.11.0-18-generic

cat /proc/asound/car*/co* |  grep Codec
Codec: Intel Geminilake HDMI
```

[/COLOR]I went through most of the stuff in the [Sound Troubleshooting]("https://ubuntuforums.org/showthread.php?t=1885240") sticky thread that doesn't require setting up a PPA. I'm getting a mite frustrated, any suggestions?
[/FONT][/COLOR][/FONT]

---

### Post by ejbiow on 2021-06-13
Perhaps the hardware is too new. This is my most recent machine. 
```
inxi -Fxz
Audio:
  Device-1: Intel Celeron/Pentium Silver Processor High Definition Audio 
  driver: snd_hda_intel v: kernel bus ID: 00:0e.0 
  Sound Server: ALSA 
```
Disabling pipewire didn't help. I did this:
[INDENT][FONT=monospace][COLOR=#000000]sudo systemctl --global disable pipewire[/COLOR]
[/FONT][/INDENT]
[INDENT][FONT=monospace][COLOR=#000000]sudo apt-mark hold libpipewire* pipewire*[/COLOR]
[/FONT][FONT=monospace]
[/FONT][/INDENT]
Pulseaudio is now the only running sound software:
 ```
fuser -v /dev/snd/* 
``````

                     USER        PID ACCESS COMMAND 
/dev/snd/controlC0:  luser         3515 F.... pulseaudio
```
I booted a USB ISO of Kali Linux and had the same issues even though no pipewire packages were installed. It is Debian-based with a recent kernel.
Linux kali 5.10.0-kali7-amd64 

The generic sound module is not loading in Hirsute or Kali.

lsmod | grep audio 
ledtrig_audio          16384  1 snd_sof

So I did a 'sudo modprobe snd_hda_codec_generic', and though not it is showing up, the situation has not changed.

lsmod | grep audio 
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_sof

There is just no sign of analog audio:
```

pacmd list-sinks 
1 sink(s) available. 
  * index: 0 
        name: <alsa_output.pci-0000_00_0e.0.hdmi-stereo> 
        driver: <module-alsa-card.c> 
        flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY 
        state: SUSPENDED 
        suspend cause: IDLE 
        priority: 9030 
        volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB 
                balance 0.00 
        base volume: 65536 / 100% / 0.00 dB 
        volume steps: 65537 
        muted: no 
        current latency: 0.00 ms 
        max request: 0 KiB 
        max rewind: 0 KiB 
        monitor source: 0 
        sample spec: s16le 2ch 44100Hz 
        channel map: front-left,front-right 
                     Stereo 
        used by: 0 
        linked by: 0 
        configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms 
        card: 0 <alsa_card.pci-0000_00_0e.0> 
        module: 7 
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
                alsa.card = "0" 
                alsa.card_name = "HDA Intel PCH" 
                alsa.long_card_name = "HDA Intel PCH at 0xa1110000 irq 138" 
                alsa.driver_name = "snd_hda_intel" 
                device.bus_path = "pci-0000:00:0e.0" 
                sysfs.path = "/devices/pci0000:00/0000:00:0e.0/sound/card0" 
                device.bus = "pci" 
                device.vendor.id = "8086" 
                device.vendor.name = "Intel Corporation" 
                device.product.id = "3198" 
                device.product.name = "Celeron/Pentium Silver Processor High Definition Audio" 
                device.form_factor = "internal" 
                device.string = "hdmi:0" 
                device.buffering.buffer_size = "352800" 
                device.buffering.fragment_size = "176400" 
                device.access_mode = "mmap+timer" 
                device.profile.name = "hdmi-stereo" 
                device.profile.description = "Digital Stereo (HDMI)" 
                device.description = "Built-in Audio Digital Stereo (HDMI)" 
                module-udev-detect.discovered = "1" 
                device.icon_name = "audio-card-pci" 
        ports: 
                hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, availa
ble: yes) 
                        properties: 
                                device.icon_name = "video-display" 
                                device.product.name = "SONY TV" 
        active port: <hdmi-output-0>

```

```

cat /proc/bus/input/devices

I: Bus=0000 Vendor=0000 Product=0000 Version=0000 
N: Name="HDA Intel PCH HDMI/DP,pcm=3" 
P: Phys=ALSA 
S: Sysfs=/devices/pci0000:00/0000:00:0e.0/sound/card0/input20 
U: Uniq= 
H: Handlers=event8  
B: PROP=0 
B: EV=21 
B: SW=140 

I: Bus=0000 Vendor=0000 Product=0000 Version=0000 
N: Name="HDA Intel PCH HDMI/DP,pcm=7" 
P: Phys=ALSA 
S: Sysfs=/devices/pci0000:00/0000:00:0e.0/sound/card0/input21 
U: Uniq= 
H: Handlers=event9  
B: PROP=0 
B: EV=21 
B: SW=140 

I: Bus=0000 Vendor=0000 Product=0000 Version=0000 
N: Name="HDA Intel PCH HDMI/DP,pcm=8" 
P: Phys=ALSA 
S: Sysfs=/devices/pci0000:00/0000:00:0e.0/sound/card0/input22 
U: Uniq= 
H: Handlers=event10  
B: PROP=0 
B: EV=21 
B: SW=140 

I: Bus=0000 Vendor=0000 Product=0000 Version=0000 
N: Name="HDA Intel PCH HDMI/DP,pcm=9" 
P: Phys=ALSA 
S: Sysfs=/devices/pci0000:00/0000:00:0e.0/sound/card0/input23 
U: Uniq= 
H: Handlers=event11  
B: PROP=0 
B: EV=21 
B: SW=140 

I: Bus=0000 Vendor=0000 Product=0000 Version=0000 
N: Name="HDA Intel PCH HDMI/DP,pcm=10" 
P: Phys=ALSA 
S: Sysfs=/devices/pci0000:00/0000:00:0e.0/sound/card0/input24 
U: Uniq= 
H: Handlers=event12  
B: PROP=0 
B: EV=21 
B: SW=140

```
Let's see if my machine explodes if I blacklist HDMI. Back in a bit.

echo "blacklist snd_hdmi_lpe_audio" | sudo tee /etc/modprobe.d/blacklist_snd_hdmi_lpe_audio.conf

---

### Post by ejbiow on 2021-06-13
Nope, just a bit of smoke, and it didn't even disable HDMI sound.

---

### Post by TheFu on 2021-06-13
I don't think pipewire is part of any Ubuntu yet. It is alpha on bleeding edge releases and has to be manually installed on Ubuntu. If you aren't both a Linux guru and sound engineer, probably best to stay on more commonly used systems like pulse or jack.

We don't discuss Kali Linux in these forums. Good way to get a thread closed.

---

### Post by ejbiow on 2021-06-14
Wrong, pipewire may not have any function on current *buntu releases, but several pipewire packages are baked into K/Ubuntu 21.04.
```
dpkg -l | grep pipewire 
ii  gstreamer1.0-pipewire:amd64                   0.3.24-3                                     
                        amd64        GStreamer 1.0 plugin for the PipeWire multimedia server 
hi  libpipewire-0.3-0:amd64                       0.3.24-3                                     
                        amd64        libraries for the PipeWire multimedia server 
hi  libpipewire-0.3-modules:amd64                 0.3.24-3                                     
                        amd64        libraries for the PipeWire multimedia server - modules 
hi  pipewire:amd64                                0.3.24-3                                     
                        amd64        audio and video processing engine multimedia server 
hi  pipewire-bin                                  0.3.24-3                                     
                        amd64        PipeWire multimedia server - programs

```
If you try to remove them it will strip out both Gnome3 & Plasma desktops.
```
apt-get remove pipewire pipewire-bin  libpipewire-0.3-0 libpipewire-0.3-modu
les 
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
The following packages will be REMOVED: 
  chrome-gnome-shell gdm3 gir1.2-mutter-7 gnome-remote-desktop gnome-shell 
  gnome-shell-extension-appindicator gnome-shell-extension-desktop-icons-ng 
  gnome-shell-extension-prefs gnome-shell-extension-ubuntu-dock 
  gnome-shell-extension-volume-mixer gnome-shell-extension-weather gnome-tweaks 
  gstreamer1.0-pipewire kinfocenter kubuntu-desktop kubuntu-settings-desktop kwin-wayland 
  libmutter-7-0 libpipewire-0.3-0 libpipewire-0.3-modules pipewire pipewire-bin 
  plasma-desktop plasma-discover-backend-snap plasma-widgets-addons plasma-workspace 
  plasma-workspace-wayland sddm-theme-breeze ubuntu-desktop ubuntu-desktop-minimal 
  ubuntu-session xdg-desktop-portal xdg-desktop-portal-gtk xdg-desktop-portal-kde 
The following held packages will be changed: 
  libpipewire-0.3-0 libpipewire-0.3-modules pipewire pipewire-bin 
0 upgraded, 0 newly installed, 34 to remove and 0 not upgraded. 
After this operation, 53.2 MB disk space will be freed. 
Do you want to continue? [Y/n] 

```
In fact there are a couple of pipewires package that I certainly did not consciously install on my focal 20.04 home server.

dpkg -l | grep pipewire 
```
ii  libpipewire-0.2-1:amd64                       0.2.7-1                                     a
md64        libraries for the PipeWire multimedia server 
ii  pipewire                                      0.2.7-1                                     a
md64        PipeWire multimedia server


``````

apt-cache policy  pipewire     
pipewire: 
  Installed: 0.2.7-1 
  Candidate: 0.2.7-1 
  Version table: 
 *** 0.2.7-1 500 
        500 [http://server:9999/ubuntu](http://server:9999/ubuntu) focal/universe amd64 Packages 
        100 /var/lib/dpkg/status

```
If I try to remove them it takes out a couple of other packages, which obviously dragged pipewire in as dependencies, to wit: gnome-remote-desktop & xdg-desktop-portal-kde.

The only reason I ran a live ISO USB image of Kali was  to see if analog sound would work on this particular hardware with a recent Debian testing build, which doesn't have any pipewire packages. Analog audio didn't work, so the problem wasn't pipewire or anything peculiar to *buntu Hirsute. I wasn't trying to troubleshoot Kali or ask for help about it on this august forum, I was just trying to figure out what the locus of the sound issue is on my K/Ubuntu installation, comparing Hirsute to another distro's live image was a useful diagnostic.

---

### Post by TheFu on 2021-06-14
This thread is for  jfaberna.  The way these forums work best is when 1 thread is for 1 problem, for 1 system.

Issues which seem similar usually are not. Other posts not specifically for the thread creator's issue confuse the support effort.

---

### Post by coffeecat on 2021-06-15
> **TheFu said:**
> This thread is for  jfaberna.  The way these forums work best is when 1 thread is for 1 problem, for 1 system.

Indeed. I've moved ejbiow's posts and posts that appear to reply to them and not jfaberna into a separate thread, and moved the new thread to the Hardware forum. 

@ejbiow, please start your own threads. It is unfair on the OP to have their support diluted by that for another, even if your problem appears to be the same or similar; inevitable differences will lead to confusion. Threads about similar problems can always be cross-referenced by links in posts if that is found to be helpful. I've also changed BBCode quote tags to code tags in your three posts, and done my best to tidy up interfering font formatting tags - there was quite a labyrinth. Please see the better readability of code tag boxes for code and terminal output. There's a link in my sig about using BBCode code tags if you need it.

> **TheFu said:**
> 
We don't discuss Kali Linux in these forums. Good way to get a thread closed.

Er - not so. Since Kali Linux has nothing to do with Ubuntu, the occasional Kali support thread posted in one of the Ubuntu official flavours sub-fora will get moved to the Other OS section, but only closed if activity disallowed by the forum Code of Conduct is involved. Of course, that is often cracking, but threads asking for help with cracking will get closed irrespective of whether the wannabe cracker is using Kali, Ubuntu, Windows or a chocolate chip ice cream.

---

