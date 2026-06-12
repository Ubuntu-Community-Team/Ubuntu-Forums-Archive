---
title: "Cannot change volume using both kmix or alsamixer"
date: 2009-05-05
forum: Hardware
---

### Post by CarNagE on 2009-05-05
Hey guys,

I have a F3Jm Asus Laptop with the HDA Intel sound card Intel 82801G. Since my upgrade to Kubuntu 9.04 (from 8.04), I cannot change the volume of the sound output anymore. In KMix, four channels are selectable as master channel: PCM, Mic, CD, and PC Beep. None of them works for setting the output volume. Thus I tried my luck with alsamixer. There I have (among others) a PCM channel and a Master **switch**. Setting the PCM level doesn't change anything, using the Master switch just mutes/unmutes. 

Does anybody have an idea how I can restore my sound control? It's quite annoying not to be able to change the overall volume of my system...

Thanks in advance, cheers,

  Tobias

---

### Post by CarNagE on 2009-05-07
Has really nobody any ideas about the cause of my problem or potential fixes?

---

### Post by Ben Leedham on 2009-05-07
When I first installed Jaunty on 2 of my laptops my sound was really low and alsamixer wouldn't change the master volume.

I followed this guide to sort it out:

[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

I don't know if some of the steps are superfluous or not but it worked for me.

---

