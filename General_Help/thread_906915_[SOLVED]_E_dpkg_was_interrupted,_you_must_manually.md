---
title: "[SOLVED] E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to corr"
date: 2008-08-31
forum: General Help
---

### Post by Gabix on 2008-08-31
I get this error in my terminal and synaptic:
[COLOR="DarkRed"]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.[/COLOR] 

It happened just after a restart. 
I guess the problem is related with some of this: 
   - Just before the restart I made lots of changes to Ubuntu (almost all referred to Hardy in here: [http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+player](http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+player)), 
   - or maybe, when I was in a terminal making a "sudo apt-get install googleearth" I lost the connection to internet and that process left unclosed. (Just after I lost the connection I restarted the computer).

I have a HP 530 notebook (Core 2 Duo 1.6 MHz, 2 GB Ram) and I'm running Hardy.
Can anybody help?
Thanks!!

---

### Post by nickgaydos on 2008-08-31
```
sudo dpkg --configure -a
``` that should work :-)

---

### Post by Gabix on 2008-08-31
Ok... That was a fast response!!!
Thanks!! It worked perfectly! :lol:

---

### Post by nickgaydos on 2008-08-31
> **Gabix said:**
> Ok... That was a fast response!!!
Thanks!! It worked perfectly! :lol:
No problem, I'm here to help :-)

---

