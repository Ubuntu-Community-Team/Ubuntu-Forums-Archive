---
title: "HP Envy 17 No Sound"
date: 2012-03-19
forum: Hardware
---

### Post by Ikith on 2012-03-19
So I just bought an HP Envy 17 and after having it for around a month I decided I wanted to see how well Ubuntu ran on it. During install I noticed a few things while entering information:

The touchpad which normally operates well in windows when I touch it with multiple fingers (One to move the mouse and one to click) it gets jumpy since the area to click is also an area where you can move the mouse. Are there any proprietary Synaptics touchpad drivers that I can install to solve this issue?

Another thing I noticed after boot is I completely have no sound and when I hop in to terminal I get "Cannot set frequency" (Refering to sound volume) spam. I've looked up multiple guides to fixing this with no avail. This is a "beats" laptop and I believe it has 4 speakers and a sub in it.

Everything else is peachy.

---

### Post by 2F4U on 2012-03-19
I would start with the basic checks to tackle the sound problem:

[http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/)

---

### Post by wegah on 2012-09-15
/etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=hp-dv7-4000

---

