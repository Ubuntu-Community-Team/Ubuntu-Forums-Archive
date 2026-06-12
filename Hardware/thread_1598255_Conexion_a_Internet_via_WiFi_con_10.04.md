---
title: "Conexion a Internet via WiFi con 10.04"
date: 2010-10-16
forum: Hardware
---

### Post by MCWandy on 2010-10-16
Yo ya no se a que foro preguntar, nadie contesta. Alguien que pueda ayudar a tener internet? Supuestamente está todo bien pero no entra internet, dice servidor no encontrado.
Es via wifi. Y la versión del Ubuntu es la 10.04
Gracias.:(

---

### Post by hectorivand on 2010-10-16
> **MCWandy said:**
> Yo ya no se a que foro preguntar, nadie contesta. Alguien que pueda ayudar a tener internet? Supuestamente está todo bien pero no entra internet, dice servidor no encontrado.
Es via wifi. Y la versión del Ubuntu es la 10.04
Gracias.:(

Hola, Bienvenido.: Pasanos alguna data de tu equipo.

Tu maquina.

¿Que placa Wifi tiene?

Si es una notebook, el resultado del comando lsusb

si es una placa wifi PC lspci

Saludos
Nacho

---

### Post by asterix77 on 2010-10-16
¿a que te refieres cuando dices que "supuestamente está todo bien?

Supongo que tal vez pueda ser que te conectas a tu acces point, pero no puedes navegar.


Sería bueno que aparte de lo que te arrojan los comandos "sudo lspci" y "sudo lsusb", mostraras que te arroja el comando "ifconfig", tanto con la wifi apagada y encendida (y conectada al ap si es que te puedes conectar.


a) Algunos proveedores de internet usan pppoe sobre wifi, por lo que te puedes asociar al ap, pero no puedes navegar. En tal caso debes correr en consola pppoeconf y sguir las indicaciones.

b) Deberias reviasar la configuración de tu router, tal vez no está confiurado de la forma correcta.


Saludos

---

