---
title: "[SOLVED] Amarok decided to stop playing mp3s"
date: 2008-10-28
forum: General Help
---

### Post by TheOrangePeanut on 2008-10-28
I was listening to music with Amarok, and it crashed.  I opened it back up and tried to play another song and it said that the xine engine could not play mp3s, and it gave me the option of 'installing' mp3 support.  I clicked the button to install mp3 support, knotify launched in the task bar (though no actual window appeared), knotify disappeared, and I still can't play mp3s.  Any idea what the problem could be or how I could fix it?  I'm running Ubuntu 7.10 with Amarok installed from the repos.

---

### Post by FAJALOU on 2008-10-28
try ```
sudo aptitude reinstall amarok
``` for starters
and if that doesn't work then you will probably want to purge amarok and do a full reinstall of it.
```
 sudo apt-get purge amarok && sudo apt-get install amarok 
```

Hopefully this helps.

---

### Post by TheOrangePeanut on 2008-10-28
I tried both of those and no dice.  I then tried removing and puring Amarok and all of the kde dependencies as well.  Still no dice.  Any other ideas?  I'm using Totem Xine as well ('cause I've never been able to get gstreamer to work correctly) and it can't play mp3s (though it can play my video files). 

Any other ideas?

---

### Post by FAJALOU on 2008-10-28
maybe trying to install the mp3 dependencies?  
[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)
and
[http://www.ubuntux.org/mp3-support-for-amarok](http://www.ubuntux.org/mp3-support-for-amarok)

hopefully those help.
If they dont....
[http://www.google.com/search?hl=en&rlz=1B3GGGL_enUS294US294&q=mp3+amarok+ubuntu&btnG=Search](http://www.google.com/search?hl=en&rlz=1B3GGGL_enUS294US294&q=mp3+amarok+ubuntu&btnG=Search)

and google ;)  hopefully someone can help you out.  good luck.

---

### Post by TheOrangePeanut on 2008-10-28
There is something really funny going on.  If I launch Amarok through sudo (gksudo actually), mp3s play fine.  No fuss about anything.  Something must be borked somewhere...

---

### Post by TheOrangePeanut on 2008-10-28
Bump for the not-AM crowd :)

---

### Post by bep on 2008-10-28
Happened to me too, this fixed it:

 sudo rm -r  ~/.xine

---

### Post by FAJALOU on 2008-10-28
i would try what the above says, although removing .xine, doesn't seem like the smartest idea... if it works it works.  also you could try reinstalling amarok-xine, found in the medibuntu repos, or libexine1-all-plugins from the repos.  I would suggest searcing for 'xine' in synaptic and see which ones you have installed, and then reinstall any that are installed.  if none, then just follow what the above said.  good luck and as always report back :)

---

### Post by TheOrangePeanut on 2008-10-28
Removing xine from my home folder (sudo rm -r ~/.xine) fixed it.  Strange.

---

### Post by bep on 2008-10-28
> **TheOrangePeanut said:**
> Removing xine from my home folder (sudo rm -r ~/.xine) fixed it.  Strange.

Glad it helped, but it is not strange, really. At some point, one or more files in that directory got corrupted (for several reasons). By deleting it, it gets rebuilt.

---

### Post by FAJALOU on 2008-10-29
please make sure to mark the thread as SOLVED.  can be found in thread tools, i believe.

---

