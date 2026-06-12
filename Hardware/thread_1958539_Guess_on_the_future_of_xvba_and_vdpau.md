---
title: "Guess on the future of xvba and vdpau"
date: 2012-04-14
forum: Hardware
---

### Post by Gannin on 2012-04-14
I've noticed it seems like more and more people using Linux are also using ATI / AMD cards, and it made me wonder what your guesses were on the future of xvba, the AMD video acceleration library.

Do you think AMD will eventually get around to completely opening xvba and more and more projects will start to adopt it?  Do you think vdpau will continue to be the main standard and AMD will continue stubbornly on, refusing to acknowledge it while use of xvba remains small?  Or do you think AMD will eventually give in and add vdpau support to their graphics cards?

---

### Post by Yellow Pasque on 2012-04-14
I don't see AMD embracing VDPAU on its fglrx/Catalyst Linux driver because of NIH (Not Invented Here) Syndrome. At least XBMC has made headway with using libxvba: [http://www.phoronix.com/scan.php?page=news_item&px=MTAyODU](http://www.phoronix.com/scan.php?page=news_item&px=MTAyODU)

AMD is (slowly) moving towards VDPAU in its open (Gallium3D) drivers. Progress would be much better if not for the lawyers being so worried about exposing DRM information in the UVD. As you can see, only basic formats are currently accelerated:
```
$ vdpauinfo 
display: :0.0   screen: 0
API version: 1
Information string: G3DVL VDPAU Driver Shared Library version 1.0

Video surface:

name   width height types
-------------------------------------------
420     8192  8192  NV12 YV12 

Decoder capabilities:

name               level macbs width height
-------------------------------------------
MPEG1                16 262144  8192  8192
MPEG2_SIMPLE         16 262144  8192  8192
MPEG2_MAIN           16 262144  8192  8192

```

---

