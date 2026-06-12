---
title: "No sound, mate 17.10 &lt;solved&gt; so sorry first post...simple solution in the end"
date: 2017-10-29
forum: Hardware
---

### Post by binskipy2u on 2017-10-29
I've read 12 different pages.. it's a clean install.. no sound at all.. 
here's the output of aplay -l
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

The only option I have in volume control is hdmi/digital for output, no analog option
I tried using alsa mixer, detected correct card, everything is up to 100% and unmuted
I tried saving an alsa.conf file and rebooting
just installed mate today.. and I've been at this for over an hour searching, trying things, rebooting 10x so far..
please help.. ask me for any information you may need.. i tried the wiki/ how-tos, etc.. nothing is working.

EDIT: I've been using the mate volume control... I used PULSE audio control and found my sound card/settings for 5.1
sorry.. but I've been at this for an hour+ didn't realize about pulse audio controlling volume and not the volume button in taskbar

---

### Post by TheFu on 2017-10-30
If solved,please mark the thread "SOLVED" using thread tools.  That helps the community.

---

### Post by vasa1 on 2017-10-30
Like so: [How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

