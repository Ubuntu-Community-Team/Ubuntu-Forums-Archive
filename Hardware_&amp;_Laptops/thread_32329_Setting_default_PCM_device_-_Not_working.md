---
title: "Setting default PCM device? - Not working?"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by cross5 on 2005-05-07
OK - I know my sound card (turtle beach santa cruz) is hw:2.0 and when I tell apps like xmms to use alsa hw:2.0 they play music great.


But I don't get system or apps using auto/esd sounds.  They just act like they are playing (obviously to the wrong device) I have multiple sound devices.

I did everything per this thread:

[PHP]http://ubuntuforums.org/showthread.php?t=27186&highlight=alsa+default+sound[/PHP]

and set pcm to hw:2.0 in /etc/asound.conf but nothing changed.  


Yet if I force an app to use alsa/hw:2.0 it plays - but default won't work.


Kinda pissing me off, I'd like system/gaim sounds and some apps won't let you force them.


Any ideas?

---

### Post by cross5 on 2005-05-07
Update:


To verify I was correct, I remove EVERY sound device except for the soundcard, reboot - 

and voilca esd and alsa work and all aps/system sounds play


So - Why is ubuntu not listening to me when I tell it which sound device to use as default with my /etc/asound.conf file?

---

### Post by cross5 on 2005-05-08
nobody?

---

