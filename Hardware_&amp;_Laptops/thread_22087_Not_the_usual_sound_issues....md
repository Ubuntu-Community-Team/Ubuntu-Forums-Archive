---
title: "Not the usual sound issues..."
date: 2005-03-25
forum: Hardware &amp; Laptops
---

### Post by out of the blue on 2005-03-25
Mine are pretty simple (at least sounds works! ;)), but still annoying.

Sound seems to work fine (though I haven't tried anything particularly off the wall yet -- just listening to music, watching videos, etc) but the preamp is a bit noisy. I mean, to keep crackling to a reasonable level, I have to turn down the in-player volume for Beep Media Player to about 70-80%, and the same for the global volume levels. This is a problem because Ubuntu's system sounds, and sounds for i.e. gaim are very loud and can be rather annoying when I have the music cranked and someone sends me an IM. :)

My sound card is a SoundBlaster Live! Old, I know, but reliable.

Anyway, my point is that in Windows I can crank all the volumes and there is no preamp crackling. I can fidget with equalisers in WinAmp, but if I do the same with BMP the crackling gets worse. Can anyone suggest a resolution?

---

### Post by teumima on 2005-03-26
There seems to be a sound issue in hoary.

I just turned off the system sounds and it works fine now. Unless all the little ding dongs excite u, try without them for now. Let me know if that did it.

---

### Post by nic on 2005-03-26
"My Hoary" used to be free of sound issues until a week ago. Now I have to keep the volume levels (too) low to avoid the crackling.
Your post says it all.

My soundcard is a sounblaster 128 pci, I did try the other sound settings (now alsa) and the system sounds are turned off.
I have also done several (negative) hardware tests.

Besides that I'm having a great experience with ubuntu which had me delete every MS stuff.

Nicolas

---

### Post by trigg on 2005-03-26
[QUOTE=nic]"My Hoary" used to be free of sound issues until a week ago. Now I have to keep the volume levels (too) low to avoid the crackling.
Your post says it all.

My soundcard is a sounblaster 128 pci, I did try the other sound settings (now alsa) and the system sounds are turned off.
I have also done several (negative) hardware tests.

Besides that I'm having a great experience with ubuntu which had me delete every MS stuff.

Nicolas[/QUOTE]

I have had similiar issues in the past, but not with Hoary.  I have heard that you should keep the PCM sound level at around 70% (I think I read that on the ALSA website somewhere)  Also, check to make sure that your "Analog Mix" in the Alsamixer is not set too high.  That has been my problem in the past. . .

trigg

---

### Post by teumima on 2005-03-27
Try changing your Mulitmedia Sound Systems even if it gives you an error.

Since u mentioned that u are using ALSA try another one (until today I was using OSS and it worked great) then:

Ctrl + Alt + Backsp

The sound should work regardless, if not try another one. Try them all.

Try also disabling sound systems.

P.S. In mine only OSS was a working option until today. Hoary has been having sound issues, so try and apt-get update and upgrade.

---

### Post by nic on 2005-03-29
Thanks for your suggestions.

I have followed these instructions:
[http://ubuntuforums.org/showthread.php?t=8882&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=8882&page=1&pp=10)
and the crackling/volume level issue is now solved (using esd with the system sounds turned on)

Nicolas

---

