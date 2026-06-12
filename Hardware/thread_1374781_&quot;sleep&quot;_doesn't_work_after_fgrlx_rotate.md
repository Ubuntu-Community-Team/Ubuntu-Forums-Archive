---
title: "&quot;sleep&quot; doesn't work after fgrlx rotate"
date: 2010-01-07
forum: Hardware
---

### Post by dyslexia on 2010-01-07
ATI Radeon 3200 in an HP Touchsmart TX2

The fglrx driver allows the screen to rotate fine... but after a rotation has been done, "sleep" mode doesn't work, even if the screen is restored to it's original orientation.  Instead, the screen goes into "dark but lit" mode, and will not respond further, fan stays on.

I've tried this with an "almost vanilla" 32 bit installation, so I don't think it's my Ubuntu mods that are causing the probem,

The xorg-xserver-video-radeon driver running on the live cd works perfectly, however.

Updating fglrx to version 9.12 doesn't work either... 9.12 garbles the screen after rotate, still dies on "suspend".

This must be a common bug, but I don't see any information concerning it elsewhere, or mention of it in the 'rotation' discussion.   Am I missing something?

---

### Post by dyslexia on 2010-01-11
Some progress... selectiing 'xterm session' from gdm (runs twm, I suppose) allows 'sleep' after a rotation is done with fglrx.

So the problem has something do with the Gnome window manager + fglrx?

...Will experiment with this further.

---

### Post by dyslexia on 2010-01-11
"gnome failsafe" works... looks like this has something to do with gnome-power-managment daemon..

this should work for me now...

Just have to keep on checking  /proc/acpi/battery/BAT0/state manually... hohum... probably someone has a little non-gnome widget out there that will do it too...

---

### Post by dyslexia on 2010-01-11
Ah, there, the little battery widget is showing depletion.... good.

still need to write a little shell script that checks if the lid is down for more that one minute / do emergency poweroff... (so the laptop doesn't get fried...)

---

