---
title: "GStreamer can't play a mp3"
date: 2005-11-07
forum: General Help
---

### Post by Titeuf on 2005-11-07
I'm using muine to play all my music, but there is one mp3 file I can't play. It play fines with mplayer and beep-media-player, but not in muine or rhythmbox.
Muine tells the following error message: 
> There were no decoders found to handle the stream, you might need to install the corresponding plugins
Other mp3 files play fine. After I try to play this one, it can't play any mp3 file anymore and have to restart muine.
[Here](http://titeuf.ph34rus.org/a.mp3)'s the mp3 if anyone wants to test this.

[SIZE="1"]*Please note: I will delete this mp3 once the problem is resolved, so don't complain it's illegal*[/SIZE]

---

### Post by tonysathre on 2005-11-07
do u have win32codecs?

---

### Post by Titeuf on 2005-11-07
[QUOTE=tonysathre]do u have win32codecs?[/QUOTE]
Yes, I can play all my mp3's except this one. I can also play divx/dvd's/wmv movies so those codecs are really installed.
And Synaptics also says those are installed.

---

### Post by phanboy_iv on 2005-11-07
Do you have all the gstreamer0.8(mainly just gstreamer0.8-mad) plugins installed? If that doesn't work, it may just be a bad mp3.

---

### Post by Titeuf on 2005-11-07
[QUOTE=phanboy_iv]Do you have all the gstreamer0.8(mainly just gstreamer0.8-mad) plugins installed? If that doesn't work, it may just be a bad mp3.[/QUOTE]
Yes I have. But when it's a broken mp3, how come totem-xine, mplayer, beep-media-player can play it ? They all don't use gstreamer.
Can someone also using a gstreamer-based player confirm this then ?

---

### Post by mcduck on 2005-11-07
[QUOTE=Titeuf]Can someone also using a gstreamer-based player confirm this then ?[/QUOTE]It works fine for me, and I use gstreamer..

---

### Post by Titeuf on 2005-11-08
[QUOTE=mcduck]It works fine for me, and I use gstreamer..[/QUOTE]
Thanks for trying it.
/me wonders why I can't play this mp3 but others just fine :confused:

---

### Post by tonysathre on 2005-11-08
maybe try finding another MP3 for that song

---

### Post by phanboy_iv on 2005-11-08
Whoa, I imported that file into Rhythmbox and it crashed when I tried to play it.

Weird.

When I ran rhythmbox from a terminal, it spit this message out:
> (rhythmbox:8901): GStreamer-WARNING **: pushing data on non-negotiated pad mad0:src, not allowed.

It repeated that a bunch of times.

Titeuf, do you get that message if you run rhythmbox from a terminal and play that mp3?

---

