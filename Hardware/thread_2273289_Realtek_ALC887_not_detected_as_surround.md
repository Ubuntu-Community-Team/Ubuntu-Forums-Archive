---
title: "Realtek ALC887 not detected as surround"
date: 2015-04-11
forum: Hardware
---

### Post by dc740 on 2015-04-11
This is SOLVED. Check the last comment. (I only have problems with the rear-right channel, because the volume control plays in all front channels)

I have this motherboard, and the sound card is supposed to work in 8 channel mode, but I can only configure it as stereo.
[http://www.asus.com/Motherboards/M5A78LM_LX/specifications/](http://www.asus.com/Motherboards/M5A78LM_LX/specifications/)

"pacmd list-sinks" always shows the HDMI and ALC887 stereo outputs only, but it should also list surround40,50 and 51 alsa devices for ALC887, and it's not happening

I've tried loading the intel module with the following options in /etc/modprobe.d/alsa-base.conf:
3stack-6ch
3stack
3stack-digout
5stack
6stack
6stack-digout

None of them work. The only sink pulseaudio sees is "stereo" for this card (and the hdmi output, of course).

I'm using Ubuntu 14.10 in a 64 bits system with the default pulseaudio installation.

Does anyone have any ideas on what to do? Thanks!

---

### Post by dc740 on 2015-04-11
I think I solved it myself. Will keep testing. but here is what I did.

I set default-sample-channels = 6 in /etc/pulse/daemon.conf (All pulseaudio guides tell you to do it)

in  /etc/modprobe.d/alsa-base.conf I added "options snd-hda-intel model=3stack-6ch"

To finish, I started alsamixer, and configured it as 6 channels (it was set to 2 by default).

Once you do that you have to fix the speakers order in /etc/pulse/default.pa
Something like this:
[https://wiki.archlinux.org/index.php/PulseAudio/Examples](https://wiki.archlinux.org/index.php/PulseAudio/Examples)

---

### Post by Bucky Ball on 2015-04-12
Please mark as solved by following the second link in my signature. Thanks. ;)

---

