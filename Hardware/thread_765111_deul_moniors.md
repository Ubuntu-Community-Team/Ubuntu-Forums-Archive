---
title: "deul moniors"
date: 2008-04-24
forum: Hardware
---

### Post by Periswell on 2008-04-24
hi 

ive just got the new ubuntu and i was wondering how do you get duel monitors. thanks.

-josh

---

### Post by Ub1476 on 2008-04-24
Open "Screens and Graphics", which is a graphical front end for detecting displays. It's probably hidden (edit menus to show it), but the launch command for it is:

```
gksu displayconfig-gtk
```

---

### Post by Dark Hornet on 2008-04-24
what gfx card do you have...if it is nVidia, you will probably want to use the nVidia drivers, and use Twinview which comes with it.  This will allow you to use both of your monitors.  Hope this helps.

Darkhornet

---

### Post by lassegs on 2008-04-24
Hmmz. I have a Nvidia 8800GT, just upgraded to 8.04. Using the nvidia drivers.

Twin View worked like a charm under Gutsy, with the nvidia display settings thingy. But in Hardy neither displayconfig-gtk nor the Screen Resolution in the System -> Prefrences menu show the second monitor.

With the open source drivers the second monitor is found, but it will just clone views (mirror)

Since I'm a big fan of the TV series IT Crowd, I tried turning the monitor on and off again :P. Tried rebooting. No go.

Tried running nvidia-xconfig, but that didnt help me either, just made the xorg.conf very messy.

Normally I would find some xorg.conf and just duplicate it, but I'm a little unsure about this whole 7.3 hotplugging thing. 

I attached my xorg.conf. Thanks in advance.

SOLVED: Saw the [http://ubuntuforums.org/showthread.php?t=764433](http://ubuntuforums.org/showthread.php?t=764433) thread, installed nvidia-settings, and everything was perfect.

---

### Post by Dark Hornet on 2008-04-24
Glad everything worked out...I have an 8800 GTX, and twinview works great for me.

Darkhornet

---

