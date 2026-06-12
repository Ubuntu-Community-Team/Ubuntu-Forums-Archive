---
title: "Hardware abstraction layer / dbus issue preventing desktop startup"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by sdbrogan on 2008-12-12
I've installed Ubuntu 8.10 from the alternate AMD64 CD. But the desktop won't start - I get a blank screen with a blinking cursor at the top left.  If I try to boot in recovery mode there are some error messages :-

Starting Avahi mDNS/DNS-SD Daemon avahi-daemon ... [FAIL]

then after that :-

Starting powernowd ... [OK]
Can't start Hardware abstraction layer - please ensure dbus is working

then I get an orange-brown screen with a pointer, but still no desktop, & no response to the mouse or keyboard.

I googled this & saw something about HAL & dbus starting concurrently when dbus should start first but I didn't really follow or know what to do about it (I'm new to Linux/Ubuntu).

I'd be very grateful if anyone could give me any advice on this.

---

### Post by sdbrogan on 2008-12-13
For the record, the problem seems to have been that no machine id had been generated for the uuid file - fixed with :

dbus-uuidgen > /var/lib/dbus/machine-id

Now HAL starts but the dsktop still hangs on startup - blank screen with pointer.

---

### Post by sdbrogan on 2009-03-20
Just to close this thread - the final problem was solved by changing the  boot parameters to 'noapic' &c.

---

