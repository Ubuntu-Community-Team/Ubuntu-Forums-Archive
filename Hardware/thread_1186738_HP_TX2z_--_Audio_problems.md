---
title: "HP TX2z -- Audio problems"
date: 2009-06-13
forum: Hardware
---

### Post by proverbs308 on 2009-06-13
I have tried sifting through all the threads about how to get this to work but has anyone been able to get the audio to work.   What I mean by work is be able to play audio files and watch movies.  I have tried everything I can think of which is little since I am returning from a long hiatus from linux.  Please pass on any advice you may have.  I probably am not the only one with problems.  Thanks

I am running 9.04

---

### Post by matthewjames on 2009-06-13
What sound card do you have? Click on the sound indicator at the top and open volume control. In the Device drop-down menu, tell me what appears for (Alsa mixer)

---

### Post by Favux on 2009-06-13
Hi proverbs308,

Basically you use the solution exophobe shows in post #72 here:  [http://ubuntuforums.org/showthread.php?t=1038898&page=8](http://ubuntuforums.org/showthread.php?t=1038898&page=8)  But since they've changed the name of alsa-base to alsa-base.conf in Jaunty you can directly edit it by typing in a terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
and add the line:
```
options snd-hda-intel model=toshiba 
```
to the end of the file.

Hope this helps.

---

### Post by proverbs308 on 2009-06-18
Thanks Favux.  I did that and also had to change /etc/modules to the following.  Then my sound worked fine.

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
```

---

