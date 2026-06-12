---
title: "no sound"
date: 2005-03-24
forum: Hardware &amp; Laptops
---

### Post by gogodidi on 2005-03-24
this isn't the classical problem, its not that I can not hear anything because the engines do not work..

i checked the volume control, I chekc my speakers, that has nothing to do with it, I could lay music before but now, when I try to use the aRTs sound server, it crashes, I have reinstalled it and everything. When I try to use the arts server in amaroK it says that dev/dsp is already in use

if I try to use the gstreamer alsa engine, it says is in use.

I cant get any sound at all
(except when using XMMS  for some strange reason

i think im gonna do a re install

but I don't want to cos ive only just gotten kdevelop to work, for the first time ever!!!

---

### Post by nihius on 2005-03-25
Does this help?
[http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)
[quote=http://www.ubuntulinux.org/wiki/RestrictedFormats]3. Sound and third party software

Ubuntu uses a program called esd to allow multiple applications to access the sound card at one time. However, many third party applications not in Ubuntu main aren't designed to use esd to access the card. On some sound cards, this causes these applications to not produce sound. To work around this problem, esd must be configured to release the sound card when it is not using it. To do this, edit /etc/esound/esd.conf and change the line that begins with spawn_options to begin with default_options. Then, change the -as 5 to -as 2. Finally, remove the two bottom lines about default_options (they are unnecessary).

Note: this problem only occurs on the Ubuntu Hoary release and newer, Warty is not affected by this. [/quote]

---

