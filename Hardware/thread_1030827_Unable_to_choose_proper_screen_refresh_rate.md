---
title: "Unable to choose proper screen refresh rate"
date: 2009-01-04
forum: Hardware
---

### Post by Zeroberry on 2009-01-04
Using an LG w2241s (1680x1050) with proprietary drivers for Geforce 9800GT. Connected through D-SUB with adapter to DIV on the card.

Ubuntu reads the LCD monitor as a CRT, I assume because of the D-SUB cable? No other option for connecting it unfortunately.

Problem is I get weird refresh rates, from 50-53 Hz (it changes by itself regularly). Using nvidia-settings I can set the frequency to 60hz but I'm not sure if it's just pretending to work. EVE Online has this weird thing where you can't choose different resolutions in "window mode" unless you have the proper frequency and I'm not allowed to choose anything but 1680.

I've tried everything I can find, editing xorg.conf with Modes, trying to force it to use a certain vertical refresh and so on, UseEDID FALSE, just reconfiguring the xorg.conf... Whatever I do I end up with odd frequencies (I've gotten 75hz, 70, 57, but never 60hz).

I'm sorry if my explanation is messy and my language is a bit off, I'm pretty new to Linux. Please ask me if you need more info. Thank you in advance for any help or insight!

---

### Post by nick09 on 2009-01-04
Ubuntu does read the LCD as CRT because of the D-SUB cable.

---

### Post by Zeroberry on 2009-01-05
Although the nvidia settings screen detects my monitor with a correct name, no matter what I try the gnome screen resolution window still says "Unknown Device" and gives me 51-53Hz options only.

---

### Post by Zeroberry on 2009-01-06
If anyone stumbles across this thread with a similar problem, I haven't solved it but I managed a little workaround. The Nvidia drivers handle the frequency so the screen is running as it should although gnome's System->Preferences->Screen Resolution stubbornly pretends it's still at 53Hz.

EVE I got to run by setting it to 1280x1050 full screen and then setting Wine to run it in a window, no problems so far.

---

