---
title: "Wow fps bad"
date: 2008-08-31
forum: General Help
---

### Post by enzodad on 2008-08-31
i just finished installing wow and gecko. plays nice but the FPS is 9 or less i tried to drop all vidoe options.. is there somethig else i can do?

---

### Post by tjwoosta on 2008-08-31
are you currently using compiz (desktop effects) ?

if so, you could get a much better framerate by switching to metacity

do this to switch to metacity  (use alt-f2 not the terminal)
```
metacity --replace
```

do this to switch back to compiz  (again use alt-f2 not the termial)
```
compiz --replace
```

---

### Post by werries on 2008-08-31
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

The registry edit and config edits REALLY help with the framerate.

And if you're using an ATI card and experience flickering, you have to turn off compiz desktop effects.

---

### Post by enzodad on 2008-09-01
I did that replace thingy and nothing changed for FPS :(

---

### Post by werries on 2008-09-03
try my solution. if you have an ATI graphics card, you CANNOT use compiz while playing WoW. Right click on desktop, hit change background, then go to Visual Effects and change them to none. you can turn em back on when you want to play WoW.

This is because the ATI proprietary drivers that are required for 3D acceleration are not compatible with compiz, dropping to a lower level of acceration and requiring the card to work harder, making any other use of it much much slower.

---

