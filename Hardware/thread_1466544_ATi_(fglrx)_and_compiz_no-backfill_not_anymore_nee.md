---
title: "ATi (fglrx) and compiz: no-backfill not anymore needed?"
date: 2010-04-30
forum: Hardware
---

### Post by Boombino on 2010-04-30
I use compiz on my laptop with ATi Mobility RadeOn HD2600. Today I moved to Ubuntu 10.04, installed newer fglrx and found out that in order to get rid of delay on minimizing/maximizing windows with compiz I can enable "Direct2D" feature of fglrx with this command:

sudo aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE

I've found it here:
[http://www.webupd8.org/2010/04/how-to-enable-direct2d-acceleration-in.html](http://www.webupd8.org/2010/04/how-to-enable-direct2d-acceleration-in.html)

Patching XServer is not needed. Is this a good alternative to no-backfill or backclear patches?

---

### Post by luismacb on 2010-04-30
I don't think so. The minimize delay disappear, however, videos are playing too slow in full screen.

Any other solution?

---

### Post by luismacb on 2010-04-30
The solution was "backclear patch":
[http://www.phoronix.com/forums/showthread.php?p=125046](http://www.phoronix.com/forums/showthread.php?p=125046)

---

### Post by jrichter on 2010-04-30
sudo aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE

That command worked for me as well.  I have not tried movies, but the minimize/maximize issue is fixed.

---

### Post by KrGAce on 2010-04-30
Thanks to all for the responses.  The new ppa for the no backfill worked for me after a reboot.


Thanks again,


AceMan

---

### Post by banker247 on 2010-11-09
what does this command actually do... i see that it worked with the lag - does it just do what the PPA does?

---

