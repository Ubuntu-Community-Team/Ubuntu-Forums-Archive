---
title: "Tuxguitar and Timidity"
date: 2008-11-13
forum: General Help
---

### Post by kaizc on 2008-11-13
So I have installed both Tuxguitar and Timidity. How do I use timidity to get sound from tuxguitar because atm theres no sound on playback.

---

### Post by semitone36 on 2008-11-13
Hey Kaizc

I had a very similar problem with this myself.  First do this: type ```
timidity -iA -Os
``` into the terminal.  Then, open tuxguitar up and go to Tools -> Settings -> Sounds -> and select one of the new timidity ports you opened in the terminal.  Close out of settings and click "yes" on the Apply Settings window that pops up.

This should work for you.  The only drawback is that it will only work for your current session.  If you reboot your computer you will have to do it again.  If you want more help you should check out the [tuxguitar forums]("http://www.tuxguitar.com.ar/forums.html") or [my post]("http://www.tuxguitar.com.ar/forum/5/880/timidity-sounds-like-a-3-yr-old-playing-guitar/") where I got help on my problem.

Hope this helps!:)

---

### Post by www.rzr.online.fr on 2008-11-26
> **semitone36 said:**
> 
This should work for you.  The only drawback is that it will only work for your current session.  If you reboot your computer you will have to do it again. 

Not with tuxguitar-snapshot-jsa :

[http://ubuntuforums.org/showthread.php?p=6255909#post6255909](http://ubuntuforums.org/showthread.php?p=6255909#post6255909)

---

