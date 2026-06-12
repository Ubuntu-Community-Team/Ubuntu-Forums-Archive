---
title: "Logitech itouch strangeness"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by Pete051 on 2005-09-08
I've been trying for a while to get my euro  symbol to work on my logitech itouch keyboard trying various combinations of keyboard layouts/models. Now this one was bought in Holland so it seems safe to assume it's a us english international W/ISO 9995-3 or maybe even a english international (with dead keys) maybe even a english international W/ISO 9995-3 (eliminate dead keys) it seemed unlikely but even a us english. Now some of these combinations will give me a euro symbol (right alt 5) but they also give me a double quote that looks like an umlaut and the single quote could be an accent but whatever they are they're useless for programming. Other combinations give me normal quotes but no euro symbol but none that I've found give me both. has anybody else found a solution to this?
Thanks 
Pete

---

### Post by Brent Dax on 2005-09-08
[QUOTE=Pete051]I've been trying for a while to get my euro  symbol to work on my logitech itouch keyboard trying various combinations of keyboard layouts/models.[/QUOTE]

As a last resort, you could pick a US English layout and use xmodmap to manually map AltGr+5 to the Euro symbol.  If you create the .Xmodmap file in your home directory and then log out and back in, Gnome will see the file and ask if it should load it; simply select "yes".  Of course, this will only work in X...

---

