---
title: "ATI FAN Control con KDE"
date: 2008-10-26
forum: Hardware
---

### Post by Hei Ku on 2008-10-26
Para los grossos que tienen una ATI y usan KDE. :lolflag:

Hay un applet de Karamba que les permite ver la temperatura y controlar la velocidad del fan.

[http://www.kde-look.org/content/show.php/ATI+Fan+Control?content=91918](http://www.kde-look.org/content/show.php/ATI+Fan+Control?content=91918)

---

### Post by jpmorelli on 2008-10-26
Me alegro que por fin de una vez la gente que tiene ATI pueda usar su placa como corresponde. Ahora que nos toca a los que usamos nvidia, jaja ?

---

### Post by faktorqm on 2008-10-26
> **jmorelli said:**
> Ahora que nos toca a los que usamos nvidia, jaja ?

Yo la proxima placa que me compre (proximamente si Dios quiere) va a ser ATI. Con Nvidia no quiero saber mas nada, cuando liberen el driver volvera a estar en mi lista de preferencia. Salu2!

---

### Post by niko_3100 on 2008-10-27
que copado ese programita, loco los usuarios de nvidia tambien merecemos una cosa asi...

---

### Post by Hei Ku on 2008-10-27
Para los que tienen curiosidad, el applet usa estos 3 comandos:

1) aticonfig --adapter=0 --od-gettemperature
2) aticonfig --pplib-cmd "get fanspeed 0"
3) aticonfig --pplib-cmd "set fanspeed 0 40" (para una velocidad del 40%)

---

