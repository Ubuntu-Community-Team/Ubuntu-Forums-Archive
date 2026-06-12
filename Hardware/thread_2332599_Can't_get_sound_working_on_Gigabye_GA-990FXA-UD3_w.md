---
title: "Can't get sound working on Gigabye GA-990FXA-UD3 with ALC889"
date: 2016-08-02
forum: Hardware
---

### Post by Devilot on 2016-08-02
Okay, here's the problem: I use the analog line out jacks for 5.1 audio, since I've had mixed success with my speakers' SPDIF support. They show up on aplay -l as

```
card 0: SB [HDA ATI SB], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


```

and aplay -L as... a whole lot of things, including the default output.

However, I can't get System Settings => Sound or pulseaudio volume control to recognize them. The former just doesn't list them, and the latter incorrectly lists every analog-out option as "unplugged." On top of that, when I try to use aplay or speaker-test with output forced to anything that should correspond with those analog outs, I get some variation on this error:

```
aplay: set_params:1239: Channels count non available
```

except through "plughw", which actually does give an appropriate output.

I've tried every solution I've managed to dredge up, and none of them have done anything.


And [here are the results of my alsainfo]("http://www.alsa-project.org/db/?f=0c204a313ceb41fee20d87cf3fb8d1184308ff1f").

---

### Post by Devilot on 2016-08-02
I've managed to get a short-term solution by inserting the lines:

```
load-module module-alsa-sink device=dmix tsched=1
load-module module-combine-sink sink_name=combined
set-default-sink combined

```
which has the added bonus of allowing me to output to both my speakers for my computer, and my TV's sound system... but it seems to just be directly patching the SPDIF stereo output to my line-out cables, so I'm only getting stereo audio when I should be capable of 5.1. So... any advice or thoughts? Really, I'm willing to try most anything. If you told me I had to glue a cat to my forehead and juggle greased watermelons, I'd at least seriously consider it.

---

### Post by Devilot on 2016-08-03
Oh, yeah, I probably should've mentioned this, but I'm using 16.04.1 LTS.

EDIT: Through tinkering and looking online, I've managed to solve this problem to the point that this topic is hopelessly outdated, as I've solved many of the problems I described here and I think narrowed down the issue. The most useful thing was using the instructions from [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) to set the relevant model for my sound device, rather than simply leaving it as "auto."

---

