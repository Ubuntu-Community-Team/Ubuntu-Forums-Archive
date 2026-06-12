---
title: "Plugging in headphones isnt muting the laptop speakers"
date: 2012-01-21
forum: Hardware
---

### Post by AaronTaylor on 2012-01-21
I've got a meenee laptop running ubuntu 11.10 and im having a problem with the headphone jack, when plugging in headphones, sound comes from both the headphones and the laptop speakers, 

i had this problem previously and fixed it but a recent kernal update has caused it to return 

this is my alsa info:

[http://www.alsa-project.org/db/?f=294e878e3ac9139604a45d8a096170724f30d655](http://www.alsa-project.org/db/?f=294e878e3ac9139604a45d8a096170724f30d655)

anyone got any ideas?

thanks

---

### Post by AaronTaylor on 2012-01-21
I just rolled back to the previous kernal and removed the new one, thats fixed the problem.  

does anyone know of another solution that allows me to have the new kernal?

---

### Post by Dngrsone on 2012-01-21
I find that I have to reinstall the ALSA update after every kernel fix.

In [this thread](http://ubuntuforums.org/showthread.php?t=1892803), I threw together a quick/dirty bash script to get the job done a little less painfully.

---

### Post by AaronTaylor on 2012-01-21
Thanks i'll give that a try next time i update

---

