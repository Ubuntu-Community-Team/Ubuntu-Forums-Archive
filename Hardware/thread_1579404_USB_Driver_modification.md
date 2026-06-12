---
title: "USB Driver modification"
date: 2010-09-21
forum: Hardware
---

### Post by bloodyserb on 2010-09-21
I need to put a USB webcam 50 feet away from me using ethernet cable.  I was looking at various hardware solutions when I found this at USB.org:

2.   I want to build a cable longer than 5 meters, why won't this work?

A:   Even if you violated the spec, it literally wouldn't get you very far. Assuming worst-case delay times, a full speed device at the bottom of 5 hubs and cables has a timeout margin of 280ps. Reducing this margin to 0ps would only give you an extra 5cm, which is hardly worth the trouble.
-------------- end -------------

Now that I know that the problem isn't degradation, but timing out, would it be possible to change the USB driver to allow longer timeout periods?  I really don't know the first thing about drivers, so please forgive me if I've written something totally stupid.

Thanks,

B.

---

