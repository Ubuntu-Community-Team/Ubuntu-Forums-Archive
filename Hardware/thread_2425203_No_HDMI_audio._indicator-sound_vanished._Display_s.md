---
title: "No HDMI audio. indicator-sound vanished. Display settings missing."
date: 2019-08-22
forum: Hardware
---

### Post by dalekky on 2019-08-22
I am having lots of problems which may or may not all be related.

System is running Ubunu 16.04 LTS on a HP laptop. The hardware for HDMI audio is [AMD/ATI] Kabini HDMI/DP Audio, Subsystem: Hewlett-Packard Company Kabini HDMI/DP Audio

Firstly. I plugged in a HDMI cable to the laptop only to discover that HDMI audio no longer appears in sound settings.
I had not used the HDMI audio out for about 10 months, so I don't know when it stopped working. All I know is it used to work just fine.

Next I tried to uninstall and reinstall everything related to alsa and pulseaudio.

The results of that was:
1. still no HDMI audio out
2. Screen Display system settings now broken
3. 2 x Printer icons in system setttings
4. No indicator-sound volume control at top of screen

This is what I've done -

sudo apt-get remove --purge alsa-base pulseaudio
killall pulseaudio; rm -r ~/.config/pulse/*

sudo  apt-get install --reinstall alsa-base alsa-utils pulseaudio linux-sound-base libasound2
pulseaudio -k
sudo alsa force-reload
pulseaudio --start
sudo apt-get install indicator-sound


more audio info here - [http://paste.ubuntu.com/p/6778HBV9t3/](http://paste.ubuntu.com/p/6778HBV9t3/)
and here - [http://paste.ubuntu.com/p/DjwVVvV5vq/](http://paste.ubuntu.com/p/DjwVVvV5vq/)

---

### Post by him610 on 2019-08-22
You could have a defective HDMI cable. I had one that became defective after over a years worth of use. You did not specify which point release of Ubuntu 16.04 you are running. Is your 16.04 installation up to date (16.04.3)? Is audio present in the laptop speakers and the headphone connector?

---

### Post by dalekky on 2019-08-23
Ubuntu 16.04.6 LTS 64-bit fully updated.
Audio works for internal speakers and the headphones socket. Both of those show up in sound settings.

---

### Post by dalekky on 2019-08-25
No answer found, so ended up removing 16.04 and replaced with 18.04 LTS.
HDMI audio is working again.

---

