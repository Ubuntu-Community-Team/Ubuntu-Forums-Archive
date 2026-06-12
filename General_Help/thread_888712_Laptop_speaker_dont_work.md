---
title: "Laptop speaker dont work?"
date: 2008-08-13
forum: General Help
---

### Post by Exile666 on 2008-08-13
I've been running Ubuntu for a while now, but ever since I switched from Windows to Ubuntu they haven't worked. However when I plug-in my headphones, I get sound. I have the drivers for it(Windows) but I don't how to use them or what to do with them. Can anyone help... Please

Regards

---

### Post by stormtrooprdave on 2008-08-13
Don't know if this will help but I had a sound related issue today. All the sound was playing at a very low volume, even with my speakers turned up full it was very low.  My hardware profile seemed ok but I couldn't figure out why it was playing so low. 

I fixed it by adding the volume control applet to a panel and turning it up from there and then removing the applet.  

Might be nothing to do with your problem but if its playing through headphones it could be something similar?

---

### Post by decoherence on 2008-08-13
in the terminal type *alsamixer* and start cranking things up until you get sound. channels that have an "MM" on the bottom are muted. Press 'm' to unmute them and ESC to quit.

hth,

---

