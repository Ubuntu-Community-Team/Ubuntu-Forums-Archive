---
title: "No sound from speakers but on headphone"
date: 2009-11-12
forum: Hardware
---

### Post by SiSL on 2009-11-12
Greetings,

I have installed Karmic as fresh install, yet, my laptop (LG LW70 Express) has only sound at headphones, when I unplug headphones or since start no headphones are plugged; it does not have any sounds...

What can I do to fix this? (PS: Beside having constantly on headphones)

---

### Post by SiSL on 2009-11-12
Ok, I guess, I found solution as:


Editing /etc/modprobe.d/alsa-base-conf and changing lines 
[COLOR=Red]**#**[/COLOR] options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel probe_mask=1 model=allout

And rebooting

---

### Post by ryry46d9 on 2010-04-25
> **SiSL said:**
> Ok, I guess, I found solution as:


Editing /etc/modprobe.d/alsa-base-conf and changing lines 
[COLOR=Red]**#**[/COLOR] options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel probe_mask=1 model=allout

And rebooting

this fixed my LG LW70 Express 9.10 but new file in 9.10 is /etc/modprobe.d/alsa-base.conf 

after trying 
[http://swiss.ubuntuforums.org/showthread.php?t=1129951&highlight=LW70](http://swiss.ubuntuforums.org/showthread.php?t=1129951&highlight=LW70) 
&
[http://swiss.ubuntuforums.org/showthread.php?t=860223&highlight=LW70](http://swiss.ubuntuforums.org/showthread.php?t=860223&highlight=LW70)
which both failed on 9.10

good job :popcorn:

now to get the on-board mic to work

---

