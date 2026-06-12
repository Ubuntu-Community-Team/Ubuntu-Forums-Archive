---
title: "Conexión perdida al reiniciar"
date: 2010-05-11
forum: Hardware
---

### Post by JoniJnm on 2010-05-11
Hola,

Hace poco instalé Ubuntu 10.04 LTS. No me iba la conexión de red, así que tuve que usar:
sudo ppoeconfig

Después de configurarlo ya tengo conexión, pero al reiniciar vuelve a estropearse y tengo que configurarlo otra vez.

Hay alguna manera para que se conecte directamente sin tener que usar ppoeconf?

Muchas gracias

---

### Post by guillermolisi on 2010-05-11
Una alternativa es configurar tu modem ADSL para que trabaje como router y disque el mismo evitando que lo tengas que hacer vos.

---

### Post by JoniJnm on 2010-05-11
Yo tengo un router. Dejo info por si hace falta:

Cuando funciona la red (después de configurar pppoeconf)

· plog
May 11 16:51:16 jonijnm-es pppd[1306]: Using interface ppp1
May 11 16:51:16 jonijnm-es pppd[1306]: Connect: ppp1 <--> eth0
May 11 16:51:17 jonijnm-es pppd[1306]: PAP authentication succeeded
May 11 16:51:17 jonijnm-es pppd[1306]: peer from calling number 00:14:7F:61:20:18 authorized
May 11 16:51:17 jonijnm-es pppd[1306]: not replacing existing default route through ppp0
May 11 16:51:17 jonijnm-es pppd[1306]: Cannot determine ethernet address for proxy ARP
May 11 16:51:17 jonijnm-es pppd[1306]: local  IP address 85.53.249.46
May 11 16:51:17 jonijnm-es pppd[1306]: remote IP address 172.31.255.254
May 11 16:51:17 jonijnm-es pppd[1306]: primary   DNS address 62.36.225.150
May 11 16:51:17 jonijnm-es pppd[1306]: secondary DNS address 62.37.228.20

· ifconfig ppp0
ppp0      Link encap:Protocolo punto a punto  
          Direc. inet:85.53.249.21  P-t-P:172.31.255.254  Másc:255.255.255.255
          ACTIVO PUNTO A PUNTO FUNCIONANDO NOARP MULTICAST  MTU:1492  Métrica:1
          Paquetes RX:487 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:430 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:3 
          Bytes RX:352973 (352.9 KB)  TX bytes:80133 (80.1 KB)

· lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

· lspci -v
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
    Subsystem: Dell Device 01d5
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at feaff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at df40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100

Cuando está desconectado es lo mismo (meno plog, que no dice nada)

Cuando terminas de configurar el pppoe, dice al final que se puede inciar la conexión con el comando
pon dsl-provider

He probado a ejecutarlo en la terminal, pero no se inicia la conexión (hay que reconfigurar la red con pppoeconf). SI hubiera funcionado lo hubiera puesto en las aplicaciones de inicio

Alguna sugerencia? :(

---

### Post by JoniJnm on 2010-05-11
Parace que ya va :)

---

### Post by anarko on 2010-05-11
Como lo solucionaste?

Al temrinar de configurar el ADSL con pppoeconf no te pregunto si querias iniciar la coneccion al iniciar el servicio de ppp? Respondiendo que si en esa instancia inicia la coneccion ADSL cuando inica las interfaces de red. 

Por otro lado ami me funciono bien la conf. desde el netwrok manager en gnome, lo primordial es hacer boton derecho y desabilitar las placas de red, luego crear las conecciones y configuraciones y luego habilitar las placas de red.

---

### Post by JoniJnm on 2010-05-11
Pues no sé qué hice, que se inicia la conexión al iniciar. Lo que dices de seleccionar, lo probé sin marcar, marcado y de todas las maneras, pero no sé cuál es la última que puse.

Lo malo es que en la conexiones de red por cableado (las que yo uso) no me viene ninguna, y al poner el comando route para conocer la puerta de enlace de mi router no me da el gateway, dice esto:

Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
172.31.255.254  *               255.255.255.255 UH    0      0        0 ppp0
default         *               0.0.0.0         U     0      0        0 ppp0

He probado con
192.168.0.1
192.168.1.1
192.168.2.1

Pero na, no carga la página. Podría volver a configurarlo con pppoeconf, pero me da cosa de que se vuelva a j***r xD

---

