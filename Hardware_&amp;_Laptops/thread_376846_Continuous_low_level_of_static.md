---
title: "Continuous low level of static"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by fearpi on 2007-03-05
I dual boot WinXP and Ubuntu 6.10. When I am in Ubuntu, I have a low level of continuous static - now that I think about it, it's a lot like listening to a cassette player. This static is not present in Windows. How can I get rid of it?

---

### Post by fearpi on 2007-03-05
Bump.

---

### Post by rocketman768 on 2007-03-05
You probably have some input (like line-in or cd) turned up in the alsamixer. Mute the unnecessary ones.

"alsamixer" to bring up the mixer.
"sudo alsactl store" to save your settings.
"sudo alsactl restore" to load your settings.

---

### Post by fearpi on 2007-03-05
Didn't do it. Also, the sound is present at the same volume, even when I change or mute the master volume.

---

