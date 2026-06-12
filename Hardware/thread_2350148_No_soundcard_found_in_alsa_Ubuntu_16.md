---
title: "No soundcard found in alsa Ubuntu 16"
date: 2017-01-21
forum: Hardware
---

### Post by rety on 2017-01-21
Hi there,

I can't have my Edirol UA-1EX recognized by alsa in Ubuntu 16.10.

Here is my ALSA informations: [http://www.alsa-project.org/db/?f=bc4e3864442934f9a8d2c50b2424675153c44e48](http://www.alsa-project.org/db/?f=bc4e3864442934f9a8d2c50b2424675153c44e48)

Thanks!

---

### Post by rety on 2017-01-21
In PulseAudio it recognizes either... :(

---

### Post by rety on 2017-01-21
**EDIT:**[COLOR=#111111][FONT=Ubuntu] I have found the solution here: [/FONT][/COLOR][http://askubuntu.com/a/595178/645228](http://askubuntu.com/a/595178/645228)[COLOR=#111111][FONT=Ubuntu] I move the soundcard from USB 3 to USB 2 and now it works![/FONT][/COLOR]

---

### Post by rety on 2017-05-05
Thank you very much! I just unppluged the Edirol-1EX from USB 3, pluged into USB 2, run command sudo alsa force-reload and it worked! Thanks!

---

