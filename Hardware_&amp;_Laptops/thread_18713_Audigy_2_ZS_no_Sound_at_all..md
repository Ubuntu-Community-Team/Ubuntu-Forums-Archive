---
title: "Audigy 2 ZS no Sound at all."
date: 2005-03-08
forum: Hardware &amp; Laptops
---

### Post by Plex on 2005-03-08
Hi

running hoary for 2 days but with no sound at all 
have searched in the forum but can figure out why I dont have sound.
help is needed!

---

### Post by Nazgoth on 2005-03-09
Same problem here ...
searched forum, google, other forums ... no solution yet =[
works fine in winxp and Mepis but refuses to work in ubuntu :/

---

### Post by dashnu on 2005-03-16
same issue for me.. I am use to gentoo I have no idea what is going on with this.. the modules are loaded everything is unmuted .. no errors in the logs.. messed around with gui sound thingys for hours tried alsa / oss / esd none work..  :confused:

---

### Post by DR_K13 on 2005-03-17
Me too/

---

### Post by bored2k on 2005-03-17
[QUOTE=DR_K13]Me too/[/QUOTE]
 gstreamer-properties, I guess you humans poked at it already right ?
If the sound is default ESD , try opening apps like beep-media-player and setting it to use ESD in the preferences.

Also try installing alsa-oss alsa-headers libesd0 esound-common alsa-base alsa-utils libpt-plugins-alsa  gstreamer's alsa plugin.

On vlume control make nothing is muted even the mic.  Then poke with esd/beep or whatever or different sound systems.

Its one of the many possibilities we us newbies have found to solve our probs.

---

### Post by popdog on 2005-03-29
I had the same problem, found that if you unmuted "Audigy Analog/Digital Output Jack" in alsamixer sound worked fine :)

Only problem is after every boot I have to unmute this setting, anyone know how to make alsamixer "remember" what I choose between boots?

---

### Post by mglukhovsky on 2005-06-05
To store the settings, do "sudo alsactl store"

---

