---
title: "Music Playback on Ubuntu (Hoary)"
date: 2005-02-05
forum: Hardware &amp; Laptops
---

### Post by cnastiuk on 2005-02-05
Just recently switched over from Windows XP to Ubuntu and am having problems using RhythmBox and Totem to play .mp3's. Whenever I try to play them, it gives me the message:

RhythmBox say:
Error loading files into library.
There is no plugin installed to handle a MP3 file. file:'filename'

Totem says:
Totem could not play 'filename.mp3'.
Failed to open; reason unknown.

All the regular Ubuntu sounds work but no luck on music. Any suggestions?

---

### Post by Sye d'Burns on 2005-02-06
I suggest you read [ubuntu-geek's excellent walk-thru](http://www.ubuntuforums.org/showthread.php?t=3713&highlight=mp3) and take particular note of number 6.

Enable MP3 support in Rhythmbox.
> sudo apt-get install gstreamer0.8-mad 

The entire guide is very handy. Give it a read.

---

