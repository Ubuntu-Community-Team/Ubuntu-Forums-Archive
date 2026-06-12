---
title: "No sound in flash (firefox) in Intrepid"
date: 2008-11-15
forum: General Help
---

### Post by R%&amp;92GH&amp; on 2008-11-15
When I try to play a flash movie (ex: a youtube video) in firefox, while listening to some other music (ex: rhythmbox), or having some program that uses sounds opened, it doesn't play any sound. If I run firefox from a console, I get the following message multiple times: 

```
ALSA lib pcm_dmix.c:996:(snd_pcm_dmix_open) unable to open slave
```

I tried several solutions offered in these forums, but none of them worked. If I close all the applications using audio and I restart Firefox, then I can hear all the youtube videos. This happened since I upgraded to Intrepid. In Hardy I didn't have this problem at all.

Any solutions?

Thanks in advance,

Marc

---

### Post by Afkpuz on 2008-11-15
I'm not sure if the appropriate word is driver, but you need to change your audio driver from ALSA (or autodetect) to pulse audio.  ALSA is only able to produce sound from 1 source at a time.  Pulse is able to do multiple.  So

goto System>Preferences>Sound  

Under sound events and music and movies, select pulseaudio sound server.  Also, make sure your mixer is set to pulse audio.  That should do it.  You might need to log out and in to make it work correctly.

---

### Post by R%&amp;92GH&amp; on 2008-11-15
I changed the sound settings from "Automatically detect" to "Pulseaudio", I rebooted, but I don't see any improvements....

But I found that changing all of them to use ALSA, solved the problem. Anyway, I don't understand why I can't use Pulseaudio, if it worked flawlessly in Hardy...

---

### Post by cofko on 2008-11-18
After I've upgraded Hardy to Intrepid , I've also had no sound in Firefox when playing movies. The problem was that Firefox was using Flash plugin in /home/*/.mozilla/plugins/libflashplayer.so , but adobe-flashplugin package installed the plugin to /usr/lib/adobe-flashplugin/libflashplayer.so . 
I just deleted ~/.mozilla/plugins/libflashplayer.so and instead created a symbolic link : 

ln -s /usr/lib/adobe-flashplugin/libflashplayer.so ~/.mozilla/plugins/libflashplayer.so

The sound was back again.

---

### Post by philinux on 2008-11-18
> **marcpalaus said:**
> I changed the sound settings from "Automatically detect" to "Pulseaudio", I rebooted, but I don't see any improvements....

But I found that changing all of them to use ALSA, solved the problem. Anyway, I don't understand why I can't use Pulseaudio, if it worked flawlessly in Hardy...

Big debate on the Jaunty dev forum.
[http://ubuntuforums.org/showthread.php?t=977562](http://ubuntuforums.org/showthread.php?t=977562)

---

