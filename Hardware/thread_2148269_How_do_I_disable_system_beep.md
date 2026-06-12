---
title: "How do I disable system beep?"
date: 2013-05-24
forum: Hardware
---

### Post by BcRich on 2013-05-24
I'm using an Elo 19" touch monitor with Ubuntu 12.04.02 and everytime i touch the monitor the computer's system speaker beeps on release. it's seriously buggin. how do I disable the system speaker without having to physically open the box and disconnect the speaker from the motherboard? Also I've tried blacklisting the speaker (as suggested in many threads) but obviously this doesn't work in ubuntu version's greater than like 9.04 (or something). Thanks!

---

### Post by BcRich on 2013-05-24
doh, sucha putz :oops:
NB. for those using the Elo driver
```
 # cd /etc/opt/elo-usb
  # ./cpl
``` 
and in the control panel applet untick "beep on touch" in sound preferences.
This worked for me.

---

