---
title: "Firefox SLOW - Ubuntu Hardy 8.04"
date: 2008-09-11
forum: General Help
---

### Post by Zulu Warrior on 2008-09-11
Brand new user of Ubuntu.  
Fresh install Ubnuntu Hardy 8.04.

System:
Intel 3.4 GHz
4GB RAM
Linsys WRT54G router

6MB DSL

Able to connect at 5.89MB (per speedtest) with other OS same connection

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

Problem:
Firefox connects but is EXTREMELY SLOW.... (5 minutes for google.com)

I have tried...
1) Fixed wireless connection speed bug (1MB to 54 MB) with sudo iwconfig wlano rate 54M - now shows correct but no improvement to speed

2) Disabled IPv6 in Firefox (about:config) and Ubuntu through changes to files in /etc/modprobe.d
verified with ip a | grep inet6
==Still no improvements

3)  sudo gedit /etc/sysctl.conf
per instructions in this thread
[http://ubuntuforums.org/showthread.php?t=251509&page=2](http://ubuntuforums.org/showthread.php?t=251509&page=2)
==Still no improvements

Please help.
Thank you.

---

### Post by stoian on 2009-01-19
BUMP!!!
Bug still there...

---

### Post by yeats on 2009-01-19
Open a console window and do: 

```
ping google.com
```

it will run until you hit Ctrl-C and it will give you stats about how long it took packets lost, etc.  If all works well you can rule the network out, at least.  You might also try an alternate browser like Epiphany or Konqueror to see if Firefox is actually the culprit.

---

### Post by stoian on 2009-01-19
I'm sorry but I can connect to the internet, ping has nothing to do with that. My other machine, a laptop, on the same internet connection, running the same Ubuntu Hardy, is much snappier (and the desktop - which is slower has newer cpu and more RAM)...

---

### Post by louieb on 2009-01-19
Sometimes the make and type of NIC makes a difference. Some cards and chip-sets just don't work as well with Linux as they do with windows. Might try a brand of NIC that has good Linux support.

---

