---
title: "Sound not working on Ubuntu 14.04 LTS aplay, pacmd not showing cards"
date: 2015-12-30
forum: Hardware
---

### Post by krishadhithya-acco on 2015-12-30
I've just assembled a new PC. I want to run monitor through a DVI-D port in the graphics card (This works). *I want to use audio out from the on board intel sound card* (_**This doesn't work**_).

_Relevant Specs:_
[LIST]
[*]Linux version 3.19.0-42-generic
[*]ASUS H170-M Plus motherboard with UEFI Bios
[*]Intel i5 (6gen)
[*]ASUS Geforce (nVidia) 750 Ti
[/LIST]

_What I've done so far:_ 
[LIST]
[*]I made ubuntu use the restricted, proprietary driver for nVidia version: 352.63. The immediate result of this was I saw the following in the system boot log, which were conspicuous (not sure if important):
```
ACPI PCC probe failed.
```
And this looks far more ominous:
```
snd_hda_intel 0000:00:1f.3: failed to add i915_bpo component master (-19)
```
[*]Initially I saw HDMI output (through the nVidia graphics card) in pavcontrol. After trying out a few things in other threads even that is gone. I don't know what exactly caused this. *I only have a dummy output in both pavcontrol and sound settings :(*
[/LIST]

_Some relevant info/outputs for commands:_

```
~$ pacmd list-cards
Welcome to PulseAudio! Use "help" for usage information.
>>> 0 card(s) available.


```

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
aplay: device_list:277: control open (1): Invalid argument


```

```
lspci -vnn
``` revealed two audio cards, listed below:
```
$ 
00:1f.3 Audio device [0403]: Intel Corporation Device [8086:a170] (rev 31)
    Subsystem: ASUSTeK Computer Inc. Device [1043:86c7]
    Flags: bus master, fast devsel, latency 32, IRQ 16
    Memory at d3240000 (64-bit, non-prefetchable) [size=16K]
    Memory at d3220000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fbc] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:84bb]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d3080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

```

Please pay attento "Capabilities: <access denied>" on both of them. Does this say anything? Regardless, based on the above and suggestions on an alsa forum thread I created a .conf file in /etc/modprobe.d/ with the following content (it didn't make a difference):
```
options snd_hda_intel enable=1,0 vid=8086,10de pid=a170,0fbc
options snd_hda_intel index=0 vid=8086 pid=a170
```

```
$ lsmod | grep '^snd' | column -t
snd_hda_codec_hdmi  53248   1
snd_hda_intel       36864   1  snd_hda_codec_hdmi
snd_hda_controller  32768   1  snd_hda_intel
snd_hda_codec       143360  3  snd_hda_codec_hdmi,snd_hda_intel,snd_hda_controller
snd_hwdep           20480   1  snd_hda_codec
snd_pcm             106496  4  snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi        16384   0
snd_seq_midi_event  16384   1  snd_seq_midi
snd_rawmidi         32768   1  snd_seq_midi
snd_seq             65536   2  snd_seq_midi_event,snd_seq_midi
snd_seq_device      16384   3  snd_seq,snd_rawmidi,snd_seq_midi
snd_timer           32768   2  snd_pcm,snd_seq
snd                 86016   9  snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device


```

Alsamixer won't work
```
$ alsamixer
cannot open mixer: No such file or directory


```

...but alsa-utils is installed
```
$ dpkg -s alsa-utils
Package: alsa-utils
Status: install ok installed
Priority: optional
Section: sound
Installed-Size: 2156
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Version: 1.0.27.2-1ubuntu2
Provides: audio-mixer
Depends: lsb-base (>= 3.0-9), kmod, whiptail | dialog, libasound2 (>= 1.0.27), libc6 (>= 2.15), libncursesw5 (>= 5.6+20080119), libsamplerate0 (>= 0.1.7), libtinfo5
Recommends: alsa-base (>= 1.0.15)
Conffiles:
 /etc/init/alsa-state.conf 735d9582d09996ab70a845b204694beb
 /etc/init/alsa-store.conf 60fdd06e7af4c4a9d165466a2fc798bf
 /etc/init/alsa-restore.conf 68b60c1bb2275a3728049a8cfe9de317
Description: Utilities for configuring and using ALSA
 Included tools:
  - alsactl: advanced controls for ALSA sound drivers
  - alsaloop: create loopbacks between PCM capture and playback devices
  - alsamixer: curses mixer
  - alsaucm: alsa use case manager
  - amixer: command line mixer
  - amidi: read from and write to ALSA RawMIDI ports
  - aplay, arecord: command line playback and recording
  - aplaymidi, arecordmidi: command line MIDI playback and recording
  - aconnect, aseqnet, aseqdump: command line MIDI sequencer control
  - iecset: set or dump IEC958 status bits
  - speaker-test: speaker test tone generator
 .
 ALSA is the Advanced Linux Sound Architecture.
Homepage: http://www.alsa-project.org/
Original-Maintainer: Debian ALSA Maintainers <pkg-alsa-devel@lists.alioth.debian.org>


```

_Conclusion/Call for help:_
I've re-installed, re-reinstalled alsa and pulse audio several times and restarted them, to no avail. From my research on it, it sounds like the nVidia restricted driver and the kernel I have don't play well together and they've caused a problem. Can the community please help me find a solution so that I can use my graphics card for video and on board card for audio? (I have seen some suggestions on other threads to remove the driver for audio through the graphics card. I would ideall not do this). HELP!!!

---

### Post by tokyobadger on 2015-12-30
```
ACPI PCC probe failed.
```
I get that too. It's not the issue.
```
Capabilities: <access denied>
```
If you study the output for all the PCI devices you'll see they all have that, so also not the issue.
```
$ alsamixer 
cannot open mixer: No such file or directory
```
That shouldn't happen. First clue.
```
snd_hda_intel 0000:00:1f.3: failed to add i915_bpo component master (-19)
```
You're right, it doesn't look good. Second clue.

The threads below suggest upgrading the sound module/driver with the steps at [Ubuntu Wiki](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

[First success](http://ubuntuforums.org/showthread.php?t=2296136)

[Second success](http://ubuntuforums.org/showthread.php?t=2293912)

Try this and see if it solves your issue

---

### Post by krishadhithya-acco on 2015-12-31
Thank you Tokyobadger,

I'd already seen that fix suggested before I posted originally. I dismissed it since their fixes were specifically for kernels 3.2, 3.5, and 3.8. Mine is [COLOR=#000000]3.19.0-42-generic.

However, I trudged on this time like a trooper ;)

I tried out this with limited success (and some of the rest with no success):
[/COLOR][oem-audio-hda-daily-dkms - 0.201512301031~ubuntu15.04.1]("https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+sourcepub/5895667/+listing-archive-extra")


First observations the bad sign from the boot log? It still exists :(
```
[COLOR=#000000][FONT=Ubuntu Mono]snd_hda_intel 0000:00:1f.3: failed to add i915_bpo component master (-19)[/FONT][/COLOR]
```
[U]
Some positives:[/U] 

I saw the analog output device in pavcontrol, sound settings, and pacmd list-cards. [B]I still did not see the nVidia sound card
[/B]
sound settings:
[ATTACH=CONFIG]266467[/ATTACH]
pavcontrol:
[ATTACH=CONFIG]266468[/ATTACH]

pacmd:
```
$ pacmd list-cardsWelcome to PulseAudio! Use "help" for usage information.
>>> 1 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_00_1f.3>
    driver: <module-alsa-card.c>
    owner module: 5
    properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xd3240000 irq 125"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "a170"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        input:analog-stereo: Analog Stereo Input (priority 60, available: unknown)
        output:analog-stereo: Analog Stereo Output (priority 6000, available: unknown)
        output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <output:analog-stereo>
    sinks:
        alsa_output.pci-0000_00_1f.3.analog-stereo/#0: Built-in Audio Analog Stereo
    sources:
        alsa_output.pci-0000_00_1f.3.analog-stereo.monitor/#0: Monitor of Built-in Audio Analog Stereo



```

_...But more negatives:_
[LIST]
[*]aplay still wont show cards
```
$ aplay -l**** List of PLAYBACK Hardware Devices ****
aplay: device_list:277: control open (0): Invalid argument
aplay: device_list:277: control open (1): Invalid argument

```
[*]Biggest of them all: **_sound test failed from both the outlets in the backpanel as well as front panel_**
[*]I still don't see the nVidia sound card
[/LIST]


What do you think?

---

### Post by tokyobadger on 2015-12-31
Can you execute alsamixer now?

---

### Post by krishadhithya-acco on 2015-12-31
No I can't execute alsamixer. I get the same result as the original post

---

### Post by tokyobadger on 2015-12-31
OK. Have you [gone through updating the LTSEnablement Stack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) to bring your 14.04 up to the latest point release?

---

### Post by tokyobadger on 2015-12-31
[SIZE=2][FONT=arial][URL="https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/272325"]Post #11 suggests that the message ```
[COLOR=#000000]snd_hda_intel 0000:00:1f.3: failed to add i915_bpo component master (-19)[/COLOR]
```[COLOR=#000000] is another false positive[/COLOR][/URL][COLOR=#000000]

However, that user updated to 15.04, so it's not a complete solution for you if 14.04 LTS is required.

The other thought that comes to mind is that there might be a BIOS setting that allows you to select which sound card will handle audio.[/COLOR][/FONT][/SIZE]

---

### Post by krishadhithya-acco on 2015-12-31
Thanks for the suggestion. I hadn't. I went ahead and updated the kernel to those from wily (15.10). My current kernel is 4.2.0-22-generic.

After reboot, nothing changed. I removed the dkms package to see if anything changed. Nothing changed again... which means, interestingly, I can see the analog audio without the dkms installed.

---

### Post by krishadhithya-acco on 2015-12-31
Woops. Just saw your comment #7. Great find!! I don't mind upgrading to 15.04 or 15.10. I just thought the LTS versions are more desirable since they are more stable.

As for the BIOS settings, I've played around with all combinations. Basically #4 in the thread you suggested gives all the options.

Quotes from there:
> [COLOR=#333333][FONT=Ubuntu]HD Audio Controller[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]- Enabled (Enabled | Disabled)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Front Panel Type
- HD Audio (HD Audio | AC97)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]SPDIF Out Type
- SPDIF (SPDIF | HDMI)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]DVI Port Audio
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]- Disabled (Disabled | Enabled)[/FONT][/COLOR]

The first option turns the on-board audio card on or off. I've tested this. The second one, I've read from other threads is the "type" of audio it is. I suppose it means the kind of codec. I've tried both. No difference for me. The third one is to do with outputs. I've got SPDIF. The last one doesn't exist in my motherboard. The Z170m plus is slightly different than mine (H170m plus)

---

### Post by tokyobadger on 2015-12-31
[It does seem to be the consensus - post #9 in this link]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/276711") that your hardware is too new for the 14.04 series - 15.10 seems to be the way to go for now and then once 16.04 LTS is released do an upgrade so you can enjoy the benefits of an LTS release

Try first with 15.10 live CD/USB of course

---

### Post by krishadhithya-acco on 2015-12-31
Thanks! Well I'm already upgrading to 15.04 over the internet. I'll report how this goes. If not I'll do a live usb install of 15.10

---

### Post by tokyobadger on 2015-12-31
I'm sure there is a way to "patch" the 14.04 to work with your set-up but I think 4 months on 15.10 and then upgrade to 16.04 would be a lot less frustrating.

Personally I would have tried the live 15.10 first to see if it would work but I hope that the 15.04 resolves the issue. I'd recommend removing or commenting out the modified .conf file in /etc/modprobe.d to see if 15.04 "works out of the box".

Good luck

---

### Post by krishadhithya-acco on 2015-12-31
Long story short: Problem solved

First, my upgrade to 15.04 failed (I was away from the computer) somehow and rendered my PC useless. So I downloaded 15.10 and put it in a live usb.

While "trying without installing" I encountered problems: the gui went into a login loop. So I figured I can solve this after installing properly. So I did. I still had this problem. So I went into text mode and installed the restricted nVidia drivers. And voila! it works, including the crisp, sweet sound!!!

However I still get
```
[COLOR=#000000][FONT=Ubuntu Mono]snd_hda_intel 0000:00:1f.3: failed to add i915_bpo component master (-19)[/FONT][/COLOR]
```
I hope this doesn't cause long term problems.

Thank you so much for your help tokyobadger! I owe you a beer if I ever meet you in person

---

### Post by tokyobadger on 2015-12-31
Really cool to hear that you fixed it. The error message you reference is looking like a "false positive"  i.e. Not anything to worry about.

Enjoy the new install, have a great 2016 and where you can, help other Ubuntu users :-)

---

### Post by krishadhithya-acco on 2016-01-01
Thanks! Happy New year!

---

