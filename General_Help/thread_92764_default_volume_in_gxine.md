---
title: "default volume in gxine"
date: 2005-11-20
forum: General Help
---

### Post by pickarooney on 2005-11-20
I've tried everything I can think of in the options of gxine and in the config files in ~/.xine and ~/.gxine but the volume level is always at 50% when I open a file.
Is there some way of setting it higher?

---

### Post by ecobuntu on 2005-11-20
[QUOTE=pickarooney]I've tried everything I can think of in the options of gxine and in the config files in ~/.xine and ~/.gxine but the volume level is always at 50% when I open a file.
Is there some way of setting it higher?[/QUOTE]
> 

Not sure if this would work or not but it's worth a try ;)

go to terminal:
alsamixer

Set the volumes where you want them.
Then run:
alsactl store

This will save your default ALSA volumes.  It should work for GXINE.

---

### Post by pickarooney on 2005-11-20
Nope, no luck with that.

---

### Post by ecobuntu on 2005-11-20
maybe you're just S.O.L. 
:)

There could be a lot worse things with your computer than this!

---

### Post by pickarooney on 2005-11-21
Oh, there could be, and there probably are :D

---

### Post by Haegin on 2006-03-11
seems to be a problem with gxine. Im also suffering from it (I have built the latest xine-libs and gxine from source and used checkinstall so it may not affect the ubuntu version.

---

