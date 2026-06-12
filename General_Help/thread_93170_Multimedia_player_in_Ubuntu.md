---
title: "Multimedia player in Ubuntu"
date: 2005-11-21
forum: General Help
---

### Post by DADDA on 2005-11-21
Hi,

I have descided to install Mplayer. I needed a allround moive player, but i can't get eny codecs to install?

Could someone help me whit the repositories and all the names on codecs I may need?

Here is a list on some codecs I whant:

Xvid
Divx
Mpeg-3
Mpeg-4
DVD-Movies
MP3
MP4
Dolby Digital

More Video and Audio codecs...

---

### Post by jamesford on 2005-11-21
i got mine from here [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by landotter on 2005-11-21
grab the codecs from the mplayer site, unpack the package and put the codecs in a directory named /usr/lib/win32. You'll need to create this directory as root.

Mplayer, Xine, and Totem (if you install totem-xine) will look to this directory for codecs.

---

### Post by DADDA on 2005-11-22
Thanks for the help...


I have now a fully function multimedia player (Mplayer) and all the codecs I will ever need, I hope atleast...

Mplayers homepage: [http://www.mplayerhq.hu/homepage/design7/news.html]("http://www.mplayerhq.hu/homepage/design7/news.html")
(Download the full codec pack from there!!! And put it in /usr/lib/win32)

Follow the Ubuntu 5.04 guide to install Mplayer.... [http://ubuntuguide.org/#mplayer]("http://ubuntuguide.org/#mplayer")

That's all, install mplayer for Mozilla Firefox also...

---

### Post by HunterCo on 2005-11-22
Don't forget, you can always try out the software script Automatix for things like that, too! That can be [found here.]("http://ubuntuforums.org/showthread.php?t=66563")

---

### Post by souki on 2005-11-22
[QUOTE=HunterCo]Don't forget, you can always try out the software script Automatix for things like that, too! That can be [found here.]("http://ubuntuforums.org/showthread.php?t=66563")[/QUOTE]
yeah, automatix works great form me too
got totem to decode everything: mp3, m4a, divx, xvid, dvd (with menus and subtitles), quicktime
I used to stay away from totem/gstreamer because of audio sync and dvd menu problems but now it's just perfect

---

### Post by Bachstelze on 2005-11-22
VLC works fine too and you don't have to install any codecs.

---

