---
title: "No sound S/PDIF AD1988B"
date: 2011-05-15
forum: Hardware
---

### Post by Essential on 2011-05-15
Hey! Since moving over to 11.04 I've had problems with my AD1988D. I've had sound on several occasions, but it seems to stop working when I reboot and/or switch inputs on my reciever. Mic input works flawlessly, but there's no sound over digital.

The only way to get it working is following another forumpost suggestion where I run this:

```
killall pulseaudio; sudo rmmod snd-hda-intel; sudo modprobe snd-hda-intel
```

Then unmute channels from alsamixer

Aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I've also tried adding
```
options snd-hda-intel model=6stack-dig
```
to alsa-base.


Is this a bug or just a configuration issue?

---

### Post by mahill on 2011-08-05
I'm having the same issue.  My mobo is an Asus P5N32-E SLI Plus.

I've tried the usual unmuting of everything in alsamixer.  If I remember right, that's all I had to do in previous versions of Ubuntu.

EDIT: Nevermind.  I think just the test sounds in the Sound Preferences weren't playing anything.  When I ran ubuntu-bug audio,  I was able to hear the test sounds.  After that, I decided to play music, and it actually worked.

---

