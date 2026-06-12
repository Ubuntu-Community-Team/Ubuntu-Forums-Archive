---
title: "Slow videos"
date: 2006-07-24
forum: Hardware &amp; Laptops
---

### Post by Toaster on 2006-07-24
I have an old dell inspiron 7000 and I am having problems with slow movies/videos. The GFXa are okay in gxine but not VLC in vlc they are really laggy and slow. In gxine everything is fine except that the sound and video are off meaning people talk before they move their mouths. :-k I have tried using Mplayer and Xine Movie Player but I get the same results the only player that the sound works right in is VLC but the video is so choppy you cant even watch it. :P I have Dapper Drake and my linux-image is 686 and is updated. ](*,) Also I have tested the videos on a newer computer no problems. :P

Thanks for any help,

Toaster

---

### Post by Liam on 2006-07-24
A bit of googling shows that it apparently has an old ATI Rage, right?

Try this:

sudo mplayer -vo xvidix *file.avi*

Unfortunately, the vidix driver needs to be run as root, but it works rather well on my crappy old PIII 800 with an 8MB Cyberblade, and it supposedly supports ATI.

WMV is kindy shaky, but mpgs and divx/xvid work just fine.

---

### Post by Liam on 2006-07-24
BTW, depending on how the file got encoded, I still occasionally run in to audio sync problems, but they can usually be fixed by finding a sharp noise somewhere in the film (eg, a car door slamming), and using +/- to sync the audio.

---

### Post by Toaster on 2006-07-24
Okay  the video runs really fast now perfect speed. :D but the sound is still messed up and I am not sure what you mean by the +/- stuff....

---

### Post by Liam on 2006-07-25
In mplayer, it'll adjust the audio delay by +/- 100ms every time you hit + or -, allowing you to sync the audio stream to the video stream.

---

