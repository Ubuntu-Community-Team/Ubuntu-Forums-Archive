---
title: "I need a way to tell pulseaudio which device to use/see when it is runned."
date: 2015-10-30
forum: Hardware
---

### Post by vyacheslav-sahno on 2015-10-30
[http://unix.stackexchange.com/questions/238104/keyboard-works-incorrectly-for-virtualbox-ubuntu-15-04-guest-in-debian-jessie-ho](http://unix.stackexchange.com/questions/238104/keyboard-works-incorrectly-for-virtualbox-ubuntu-15-04-guest-in-debian-jessie-ho)
[http://askubuntu.com/questions/691548/sound-disappears-after-several-reboots-in-15-10-for-alc887-possibly-because-of-n](http://askubuntu.com/questions/691548/sound-disappears-after-several-reboots-in-15-10-for-alc887-possibly-because-of-n)

According to posts i am able to see 5.1 device in aplay.

aplay -L

    surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers

When pulseaudio disabled i am able to play sounds in device surround51 with aplay:

aplay --device=surround51 sample.wav

I need a way to tell pulseaudio which device to use/see when it is runned so it would use "Built-in Audio Analog Stereo"(for example) instead of "Built-in Audio digital Stereo IEC958"(S/PDIF)

---

### Post by yoshii on 2015-10-31
I think you can do this in Pulse Audio Volume Control from the application menu.  It's under Mixers and Card Control.   Check the devices and configuration tabs for stuff to change and also use the checkboxes for setting defaults.  Sorry I can't describe this very well.  I'm somewhat new at this.  Also QasMixer might be helpful for setting ALSA hardware defaults.  QasMixer is near the menu for Pulse Audio Volume Control.

---

### Post by vyacheslav4 on 2015-10-31
No. When this system behaviour occurs there are no device called "Analog Stereo" in pavucontrol utility. 

Unable to reproduce bug right now(I've reinstalled the OS) and tell you whether QasMixer helps or not. Though there are no device selection options there and i think OS default audio card selection dialog should work.

Anyway I am asking more of terminal way of configuration of pulseaudio or alsa driver.

---

### Post by vyacheslav4 on 2015-10-31
vyacheslav4 is vyacheslav-sahno.

---

