---
title: "Ubuntu 13.10: Fatal: Module ndiswrapper not found."
date: 2014-03-05
forum: Hardware
---

### Post by madbyte on 2014-03-05
Buenas,

Tengo el fatídico Realtek 8187, venía zafando con el ndiswrapper y andaba perfecto, pero desde que salío la 13 al cargar con modprobe me tira:

FATAL: Module ndiswrapper not found.

Tuve que cambiar la PC de lugar y el driver rtl8187 es muy inestable, se desconecta, cambia el comportamiento dependiendo de la intensidad de la señal, etc, etc, etc y me tiene los h..... por el piso...
La versión que instalé del ndiswrapper es la disponible desde el Synaptic, 1.58-2 y lo que encontré buscando no me deja en claro la solución (Posible incompatibilidad con mi kernel pae?).

Alguna ayuda o comentario al respecto?

Muchas gracias.

---

### Post by guillermolisi on 2014-03-15
> **madbyte said:**
> Buenas,

Tengo el fatídico Realtek 8187, venía zafando con el ndiswrapper y andaba perfecto, pero desde que salío la 13 al cargar con modprobe me tira:

FATAL: Module ndiswrapper not found.

Tuve que cambiar la PC de lugar y el driver rtl8187 es muy inestable, se desconecta, cambia el comportamiento dependiendo de la intensidad de la señal, etc, etc, etc y me tiene los h..... por el piso...
La versión que instalé del ndiswrapper es la disponible desde el Synaptic, 1.58-2 y lo que encontré buscando no me deja en claro la solución (Posible incompatibilidad con mi kernel pae?).

Alguna ayuda o comentario al respecto?

Muchas gracias.

Proba de iniciar la maquina en modo Live con una imagen de la beta de Ubuntu 14.04 y fijate como reconoce al adaptador de red.
Si lo reconoce al toque, sera cuestion de hacer el cambio de version en Abril y te desligas de usar ndiswrapper o, si aceptas lo que significa usar una version beta, hacer el cambio de version ahora (con los riesgos y "molestias" que ello implica).

---

### Post by madbyte on 2014-03-20
Espero que sea justo al revés, que pueda seguir usando ndiswrapper y no el driver rtl8187. Desde que empecé con Ubuntu 9.10 hasta la 13.10 que tengo problemas con el rtl8187. La única manera que pude lograr una conexión descente fue gracias al ndiswrapper pero hasta antes de estas dos últimas versiones (13.04 y 13.10) que me tira el error al intentar cargarlo. Anda tan mal el driver rtl8187 que me siento como cuando empece a usar la 9.10 por eso si me guío por la experiencia con esto no creo que el rtl8187 funcione una maravilla en la 14.04.

Saludos

---

