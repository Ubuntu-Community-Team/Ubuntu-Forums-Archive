---
title: "[SOLVED] Mouse bluetooth en Xubuntu"
date: 2008-09-25
forum: Hardware
---

### Post by santiagoward2000 on 2008-09-25
Hola!
Cambié la laptop (tengo una hermosa Dell XPS m1330) y le metí Xubuntu (obvio). El tema es que vino con un mouse bluetooth, y no encuentro cómo configurarlo. ¿Alguien tiene algún buen tuto para pasarme?
Gracias!

---

### Post by niko_3100 on 2008-09-25
Tremenda maquina para xubuntu? te debe de encantar jeje, ahora mi pregunta es no te reconoce el mouse ni siquiera para usarlo? o queres configurar la velocidad de desplazamiento etc etc..

---

### Post by santiagoward2000 on 2008-09-25
> **niko_3100 said:**
> Tremenda maquina para xubuntu? te debe de encantar

¿Te parece? Jeje!

> **niko_3100 said:**
> jeje, ahora mi pregunta es no te reconoce el mouse ni siquiera para usarlo? o queres configurar la velocidad de desplazamiento etc etc..

Así cómo está no lo reconoce, pero no configuré nada. En Windows tuve que buscarlo para agregarlo, supongo que acá tendré que hacer algo así, pero no sé cómo.
Gracias!

---

### Post by User21 on 2008-09-25
Antes que nada, deberias tener soporte BlueTooth. Pegate una mirada a esto:
[http://linuxchronicles.wordpress.com/2008/06/20/bluetooth-in-xubuntu-804/](http://linuxchronicles.wordpress.com/2008/06/20/bluetooth-in-xubuntu-804/)
Quizas sirvá para el arranque... Esperamos novedades.

---

### Post by santiagoward2000 on 2008-09-25
> **User21 said:**
> Antes que nada, deberias tener soporte BlueTooth. Pegate una mirada a esto:
[http://linuxchronicles.wordpress.com/2008/06/20/bluetooth-in-xubuntu-804/](http://linuxchronicles.wordpress.com/2008/06/20/bluetooth-in-xubuntu-804/)
Quizas sirvá para el arranque... Esperamos novedades.

GRANDE! ANDA!!
Todavía no hice todo, tengo que configurar para que ande cuando prendo la máquina, pero anda!
Gracias!

---

### Post by User21 on 2008-09-25
Snif! Hoy hice feliz a otro ubuntero... Que fabulosa comunidad, no? :D

---

### Post by santiagoward2000 on 2008-09-28
Recién me puse a seguir todos los pasos para que detecte el mouse cuando preondo la máquina pero no me anduvo. Si corro:
```
sudo hidd --search
```
me encuentra y conecta el mouse, pero tengo que correrlo cada vez que prendo.
¿Alguna idea?

---

### Post by kowal on 2008-09-28
> **santiagoward2000 said:**
> Recién me puse a seguir todos los pasos para que detecte el mouse cuando preondo la máquina pero no me anduvo. Si corro:
```
sudo hidd --search
```
me encuentra y conecta el mouse, pero tengo que correrlo cada vez que prendo.
¿Alguna idea?

Podés:

- Agregar el comando al final del archivo /home/tu_usuario/.bashrc

- Crear un script para que se ejecute solo en /etc/init.d/

- Agregar el comando al final del archivo /etc/rc.local

- Etc..

---

### Post by santiagoward2000 on 2008-09-28
> **kowal said:**
> Podés:

- Agregar el comando al final del archivo /home/tu_usuario/.bashrc

- Crear un script para que se ejecute solo en /etc/init.d/

- Agregar el comando al final del archivo /etc/rc.local

- Etc..

Si, la pensé (y por ahora lo tengo así). El tema es que además de correr el comando tengo que poner el mouse en modo "encuentrame" para que **hidd --search** lo encuentre. La idea era que la máquina lo conecte apenas lo prendo.
Saludos!

---

### Post by User21 on 2008-09-29
Y si agregas el comando en Sistema > Preferencias > Sesiones ?
Espero no haber dicho una burrada ¬_¬  Ah, si, fue una burrada. Estás en Xubuntu! JAJAJJA xD

---

### Post by santiagoward2000 on 2008-09-29
> **User21 said:**
> Y si agregas el comando en Sistema > Preferencias > Sesiones ?
Espero no haber dicho una burrada ¬_¬  Ah, si, fue una burrada. Estás en Xubuntu! JAJAJJA xD

JAJAJA! Igual la idea está. Yo lo puse en Autostarted Applications, pero cuando prendo la máquina tengo que prender el mouse y después mantener un botón que lo pone a mandar señal para que otro lo encuentre (como los celus). Cuando entro a Windows se conecta solo, sin que yo tenga que apretar eso.
Igual es un capricho, si tengo que hacerlo cada vez y correr el comando tampoco es tan grave :)

---

### Post by santiagoward2000 on 2008-10-14
Bueno, al final me cansó eso de tener que buscarlo cada vez que prendo la máquina, y terminé usando el bluez-gnome para que lo detecte y lo acepte solo. Me imagino que debe haber alguna otra forma, pero ya fue!

---

