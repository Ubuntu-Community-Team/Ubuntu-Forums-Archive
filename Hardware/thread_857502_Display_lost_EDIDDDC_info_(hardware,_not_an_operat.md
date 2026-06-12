---
title: "Display lost EDID/DDC info (hardware, not an operating system problem I believe)"
date: 2008-07-12
forum: Hardware
---

### Post by el_es on 2008-07-12
Hi,

the problem I am about to tell, is NOT Ubuntu related generally, only that it started there and Windows does this too :(

This is my laptop : [https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire3023](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire3023)
It is already 3 years old machine, that must be said.

Some two-three weeks ago, happened that I needed to do a SAK (alt-sysrq-S,U,B) because something froze and I could not go back to system normally.

On reboot, I've noticed, that the screen looks weird.

Laptop's native resolution is 1280x800 (panoramic). However, it now displays 1024x768 screen stuck to upper-left corner, and the remaining space of the monitor is last column to right and last row to bottom repeated.

In ascii-art it would be:
<pre>
<---------------1280----------->
+--------1024-----------+-------+
|    ^                  |       |
7    |                  |       |
6    |                  |       |
8    8                  |       |
|    0                  |       |
|    0                  |       |
+--  |   ---------------+-------+
|    v                  |       |
+-----------------------+-------+
</pre>
The physical size is 15", resolution 1280x800,
however only 1024x768 is displayed now, the rest is the last column of the screen, repeated, and the last row of the screen also repeated. I can see it when I move my mouse to the edge of the screen, the rubbish on the right or bottom changes where the cursor is...

In /var/log/XOrg.0.log I see, that the X server detects the monitor as 1024x768 native resolution... instead of the one that should appear.

The usplash, where the native resolution is encoded, also displays itself this way. the text console as well. Here I attach my XOrg.0.log (cut into pieces, hope I did it right ;)

If anybody could help, would be fantastic... This laptop is living long enough to be replaced already, I am considering a Dell this time ;) but I wonder if anything can be done. 

I will post my xorg.conf in the next posting (out of attachment space...)> [QUOTE][/QUOTE]

---

### Post by el_es on 2008-07-12
Here is the xorg.conf and the last part of XOrg.0.log.

Please tell me, what can I post more to help ?

---

