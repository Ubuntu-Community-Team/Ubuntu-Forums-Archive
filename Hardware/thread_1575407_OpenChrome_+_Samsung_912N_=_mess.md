---
title: "OpenChrome + Samsung 912N = mess"
date: 2010-09-15
forum: Hardware
---

### Post by maestrobwh1 on 2010-09-15
When this combination of items is used on my desktop, when kdm or gdm comes up, the screen is a complete mess:  off center, shaky lines, a shadow of the login dialog occurs on the left side.  I am unable to input any information via the mouse (it moves, but nothing clicks (like the pulldown).  The keybaord works so I can login, and the mess continues.

The monitor supports 1280x1024, but I can say that that is not the resolution being attempted, and it seems to me as if the refresh or the sync is not being detected properly.

I only have one item entered into an xorg.conf so that the openchrome driver is selected over vesa.

I would hate to think I have to mess around with modelines and such to get this to work.

The monitor works on one computer with Lucid and an Intel 950 GMA, and the computer with the OpenChrome card works with an old dell LCD monitor with a maximum resolution of 1024x768.

It seems everything works, except when the openchrome videocard is paired with the samsung...

Help?

---

### Post by maestrobwh1 on 2010-09-18
bump... anyone with a samsung 912N monitor or openchrome with similar issue or fix?

---

