---
title: "Killing Screenlets daemon"
date: 2008-09-10
forum: General Help
---

### Post by pwaugh on 2008-09-10
Hey,

Tried screenlets, and didn't like/need it, but I can't get rid of it.  There is still the daemon running an icon in the upper panel.

I did this:

sudo apt-get remove --purge screenlets

and then rebooted, but it is still there.

Also, what is the correct way to get something to run on boot?

Patrick

---

### Post by frankleeee on 2008-09-10
If you installed with apt-get run sudo apt-get remove (program name) or look in synaptic and remove it there. The purge may have only removed the screenlets themselves not the program.

---

