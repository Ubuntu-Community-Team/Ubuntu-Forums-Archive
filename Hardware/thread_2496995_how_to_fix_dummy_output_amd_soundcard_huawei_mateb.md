---
title: "how to fix dummy output amd soundcard huawei matebook d15 ubuntu 22.04?"
date: 2024-04-19
forum: Hardware
---

### Post by jesse-username on 2024-04-19
Hello I've been trying to fix the dummy output in my ubuntu 22.04 for a long time. I've tried everything on the internet and nothing helped(sometimes I got a second dummy output but when I switched to it settings app just crashed and after that there was only 1 dummy  output as before). I also tried this: [https://github.com/Smoren/huawei-ubuntu-sound-fix](https://github.com/Smoren/huawei-ubuntu-sound-fix) but it didn't help either. The system also can't detect my microphone so I have no input devices. Wired headphones don't work either. I can't even connect my bluetooth headphones. I can connect 'em for about 10 seconds(and then they disconnect). As always there's no sound in the bluetooth headphones when they are connected and I can't see 'em in the output devices either. This is my inxi -F output

```
System:
  Host: andrey-BOM-WXX9 Kernel: 6.5.0-28-generic x86_64 bits: 64
    Desktop: GNOME 42.9 Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: HUAWEI product: BOM-WXX9 v: M1010
    serial: <superuser required>
  Mobo: HUAWEI model: BOM-WXX9-PCB-B2 v: M1010 serial: <superuser required>
    UEFI: HUAWEI v: 2.12 date: 03/16/2023
Battery:
  ID-1: BAT1 charge: 19.4 Wh (35.5%) condition: 54.6/54.9 Wh (99.3%)
    volts: 7.4 min: 7.6
CPU:
  Info: 6-core model: AMD Ryzen 5 5500U with Radeon Graphics bits: 64
    type: MT MCP cache: L2: 3 MiB
  Speed (MHz): avg: 483 min/max: 400/4056 cores: 1: 400 2: 400 3: 400
    4: 400 5: 400 6: 400 7: 1398 8: 400 9: 400 10: 400 11: 400 12: 400
Graphics:
  Device-1: AMD Lucienne driver: amdgpu v: kernel
  Device-2: IMC Networks ov9734_azurewave_camera type: USB driver: uvcvideo
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: gpu: amdgpu resolution: 1920x1080~60Hz
  OpenGL: renderer: RENOIR (renoir LLVM 15.0.7 DRM 3.54 6.5.0-28-generic)
    v: 4.6 Mesa 23.2.1-1ubuntu3.1~22.04.2
Audio:
  Device-1: AMD Renoir Radeon High Definition Audio driver: snd_hda_intel
  Device-2: AMD Raven/Raven2/FireFlight/Renoir Audio Processor
    driver: snd_rn_pci_acp3x
  Sound Server-1: ALSA v: k6.5.0-28-generic running: yes
Network:
  Device-1: Realtek RTL8822CE 802.11ac PCIe Wireless Network Adapter
    driver: rtw_8822ce
  IF: wlp1s0 state: up mac: 84:c8:a0:50:ff:86
Bluetooth:
  Device-1: Realtek Bluetooth Radio type: USB driver: btusb
  Report: hciconfig ID: hci0 state: up address: 84:C8:A0:50:FF:87 bt-v: 3.0
Drives:
  Local Storage: total: 476.94 GiB used: 10.41 GiB (2.2%)
  ID-1: /dev/nvme0n1 model: PCIe-8 SSD 512GB size: 476.94 GiB
Partition:
  ID-1: / size: 118.65 GiB used: 10.38 GiB (8.7%) fs: ext4
    dev: /dev/nvme0n1p3
  ID-2: /boot/efi size: 96 MiB used: 32.8 MiB (34.1%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 36.0 C mobo: N/A gpu: amdgpu temp: 34.0 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 329 Uptime: 4m Memory: 14.95 GiB used: 1.87 GiB (12.5%)
  Shell: Bash inxi: 3.3.13
```

also my apply -l:
```
** List of PLAYBACK Hardware Devices **
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
When I try alsamixer I can't do anything either.

Switching to ubuntu 23.10 doesn't help either so I was curious. 
Is there any way to fix my problem or is my laptop not for linux cuz of its soundcard? should I just give up and use windows again instead?

---

### Post by TheFu on 2024-04-19
So, most Linux desktops use either PulseAudio or Pipewire to manage audio devices.  ALSA is there, but seldom used directly.

There is a _linux audio troubleshooting script_ that you should find, download, run and post the results from so the audio gurus can see the issues and make recommendations.  Please don't make people ask 10 times for all the different information that script already provides.  I don't know where the script is, not exactly, but I'd google for those terms. It is probably a github project or there might be a sticky post with the link in the Multimedia subforum here.

BTW, I have a Ryzen 5600G and don't have any issues with the audio on that machine. I'm not using 22.04. Still on 20.04, but here's the audio output for the system ... with some unrelated things (blackmagic card and KVM HDMI/USB switch) removed.
```
$ inxi -Axx
Audio:
...
  Device-2: AMD vendor: ASUSTeK driver: snd_hda_intel 
  v: kernel bus ID: 09:00.1 chip ID: 1002:1637 
  Device-3: AMD Family 17h HD Audio vendor: ASUSTeK 
  driver: snd_hda_intel v: kernel bus ID: 09:00.6 
  chip ID: 1022:15e3 
  Sound Server: ALSA v: k5.15.0-101-generic 

```

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Generic [HD-Audio Generic], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Device [USB Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Generic_1 [HD-Audio Generic], device 0: ALC1220 Analog [ALC1220 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Generic_1 [HD-Audio Generic], device 1: ALC1220 Digital [ALC1220 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
I actually use the front audio plug on the system to connect to 2 speakers via analog connections. I don't use digital or HDMI audio on the system at all.

With another nearly identical computer, audio is still analog, but to a 5.1 surround sound speaker system.

My guess, being someone that hasn't had to do much related to sound on these systems is that the incorrect driver got loaded or that pulseaudio isn't setup correctly to use the audio output that you have connected to speakers.  Running the **pavucontrol** tool (it may need to be installed), will provide lots of access to audio settings, assuming the drivers loaded are fine.

BTW, it would be really helpful if you included the command used when you post output, with all options.  Don't make us guess.

---

### Post by him610 on 2024-04-19
I also have a Ryzin 5 5600G; however, I am using Xubuntu 22.04.4. 
A few weeks ago I did experience an issue with Audio. I think I somehow misconfigured it. I got so frustrated trying to get it back to its normal state that I wound up re-installing the OS.
Everything is back to normal now. 
```
$ inxi -Axx
Audio:
  Device-1: AMD Renoir Radeon High Definition Audio driver: snd_hda_intel
    v: kernel pcie: speed: 8 GT/s lanes: 16 bus-ID: 07:00.1 chip-ID: 1002:1637
  Device-2: AMD Family 17h HD Audio vendor: ASRock driver: snd_hda_intel
    v: kernel pcie: speed: 8 GT/s lanes: 16 bus-ID: 07:00.6 chip-ID: 1022:15e3
  Device-3: Microdia Webcam Vitade AF type: USB
    driver: snd-usb-audio,uvcvideo bus-ID: 1-6.4:24 chip-ID: 0c45:6366
  Sound Server-1: ALSA v: k6.5.0-21-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes

```
By the way my alsamixer works; I use it quite often.

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Generic [HD-Audio Generic], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Generic [HD-Audio Generic], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Generic [HD-Audio Generic], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Generic_1 [HD-Audio Generic], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```[ATTACH=CONFIG]293644[/ATTACH]

---

### Post by jesse-username on 2024-04-19
Hello thanks for your attention. First I used a script from this repository:  [https://github.com/brendaningram/linux-audio-setup-scripts](https://github.com/brendaningram/linux-audio-setup-scripts). Here is the whole output text: [https://paste.ubuntu.com/p/n2HB5T8sWn/](https://paste.ubuntu.com/p/n2HB5T8sWn/).
After using it I finally got something in alsamixer (I still don't hear anything and have nothing but the dummy output)
Then I used a script from here:  [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure). I've done all the steps and saved all output here: [https://paste.ubuntu.com/p/qk8QQytqyn/](https://paste.ubuntu.com/p/qk8QQytqyn/). Also here is an alsa output:  [http://alsa-project.org/db/?f=93fc8fdc46724292fcb271cbb978fd1b0034b203](http://alsa-project.org/db/?f=93fc8fdc46724292fcb271cbb978fd1b0034b203)

My output after all the things I've done:

```
andrey@andrey-BOM-WXX9:~$ inxi -Axx
Audio:
  Device-1: AMD Renoir Radeon High Definition Audio vendor: QUANTA
    driver: snd_hda_intel v: kernel pcie: speed: 8 GT/s lanes: 16
    bus-ID: 03:00.1 chip-ID: 1002:1637
  Device-2: AMD Raven/Raven2/FireFlight/Renoir Audio Processor
    vendor: QUANTA driver: N/A pcie: speed: 8 GT/s lanes: 16 bus-ID: 03:00.5
    chip-ID: 1022:15e2
  Sound Server-1: ALSA v: k6.8.7-2-liquorix-amd64 running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: no
  Sound Server-3: PipeWire v: 1.0.3 running: yes
andrey@andrey-BOM-WXX9:~$ aplay -l
** List of PLAYBACK Hardware Devices **
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
andrey@andrey-BOM-WXX9:~$
```

I've attached screenshots below. I opened pavucontrol and I got some interesting things. On the configuration tab I have my soundcard and several profiles. All but one are unplugged and unavailable and when I select 'em I have literally nothing as an output device. When I choose "pro audio" profile I see my soundcard name as an output device but no sound anyway and there's configuration option below the output device selection (there are unplugged and unavailable ones. when I choose something I come back to  nothing as an output devices. Btw I'm sure that my soundcard works properly cuz I in windows I have sound. Hope I was clear and got you everything that may help.

---

### Post by jesse-username on 2024-04-20
Btw I also did those things:
1. I downloaded amd driver from here: [https://www.amd.com/en/support/linux-drivers](https://www.amd.com/en/support/linux-drivers)
2. I created /etc/modprobe.d/default.conf and typed "options snd_hda_intel index=1" there. Also, added "options snd-hda-intel model=generic options snd_hda_intel index=1" in /etc/modprobe.d/alsa-base.conf Idk what does it mean I just found it on the internet when I was searching something about my soundcard.
3. I rebooted my PC and I got lots of things in alsamixer. I guess it's because of "pro audio mode" in pavucontrol but I still don't have sound. 


```
andrey@andrey-BOM-WXX9:~$ aplay -l
** List of PLAYBACK Hardware Devices **
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
andrey@andrey-BOM-WXX9:~$ inxi -Axx
Audio:
  Device-1: AMD Renoir Radeon High Definition Audio vendor: QUANTA
    driver: snd_hda_intel v: kernel pcie: speed: 8 GT/s lanes: 16
    bus-ID: 03:00.1 chip-ID: 1002:1637
  Device-2: AMD Raven/Raven2/FireFlight/Renoir Audio Processor
    vendor: QUANTA driver: N/A pcie: speed: 8 GT/s lanes: 16 bus-ID: 03:00.5
    chip-ID: 1022:15e2
  Sound Server-1: ALSA v: k6.8.7-2-liquorix-amd64 running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: no
  Sound Server-3: PipeWire v: 1.0.3 running: yes

```

And one more thing - I was trying to turn on pulseaudio to check what it will do but I got this:

```
andrey@andrey-BOM-WXX9:~$ systemctl --user start pulseaudio.socket
systemctl --user start pulseaudio.service
Job failed. See "journalctl -xe" for details.
Failed to start pulseaudio.service: Unit pulseaudio.service is masked.
```

I uploaded whole "journalctl -xe" output here: [https://paste.ubuntu.com/p/29nGgQVBmG/](https://paste.ubuntu.com/p/29nGgQVBmG/)

And!! I finally can hear something by connecting my bluetooth headphones(as I typed before my headphones disconnect after 10 seconds and there was no sound). I've attached screenshots that may be useful

I've also done hw probe. the whole terminal output is here: [https://paste.ubuntu.com/p/FG8Kr79SD7/](https://paste.ubuntu.com/p/FG8Kr79SD7/)
and the probe is here: [URL="https://linux-hardware.org/?probe=44ae5efad2"]https://linux-hardware.org/?probe=44ae5efad2

[/URL]
I found some info about my soundcard. If I got it right on [this page]("https://linux-hardware.org/?id=pci:1002-1637-152d-1365&page=1#status") it says that my soundcard is supported up to 6.3 kernel version but I have 6.8.7-2-liquorix-amd64. is this the cause of problem? should I like downgrade my kernel version or something?

---

### Post by TheFu on 2024-04-20
PipeWire.   I know nothing about PipeWire.  I'm a "late adopter" of most new stuff on Linux.  I did my bleeding edge time with Linux in the 1990s. Never again. That is for younger people with more passion than me.

---

### Post by him610 on 2024-04-20
My suggestions are limited because our hardware (laptop vs desktop) is different even though we are using same OS and similar AMD APUs.
You may want to read this, [https://askubuntu.com/questions/1406646/ubuntu-22-04-audio-output-not-working-dummy-audio]("https://askubuntu.com/questions/1406646/ubuntu-22-04-audio-output-not-working-dummy-audio")

I even looked up the purpose of *dummy output*...
> "Dummy Output" can appear in Ubuntu 22.04 when audio output isn't working. One possible fix is to use the "pavucontrol" tool to set up input and output settings. To do this, start at the far right tab and work left. It's best to disable all but the single speaker or plug you want to use, and make sure mute is disabled.
I have no other suggestions. I hope you find a solution to your issue.

---

### Post by #&amp;thj^% on 2024-04-20
Not sure I can help, but also can we take a peek at:
```
systemctl status --user pipewire pipewire-session-manager --no-pager -l

```

---

### Post by jesse-username on 2024-04-21
I tried but everything in pavucontrol ain't working

---

### Post by jesse-username on 2024-04-21
sure here you go: 

```
andrey@andrey-BOM-WXX9:~$ systemctl status --user pipewire pipewire-session-manager --no-pager -l
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2024-04-21 16:13:07 +05; 4h 58min left
TriggeredBy: &#9679; pipewire.socket
   Main PID: 916 (pipewire)
      Tasks: 6 (limit: 18305)
     Memory: 9.1M
        CPU: 55ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire.service
             &#9492;&#9472;916 /usr/bin/pipewire

&#1072;&#1087;&#1088; 21 16:13:07 andrey-BOM-WXX9 systemd[906]: Started PipeWire Multimedia Service.
&#1072;&#1087;&#1088; 21 16:13:07 andrey-BOM-WXX9 pipewire[916]: mod.jackdbus-detect: Failed to receive jackdbus reply: org.freedesktop.DBus.Error.ServiceUnknown: The name org.jackaudio.service was not provided by any .service files
&#1072;&#1087;&#1088; 21 16:13:07 andrey-BOM-WXX9 pipewire[916]: [0:00:04.692019165] [916]  WARN IPAManager ipa_manager.cpp:154 No IPA found in '/usr/lib/x86_64-linux-gnu/libcamera'
&#1072;&#1087;&#1088; 21 16:13:07 andrey-BOM-WXX9 pipewire[916]: [0:00:04.692060441] [916]  INFO Camera camera_manager.cpp:284 libcamera v0.2.0

&#9679; wireplumber.service - Multimedia Service Session Manager
     Loaded: loaded (/usr/lib/systemd/user/wireplumber.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2024-04-21 16:13:07 +05; 4h 58min left
   Main PID: 919 (wireplumber)
      Tasks: 8 (limit: 18305)
     Memory: 15.7M
        CPU: 118ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/wireplumber.service
             &#9492;&#9472;919 /usr/bin/wireplumber

&#1072;&#1087;&#1088; 21 16:13:07 andrey-BOM-WXX9 systemd[906]: Started Multimedia Service Session Manager.
&#1072;&#1087;&#1088; 21 16:13:07 andrey-BOM-WXX9 wireplumber[919]: Failed to get percentage from UPower: org.freedesktop.DBus.Error.NameHasNoOwner
&#1072;&#1087;&#1088; 21 16:13:07 andrey-BOM-WXX9 wireplumber[919]: [0:00:04.516389022] [919]  WARN IPAManager ipa_manager.cpp:154 No IPA found in '/usr/lib/x86_64-linux-gnu/libcamera'
&#1072;&#1087;&#1088; 21 16:13:07 andrey-BOM-WXX9 wireplumber[919]: [0:00:04.516426806] [919]  INFO Camera camera_manager.cpp:284 libcamera v0.2.0
&#1072;&#1087;&#1088; 21 16:13:07 andrey-BOM-WXX9 wireplumber[919]: <WpPortalPermissionStorePlugin:0x5e80ffb221d0> Failed to call Lookup: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for camera
&#1072;&#1087;&#1088; 21 16:13:07 andrey-BOM-WXX9 wireplumber[919]: <WpPortalPermissionStorePlugin:0x5e80ffb221d0> Failed to call Lookup: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for camera

```

---

### Post by #&amp;thj^% on 2024-04-21
I'm guessing your hitting a race condition, but I can't see anything jumping out at me just yet.

I did notice a liquorix PPA mentioned, what kernel are you now using?

I see these were removed as well:
```
linux-headers-6.5.0-18-generic
  linux-hwe-6.5-headers-6.5.0-18 linux-image-6.5.0-18-generic
  linux-modules-6.5.0-18-generic linux-modules-extra-6.5.0-18-generic
```

I wish i had more hands on experience with your hardware though.

I'm not second guessing you, but maybe you tell me more about these sources:
```
/ppa.launchpadcontent.net/damentz/liquorix/ubuntu jammy InRelease
ppa.launchpadcontent.net/pipewire-debian/pipewire-upstream/ubuntu jammy InRelease
ppa.launchpadcontent.net/pipewire-debian/wireplumber-upstream/ubuntu jammy InRelease
```

I'm assuming you need this one as well:
```
https://repo.radeon.com/amdgpu/6.0.2/ubuntu jammy InRelease     
```

I can see your a bit frustrated, as well I would be, but will you try this a couple of times, just to be sure we have given our best efforts to help.
```
sudo alsa force-reload

```
Please try that while playing some Audio File or Stream. Thanks

---

### Post by TheFu on 2024-04-21
> **jesse-username said:**
> I tried but everything in pavucontrol ain't working

**pavucontrol** is for PulseAudio.  I don't know if it is supposed to work with pipewire or not.  Audio on Linux is confusing due to history.  I was assuming that Pulse was still being used in 22.04.  I have a Mint Linux desktop based on Ubuntu 22.04 and it has PulseAudio running. I don't use audio with it, so it isn't very useful for this issue.  Hummmm.  Not only is pulsed running, but so is the pipewired. Interesting.
```
lightdm     2026    1979  0 12:46 ?        00:00:00 /usr/bin/pulseaudio --daemonize=no --log-target=journal
lightdm     2025    1979  0 12:46 ?        00:00:00 /usr/bin/pipewire 
```

ESS --> ALSA --> PulseAudio ---> Jack ---> Pipewire

Jack is more complex than Pulse, but has many more capabilities needed by artists trying to play from different locations around the world. I think Jack became popular for audio producers and that forced it onto people during COVID lockdowns.

PulseAudio is a layer on ALSA meant to make it more flexible and easier.
I don't know how Jack works. Could be a layer over Pulse or connecting directly to ALSA.
I don't know how Pipewire works either.  I've read that it is a layer over Pulse too, but IDK.

Anyway, if you can figure out/find how Pipewire relates to the others and what configurations are mandated, that would be helpful to resolving this issue.  Also, you can test using direct ALSA tools to see of there are driver or other hardware issues and it isn't just a configuration problem.

When it comes to testing things, one of the easiest ways to accomplish that is by booting into a Try Ubuntu mode off the USB Flash drive you made from the install ISO.  This is a great tool for when there are booting issues due to system configurations, some hardware issues, and personal configuration issues.  Pop in the flash drive, boot it and see if the audio doesn't "just work".  If it does, you've eliminated a huge set of possible issues.  Of course, if the system won't even boot off flash, then something much worse is happening.

For pipewire, seems these tools are available on my system:
```
$ man -k pipewire
pipewire (1)         - The PipeWire media server
pipewire.conf (5)    - The PipeWire server configuration file
pw-cat (1)           - Play and record media with PipeWire
pw-cli (1)           - The PipeWire Command Line Interface
pw-dot (1)           - The PipeWire dot graph dump
pw-metadata (1)      - The PipeWire metadata
pw-mididump (1)      - The PipeWire MIDI dump
pw-midiplay (1)      - Play and record media with PipeWire
pw-midirecord (1)    - Play and record media with PipeWire
pw-mon (1)           - The PipeWire monitor
pw-play (1)          - Play and record media with PipeWire
pw-profiler (1)      - The PipeWire profiler
pw-record (1)        - Play and record media with PipeWire
```
There must be a GUI tool, that would be easier to use. I don't know what it is. Sorry.

---

### Post by bobunderwood99 on 2024-04-21
**"Does PipeWire run on top of a PulseAudio or JACK server?**

 No, PipeWire is a complete reimplementation of a PulseAudio server and a JACK server. It only requires ALSA to make sound (and bluez5 for bluetooth).
 PipeWire still uses the original PulseAudio client library but has a reimplementation of the client JACK library for compatibility with existing applications.

 PipeWire also reuses the ALSA card profile code from pulseaudio. This code is responsible for setting up devices and managing the profiles and mixer settings."

[https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/FAQ](https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/FAQ)

---

### Post by Yellow Pasque on 2024-04-24
The bad news is that no one has ever explicitly reported the sound on this laptop to work under any Linux distro: [https://linux-hardware.org/?id=pci:1002-1637-152d-1365](https://linux-hardware.org/?id=pci:1002-1637-152d-1365)

Get a LiveUSB of Ubuntu 24.04 (I think the final version comes out tomorrow) and boot that. If sound doesn't work there, I think it's extremely unlikely you get sound in Ubuntu 22.04 and it's time to start looking at USB or Bluetooth audio solutions if you want sound under Linux.

```
** List of PLAYBACK Hardware Devices **
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So the kernel module (snd-hda-intel) is loaded, but no device (except the HDMI audio) shows in aplay. It seems this also happens to everyone else using this notebook. That's bad news. If you can't get the device to show in aplay, you can play with Pulseaudio or Pipewire all day and night, but you're just spinning your wheels.

> If I got it right on this page it says that my soundcard is supported up to 6.3 kernel version but I have 6.8.7-2-liquorix-amd64. is this the cause of problem? should I like downgrade my kernel version or something?
No, that's just a quirk of that site. I think their database only goes up to 6.3.

> I also tried this: [https://github.com/Smoren/huawei-ubuntu-sound-fix](https://github.com/Smoren/huawei-ubuntu-sound-fix) but it didn't help either.
That's for a completely different sound device. Use the uninstall.sh script to undo that.

> options snd-hda-intel model=generic options snd_hda_intel index=1
I would undo that if it didn't help.

---

