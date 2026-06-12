---
title: "headphone notebook not recognized (intel HDA)"
date: 2008-10-23
forum: Hardware
---

### Post by pfaf on 2008-10-23
Hi all,

I recently installed Ubuntu (8.04) on my new Medion Notebook. Everything worked out-of-the-box, except the sound was very damped. Trying around with alsa-drivers a bit fixed this problem. One problem I can't solve though is that my headphone jack doesn't seem to be recognized. 

If I plug it in it works perfectly, but the front speakers keep playing as well. A lot of channels are available through alsamixer, but the ones that seem interesting are:

```

Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 28 [90%] [-4.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Headphone268',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 60 [94%] [-4.00dB] [on]
  Front Right: Playback 60 [94%] [-4.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 240 [94%] [-3.00dB]
  Front Right: Playback 240 [94%] [-3.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 19 [61%] [-18.00dB] [on]
  Front Right: Playback 19 [61%] [-18.00dB] [on]


```

With headphone plugged in, the following happens:
- muting master obviously turns off both headphones and speakers
- muting the headphone swith and/or headphone volume slider both speakers and headphones keep playing(!, these controls do nothing!)
- muting 'front' turns off the headphone and speakers

So it seems the headphone sound is linked with ( channeled through) the speakers. Turning the speakers off, does the same to the headphone...

**aplay -l** gives:
```

ALC888
ALC269

```

So the last line of my *alsa-base* file is (according to [http://ubuntuforums.org/showpost.php?p=3796486&postcount=1):](http://ubuntuforums.org/showpost.php?p=3796486&postcount=1):)

options snd-hda-intel model=medion

But i also tried others like acer and auto.

Does anyone know what's wrong? I'd really like to use my notebook in the train and other public places. ;)

Regards, pfaf

---

