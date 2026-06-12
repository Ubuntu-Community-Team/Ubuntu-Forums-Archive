---
title: "problema con el disco extraíble"
date: 2011-01-02
forum: Hardware
---

### Post by liightmyfire on 2011-01-02
hola, si bien hasta ahora no había tenido problemas con esto, hoy intenté conectar un disco duro extraíble al USB y no solo no veo que se monte sino que creo que ni siquiera llega a iniciarse (quiero decir, se reinicia constantemente, supongo que es por eso que no se monta, pero en las otras computadoras no me pasa), me encantaría saber qué puede ser lo que pasa

---

### Post by alfplayer on 2011-01-03
Si se conecta a un hub USB, puede suceder que no esté recibiendo la cantidad suficiente de energía.

---

### Post by asterix77 on 2011-01-05
Debería postear la salida de lsusb con el disco externo conectado, para saber si lo reconoce al menos ubuntu.

Saludos

---

### Post by guillermolisi on 2011-01-05
> **alfplayer said:**
> Si se conecta a un hub USB, puede suceder que no esté recibiendo la cantidad suficiente de energía.
Coincido. Cuando el disco nunca termina de ponerse en regimen de trabajo generalmente es porque la corriente que entrega la salida USB esta por debajo de los valores requeridos.

Cada salida USB esta limitada a 500mA (0.5A), por eso algunos discos portatiles vienen con un cable que ocupa dos bocas USB (para recibir hasta 1A de corriente).

---

