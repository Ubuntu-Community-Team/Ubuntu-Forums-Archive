---
title: "Sound stops working after suspend"
date: 2009-06-14
forum: Hardware
---

### Post by SpoookyKid on 2009-06-14
I have an older Gateway laptop running both Ubuntu Jaunty and Xubuntu alternatively.  When my laptop goes into suspend, either from closing the lid or as a power save option, and I return to using it, the sound no longer works.  This includes in-browser, as well as globally with programs and system noises.

Any ideas?

---

### Post by scrooge_74 on 2009-06-16
The old suspend problems, try restarting the sound deamons, from a console type:

sudo sh /etc/init.d/alsa-utils stop
sudo sh /etc/init.d/alsa-utils start

See if that fixes it

---

### Post by SpoookyKid on 2009-06-16
I tried it, it didn't work.  I was also told to add that this happens every time my computer suspends.

---

### Post by scrooge_74 on 2009-06-16
You should work then on your suspend and hibernate since the problems are there. Linux still has some problems in that area, I dont suspend any of my laptops, they always come back with some quirks, at least hibernation is working for me on this old nx6110

---

