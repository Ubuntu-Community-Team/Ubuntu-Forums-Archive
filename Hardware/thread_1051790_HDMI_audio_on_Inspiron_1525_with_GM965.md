---
title: "HDMI audio on Inspiron 1525 with GM965"
date: 2009-01-27
forum: Hardware
---

### Post by lorandsm on 2009-01-27
Hi,

Is there somebody who managed to get sound on the HDMI connector. I've tried using mplayer like this:

mplayer -ao alsa:device=hw=0.3 something.avi

I used hw:0,3 because aplay -l dispalys the intel HDMI device as card 0, device 3. Mplayer does not give any error related to the sound device but no sound on the LCD display. I'm using debian testing.

---

### Post by delkarrr on 2009-09-08
> **lorandsm said:**
> Hi,

Is there somebody who managed to get sound on the HDMI connector. I've tried using mplayer like this:

mplayer -ao alsa:device=hw=0.3 something.avi

I used hw:0,3 because aplay -l dispalys the intel HDMI device as card 0, device 3. Mplayer does not give any error related to the sound device but no sound on the LCD display. I'm using debian testing.
Did you ever solve this problem? How?

---

### Post by Githlar on 2010-04-23
It took me a minute, but I managed to get sound through HDMI on a 1525. All you have to do is restart after plugging in the display. My best guess is that another module gets loaded on boot-up to allow HDMI audio. I'm still investigating. I'll continue tomorrow for an on-the-fly solution.

---

### Post by Gömböc on 2011-03-26
I just got HDMI audio working on my Inspiron 1525 by installing PulseAudio Volume Control.

```
sudo apt-get install pavucontrol
```

Go to the Configuration tab, then select "Digital Stereo (HDMI) Output".

---

