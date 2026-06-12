---
title: "Ubuntu netbook remix can't recognize my webcam"
date: 2010-07-18
forum: Hardware
---

### Post by ygtersoy on 2010-07-18
I use ubuntu netbook remix with my netbook. I can't install my webcam. please help me:( My computer is exper style. &#304; am  writing from Turkiye.

---

### Post by howefield on 2010-07-18
Is the camera recognised ?

Open a terminal and type

```
lsusb
```

See if you can find a line corresponding to the webcam, eg, mine looks like this...


Bus 002 Device 005: ID 046d:09a4 Logitech, Inc. QuickCam E 3500

You could then search for information on the ID string.

---

