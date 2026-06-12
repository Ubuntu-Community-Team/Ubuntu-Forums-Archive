---
title: "Problem with new sound card on karmic"
date: 2009-12-17
forum: Hardware
---

### Post by mjtodd on 2009-12-17
As the in built sound card on my laptop (an ergo microlite 411) died, I got a replacement usb sound card, an Aureon Dual from Terratec, which is *meant *to be compatible. So far I've managed to get the laptop to acknowledge the presence of the sound card when plugged in, but there's no sound coming out? Any suggestions? I've been trying to fix this on an insomnia kick, but no joy. Not even my proven method of rebooting is working! ](*,)

---

### Post by Rmantingh on 2009-12-17
Have you checked your pulseaudio settings? System -> Preferences -> Sound -> Hardware tab
It seems other users have had similar problems.
See [http://forums.fedoraforum.org/showthread.php?t=181692](http://forums.fedoraforum.org/showthread.php?t=181692)

---

### Post by sojournerC on 2010-01-04
I too have been fighting with a usb sound card. If it doesn't appear in preference>sound>hardware then likely alsa is not loading the proper module for it. Pulseaudio cannot find anything that alsa doesn't as pulse uses alsa as its sound server not specific soundcards. Focus on alsa, 

See what the output of cat /proc/asound/modules is. If your card appears there then that's progress. 

For me, my card is recognized by /proc/asound/modules and under lsusb, 

try this: [http://ubuntuforums.org/showthread.php?t=922860&highlight=usb+sound+card](http://ubuntuforums.org/showthread.php?t=922860&highlight=usb+sound+card)

but in karmic, the file you edit is called /etc/modprobe.d/alsa-base.conf

---

