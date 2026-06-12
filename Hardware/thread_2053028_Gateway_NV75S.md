---
title: "Gateway NV75S"
date: 2012-09-04
forum: Hardware
---

### Post by ammw999 on 2012-09-04
I am haveing problems in ubuntu 11.04 with my sound everything works with the integrated speakers on my laptop but my headphones dont work at all i have treid adjusting settings unmuting i read other threads nothing works the oem driver for my laptop is realtek ac 97 but i cant find drivers for ubuntu right now ubuntu has intel hd audio installed for my laptop.

---

### Post by ammw999 on 2012-09-04
Bump Still need help

---

### Post by TREESofRIGHTEOUSNESS on 2012-09-23
I am not sure I can answer your question, but it is always worth a shot, and will help bump your post.
running lspci and posting the output (mainly the sound related info) could be helpful to getting it solved.  As well, you could try using Ubuntu 12.04.1 (the Newest version) as there are many problems that have been fixed, etc..  Secondly installing a secondary mixer ```
sudo apt-get install gnome-alsamixer
``` has helped me.  ((Enable Jack Sense))
Really I would try running a Live CD of the latest Ubuntu and checking your headphones FIRST.  If they work Hurray!!!!  If not go to the next step

---

