---
title: "xauth (.Xauthority) problems"
date: 2005-11-05
forum: General Help
---

### Post by themacmeister on 2005-11-05
Hi All,

I am using Ubuntu 5.10rc2 off the live/install DVD, and it is so riddled with bugs (on my machine) that I don't quite know where to begin.

The most problematic thing is my .Xauthority file, becomes corrupt on each startup. This severely limits my ability to launch any xwindows software with sudo. If I delete the file, cntrl-alt-backspace and restart X, the .Xauthority file is recreated and works perfectly for that session...

Can anyone help me with this... I have tried an init.d script that deletes the .Xauthority file, but this doesn't seem to work. There may be a command to use with xauth or xauthd that recreated the file, but I am unaware of this.

Any and all help appreciated,

themacmeister

---

### Post by Remmelas on 2005-11-05
are you using it from your hard drive then, or still using it from the live disc?  If from your hard drive, I have to ask, have you updated all of your software packages?

---

