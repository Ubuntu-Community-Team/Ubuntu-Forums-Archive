---
title: "[SOLVED] Sound Becomes Choppy and Internet Dies"
date: 2008-11-10
forum: General Help
---

### Post by Unanimated on 2008-11-10
This almost caused me to leave Ubuntu, which I did for about 3 days.

Sometimes, like when starting Rosegarden for MIDI editing (which the playback in that doesn't work) or when the computer almost crashes due to something sound-related, Pulseaudio makes all my sound ridiculously slow and choppy, and for some reason, my internet dies simultaneously. Pulseaudio -D returns an error saying it doesn't know what that is.

---

### Post by Unanimated on 2008-11-11
bump

---

### Post by Unanimated on 2008-11-11
bump

---

### Post by Unanimated on 2008-11-11
bump

---

### Post by Unanimated on 2008-11-12
Bump

---

### Post by Unanimated on 2008-11-12
Anybody?

---

### Post by Hyper Tails on 2008-11-12
try this

I hope this works for you

```
sudo /etc/init.d/alsa-utils restart
```

---

### Post by Unanimated on 2008-11-12
Thanks, I'll try that the next time it happens.

---

### Post by starcannon on 2008-11-12
You can also manually choose Alsa instead of pulse:

System>Preferences>Sound

Choose Alsa from the drop down menu's and give that a shot and see if it clears up the Pulse problem (I've used this work around on a few computers for myself and clients)

GL and have fun.

---

### Post by directcharitycontribution on 2008-11-12
[http://ubuntuforums.org/tags.php?tag=pulseaudio](http://ubuntuforums.org/tags.php?tag=pulseaudio)

---

### Post by Unanimated on 2008-11-12
YAY! Thanks for the link. I went to a thread that had some answers that solved my problem (hopefully) and let me get rid of Pulseaudio. Thanks! Now I just need to figure out why the Network Manager freaks out after an xserver restart. Could a mod please change the title?

---

### Post by starcannon on 2008-11-13
You can change the title, just edit the first post in advance mode.

Happy to hear you found a possible solution, if it works be sure to share "how you did it" and be sure to click on "Thread Tools" and mark post as solved, and be sure to thank the post that did it for you, as well as any posts in subsequent threads. Praise and Atta Boys is the currency of volunteer work. 

GL and have fun

p.s. thankyou's are the little medal lower right of each posters post.

---

### Post by Unanimated on 2008-11-15
Now my problem has been completely solved. I experienced problems after removing PulseAudio, so I reluctantly reinstalled it. I replaced all the configuration files that allowed it to work, then I logged out and back in. I experienced this problem once again - I restarted it. Today, I had it again. I found out that sudo /etc/init.d/NetworkManager restart fixes the networking problem, then closing Amarok, choosing my correct output/input devices in PulseAudio, then restarting Amarok fix everything.

---

