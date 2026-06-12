---
title: "problem with sound"
date: 2005-03-10
forum: Hardware &amp; Laptops
---

### Post by viperman on 2005-03-10
hello

how can i run in ubuntu more than one sound process at the same? for example. i want to  listen music and talking with skype at the same time...

i have  soundcard integrated on moterhboard witch AC 97 Codec. 
I use  Realtek  ALCP200/200P and  VIA 8235 ALSA mixers. thanks.


It works properly in the Windows XP....

thanks.

---

### Post by bored2k on 2005-03-10
Preferably for AC97 Sound

1. Install alsa-oss
2. Install alsa-headers
3. Make sure you have libesd0 and gstreamer0.8-esd installed. (if not, install)
4. Make sure esound and esound-common are installed. (if not, install)
5. Install alsa-base
6. Install alsa-utils
7. Install gstreamer0.8-alsa
8. Install libpt-plugins-alsa

Ok, next.
1. Right click on the little volume control in your top panel and the
choose Open volume control.
2a. *IF* it opens, you should see two tabs, one for OSS and the other
for Alsa. Make sure nothing is muted.
2b. If it does not open and instead gives you an error, let me know.

We're going to switch you to a sound daemon that allows multiple sounds.
1. In gstreamer-properties, change the Default Sink to output: ESD -
Enlightenment Sound Daemon (Why not alsa you ask? Because alsa makes
crackling noises with the ac97)
2. Change your Output plugin in XMMS to eSound output plugin. (You
also might want to think about using beep-media-player ; it's
essentially identical to xmms, uses same plugins and skins, only it's
made for gtk2 and it's much nicer.)
3. Enable your sound server startup.

That should do it :-D

---

