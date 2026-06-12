---
title: "Upgrade and lost keyboard config"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by telefono on 2009-11-05
Hi there! ):P 

i recently upgraded to 9.10, and i lost all the configuration of my keyboard:

when i press the apostrophe, this return ´ and +shift ¨

in 9.04 i changed the [B]/etc/X11/xkb/symbols/us

with this:[/B]line 76:     key  { [     grave, asciitilde,    dead_grave,       dead_tilde ] };
line 106:    key  { [apostrophe,   quotedbl,    dead_acute,   dead_diaeresis ] };

but where should be this config file in the 9.10? i cant find it : ((

really thanks! 

pd: i love the new ubuntu : D

---

### Post by telefono on 2009-11-05
I found the file : DD

This now are in **/usr/share/X11/xkb/symbols**/

gooooooood luck!

---

### Post by telefono on 2010-04-30
This solves my lifes trougth every ubuntu version:

[http://gepatino.blogspot.com/2007/10/teclado-en-ingls-caracteres-acentuados.html](http://gepatino.blogspot.com/2007/10/teclado-en-ingls-caracteres-acentuados.html)

---

