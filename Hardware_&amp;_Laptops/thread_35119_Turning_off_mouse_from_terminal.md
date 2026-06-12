---
title: "Turning off mouse from terminal"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by garfield on 2005-05-17
Hi,
Does anybody know how to turn off mouse (ps/2) from terminal and turn it back?
I need this to not turn on display when it is suspend.
tnx! bye.

sorry for bad english :(

---

### Post by nad on 2005-05-17
I'm not sure you can do this. The mouse in an X server is controlled by the server. In order to stop the mouse, you have to shut down the X server displaying your apps. I assume that what you wish to do is to have your X apps un-suspend where you left them, in which case this is not an option.

If you were running only command line apps, you could just stop gpm.

---

### Post by garfield on 2005-05-18
Or maybe its option in monitor suspend to not turn on when mouse is active?

---

