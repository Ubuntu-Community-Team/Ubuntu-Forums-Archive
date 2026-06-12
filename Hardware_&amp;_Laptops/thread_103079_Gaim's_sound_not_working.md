---
title: "Gaim's sound not working"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by Speedyz2 on 2005-12-13
Hey guys, 
  I looked but couldn't find a thread for this, sorry if I happened to miss it and did a repost. I installed Gaim and it works fine and everything but the sound won't work. Any ideas? My sound on EVERYTHING else is fine. I'm using Kubuntu Breezy, if that helps and my Hardware is set to ALSA. Thanks for the input guys.

---

### Post by khc on 2005-12-14
What's your "Sound method" set to? Try setting it to ARTS.

---

### Post by Speedyz2 on 2005-12-14
what do you mean "sound method"? and ARTS.....thx for the info but could you explain it a little better please. Thank you.

---

### Post by khc on 2005-12-14
Look at the preference for gaim.

---

### Post by Speedyz2 on 2005-12-15
worked awesome..thnx again guys.

---

### Post by roots on 2005-12-18
um...i just installed gaim 1.5 and then 2.0beta in ubuntu hoary but in gaim sound preferences i can only choose "console beep" or "command" as sound method. what about "ARTS" or am i just missing the point?

cheers,
.roots

---

### Post by khc on 2005-12-18
Install libaudiofile-dev and libao-dev before you compile gaim.

---

### Post by roots on 2005-12-19
cheers - that worked out! nevertheless - it doesn't work if i set it to "arts" but "auto" works fine for me!

thanks a lot!
.roots

---

