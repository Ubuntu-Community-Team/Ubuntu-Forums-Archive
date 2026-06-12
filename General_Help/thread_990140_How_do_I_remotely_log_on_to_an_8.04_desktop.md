---
title: "How do I remotely log on to an 8.04 desktop?"
date: 2008-11-22
forum: General Help
---

### Post by jamieh on 2008-11-22
I know how to SSH to by Ubuntu 8.04 desktop, but how to I remotely log on so I can actually see and control the deskop as if I were logged onto the computer?

The computer I want to connect from is a Mac Pro with OS X 10.5.5.

Thanks

---

### Post by Peter09 on 2008-11-22
use FreeNX here

[http://packages.debianbase.de/stable/](http://packages.debianbase.de/stable/)

this will give you the ability to have a remote desktop on  a machine (even if there is no user logged in)

Its easy to use and configure - give it a go.

---

### Post by mihaiv on 2008-11-22
Enable remote desktop in ubuntu (System->Preferences->Remote Desktop). Search for a VNC Mac client (like [cotvnc]("http://sourceforge.net/projects/cotvnc")).

---

### Post by jamieh on 2008-11-22
> **Peter09 said:**
> use FreeNX here

[http://packages.debianbase.de/stable/](http://packages.debianbase.de/stable/)

this will give you the ability to have a remote desktop on  a machine (even if there is no user logged in)

Its easy to use and configure - give it a go.

Is there an apt-get command to download this? It wasn't in the link as far as I could tell.
Thanks

---

### Post by jamieh on 2008-11-22
Thank you sir :D :D

---

### Post by jamieh on 2008-11-22
Stupid question - If I close the X11 window, all of the running apps say open, right?

---

### Post by Peter09 on 2008-11-22
If you are using FreeNX you have the option to leave the session running or terminate it.

---

