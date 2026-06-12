---
title: "evo n610c tv out"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by thefamousnomo on 2007-04-17
hello people

using 6.06lts on my compaq evo n610c with not very many issues. Radeon 7500 Mobility chipset seems to render strangeness on dialogue box buttons but i can live with it!

has anybody had any luck with the s-video tv-out? i have searched the wiki and only found nvidia chipset help for this... how can i get this running?

thanks

---

### Post by thefamousnomo on 2007-04-18
nobody any joy with this... should i configure x again with the tv plugged in...?

---

### Post by thefamousnomo on 2007-04-19
* bump *

come on guys, somebody must be using this... any info with configuring x for dual using ati would be really appreciated.

---

### Post by thefamousnomo on 2007-04-24
*
b
u
m
p
*

c'mon folks..... no-one?

---

### Post by thefamousnomo on 2007-04-26
gutted

bit of a let down... :(

---

### Post by enopepsoo on 2008-05-04
BUMP.  I'm on the same setup(compaq n610c) with 8.04.

lspci says my video card is:
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

```

And there is no proprietary driver installed (I'm not sure if ATI requires these).

---

### Post by enopepsoo on 2008-05-05
I am getting there.  I found something on this page:

[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

When I run
```
xrandr --output S-video --set load_detection 1
``` I get a monochrome representation of the top left corner of my display.  Progess.

edit: Looking at launchpad, it seems that this may be an unresolved bug,

---

