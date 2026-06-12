---
title: "3D Acceleration for ATI Radeon X1200?"
date: 2010-01-30
forum: Hardware
---

### Post by Kazuki Mishima on 2010-01-30
Is 3D acceleration for my ATI Radeon X1200 chip planned for any point in the future? It kind of irks me that I can't use Google Earth or any nifty GNOME desktop effects.

---

### Post by Yellow Pasque on 2010-01-31
A Gallium3D driver is coming to bring OpenGL 2.x: [http://www.phoronix.com/scan.php?page=news_item&px=NzY4Ng](http://www.phoronix.com/scan.php?page=news_item&px=NzY4Ng)

However, you should be able to run Compiz with the current open-source drivers. Give more info and maybe we can help. Post output of:
```
glxinfo
compiz --replace
```

---

### Post by Kazuki Mishima on 2010-01-31
I found a replacement driver that works! I switched from the fglrx driver that was installed by default to a package I found in the repository called xserver-xorg-video-radeonhd. I had tried envyng and drivers from the catalyst website before. This was the first time I found something that really works.

Thanks for the advice.

---

### Post by Tethtibis on 2010-02-02
Ok, I downloaded that same package, now how to i switch from The pre-installed to the new one?

---

### Post by Kazuki Mishima on 2010-02-02
I think to do that I simply removed any packages with "fglrx" in the name.

---

