---
title: "Reconfigurar Adsl"
date: 2008-12-16
forum: Hardware
---

### Post by deambulante69 on 2008-12-16
Qué tal, 
este es mi primer mensaje en el foro, pero no el último y esperemos que próximamente pueda ser yo el que aporte. sin embargo ahora les escribo por un problema de conexión que estoy teniendo.

les paso a contar:
en mi casa me conecto con Arnet Adsl (modem usb amigo) y a la hora de configurar la conexión no tuve mayores problemas, siempre teniendo que ejecutar, a la hora de conectarme los siguientes comandos:
> sudo modprobe br2684
sudo br2684ctl -c 0 -b -a 0.33
sudo ifconfig nas0 up
sudo pppoe-start

sin embargo, cuando me voy de casa, suelo utilizar la placa wifi, y para ello instale el WiCD, pudiendome conectar sin problemas.

El problema fue cuando despues de 1 semana quise conectar la computadora de nuevo a la conexion ADSL de Arnet. Ejecute loscomandos como solia hacerlo, luego del pppoe-start recibi el Connected! que mas de una vez me saco una sonrisa, sin embargo, al abrir el firefox o el gestor de actualizaciones, seguia desconectado. probe poniendo los dns de arnet y no hubo caso, tambien incorporando la interfaz nas0 al Wicd, pero tampoco.

a alguien se le ocurre que puede ser? o en su defecto, como hacer para reinstalar la conexion adsl?

muchas gracias

(uso intrepid ibex)

---

### Post by deafters on 2008-12-17
> **deambulante69 said:**
> Qué tal, 
este es mi primer mensaje en el foro, pero no el último y esperemos que próximamente pueda ser yo el que aporte. sin embargo ahora les escribo por un problema de conexión que estoy teniendo.

les paso a contar:
en mi casa me conecto con Arnet Adsl (modem usb amigo) y a la hora de configurar la conexión no tuve mayores problemas, siempre teniendo que ejecutar, a la hora de conectarme los siguientes comandos:


sin embargo, cuando me voy de casa, suelo utilizar la placa wifi, y para ello instale el WiCD, pudiendome conectar sin problemas.

El problema fue cuando despues de 1 semana quise conectar la computadora de nuevo a la conexion ADSL de Arnet. Ejecute loscomandos como solia hacerlo, luego del pppoe-start recibi el Connected! que mas de una vez me saco una sonrisa, sin embargo, al abrir el firefox o el gestor de actualizaciones, seguia desconectado. probe poniendo los dns de arnet y no hubo caso, tambien incorporando la interfaz nas0 al Wicd, pero tampoco.

a alguien se le ocurre que puede ser? o en su defecto, como hacer para reinstalar la conexion adsl?

muchas gracias

(uso intrepid ibex)

Hola como va, yo tengo apenas un par de semanas en esto pero  desde mi corto conocimiento te cuento que seria bueno que hagas todo tu procedimiento de coneccion y luego ejecutes el comando ifconfig y que pegues aca lo que te devuelve comop para poder comprender un poco mas que esta pasando, un saludo

---

