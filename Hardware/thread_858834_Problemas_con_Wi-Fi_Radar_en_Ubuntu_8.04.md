---
title: "Problemas con Wi-Fi Radar en Ubuntu 8.04"
date: 2008-07-14
forum: Hardware
---

### Post by tuliobalcaldi on 2008-07-14
Hola, que tal? Instale Ubuntu en estos dias y sigo con muchisimas dudas, soy un novato 100% e instale este sistema por una cuestion de cambio (estoy cansado de microsoft ya) y para probar algo totalmente distinto.
Instalé en una Dell Latitude D630 y anda todo perfecto, le instale el Wi-Fi Radar ([http://wifi-radar.systemimager.org)para](http://wifi-radar.systemimager.org)para) poder simplificar la busqueda de conexiones. La placa inalambrica que trae es una Intel PRO/Wireless 4965 AGN Network Connection.

Para saber si la placa esta instalada hice "sudo lshw -C network" y me salio lo siguiente:

*-network
description: Network controller
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:0c:00.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=iwl3945 latency=0 module=iwl3945
*-network
description: Ethernet interface
product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:09:00.0
logical name: eth0
version: 02
serial: 00:1c:23:26:2f:ff
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5755m-v3.29 latency=0 link=no module=tg3 multicast=yes port=twisted pair



Cuando pongo "sudo aptitude install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9" me sale esto:

tulio@tulio-laptop:~$ sudo aptitude install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "ndiswrapper-common"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "ndiswrapper-utils-1.9"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "ndiswrapper-common"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "ndiswrapper-utils-1.9"
No se instalará, actualizará o eliminará ningún paquete.
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
tulio@tulio-laptop:~$

Esto quiere decir que esta instalada bien la placa? 
Mi problema radica que cuadno quiero abrir Wi-Fi Radar desde el menu correspondiente (Aplicaciones -> Internet) me sale una entanita con lo siguiente:

"No se puede lanzar el elemento del menu. Ha ocurrido un error al ejecutar el proceso hijo <<su-to-root>> (no existe el fichero o directorio)"

Pero segun el programa que trae para instalar y quitar programas y segun terminal esta todo bien instalado!! Como puedo correr la ventana grafica del programa? No entiendo :S

Saludos y mil disculpas! Soy un total neofito

---

### Post by Hei Ku on 2008-07-14
en la consola, pone: 

iwconfig

y postea lo que te tira. Siendo una placa Intel, no creo que tengas que usar ndiswrapper para usarla. De paso, probaste a usar el Network Manager? Viene instalado ya y creo que tiene para ver las redes inalambricas.

---

### Post by FlyerDie on 2008-07-14
Hacela nas facil y no te la compliques, desde consola pone:

```
$ sudo apt-get install wifi-radar 

```

Y listo, las dependencias que necesites te las va a instalar solas ;)

Saludos!

---

### Post by tuliobalcaldi on 2008-07-15
Arranco perfectamente! Pero logre usarlo sin wi-fi radar.
Mil gracias igual :)

---

