---
title: "Remote controller - keymaps, event type, scancode"
date: 2014-12-09
forum: Hardware
---

### Post by tonymihajlovic on 2014-12-09
Hi!


I was trying to make my TV remote controller fully functional trough lirc, but I find out some problems. I have Leadtek Winfast TV2000 Global and right after I install drivers for it some of buttons (on rc) starts working with some predefined functions. I have problem with one of those functions. SLEEP button starts hibernate-sleep and it's on very nice spot on remote controller so I hit it by accident frequently. Where is the file that define this predefined functions for remote controller? It's not lirc.


Sry for bad English. ( :

---

### Post by tonymihajlovic on 2014-12-10
I figure it out...


There were no predefined key functions. Linux see some keys on remote controller as multimedia keyboard keys (SLEEP, VOLUME UP/DOWN,...). There are two solutions:


1. Delete any row with SLEEP in:
/usr/share/X11/xkb/keycodes/evdev


or


2. Change name of SLEEP button in:
/etc/rc_keymaps/winfast

---

