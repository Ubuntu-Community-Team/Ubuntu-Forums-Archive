---
title: "Why is sound much worse overall in Ubuntu (I think hardware related...)"
date: 2005-06-02
forum: Hardware &amp; Laptops
---

### Post by magomago on 2005-06-02
I'm just wondering this.  Normally I like my speakers at 25% volume and then i adjust via the computer for loudness or not, but when playing MP3s through any program it sounds substancially worse than in Windows.  Constant screeching, horrible base, etc etc...why does windows make it sound better?

I was thinking towards perhaps the plugins.  I followed the installations for all the codecs, but using XMMS/Beep I can ONLY get music to play if I use eSound, not OOS or ALSA (regretfully).  Is that the reason right there?  

IF so, what steps can I take to isolate why my sound isn't outputting with ALSA driver?  

Thanks

---

### Post by magomago on 2005-06-03
[QUOTE=magomago]I'm just wondering this.  Normally I like my speakers at 25% volume and then i adjust via the computer for loudness or not, but when playing MP3s through any program it sounds substancially worse than in Windows.  Constant screeching, horrible base, etc etc...why does windows make it sound better?

I was thinking towards perhaps the plugins.  I followed the installations for all the codecs, but using XMMS/Beep I can ONLY get music to play if I use eSound, not OOS or ALSA (regretfully).  Is that the reason right there?  

IF so, what steps can I take to isolate why my sound isn't outputting with ALSA driver?  

Thanks[/QUOTE]
 bump

---

### Post by jjross on 2005-06-06
try going to applications/sound and video/volume control and play around with the settings in there i had the same issues and i tweaked it around in there and got it sounding a lot better. i have a sound blaster live sound card and it sounded like it was overdriving everything.
                    good luck.
everything you need to know is somewhere on this forum,i use the search feature a lot

---

### Post by bored2k on 2005-06-06
Tip 1 : System > Preferences > Sound > Uncheck sound for events
Tip 2 : System > Preferences > Sound > Disable sound server. After this, go to xmms or whatever your media player  is and select alsa or arts or whatever.
Tip 3 : [http://www.ubuntuforums.org/showthread.php?t=32063&highlight=alsa+esd+gandalf](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=alsa+esd+gandalf)

---

