---
title: "Need Help"
date: 2005-11-19
forum: General Help
---

### Post by Drifter on 2005-11-19
I have XDVDShrink installed now, it works, but I can't get it to burn dvd's.  Its says no readable media etc.  I can play movie's just fine in the dvd writer.  What to do to get it to rip the movie.

---

### Post by manicka on 2005-11-19
File-->Configure

Check that the reader and writer device is correct. Should be something like /dev/dvd

Once that is working I would recommend using xdvdshrink to create an iso image (check - Create iso image only) and then burn the resulting iso image with nautilus or k3b instead of xdvdshrink itself, which during my testing was very slow to burn dvd's.

---

