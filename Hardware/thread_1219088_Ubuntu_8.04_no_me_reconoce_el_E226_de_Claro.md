---
title: "Ubuntu 8.04 no me reconoce el E226 de Claro"
date: 2009-07-21
forum: Hardware
---

### Post by vicherot on 2009-07-21
Estimados, ya he googleado hasta el dolor de cabeza y dedos este problema... si bien encuentro que todo el mundo puede conectar el modem Huawei E226 (que el ubuntu reconoce com E220) yo no puedo hacerlo debido a que no me lo reconoce.
Todos indican conectarlo y hacer un un lsusb para ver en que puerto está, pero ya sea que bootee con el modem conectado o lo conecte despues, al hacer un lsusb este se queda colgado... queda el cursor titilando. He realizado un lsusb sin el modem, con mi pen drive conectado y funciona barbaro, al conectar el modem se muere el lsusb y tengo que rebootear.
Cuando hago un sudo ls -l /dev/ttyUSB* no me detecta nada y eso con el pen drive montado y funcionando el cual esta en /media/kingston.
Tambien dicen que lo puede reconocer como cdrom, pero solo me figura montado el cdrom de la maquina...
Ya hice de todo, puse enable al Network Manager, al Administrador de Dispositivos... renegue con el rmmod y el modprobe... ya no se que hacer.

Algun tip para hacerle detectar o montar a la fuerza este bendito modem ???
Utilizo Ubuntu 8.04.1 con Kernel 2.6.24-19 instalado de cero.

Espero alguien se apieade de esta alma encadenada al software privativo, GRACIAS !!!

---

### Post by staar on 2009-07-21
mmm raro che, en otro SO anda bien el modem? probaste conectarlo el cable 'doble' que trae el modem, con los dos usb conectados? (puede que tus puertos usb no le den suficiente energía para que el modem funcione correctamente)

hace una cosa, conecta el modem, y en una terminal corré un ```
dmesg
``` y pegá la salida acá...

igual, en las versiones más nuevas de ubuntu (y del kernel) el soporte para 3g mejoró muchisimo, si tenés la posibilidad, te recomendaría que actualizes...

saludos

---

### Post by vicherot on 2009-07-22
Gracias por el ofrecimiento staar, pero hice lo siguiente.
Ejecute el comando que me dijiste y analise la salida, ahi me di cuenta que me estaba jorobando los parametros que le paso al kernel (le pasaba el noapic, nolapic y acpi=off) para poder bootear sino no entraba al ubuntu... y ahi me di cuenta que el nolapic estaba demas y precisamente debe ser lo que j***a por que me engancho el modem de uno... pero bue, me lo tomaba com E870 y el Vodafone que baje de por ahi no me lo tomaba... corte por lo sano, me instale el 9.04 y bootee con los parametros noapic y acpi=off porque sino no entraba y me reconocio el modem al toque... configure para CTI y ahora te escribo desde el FF en Ubuntu 9.04....
UNA MASA !!! Chau Güindous, si te he visto no me acuerdo JA!!
Un abrazo a todos, ahora abro otro hilo porque instale el Apache y nadie entra a mi pagina (el 80 figura invisible en los scan de puertos, ya vere)

---

