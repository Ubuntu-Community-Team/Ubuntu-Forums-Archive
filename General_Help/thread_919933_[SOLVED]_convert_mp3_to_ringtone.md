---
title: "[SOLVED] convert mp3 to ringtone"
date: 2008-09-14
forum: General Help
---

### Post by jmd9qs on 2008-09-14
hey,

anybody know of a program that i can use to convert my mp3's to AAC format so i can play them as ringtones on my phone?

---

### Post by Dave-ie on 2008-09-14
Try this shell command: 

ffmpeg -i INPUTFILE -ab 128k -acodec aac OUTPUTFILE

---

### Post by jmd9qs on 2008-09-15
thanks... that works great!

---

### Post by kpbartolome on 2009-07-26
I have no idea where to put: ffmpeg -i INPUTFILE -ab 128k -acodec aac OUTPUTFI???help I'm a total beginner

---

### Post by zarqoon on 2009-07-26
in your applications->accessoires there is a program named terminal.
Start that.

---

