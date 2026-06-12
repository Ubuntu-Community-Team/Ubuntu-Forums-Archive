---
title: "Mac Pro Internal audio no output (not working)"
date: 2011-12-21
forum: Hardware
---

### Post by base2112 on 2011-12-21
Hi there Ubuntu forums.

I am having some real problems with the internal audio on my Mac when running Ubuntu.

The model of the Mac Pro is 5,1 and I am attempting to get sound output to my headphones through the front audio however nothing I have tried (and I have googled quite a lot) has worked.

I have tried the following without success:

Any of these individually in my /etc/modprobe.d/alsa-base.conf 
```

options snd-hda-intel model=auto
options snd-hda-intel model=mb5
options snd-hda-intel model=mbp5
options snd-hda-intel model=mbp3
options snd-hda-intel model=mac24
options snd-hda-intel model=imac24

```Although the mac24 and the imac24 gave me more options on my devices in the sound center (things like 5.1 audio output and things) none of them have proved to work yet.

I have also installed alsamixer (command line) and alsamixer-gnome packages to try and look for "muted" devices, however as yet I haven't found any.

Here's the output of *aplay -l*
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [Display Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Audio_1 [Display Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I am completely stuck and would love some help. Thanks very much in advance!

Tom

---

### Post by base2112 on 2011-12-22
By the way the two display audio's do work correctly - it's just the internal speaker and headphones that don't produce any output.

---

### Post by base2112 on 2011-12-27
Can anyone help with this?

---

### Post by base2112 on 2012-01-06
Little bump?

---

