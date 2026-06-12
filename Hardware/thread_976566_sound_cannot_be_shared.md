---
title: "sound cannot be shared"
date: 2008-11-09
forum: Hardware
---

### Post by kazzmir on 2008-11-09
I have had this annoying problem for a while. Whenever I play music with mplayer another application cannot use sound. Especially annoying is that if mplayer is running and then I play a flash video in firefox, the video won't produce sound and will hang after playing for 3 seconds. I have to kill mplayer and restart firefox to make the video play. Then when I am done I have to kill firefox, start mplayer, and then start firefox.

How can I make sound be properly shared among all applications? I use pulseaudio and alsa.

---

### Post by kazzmir on 2008-11-10
I'm not sure why, but after force reloading alsa via 
```

sudo /sbin/alsa force-reload

```

Now applications properly share the sound device.

---

### Post by Sisyphus48 on 2008-11-12
Just wanted to share.  My problem was that I put a new video card in and suddenly the sound worked in some things (online movies) but not in others(Nexiuz and Alien Attack).  I tried Kassmir's solution from above and now everything works!!  Thanks Kassmir.

---

