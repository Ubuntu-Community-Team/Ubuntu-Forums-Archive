---
title: "Restart TBS drivers"
date: 2013-06-05
forum: Hardware
---

### Post by AmbiguousOutlier on 2013-06-05
Hello, I have a TBS 6981 DVB S2 card which I had to manually install drivers for, this link worked fine for me. 

[http://www.robclarkey.com/technology/2012/06/05/installing-tbs6981-dvb-s2-dual-tuner-on-ubuntu-11-04/](http://www.robclarkey.com/technology/2012/06/05/installing-tbs6981-dvb-s2-dual-tuner-on-ubuntu-11-04/)

However after a couple weeks the card just stops working, and I have to re-install the drivers. After a fresh install I get this message;

```
dmesg | grep frontend

DVB: registering adapter 0 frontend 0 (TurboSight TBS 6981 DVBS/S2 frontend)...
DVB: registering adapter 1 frontend 0 (TurboSight TBS 6981 DVBS/S2 frontend)
```

However after a couple weeks, if I run the same code, I get nothing. Is there a way to restart drivers in general without reinstalling them, I can then keep a track of what I'm doing to help narrow down the issue. 

Regards

---

