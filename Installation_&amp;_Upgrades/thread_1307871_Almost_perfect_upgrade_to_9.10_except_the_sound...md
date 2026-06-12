---
title: "Almost perfect upgrade to 9.10 except the sound.."
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Stosskraft on 2009-10-31
Ok after many troubles with an update, I did a clean install if 9. 10 64-bit and it seems to work really well.

First thing I did, was install the restricted codec and Tweak. using tweak I added Chromium and VLC.

Then I right-click the speaker icon and un-muted the system. I then opened the Sound preference and in the hardware menu and disabled the Internal Audio and the R700 Audio Device. The Sound Blaster Live Value card is the only one highlighted..the Setting is "Analog Surround 5.0 Output".

But still no sound!! When I did a fresh install of 9.04 the sound was automatically installed and I got the start up drum sound but nothing now. Kinda frustrating considering everything else seems to work fine compared to others..even feels a little better than 9.04 but the sound thing is not cool.

Here is the terminal output for aplay -l:

> **** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Thanks for any help available, hoping to solve this one and enjoy the new update.

---

### Post by Stosskraft on 2009-10-31
Help,

Also checked the alsa mixer everything is on in there. Any ideas?

---

### Post by alek01 on 2009-11-02
Hi Stooskraft,
Try re-installing ALSA as described in this thread
[http://swiss.ubuntuforums.org/showthread.php?t=1248428&highlight=sound+HDMI](http://swiss.ubuntuforums.org/showthread.php?t=1248428&highlight=sound+HDMI)

Good luck,
Alek

---

