---
title: "ICC loding when X starts"
date: 2009-11-11
forum: Hardware
---

### Post by lambengolmor on 2009-11-11
Hi everybody, I hope this is the right section, feel free to move if it's the case...
I have a Macbook Pro and was surprised of how photos looked different in linux from MacOS... So I discovered the existence of xcalib, copied the icc profile from MacOS and everything looked great. Some days ago I upgraded to Karmic and noted that X starts earlier than before, so that's the question:

Is it possible to load an icc profile (i.e. to launch xcalib, simple bash command) when X starts?

I want this because loading it when user logs in gives a bad feeling (colours changes from gdm to gnome). I have tried to add a script that execute xcalib in /etc/X11/Xsession.d and gave it a low id (it is named 19custom_xcalib) so it starts before anything. This solves the other issue I had (set the colour profile for all users) but still gives the bad feel (from what I understood it's gdm that launches xsession so every change I make in that direction would be useless).
Thanks for anyone that replies (any info about the new splash method would be appreciated)

---

### Post by Rollmops on 2009-11-11
I use dispwin from *Argyll color management* which is available for karmic and *DispcalGUI* as a GUI for it.

To load the color profile when X starts, I added the line
```
/usr/bin/dispwin <profile>
```
to */etc/gdm/Init/Default* before the last line which reads
```
exit 0
```

---

### Post by lambengolmor on 2009-11-11
I've tried it with xcalib and of course it works. There's still a percievable fraction of second where X's without the colour but I can bear with it :P
Thanks a lot, if you can point me to some guide in choosing the colour profile manager (xcalib? argyll? littleCMS?) that'll be wonderful :)

---

