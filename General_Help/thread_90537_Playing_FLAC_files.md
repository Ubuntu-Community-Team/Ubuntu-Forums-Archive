---
title: "Playing FLAC files"
date: 2005-11-15
forum: General Help
---

### Post by Ak37 on 2005-11-15
How do I play flac files using totem/beep media player. Both won't run my flac files. I got libflac installed. I've tried installing xmms-flac and copy the file to bmp's lib folder. It's recognized, but unstable.

Actually I can run the files using AmaroK. But sometimes I just want to start the files without AmaroK.

Thanks in advanced.

---

### Post by bionnaki on 2005-11-15
the only way is to copy libxmms-flac.la and libxmms-flac.so from /usr/lib/xmms/Input to /usr/lib/bmp/Input

flac will play without trouble.
the only bug I see is bmp will
crash if you right-click & view track info.
other than that it works.

---

### Post by SickTwist on 2005-11-15
What bionnaki said is correct. However, you may need to install the FLAC plug-in for xmms if it is not present:

sudo apt-get install xmms-flac

Totem could be using either gstreamer or xine for its backend. If it is using gstreamer (the Ubuntu default) you need to install the FLAC plug-in for gstreamer in order for Totem to play FLAC files:

sudo apt-get install gstreamer0.8-flac

---

### Post by statekilla1 on 2008-01-25
E: Couldn't find package xmms-flac
kingofkings@lolabear-desktop:~$ 


This was a result of typing in the command.  Where do I get the xmms-flac package?
jd

---

### Post by doug1212 on 2008-01-25
Yup, it seems to be missing, I'm using audacious from Morgoth's repo:

[http://morgoth.free.fr/ubports/](http://morgoth.free.fr/ubports/)

Doug.

---

