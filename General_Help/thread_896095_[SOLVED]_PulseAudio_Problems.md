---
title: "[SOLVED] PulseAudio Problems"
date: 2008-08-20
forum: General Help
---

### Post by Unanimated on 2008-08-20
PulseAudio says connection refused, even though I have the server set to Default. When I click Manager and hit Connect, it says connection refused, and I can't open any of the windows it has without it saying connection refused. I have ALSA set up to go through PulseAudio and none of the other drivers work, so this is kind of a major issue. Help please?

---

### Post by Comhra on 2008-08-20
These might help.

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)


[http://www.uburocks.com/2008/08/18/flash-is-fixed-in-ubuntu/](http://www.uburocks.com/2008/08/18/flash-is-fixed-in-ubuntu/)

---

### Post by Unanimated on 2008-08-20
These are the same instructions that I used before. I think my problem is that PulseAudio isn't able to connect to its own server for whatever reason.

---

### Post by Unanimated on 2008-08-20
Huh - I restarted again, and my sound works now. Thanks!

---

### Post by ctswhole on 2008-08-20
That post I did at uburocks.com is definitely a lifesaver for those running 32-bit. But all the credit definitely goes to psyke83 for coming up with this.  I followed the bug reports for a while on these flashplugin-nonfree/libflashsupport/pulseaudio problems and gave up a few weeks ago.  Revisited them a few days ago and came across his wonderful fix.  

I've tried googling for answers to this, but always came up short.  That's why I reprinted his solution; to hopefully better spread the word of his fix.  

Kudos to psyke83!

---

