---
title: "No puedo iniciar Ubuntu"
date: 2008-10-14
forum: Hardware
---

### Post by PeTTi on 2008-10-14
Tengo Ubuntu 8.04, y cuando quiero entrar, una vez que pongo el usuario y la pass se carga y me aparece una pantalla blanca que jamas desaparece, y cuando reinicio la pc desaparece esa pantalla blanca y se puede ver el escritorio, pero por menos de un segundo.. ya actualize los paquetes, reinstale Gnome y sigue igual.. :S

Gracias.

---

### Post by guisheca on 2008-10-14
A lo único que me suena eso es a un compiz tratando de ejecutarse donde no puede. Podrías darnos los datos de tu pc?? sobre todo la placa de video. Te cuento lo que pienso que puede ser, de alguna forma activaste los efectos de escritorio pero no tenés los controladores necesarios para tu placa de video, por lo tanto cuando cargan los efectos de escritorio se vuelve blanca la pantalla.
La próxima ves que intentes entrar, luego de poner tu usuario y contraseña y te salga la pantalla blanca, apretá ctrl+alt+F1, te va a aparecer una consola de textos, te va a pedir que te loguees nuevamente, luego de ello tipeá: metacity --replace. Luego de esto apretá ctrl+alt+F7, si mi teoría es correcta con eso tendrías que tener solucionado tu problema.
Saludos.

---

### Post by PeTTi on 2008-10-14
> **guisheca said:**
> A lo único que me suena eso es a un compiz tratando de ejecutarse donde no puede. Podrías darnos los datos de tu pc?? sobre todo la placa de video. Te cuento lo que pienso que puede ser, de alguna forma activaste los efectos de escritorio pero no tenés los controladores necesarios para tu placa de video, por lo tanto cuando cargan los efectos de escritorio se vuelve blanca la pantalla.
La próxima ves que intentes entrar, luego de poner tu usuario y contraseña y te salga la pantalla blanca, apretá ctrl+alt+F1, te va a aparecer una consola de textos, te va a pedir que te loguees nuevamente, luego de ello tipeá: metacity --replace. Luego de esto apretá ctrl+alt+F7, si mi teoría es correcta con eso tendrías que tener solucionado tu problema.
Saludos.
Mi Laptop es una Packardbell Easynote, y como la compre asi quedo, o sea no le agrege nada...
Y Hoy a la tarde intento lo que me decis. Gracias.-

---

### Post by PeTTi on 2008-10-14
> ctrl+alt+F1, te va a aparecer una consola de textos, te va a pedir que te loguees nuevamente, luego de ello tipeá: metacity --replace. Luego de esto apretá ctrl+alt+F7
Hice eso, y pongo en la terminal metacity --replace y me dice:
Error de gestor de ventanas: Unable to open X display.

---

### Post by PeTTi on 2008-10-15
Le instale KDE por la terminal y se pone la pantalla negra...
y cuando apreto alt+ctrl+f1 me dice:

kinit: name_to_deb_t (/dev/disk/by-uuid/2c9aa696y sigue...
kinit: trying to resume from /dev/disk/by-uuid/2c.... y sigue
kinit: No resume image, doing normal boot...

y luego me aparece para escribir en la terminal.

ahora entre otra vez e hice lo mismo y en una parte dice:
not starting K display manager (kdm); ir is not the dehaulr display manager.

---

### Post by Hei Ku on 2008-10-15
Pudiste entrar al entorno gráfico alguna vez?
No será un problema de drivers?

---

### Post by PeTTi on 2008-10-15
> **Hei Ku said:**
> Pudiste entrar al entorno gráfico alguna vez?
No será un problema de drivers?
Siempre pude entrar, la ultima vez fue el domingo pasado... y la apague bien

---

### Post by ADICTOALMAXIMO on 2009-04-15
Mmm

que podra ser

che che che

---

### Post by faktorqm on 2009-04-17
> **ADICTOALMAXIMO said:**
> Mmm

que podra ser

che che che

y... podra ser que la fecha del ultimo post es de 15 de octubre de 2008 y que estoy 99,99% seguro de que ya lo soluciono reinstalando o haciendo otra cosa o no se.... te parece?

---

