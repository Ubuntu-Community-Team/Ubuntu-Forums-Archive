---
title: "Cannot get sound to work properly"
date: 2013-12-07
forum: Hardware
---

### Post by nbpowell on 2013-12-07
I have found many similar problems and solutions on the forum but none show exactly my problem, nor do the solutions work.
When playing sound files or video files, at first all is well, then increasingly there will be a slight stutter and by the time 30 mins of audio has been played, sound comes in 0,5 second bursts with 0.1 of silence between each.  On video files, when the sound breaks up, the video often breaks up too.

I am convinced this is an audio issue though as closing the media player (it's the same regardless of VLC, Totem, flash media in Firefox etc) and relaunching doesn't work but issuing the command

```
sudo killall pulseaudio
```

then restarting the media player does work to reset the problem.

The soundcard is this one ```
$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

Any further info gladly provided but this one is driving me nuts.
I have a session capture video to illustrate the problem in full swing if this might help anyone.

Thanks in advance for any assistance.

---

### Post by nbpowell on 2013-12-07
Ubuntu 12.04 64-bit btw

---

