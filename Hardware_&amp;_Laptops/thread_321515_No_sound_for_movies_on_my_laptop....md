---
title: "No sound for movies on my laptop..."
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by Contrast on 2006-12-19
I have the exact same codecs installed on both my laptop and my desktop. Playing video files on my desktop works fine (I'm using Kaffeine on both machines), but on my laptop, I get no sound. This is only the case with video files, as I'm able to hear everything else on my laptop fine. Any ideas? Please keep in mind I'm a relative Linux newjack, so if you have any advice, please give it in a step-by-step fashion. Thanks in advance. :D

---

### Post by renzokuken on 2006-12-19
what type of format are the movies that dont work (.avi / .mpeg / .ogm ???)

---

### Post by xyz on 2006-12-19
See the settings/volume levels. Run in a terminal:
```
alsamixer
```
Hopefully....
Also Application > Sound & Video > Volume Control

---

### Post by Contrast on 2006-12-24
Thanks for the replies. The main format I'm having problems with is .wmv (surprise, surprise)-- Pretty much all my other videos play fine (unfortunately, most of my video files are .wmv). I ran alsamixer in the terminal and came across this:
```
Item: Video [Off]
```
I switched it to On, without expecting much since it seems to be a format-specific problem, and still no sound. Any ideas?

---

### Post by Contrast on 2006-12-24
I found a workaround. If I play them in Firefox using the mozilla-mplayer plugin, they play fine. The weird thing about this is when I try playing any video in MPlayer, I get this message: "Fatal error! Error opening/initializing the selected video_out (-vo) device." While the workaround is better than nothing, I'd still like to know how I can get the sound working in Kaffeine.

---

### Post by Contrast on 2006-12-24
Nevermind, I figured it out. Stupid mistake - didn't have libxine-extracodecs installed.

---

