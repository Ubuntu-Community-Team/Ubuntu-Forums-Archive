---
title: "No tty sessions screen"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by charles.g.moore on 2006-12-07
I do a ctrl+alt+f1 or f2,f3 etc and the screen goes blank, it is a hp dv6000t running 6.06

any ideas???

If i ctr+alt+f7 it does kick me back into X...

---

### Post by K.Mandla on 2006-12-07
Look inside /etc/inittab, and make sure the tty commands aren't commented out. That might prevent them from spawning properly. That's the first thing that comes to mind, anyways.

---

### Post by charles.g.moore on 2006-12-08
This is whats in there...

# Format:
#  <id>:<runlevels>:<action>:<process>
#
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

---

