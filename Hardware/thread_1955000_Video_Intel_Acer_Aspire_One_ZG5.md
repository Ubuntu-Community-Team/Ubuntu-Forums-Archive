---
title: "Video Intel Acer Aspire One ZG5"
date: 2012-04-09
forum: Hardware
---

### Post by fedecape on 2012-04-09
Muy buenas,

Acabo de instalar Ubuntu 11.10 en la netbook Acer Aspire One ZG5 y en la información de sistema, pestaña de video obtengo esto. Parecería que la placa de video no esta funcionando..
Les adjunto capturas.

Por qué será? Como puedo hacer para que Ubuntu verifique e instale? Es un driver común, me imagino.

saludos

---

### Post by gmunioz on 2012-04-09
El que informe desconocido, no significa que el driver no este funcionando, tienes una tarjeta gráfica Intel, los drivers son libres y estan incorporados al kernel.
Abre una terminal y ejecuta:
sudo su
lspci
lsusb
Y tendrás un listado de todos los componentes, reconocidos y funcionantes en el sistema.

---

