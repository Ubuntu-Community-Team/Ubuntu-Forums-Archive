---
title: "Firefox Problem With Rythmbox And/Or Other Music Players"
date: 2008-11-16
forum: Hardware
---

### Post by Saytr on 2008-11-16
Whenever Rhythmbox is playing music or paused, I open Firefox to watch videos on Youtube for example, and the video doesn't play any sound and freezes at 0:02 seconds. but However, when I go to Youtube without Rhythmbox, the video plays perfectly without any disturbances, I am on Ubuntu 8.04. What can I do ??

---

### Post by frmdstryr on 2008-11-27
Same thing happens to me, it is something with audio mixing.  I can't figure it out either.

---

### Post by frmdstryr on 2008-11-27
I found a fix that worked for me.. [here]("http://buglandia.blogspot.com/2007/08/howto-software-audio-mixing-in-ubuntu.html").  After saving, you have to go to system > preferences > sound (or gnome-sound-properties from the terminal) and change everything to alsa.  Then restart firefox/rythmbox.  Hope this helps!

---

