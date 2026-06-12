---
title: "video problem xfx nvidia mx4000"
date: 2005-07-02
forum: Hardware &amp; Laptops
---

### Post by bajabug72 on 2005-07-02
ive got everything working with ubuntu but my video resolution is stuck at 640x480. :mad:   it was fine at 1024x768 when i first installed but ubuntu didnt like my network card, so i swapped it and now its stuck at 640x480.  i looked at /etc/X11/xorg.conf because it was mentioned in other posts w/ the same problem and it lists everything from 640x480 to 1280x1024.  whats my problem???  im using GNOME but may be running KDE in the near future.  dunno if it matters, but its there

thanks in advance, Jon

---

### Post by frodon on 2005-07-03
ok, don't worry it's a common problem to have resolution stuck at 640x480 or higher, just post here your xorg.conf : ```
gedit /etc/X11/xorg.conf
```
It's totally independant of gnome.

---

