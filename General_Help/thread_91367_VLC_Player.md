---
title: "VLC Player"
date: 2005-11-17
forum: General Help
---

### Post by vxj9219 on 2005-11-17
My second question of the day. [I installed Ubuntu today].
Now VLC wont play DVDs. I followed these instructions:

[http://www.videolan.org/vlc/download-debian.html](http://www.videolan.org/vlc/download-debian.html)

When I insert a DVD in the drive and try to play it in VLC, it wont respond. Help me fix it!

---

### Post by jaypeasy on 2005-11-17
Do you have libdvdcss installed? You will need this to play dvds regardless of which media player you use.

This thread should help you.

[http://www.ubuntuforums.org/showthread.php?t=81124&highlight=libdvdcss]("http://www.ubuntuforums.org/showthread.php?t=81124&highlight=libdvdcss")

---

### Post by vxj9219 on 2005-11-17
i installed sarge, as stated in the vlcplayer link. which means i installed libdvdcss2.

so how can i play dvds now? totem also doesnt work.

---

### Post by madjo on 2005-11-17
Sarge is one of Debian's flavour of Linux, not Ubuntu's.

Ubuntu doesn't have libdvdcss2 by default, you need to install it separately. (same with mp3 and other types of non-free media libraries)
read this page for more info:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by vxj9219 on 2005-11-17
still no luck with VLC even after installing libdvdcss2. it wont play DVDs. so i installed totem-xine which works fine. BTW wtf is wrong with vlc?

---

### Post by bionnaki on 2005-11-17
I never really had any luck with vlc either - on xp and on ubuntu. I recommend gxine. just install that & all your codecs/libdvdcss. enable dma (if necessary) and modify the location of your dvd player (mine is at /dev/hdc). to play dvds in gxine, file>dvd

works great.

---

