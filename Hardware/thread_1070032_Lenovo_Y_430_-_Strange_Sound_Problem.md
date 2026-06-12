---
title: "Lenovo Y 430 - Strange Sound Problem"
date: 2009-02-14
forum: Hardware
---

### Post by ain on 2009-02-14
Hi ppl,

I am having an unusual problem with a Lenovo Ideapad Y 430.

The laptop uses three speakers, two tweeters at the front and one internal subwoofer underneath. It uses a Conexant soundcard (not sure which one). 

So here is the issue. 
When using the standard install, the mute button only mutes the two speakers and not the subwoofer. If I change to the ALSA driver the mute works but when I connect headphones, the subwoofer does not mute. 

Anyone got any ideas?

---

### Post by kitts on 2009-02-15
I use lenovo y510. to solve the above issue u need to add a line to /etc/modprobe.d/alsa-base.  For details check this post. 

[http://ubuntuforums.org/showthread.php?t=687663&page=2](http://ubuntuforums.org/showthread.php?t=687663&page=2)

---

