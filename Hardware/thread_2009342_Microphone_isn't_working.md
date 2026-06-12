---
title: "Microphone isn't working"
date: 2012-06-24
forum: Hardware
---

### Post by charlescarroll1 on 2012-06-24
I'm running Ubuntu 12.04 with Gnome 3 on my Toshiba C655-S5141 laptop. I noticed that my microphone isn't working but it had been in previous versions of Ubuntu I've used (I think). Anybody have any ideas on how to get my microphone working? I feel like half a man without a microphone...

---

### Post by Enigmapond on 2012-06-24
Install gnome-alsamixer and make sure the mic volume is up and not muted.

---

### Post by charlescarroll1 on 2012-06-24
I found some threads suggesting to install Pulse Audio, which I did but didn't work.

I also install gnome-alsamixer which showed that everything was unmuted. 

After doing both those things, I restarted my system and opened up Pulse Audio again and noticed that under input devices I was seeing the noise meter fluctuate based on the noises I was making. 

My microphone is working now and I don't know if it was gnome-alsamixer or Pulse Audio. I also played around with the input settings a bit in Pulse Audio which may also have helped it work.

Thanks! ):P

---

### Post by Enigmapond on 2012-06-24
Well I'm glad something worked..:) Cheers!

---

