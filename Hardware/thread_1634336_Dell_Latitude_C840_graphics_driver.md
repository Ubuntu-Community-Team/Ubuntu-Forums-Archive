---
title: "Dell Latitude C840 graphics driver"
date: 2010-11-30
forum: Hardware
---

### Post by metalmaniac248 on 2010-11-30
Hi there

I'm trying to get a dell latitude up and running with Ubuntu maverick and for the most part it seems to work OK

The big issue though is that i can't get the graphics drivers working, (it has a nvidia gefore 440 go in it) there is no drivers in the additional drivers windows (System > Admin > additional drivers) and i tried installing the nvidia-glx-96 which claims to be compatible with gefore 440 however no luck. 

Any clues what I should be doing here?

---

### Post by Fafler on 2010-11-30
What happens when you try to install the 96 drivers from the terminal? The Open Source driver for the  card should already be installed and people claims it works quite well. Can you use that? You probably already are.

---

### Post by metalmaniac248 on 2010-12-02
The 96 driver installs, but then in additional drivers it shows as installed but not in use
And I'm fairly sure I'm not using the driver because I can't get any desktop effects working and video playback is terrible.

---

### Post by souta95 on 2010-12-08
There are issues with the legacy Nvidia drivers and Ubuntu 10.10.  I learned this when I was messing around with my Latitude C840.

In addition to that there is problems with a bug in the LCD screen's firmware which causes resolution issues.  I am currently trying to get Ubuntu 10.04 working on mine (the Nvidia-96 driver works in 10.04).  So far no luck as I am getting really strange issues.

My forum post regarding my issues:  [http://ubuntuforums.org/showthread.php?t=1640614](http://ubuntuforums.org/showthread.php?t=1640614)

---

