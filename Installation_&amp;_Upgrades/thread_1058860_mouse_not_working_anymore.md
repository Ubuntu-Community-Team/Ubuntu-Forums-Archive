---
title: "mouse not working anymore"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2009-02-03
I have an eeepc 1000. It comes with a touchpad, which is now my savior.

I used to use Logitech Bluetooth mouse or a wireless optical mouse.

A few days ago I installed eee-control-tray 0.8.3.
Unfortunately with that both of my mice are not working anymore:

Bluetooth mouse connect / disconnect all the time and no mouse movement/mouse button work. I thought only bluetooth mouse got mad with the eee-control, but also the wireless mouse shows no reaction.

In /var/log/messages I see the wireless mouse, when I attache the dongle.


How can I get my mouse back?

bye

R.

---

### Post by khelben1979 on 2009-02-03
I think that maybe it's a good thing to experiment with different versions of that program.

I found [this]("http://forum.eeeuser.com/viewtopic.php?pid=496755") during a recent google search.

You can always try to uninstall the program also to see if it helps:

sudo apt-get remove eee-control-tray
(adding the purge parameter might also be a good thing)

---

### Post by ELMIT on 2009-02-03
I used apt-get remove eee-control, but it did not give me my mouse back :-(

Any other ideas?

bye

R.

---

