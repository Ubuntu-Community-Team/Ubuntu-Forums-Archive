---
title: "audio stream delayed in video playback"
date: 2006-04-15
forum: Hardware &amp; Laptops
---

### Post by fubar0 on 2006-04-15
The audio stream of my videos, which play well on Windoze, lags behind the Video playback. How can I fix this?

This phenomenon seems worse with Totem than with MPlayer.

Any ideas?

---

### Post by mostwanted on 2006-04-15
Install totem-xine if you haven't already (this only goes for Breezy, in Dapper Gstreamer is much better).

---

### Post by fubar0 on 2006-05-18
ok, maybe this can help you:

my installed codecs:
gstreamer0.8-faac (multiverse)
gstreamer0.8-faad (multiverse)
gstreamer0.8-ffmpeg (universe)
gstreamer0.8-lame (multiverse)gstreamer0.8-mad
gstreamer0.8-plugins (universe)
gstreamer0.8-plugins-multiverse
gstreamer0.8-xvid (multiverse)
libquicktime1

The videos I am talking about are around 700 MB in size and mostely encoded with XviD or DivX, embedded in the avi container. 
They are saved on FAT32 partitions, however, that should not be the reason for my problem, for I have tested some of them on a ext3 drive which didn't sort it out.

P.S.: I am running a Athlon64 machine, so I've got mplayer-amd64 installed. There are NO w32codecs installed.

edit: I know this thread should be in 'Video and Sound', but I continued it here so we do not produce another crosspost.
May a moderator be so kind to move it in the appropriate forum?

---

