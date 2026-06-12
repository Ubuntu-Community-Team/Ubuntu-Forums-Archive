---
title: "[SOLVED] pulseaudio sucks... any solutions?"
date: 2008-07-12
forum: General Help
---

### Post by chris4585 on 2008-07-12
well.. I wish ubuntu didn't come with pulseaudio.. when i want to watch a youtube, usually i have to kill my music player, kill pulseaudio, kill firefox, then restart pulseaudio and then restart firefox with my 2543453 tabs, just to watch a youtube... how can i fix this???  how could i possibly use what gutsy gibbon used?

update:

i can just close my music program and refresh the youtube video, but still i get other errors when i want to play music apps, such as beep-media-player i have to do some xkilling heh

---

### Post by sdennie on 2008-07-12
You could either try to fix pulse audio using this guide: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) or, go to System->Preferences->Sound and change everything to use ALSA.  You will probably need to restart any apps using the soundcard and firefox for this to take effect.

---

### Post by chris4585 on 2008-07-12
Thanks, that worked as far as i can see, and as for beep-media-player i had to go to its preferences and set which audio plugin to use.

thank you so much vor :)

---

### Post by markharding557 on 2008-07-12
I use alsa as well,pulse is too buggy so iv'e uninstalled it.
I think this is another example of ubuntu putting new features in before they are ready

---

### Post by chris4585 on 2008-07-12
yeah pretty stupid if you ask me... but meh

---

