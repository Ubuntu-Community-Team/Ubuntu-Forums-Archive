---
title: "Configurar el DHCP ubuntu 9.04"
date: 2009-06-11
forum: Instalación y Actualización
---

### Post by ruizse01 on 2009-06-11
Hola.
Yo tengo mi compu instalada con xp y ubuntu 9.04. En 2 particiones diferentes.
Me conectaba a internet en xp marcando la conexion a speedy. En ubuntu configure el ppoeconfig
y de maravilla los 2.
Bien ahora, compre un router para armar una red. El modem se encarga de la conxexion.
Xp toma ip mediante dhcp. Pero en ubuntu que tengo que cambiar para que salga a internet por el router.
En xp tilde en iexplorer la opcion no marcar nunca una conexion.
En ubuntu como hago para desactivar el pon dsl-provider y activar el DHCP.
Bueno si sabes algo te agradesco.
Saludos
Sergio

---

### Post by moreback on 2009-06-12
Borra todas las configs que hubieras hecho con el pppoeconf y configura tu nueva red cableada desde el icono del Network-Manager en tu panel.

---

### Post by Iced_R on 2009-06-12
Network Manager, en la conexión por defecto (auto eth0) marca la opción que te pida una IP por DHCP. Deberías volver a habilitarla y listo.

Saludos.

---

