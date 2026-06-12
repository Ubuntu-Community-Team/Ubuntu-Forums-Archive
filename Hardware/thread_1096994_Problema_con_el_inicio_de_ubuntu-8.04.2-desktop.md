---
title: "Problema con el inicio de ubuntu-8.04.2-desktop"
date: 2009-03-15
forum: Hardware
---

### Post by Frolick on 2009-03-15
Buenas comunidad, tengo un problema con el inicio de ubuntu, al terminar el preloader queda en pantalla negra. Ahora yo tengo el monitor conectado por la placa de video que es una **Geforce FX5200 128mb** que creeria que es la que esta causando el problema, quisiera saber en que modo entrar y que comandos ejecutar para poder instalar los drivers antes que inicie ubuntu.
Desde ya Gracias :D !

---

### Post by josecuervo86 on 2009-03-15
No se te ve nada? Por que a mi me paso lo mismo apenas puse la placa, y justamente se ve asi porque no tiene los drivers. Pero yo podia ver algo, muy poco pero algo se veia, entonces a tientas me fui a Sistema -> Administración -> Controladores de hardware y ahi elegis el driver. Fijate si no podes aumentar el brillo desde la pantalla para que se vea algo ;)

---

### Post by Frolick on 2009-03-15
Josecuervo .. no no se ve nada .. anteriormente habia solucionado .. pero entrando en modo de simbolo de sistema .. y de ahi solucione.. pero ahora no me acuerdo los comandos que ejecute

---

### Post by Hei Ku on 2009-03-15
Proba apretando Ctrl+Alt+F1 y despues pone:

sudo dpkg-reconfigure -phigh xserver-xorg

---

