---
title: "pulseaudio autostart per user + openbox"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by AndEat on 2009-03-27
Intrepid 64bit ver. done over netinstall
basic server version package set 

My goal is to build from the ground up. 

My problem? I can't seem to gt pulseaudio to auto load - I can get it to load from the command line and that is the only way I've found: manual start

here are the sound packages and their dependencies I installed: 

apt-get install linux-sound-base alsa-base alsa-utils libasound2 libasound2-plugins gnome-alsamixer aumix 
apt-get install pulseaudio pulseaudio-module-zeroconf alsamixergui \
pulseaudio-utils pulseaudio-esound-compat pulseaudio-module-hal pulseaudio-module-x11 gstreamer0.10-pulseaudio libao-pulse \
pulseaudio-module-gconf asoundconf-gtk alsa-oss \
paprefs paman pavucontrol pavumeter padevchooser 

Basically I've been to tutorial to tutorial, on this board and others, I've tried a number of solutions over the past months, nothing has worked. 

I just want multiple sound sources autoloaded, run through pulseaudio, I prefer to run a lightdesktop through openbox. I'm posting here for suggestions (keep it to the command line and config files please, the sheer number of "hints' I found pointing me to a gnome or kde menu is appalling, my 2cents) 

Any assistance appreciated though.

---

### Post by madmax1735 on 2010-02-04
hey.... i have a similar problem i think....


there are no audio output devices listed under the normal user.... only the dummy out put is listed.

but if i check devices using sudo my sound card appears.... also i can hear sound when using any application like rhythmbox in sudo mode.

i get a warning "pulseaudio configure is per-user mode" on every startup

i am using ubuntu karmic alternate command line version with openbox on top.

did u manage to fix the issue. 

any help... suggestions....


thnx in advance

---

