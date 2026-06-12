---
title: "Why no Kubuntu sticky threads?"
date: 2005-11-19
forum: General Help
---

### Post by mortram on 2005-11-19
I've had a really tough time getting simple things like mp3, dvd, multimedia support working in Kubuntu, and have not had a lot of luck searching the forums..  The Ubuntu guide has very little information on similar setup operations within Kubuntu... installing the gstreamer plugins through apt-get or adept seems to not work (depends on packages which are unavailable).  Many google searches and yahoo searches have generally not led me to any useful information for Kubuntu, just Ubuntu/Gnome stuff.

Is there some obvious place with this information I'm missing?

Is everyone using Kubuntu just doing so without dvd and multimedia playback capabilities?

---

### Post by aysiu on 2005-11-19
Kubuntu and Ubuntu are essentially the same. The only difference is that Ubuntu is Gnome and Kubuntu is KDE.

There are two main reasons the Ubuntu Guide may not be working for you:

1. It's outdated, and some of the things that were available at the time it was written are no longer available for legal reasons. You have to get them through other channels (libdvdcss2 and w32codecs, for example).

2. Even though the general procedures are the same, one major difference is that the Ubuntu Guide will ask you to *sudo gedit* stuff, but Gedit is a Gnome text editor. If you see *sudo gedit* translate that to mean *sudo kwrite*. KWrite is a KDE text editor (do not use *sudo kate*--you may run into problems if you do).

---

### Post by bored2k on 2005-11-19
You would want akode-mpeg gstreamer0.8-mad and then do a *killall artsd* to restart the sound server to get mp3 support. You can have DVD and other movie playback using the Ubuntu guides on this forum (install libdvdcss2, w32codecs and optionally mplayer-686 or mplayer-k7).

[http://www.ubuntuforums.org/showthread.php?t=87946&highlight=plf+sources.list](http://www.ubuntuforums.org/showthread.php?t=87946&highlight=plf+sources.list)

---

### Post by tokyovigilante on 2005-11-20
Comprehensive guides to the Kubuntu desktop are being worked on for the next (Dapper Drake) release, but in the meantime have a look at the [KUDOS]("http://kudos.berlios.de/kf/kf1.html") (Kubuntu is a User friendly Desktop OS) site for a list of common tasks and how to go about them.

---

### Post by mortram on 2005-11-20
ah, that site is exactly what i was looking for, thanks!

---

