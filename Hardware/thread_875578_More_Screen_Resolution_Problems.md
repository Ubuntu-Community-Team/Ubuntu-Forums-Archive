---
title: "More Screen Resolution Problems"
date: 2008-07-31
forum: Hardware
---

### Post by childresspta on 2008-07-31
Ok I have GeForce 4100 Card.  Ever since the -19 kernel upgrade I have not been able to get my resolution above 640 with drivers enabled.  I have done fresh install, I have used envy, and when I run gksudo gedit /etc/x11/xorg.conf I get a blank document?  Is my card just too old?

---

### Post by overdrank on 2008-07-31
> **childresspta said:**
> Ok I have GeForce 4100 Card.  Ever since the -19 kernel upgrade I have not been able to get my resolution above 640 with drivers enabled.  I have done fresh install, I have used envy, and when I run gksudo gedit /etc/x11/xorg.conf I get a blank document?  Is my card just too old?

HI and first thing you get a blank doc is it is X11, capital X. You may also try what PmDematagoda suggested here
```
Do this:-
1) Open a modules file for editing with:-
Code:

sudo nano /etc/default/linux-restricted-modules-common

2) Edit the DISABLED_MODULES line to make it look like this:-
Code:

DISABLED_MODULES="nv nvidia_new"

and save the file.

Then reboot the PC and see if the Nvidia driver now works.
```
[http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)

---

### Post by childresspta on 2008-07-31
I had tried that, and did not think it worked, but when I booted up this morning it was working, so I will let you know if it comes back next time.

---

