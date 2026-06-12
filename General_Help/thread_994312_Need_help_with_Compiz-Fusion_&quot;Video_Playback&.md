---
title: "Need help with Compiz-Fusion &quot;Video Playback&quot;"
date: 2008-11-26
forum: General Help
---

### Post by mvalviar on 2008-11-26
Does anyone know how to make the Compiz-Fusion Effect/Plugin "Video Playback" work? I think its a nifty and useful feature. I've already looked for guides on how to do it but non of them worked. I ended up having Totem (xine and gstreamer), VLC and mPlayer tweaked all of them but got no where. Please help me out. I'm on Hardy and yes, I have all the codecs.

---

### Post by mvalviar on 2008-11-27
*bump* man I can't seem to find any answers to any of my questions.](*,)

---

### Post by Izek on 2008-11-27
Have you tried using totem to play the movies instead?

---

### Post by mvalviar on 2008-11-28
Wow I finally got someone to have a look at this. Thanks a lot. Well like I said. I tried to play videos on mplayer, totem and vlc. They play the videos on their own window even though I got the plugin enabled, they play on their own window not on the desktop or on the faces of the cube. I saw youtube videos of this feature and they worked. I think they used mplayer.

---

### Post by Izek on 2008-11-28
Have you enabled video playback in ccsm? The real one, not simple-ccsm. (I don't use simple-ccsm by the way, as I don't really like it.)

If you have, have you tries making the video output to X11 / No xv? You can do this by typing in the terminal (Applications > Accessories) gstreamer-properties and going to the video tab, and changing the output.

---

### Post by mvalviar on 2008-11-29
> **Izek said:**
> Have you enabled video playback in ccsm? The real one, not simple-ccsm. (I don't use simple-ccsm by the way, as I don't really like it.)

If you have, have you tries making the video output to X11 / No xv? You can do this by typing in the terminal (Applications > Accessories) gstreamer-properties and going to the video tab, and changing the output.

Yes I have ccsm and I have it enabled. And yes its already set it to X11/No xv the test works perfectly. But the output is still in the totem window.

---

