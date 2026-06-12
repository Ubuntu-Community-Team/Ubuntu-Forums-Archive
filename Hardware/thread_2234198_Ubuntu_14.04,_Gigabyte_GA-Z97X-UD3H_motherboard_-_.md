---
title: "Ubuntu 14.04, Gigabyte GA-Z97X-UD3H motherboard - no audio"
date: 2014-07-13
forum: Hardware
---

### Post by gogogardev on 2014-07-13
Hey everyone,

I just bought a new PC and installed ubuntu 14.04. Everything runs amazing, except I have no audio.
The setup is: a z97x-ud3h motherboard from gigabyte, front mic and headphones ports (on the case) and 6 at the back on the motherboard.

When I try to plug headphones in the front panel music gets through them, but there's a lot of noise, crackling etc.
When I try to plug speakers in the back panel, there's just nothing. I installed pavucontrol and I see that it's recording some activity, but I can hear nothing (screenshots attached).

Output of **aplay -l**
```
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC1150 Analog [ALC1150 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC1150 Digital [ALC1150 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

[Here's my alsa info]("http://www.alsa-project.org/db/?f=c5bb065f40f72dec7198c61a79f457cdd182be3e")

I've tried adding:
```
options snd-hda-intel model=6stack-automute
```
in */etc/modprobe.d/alsa-base.conf*, but that didn't work out.


Any help/ideas will be much appreciated. Also  if I can provide more debugging info just let me know :)

Thanks,
George

P.S. I tried running Windows, and everything works fine there, so It's not a hardware issue.

**Edit 1:**

Output of [B]lspci -v | grep -A7 -i "audio":
[/B]```
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)        Subsystem: Intel Corporation Device 2010
        Flags: bus master, fast devsel, latency 0, IRQ 47
        Memory at f7c34000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel


00:14.0 USB controller: Intel Corporation Device 8cb1 (prog-if 30 [XHCI])
--
00:1b.0 Audio device: Intel Corporation Device 8ca0
        Subsystem: Gigabyte Technology Co., Ltd Device a182
        Flags: bus master, fast devsel, latency 0, IRQ 48
        Memory at f7c30000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel

```

**Edit 2:**

When I plugged the speakers in the orange instead of the green port, there's music, but same as the headphones - a ton of crackling, noise, skipping seconds, etc.
[B]
Edit 3:

Well.. After two days of searching for solutions I decided to finally ask you guys, and fifteen minutes after starting this thread I found the solution for me:

[/B][COLOR=#333333][FONT=Ubuntu]sudo apt-add-repository ppa:ubuntu-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]audio-dev/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]alsa-daily[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]sudo apt-get update[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]sudo apt-get install oem-audio-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]hda-daily-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]dkms

Anyway, I guess I'll leave this here if someone else has the same problem.[/FONT][/COLOR]

---

### Post by ian49 on 2014-07-13
> **gogogardev said:**
> [B]Well.. After two days of searching for solutions I decided to finally ask you guys, and fifteen minutes after starting this thread I found the solution for me:

[/B][COLOR=#333333][FONT=Ubuntu]sudo apt-add-repository ppa:ubuntu-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]audio-dev/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]alsa-daily[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]sudo apt-get update[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]sudo apt-get install oem-audio-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]hda-daily-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]dkms

Anyway, I guess I'll leave this here if someone else has the same problem.[/FONT][/COLOR]

Thanks for posting this... I was having the same problem and getting nowhere fast but this fixed it for me too so thanks for leaving the post up!

---

### Post by chilna on 2014-07-17
Yes please leave leave this post here.  I've had the same problem.  I will edit this post if this doesn't fix my audio issue.  Thanks for looking into this issue; your efforts are much appreciated.

---

### Post by Yellow Pasque on 2014-07-18
[https://bugs.launchpad.net/bugs/1321421](https://bugs.launchpad.net/bugs/1321421)

---

### Post by antar on 2014-07-18
This was very helpful. Thank you for posting it. I just wanted to add that when I got my GA-Z97X-UD5H mobo this week, I ended up performing the Ubuntu 14.04 install only after first disabling the motherboard's audio in the BIOS. Then after I installed oem-audio-hda-daily-dkms, I went back into the bios, turned the audio controller back on, and it worked like a charm.

I'm not sure how "necessary" this was--I was having a lot of issues with freezes and reboots, but at least some of that is [likely hardware]("http://www.tomshardware.com/answers/id-2224387/computer-unexpectedly-reboots-confirm-psu-blame.html"), and other parts of it were likely related to my rather eccentric graphics setup (I'm running both my displays off the Intel integrated graphics controller, but I need an nVidia GPU and proprietary drivers so that my Win7 VMWare virtual machine can use Direct3D).

---

