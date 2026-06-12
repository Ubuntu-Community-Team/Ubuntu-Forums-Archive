---
title: "Acer 5920G: Having issues with my mediakeys + music player (non KK related :P)"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Pott on 2009-10-29
Well I followed this [http://ubuntuforums.org/showthread.php?t=997860&highlight=acer+5920](http://ubuntuforums.org/showthread.php?t=997860&highlight=acer+5920) thread to the letter on how to create a script for the media keys to work. However they still don't. (yes I have an Acer 5920G, running Jaunty) 

I have the xbindkeysrc file as it's on this thread, except with gmusicbrowser written instead of exaile. 

"#Multimedia control keys:

"xvkbd  -text "\[XF86AudioPlay]""
    b:17
"xvkbd  -text "\[XF86AudioStop]""
   b:18:
"xvkbd  -text "\[XF86AudioPrev]""
    b:19
"xvkbd  -text "\[XF86AudioNext]""
    b:20

#Map 'e' key to launch exaile
"gmusicbrowser %f"
    c:219"

The script for the media keys is:
"#!/bin/sh

#Remaps the second Synaptics touchpad entry.

xinput set-button-map "`xinput list | grep Synaptics | tail -1 | grep -o id=. | tr -d id=`" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16

#Note- to remap the first entry, replace tail with head."


So it doesn't work with VLC, didn't work with Exaile, doesn't work with Rythmbox, doesn't work with gmusicbrowser...

It's a bit frustrating. I love to control my music from anywhere on the desktop, no matter what software I'm using or what I'm doing.

A number of things could be wrong... As I always have the PC starting up with a mouse in a USB port, it could be that the mapping of the mediakeys is wrong (Linux thinks it's a mouse device). But I don't know how to check that.
In the Mouse options (system, preferences) I have disabled the touchpad. Maybe that also disabled the media keys? Though whenever they're enabled, they still run as scrolling functions.

So what I'd love to do is have those keys (play/pause, stop, next song, previous song) working for VLC (DVD playback) and gmusicbrowser or rythmbox or even another decent music player... I'd be willing to swap player to get these working though gmusicbrowser is the best so far...

Thanks...

---

### Post by Pott on 2009-11-03
Still can't figure this out... :(

---

### Post by Dao984 on 2010-01-30
hello
i have your same problem, maybe can someone help us?
For VLC particularly ;)

---

