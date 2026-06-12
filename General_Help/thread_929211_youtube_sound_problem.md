---
title: "youtube sound problem"
date: 2008-09-24
forum: General Help
---

### Post by funkyhair143 on 2008-09-24
what the title says, I can listen to music in rythmbox fine but when I try to watch something on Youtube, theres video but no sound. I've tried a few things I've found on the forums but they didn't work, so I'm not sure whats going on. It was working fine then I had some updates to install and it didn't work after that.

---

### Post by spiderbatdad on 2008-09-24
have you tried adding the package libflashsupport from synaptic? Have you tried using alsa instead of pulseaudio in sound preferences...and rebooting?

---

### Post by Bölvaður on 2008-09-24
The reason is that flash (the stuff that youtube videos run on) are using different sound source than your mediaplayer. So if you have Rythmbox open the soundcard is unavailable by the sound source of the flashplayer when you watch youtube.

What you need is to put everything under pulse-audio.




 *added* uh... put everything on alsa, he was right.. it works good

---

### Post by funkyhair143 on 2008-09-24
all right now its working thanks guys the guide I was looking at said to uninstall that libflashsupport package, so thats probably what happened

---

