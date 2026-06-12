---
title: "Sound works, but not built-in mic for the Aspire One 532h-2588"
date: 2011-05-29
forum: Hardware
---

### Post by vangbe on 2011-05-29
I have already installed my sound card.
____________________________________________________

[B]aplay -l
[/B]

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

Followed through this:

[B]sudo gedit /etc/modprobe.d/alsa-base.conf
[/B]

and added

[B]options snd-hda-intel model=auto position_fix=0
[/B]
____________________________________________________

After all of this, the built-in mic still doesn't work.
I'm using a Aspire One 532h-2588 laptop. Please I need to get this working so I can use VOIP. If anybody is curious what I'm using. I'm using ZoIper.

---

### Post by vangbe on 2011-06-02
any thoughts?

---

