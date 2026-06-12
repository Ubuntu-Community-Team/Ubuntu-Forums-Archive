---
title: "USB Headphones not working"
date: 2017-01-23
forum: Hardware
---

### Post by Macamba on 2017-01-23
I upgraded my system to  16.0.4 LTS. What worked before, my headphones, does not work anymore. And strangely enough, the headphones work during a Live CD Session.

The headphones are recognized by the system:
[IMG]https://s13.postimg.org/xm1zzbrjr/Sound_system.png[/IMG]

I have been fooling around a bit. First is the sound card recognized? ```
me@system:~$ clear;sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Set [USB Headphone Set], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```
It is. 

My sound modules are installed. When entering ```
find /lib/modules/`uname -r` | grep snd
``` I get a long list with items. So that checks out alright. 

Lastly I tried to reinstall my drivers with
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
But that did not seem to result in sound through my headphones. I'm at wits end. What options do I have more?

---

### Post by Macamba on 2017-01-25
Any1?

---

### Post by Macamba on 2017-02-18
On my continuing quest to get a sound from my headphones I found the [command]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit#")```

speaker-test -D Headphones
```

Maybe someone knows what to do after the following output:```

macamba@system:~$ speaker-test -D headphones

speaker-test 1.1.0

Playback device is headphones
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib pcm.c:2266:(snd_pcm_open_noupdate) Unknown PCM headphones
Playback open error: -2,No such file or directory
```

Does this error message point to a solution someone can give me?

---

