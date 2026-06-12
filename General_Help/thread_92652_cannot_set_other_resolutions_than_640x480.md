---
title: "cannot set other resolutions than 640x480"
date: 2005-11-20
forum: General Help
---

### Post by chris_wong on 2005-11-20
I have a daewoo 15" x511 screen with maximum resolution of 1024*768.
The problem is, that there are no other options than 640*480.
I think that it might be caused by the fact, that ubuntu automatically tries to use 24 bit color depth, while this monitor only supports 16 bit, but i don't know. tried changing the default color depth and ctrl+alt+backspace but it didn't work.

Can anyone help me?

---

### Post by Chris180775 on 2005-11-20
I'm not an expert but type to the console:

sudo dpkg-reconfigure xserver-xorg
Password: your password

I resolved the same problem.

---

