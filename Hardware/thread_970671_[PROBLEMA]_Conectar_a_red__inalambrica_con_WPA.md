---
title: "[PROBLEMA] Conectar a red  inalambrica con WPA"
date: 2008-11-04
forum: Hardware
---

### Post by FedeCC on 2008-11-04
Si me tienen paciencia les cuento mi problema. 

Empece a usar Ubuntu hace poco con Hardy. Todo andava bien hasta que descubri que no podia conectarme a redes inalambricas que tengan proteccion WPA. Si no estan protegidas se conecta perfecto, es decir no es un problema de la placa wireless. Este problema practicamente convertia a ubuntu en algo inutil ya que no puedo andar con la red desprotegida, por lo que volvi a windows.

Me lei toda la internet para poder hacer funcionar el tema. Intente de mil maneras, instale drivers, configure archivos, en fin, hice de todo. De hecho hice tantas cosas que al final mi ubuntu termino siendo un desconche como diria Pinti.

Decidi esperar a que salga la nueva version 8.10 y hacer una instalacion de cero. Y eso hice, ahora tengo Intrepid recien salidito del horno y sin alterar. Probe denuevo con la red y sigue el mismo problema, se conecta perfecto cuando no hay proteccion, pero no cuando hay una clave wpa.

Mi consulta es basicamente que me conviene hacer. Si alguien tuvo un problema similar como lo resolvio?

Es una macana porque es el unico obstaculo que tengo para usar ubuntu, pero si no lo soluciono no lo puedo usar, es condicion necesaria...

Mi maquina es una laptop y la placa inalambrica usa drivers ralink rt73.

Saludos.

---

### Post by faktorqm on 2008-11-04
Hola, todos los caminos conducen aca: [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73)
Aca hay otro dispositivo, mismo chipset: [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver))

Éste se compila su propio driver, te puede servir de mucho: [http://www.spinthiras.net/2008/09/20/ubuntu-and-the-ralink-rt73-chipset/](http://www.spinthiras.net/2008/09/20/ubuntu-and-the-ralink-rt73-chipset/)

Fijate aca que hay un par de modelos no soportados, mismo chipset pero distinto fabricante (D-link), fijate con lspci o lsusb si el tuyo figura [http://linux-wless.passys.nl/query_part.php?brandname=D-Link](http://linux-wless.passys.nl/query_part.php?brandname=D-Link)

Aca para intrepid ibex: [http://mcmlxxii.co.uk/2008/10/22/rt73-ubuntu-intrepid-8-10/](http://mcmlxxii.co.uk/2008/10/22/rt73-ubuntu-intrepid-8-10/)

mas guias: [http://alumnosici.top-board.com/software-libre-open-source-f51/guia-como-adapatadores-wifi-chipset-ralink-rt73-gnu-linux-t436.htm](http://alumnosici.top-board.com/software-libre-open-source-f51/guia-como-adapatadores-wifi-chipset-ralink-rt73-gnu-linux-t436.htm)
[http://foros.ubuntu-cl.org/viewtopic.php?p=22482](http://foros.ubuntu-cl.org/viewtopic.php?p=22482)

En google no buscaste no?....

---

### Post by FedeCC on 2008-11-05
Yo ya habia logrado instalar con exito (creo) los drivers rt73 pero eso no soluciono mi problema, todo siguio igual. 

Voy a probar devuelta con tu guia a ver si ahora sale. Gracias igual por tu respuesta.


EDIT: 

Probe sueguir tu guia faktorqm. Instale los drivers y despues instale el rutilt (que no habia probado antes). Pero pasa algo muy raro. Cuando la red esta sin proteccion se conecta perfecto, pero cuando esta con WPA se conecta y desconecta intermitenemente. En fin...

---

### Post by FedeCC on 2008-11-12
Bueno, al final lo pude solucionar. No se que paso, de pronto funciono bien. En fin, gracias faktorqm, tu guia me soluciono el problema.

---

### Post by edfsoft on 2012-04-05
Yo estuve peleando con el mismo problema durante mucho tiempo.
Ubuntu no se conectaba a las redes inalámbricas. Actualicé desde la versión 8 a la 10.04 y no se solucionó.
Hoy encontré la respuesta probando.
Lo que hice fue lo siguiente.
Eliminé todo el contenido del archivo
/etc/network/interfaces
Reinicié el equipo y la red wifi comenzó a funcionar perfectamente.

---

