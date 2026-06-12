---
title: "Desktop Effects"
date: 2009-06-15
forum: Hardware
---

### Post by Mosaab on 2009-06-15
hi,

when I change the visual effects to extra I get the message "Desktop effects could not be enabled"

This happaned after i made a fresh install of ubuntu 9.04 !! I had no problem in prev versions.
Please check the output of compiz 

```
mosab@mosab-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 

```

by the way, when I want to configure Xorg it gives me this:
```
mosab@mosab-laptop:~$ Xorg -configure

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log

```

---

### Post by rbolio on 2009-06-16
I'm not really good at this but,  do you have the necesary hardware drivers activated?

(control center-> hardware drivers)

---

### Post by Mosaab on 2009-06-16
No its not.

by the way, my VGA is Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by Mosaab on 2009-06-17
I found out that its actually blacklisted in the compiz-manager file.. I just removed it from the black listed devices and it worked fine..

it was not black listed on earlier ubuntu versions .. why did they block it in this ?

---

