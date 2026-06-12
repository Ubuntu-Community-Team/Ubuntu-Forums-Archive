---
title: "Problema con Tv-Out ATI y kubuntu 9.04"
date: 2009-05-05
forum: Hardware
---

### Post by Misterioso_Gitano on 2009-05-05
Hola como andan?

Al fin logre q mi ubuntu no se reinicie me gustaria saber si puedo hacerlo funcionar desde la salida de tv...
Por ejemplo cuando prendo la pc funciona todo desde la tele pero cuando inicia kdm o mejor dicho el servidor X, la pantalla de la tv vuelve a verse azul y no hay señal, pero si voy a la primer tty (ctr + alt + F1) vuelve a tener señal...
Intente con los pasos de :
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://wiki.archlinux.org/index.php/ATI](http://wiki.archlinux.org/index.php/ATI)
[http://www.x.org/wiki/radeonTV](http://www.x.org/wiki/radeonTV)
Para habilitarlo estatica y dinamicamente pero no funciona...

Alguno sabe como configurarlo? muchas gracias!

---

### Post by dirty fingers on 2009-05-05
que tipo de conexión estas usando de la placa a la tv ?

¿
c-video
s-video
cvi
dvi
vga
 ?

---

### Post by Misterioso_Gitano on 2009-05-05
S-video

---

### Post by Misterioso_Gitano on 2009-05-05
> **dirty fingers said:**
> que tipo de conexión estas usando de la placa a la tv ?

¿
c-video
s-video
cvi
dvi
vga
 ?

s-video ^^

---

### Post by dirty fingers on 2009-05-05
Según como se setea la placa los mismos pines cumplen distinta función en algunas placas. así que seguro la tuya es así y por eso ves imagen azul. Le estas errando al seteo de la salida.
En nvidia se setea así, en ati ni idea, pero con probar si es igual que no perdes nada. [http://ubuntuforums.org/showthread.php?t=1146808](http://ubuntuforums.org/showthread.php?t=1146808)

---

### Post by Hei Ku on 2009-05-05
Como tenes configurado el xorg.conf?

Probaste usar xrandr?

---

