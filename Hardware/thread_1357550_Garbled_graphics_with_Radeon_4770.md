---
title: "Garbled graphics with Radeon 4770"
date: 2009-12-17
forum: Hardware
---

### Post by BuffaloX on 2009-12-17
I tried both open source and proprietary driver, and I've tried the newest AMD driver too.

In Gnome the problem only appear in the appearance settings, but I wanted to try Kubuntu, and it was all over the place.

Looks a bit like an attempt to use non existing RAM.
I don't see this error anywhere in Win XP, games, any of my Gnome apps.
I tried to run a self-diagnostic in the Win-XP driver OC options, but I have not ocverclocked anything on this system.

Anyone have an idea if this is a driver bug or hardware error.

---

### Post by philhughes on 2009-12-19
I filed a bug report about this:

[https://bugs.launchpad.net/bugs/440544](https://bugs.launchpad.net/bugs/440544)

Using the fglrx drivers on Ubuntu 9.10, the only place I see it is in the Appearance settings as in your screen shot. Using the radeon drivers it's much worse, and from memory seemed to affect KDE apps more than Gnome apps.

---

### Post by BuffaloX on 2009-12-19
Thanks philhughes,
I was just about to bump this.
It's clearly a driver problem then.

---

### Post by philhughes on 2009-12-31
See the launchpad thread for a workaround.

---

### Post by BuffaloX on 2010-01-01
Thanks, it seems this solution is for the open source driver.
I'm currently using fglrx.

---

