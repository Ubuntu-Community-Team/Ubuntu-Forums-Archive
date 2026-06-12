---
title: "problem with exaile"
date: 2008-08-09
forum: General Help
---

### Post by mhh91 on 2008-08-09
there's something weird going on,when i try to play my mp3's with exaile i get distorted sound coming out,but when i try 2 use any other application like rhythmbox,it plays sound properly,what's the problem here


i'm using ubuntu 8.04

---

### Post by mhh91 on 2008-08-09
hello,anybody there?

---

### Post by ad_267 on 2008-08-09
I'm here. Not sure how to help though. Is it just mp3s that sound distorted with exaile or all formats? Both exaile and rhythmbox use gstreamer so that's kind of weird.

You could try playing around with settings in system - preferences - sound and changing the sound playback or change the output options in exaile if there are any.

---

### Post by mhh91 on 2008-08-09
i've tried ALSA,ESD,OSS,pulse audio and even the autodetect option in "sound",they all give the same output

all of those output sound in the test,by the way

---

### Post by mhh91 on 2008-08-10
bump

---

### Post by kenaih on 2008-08-20
I got this problem yesterday, solution was already in the forum but for rhythmbox. 

Just remove gstreamer0.10-fluendo-mp3 and use gstreamer0.10-plugins-ugly{-multiverse} instead. (or just install libmad0).

---

