---
title: "placa de red no arranca"
date: 2009-05-15
forum: Hardware
---

### Post by pol666 on 2009-05-15
Ayer se corto internet, por lo que intente lo imposible para que volviera, incluso resetear el modem a default aunque no sirvio de nada, a las 12hs volvio la linea, el problema era que  el modem que antes estaba routeado, ahora no lo estaba. 

Para volver a hacerlo, primero hice un pppoeconf con el fin de conectarme y buscar en google los pasos necesarios, una vez con el modem en modo router, cancele la anterior conexion borrando "algo" de un archivo [B]/etc/ppp/peers/dsl-provider
[/B]

Es ahí donde creo que me mande un moco, al reiniciar el PC, no reconocia una de las placas de red y en el gestor de conexiones me figuraba lo siguiente 
[B]
networking interface[/B]
[No actualizado aun]
**Direccion IP**: dum.my.ip.adrr

serio problema, por que no puedo acceder a la configuración del modem desde ahí.

Nota: Si bien tengo 2 placas de red, una no funciona bien en ubuntu, mientras que la otra no lo hace en windows, así que son complementarias. En windows la conexion arranca sin ningun problema, y en ubuntu no funciona la placa de red correspondiente. 

Nota 2: Les dejo el ifconfig por si a alguien le interesa

> eth0      Link encap:Ethernet  direcciónHW 00:40:f6:cc:98:98
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:17 Dirección base: 0xb400
eth1      Link encap:Ethernet  direcciónHW 00:1a:92:cc:ad:ca
          inet dirección:192.168.1.4  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::21a:92ff:fecc:adca/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:5482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4593 errors:0 dropped:0 overruns:0 carrier:1
          colisiones:0 txqueuelen:1000
          RX bytes:4830431 (4.8 MB)  TX bytes:0 (0.0 B)
          Memoria:ddec0000-ddf00000


nota 3: aca el fichero  **/etc/network/interfaces**
antes de moficarlo

> auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

luego de modificarlo

> auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp




Nota 4: el fichero **/etc/ppp/peers/dsl-provider** tal cual como esta ahora

> # Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20


):P se que es confuso, pero cualquier cosa lo aclaro más.
en sintesis, toque y rompi :P.

---

### Post by Hei Ku on 2009-05-15
Como se puede patear, la pateamos al subforo de hardware.
[¿Qué se puede publicar acá?]("http://ubuntuforums.org/showthread.php?t=1150805")

---

### Post by pol666 on 2009-05-15
pobrecita, yo estaba insultando a los ficheros nada mas :P

---

