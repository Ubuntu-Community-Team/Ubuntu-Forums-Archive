---
title: "Yamaha OPL-3SA2 soundcard woes...."
date: 2005-03-31
forum: Hardware &amp; Laptops
---

### Post by reddeathdrinker on 2005-03-31
Following on from [http://ubuntuforums.org/showthread.php?t=22511](http://ubuntuforums.org/showthread.php?t=22511) , I got the ALSA drivers installed fine, but now on boot, I get the "soundcard not found, or busy" error message.

So the question asked is "How do I get Warty to recognise my soundcard at boot?"

Again, TIA,
Alasdair

---

### Post by m4ng0 on 2005-03-31
Have a look at
[http://ubuntuforums.org/showthread.php?t=16285](http://ubuntuforums.org/showthread.php?t=16285)
above all the second page.

---

### Post by reddeathdrinker on 2005-03-31
[QUOTE=m4ng0]Have a look at
[http://ubuntuforums.org/showthread.php?t=16285](http://ubuntuforums.org/showthread.php?t=16285)
above all the second page.[/QUOTE]
 duh :) 

All I needed to do was put the modules into /etc/modules, so the flaming things would load....

Cheers!

---

### Post by scotty on 2005-04-15
Dang, I have no sound with the same card.  What module is the one to add?  I managed to get my sound working ages ago under Redhat, but that was with sndconfig available.

So, what was the module that you needed?

Thanks,
Scott

---

