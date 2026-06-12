---
title: "No Sound MCP51, 8.04"
date: 2009-01-19
forum: Hardware
---

### Post by srilyk on 2009-01-19
Hi,

I just moved, and as far as I recall, just before my shutdown pre-move, my sound worked fine. On the boot up post-move, the sound no longer makes it to the speakers.

lspci gives me this:
```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
```

When I play in xmms or totem, the visualizations show frequency response. None of my channels are muted in alsamixer.

```
srilyk@media-box:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

It's a 5.1 card, and none of the sound outputs, any of the 3 for the 5.1, the "normal" jacks, or the jacks on the front provide any sound.

Hope someone can help! (I've also looked at the comprehensive sound guide thing, with no luck, and googled a fair amount with similar success (or lack thereof))

TIA

---

### Post by teaker1s on 2009-01-19
so you have tried alsa mixer gui to un mute, tried hda intel model setting and also tried sound preference switches?

---

### Post by srilyk on 2009-01-20
I'm pretty sure I did the switches - if it's the thing in volume control switches tab.

I have:
headphone
IEC958
IEC958 Capture

And the switches are all unchecked.

I'm not sure about the intel part?

---

### Post by teaker1s on 2009-01-22
to enable options switches must be checked
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

scroll down to 
Manually Specify Module Parameters

if your brand is listed try it or auto or basic option,REBOOT, if it doesn't work you can remove the option line.

---

### Post by srilyk on 2009-01-23
Tried a few different settings, including auto and basic. None worked so far.

Any other options?

---

### Post by teaker1s on 2009-01-25
try 
```
sudo alsamixer
``` use + key to turn it up, may be muted

---

