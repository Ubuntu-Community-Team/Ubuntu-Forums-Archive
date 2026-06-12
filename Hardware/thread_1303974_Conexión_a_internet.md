---
title: "Conexión a internet"
date: 2009-10-28
forum: Hardware
---

### Post by NGP on 2009-10-28
Gente,

No puedo conectarme a Internet desde mi laptop. Es nueva y no sé como se configura (además de que soy nueva en Ubuntu, je)
De acuerdo a lo que leí, le conecté el cable (que viene de un router) y ejecuté:

sudo pppoeconf
El mensaje que me da es el siguiente:

"Sorry, I scanned 3 interfaces, but the acces concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls de modem".

---

El cable, el modem y el router funcionan bien dado que lo tengo conectado a la DESKTOP y es la conexión que estoy utilizando para postear esto.

Desde ya millones de gracias x la ayuda :D

---

### Post by Mauro22 on 2009-10-28
Si el router es el que se encarga de conectarse (lease: desde el desktop no hago nada salvo navegar)... en ubuntu seria igual... 

Dudo que tengas un router para varias pcs y aun asi tengas que "marcar" manualmente, en ese caso deberias configurar el desktop para compartir la conexion y conectarte a esa pc, obvio.

---

### Post by NGP on 2009-10-28
A ver...no sé si me expresé bien...

Tengo un router desde hace años del cual conecto dos PC de escritorio, sin problemas (y tiene para conectar aún más). Lo que hice fue desconectar el cable de una PC y ponerlo en la laptop. Luego de eso ejecuté el pppoeconf y me tiró ese mensaje...

Se entiende??

---

### Post by Mauro22 on 2009-10-28
Creo que entiendo. Ahora si el router se conecta solo, no hace falta usar el asistente de ppp ya que no hay que marcar.. 

Las otras pc tienen Internet apenas las encendes?? O tenés q hacer algo ?


Para resumir si no tenés que conectarte manualmente en las otras pc , acá tampoco...

---

### Post by NGP on 2009-10-28
Cuando enciendo las PC no tengo que hacer nada (éstas tienen windows). En la laptop nueva que tiene ubuntu, conecto el cable y no pasa nada. Habrá que configurar algo en la opción "Wired Network"?

---

### Post by Mauro22 on 2009-10-28
Lo único que se me ocurre es que no te reconozco la placa o algo así. Con router tendría que levantar de una! 

Raro Che, haber si se me ocurre algo...

---

### Post by pablo.s on 2009-10-28
Posteà el contenido
del archivo
/etc/network/interfaces
en un nuevo post.

---

### Post by anarko on 2009-10-28
Puede que quien preinstalo la notebook con ubuntu te dejo puesta una IP fija, lo que impediria que el router configure la interface de red de la notebook para navegar a travez de el. Proba lo siguiente :
Abri una terminal, Applicaciones -> Accesorios -> Terminal 
Esto te abre una ventanita con fondo blanco ( si es que esta todo default ) en esa ventanita escribi "ifconfig" sin las comillas y dale enter.
Te deberia salir algo masomenos asi : 
```

anarko@AnArKa:~$ ifconfig 
eth0      Link encap:Ethernet  direcciónHW 00:1f:c6:c1:d8:66  
          Direc. inet:192.168.0.99  Másc:255.255.255.0
          Dirección inet6: fe80::21f:c6ff:fec1:d866/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:29212 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:29554 errores:0 perdidos:0 overruns:0 carrier:2
          colisiones:0 long.colaTX:1000 
          Bytes RX:17160878 (17.1 MB)  TX bytes:3040074 (3.0 MB)

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:8 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:8 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:568 (568.0 B)  TX bytes:568 (568.0 

```

Despues de eso en la misma temrinal pone : "cat /etc/network/interfaces" sin las comillas

Copialo todo y pegalo aca, asi vemos como esta conf. la placa de red y si esta configurado del mismo modo, la parte mas importante es la que dice "eth0"

---

### Post by NGP on 2009-10-28
Acá va!! Mil gracias x la ayuda que me están dando :D

eth1    Link encap:Ethernet  HWaddr 00:24:25:05:61:af  
          inet6 addr: fe80::224:25ff:fe05:61af/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7878 (7.8 KB)  TX bytes:0 (0.0 B)
          Interrupt:253 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4556 (4.5 KB)  TX bytes:4556 (4.5 KB)

pan0   Link encap:Ethernet  HWaddr 2a:19:55:f2:81:b4  
          inet6 addr: fe80::2819:55ff:fef2:81b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:804 (804.0 B)

a@a-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by anarko on 2009-10-28
Bueno apartentemente nadie le dijo a la interface de red que tenia que conectarse a algun lado.
Hace lo siguiente : 
En esa misma terminal escribi "sudo gedit /etc/network/interfaces"
Te va a pedir que ingreses tu contraseña ya que el archivo que vas a editar es un archivo de configuracion del sistema. 
Nota : si te dice "command not found" en ves de gedit pone kate.
Eso te abre un editor de texto con el archivo de configuracion. 
Dejando una linea en blando debajo de "iface lo inet loopback"
agrega lo siguiente :
```

auto eth1
iface eth1 inet dhcp

```
Loego de agregar esto pones guardar y cerras el editor, acto seguido enchufa el cable que va del router a la notebook, y en la misma temrinal de siempre pone "sudo /etc/init.d/networking restart" y dale enter, si todo sale bien el proximo post deberia ser desde ubuntu :).

Una vez hecho esto no hace falta volver a hacer nunca mas, siempre y cuando uses el mismo router o un router que asigne IP automaticamente, yo personalemnte no recomiendo usar el gestor de redes que trae ubuntu ya que jamas ha funcionado bien.

El pppoeconf que nombraste es solamente si tenes ADSL ( speedy o simil ) y el modem esta conectado directamente a la PC sin mediar un router

---

### Post by NGP on 2009-10-28
Acá va!! Mil gracias x la ayuda que me están dando :D

eth1    Link encap:Ethernet  HWaddr 00:24:25:05:61:af  
          inet6 addr: fe80::224:25ff:fe05:61af/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7878 (7.8 KB)  TX bytes:0 (0.0 B)
          Interrupt:253 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4556 (4.5 KB)  TX bytes:4556 (4.5 KB)

pan0   Link encap:Ethernet  HWaddr 2a:19:55:f2:81:b4  
          inet6 addr: fe80::2819:55ff:fef2:81b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:804 (804.0 B)

a@a-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by NGP on 2009-10-28
JA! Se está haciendo esperar mi ubuntu!!

Te paso lo que me pone:

a@a-laptop:~$ sudo /etc/init.d/networking restart
[LEFT] * Reconfiguring network interfaces...                                                                                       Internet Systems Consortium DHCP Client V3.1.1
[/LEFT]
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ethl: ERROR while getting interface flags: No such device
ethl: ERROR while getting interface flags: No such device
Bind socket to interface: No such device:razz:
Failed to bring up ethl.

---

### Post by NGP on 2009-10-28
JA! Se está haciendo esperar mi ubuntu!!

Te paso lo que me pone:

a@a-laptop:~$ sudo /etc/init.d/networking restart
[LEFT] * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.1.1
[/LEFT]
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ethl: ERROR while getting interface flags: No such device
ethl: ERROR while getting interface flags: No such device
Bind socket to interface: No such device:razz:
Failed to bring up ethl.

---

### Post by anarko on 2009-10-28
Creo que hubo un problema de entendimiento, volve a repetir los pasos de la parte del gedit o kate, pero cambia donde vos pusiste ethl ( ele ) tenes que poner eth1 ( uno en numero ), he ahi el quis del error.

---

### Post by NGP on 2009-10-28
Aquí va lo que me tira:
(Ya cambié la L por el 1)

a@a-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                       RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 7692
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:24:25:05:61:af
Sending on   LPF/eth1/00:24:25:05:61:af
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:24:25:05:61:af
Sending on   LPF/eth1/00:24:25:05:61:af
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by anarko on 2009-10-28
Bueno veo que se resiste, me gustan los desafios, hagamos lo siguiente : 

Ponete frente a la maquina con windows que si funciona con el router, anda a inicio -> configuracion -> conexiones de red
Ahi busca una conexion que diga "Conexion de area local" y abajo diga "conectado"
hace boton derecho del mouse -> propiedades, selecciona de la lista el item que dice "Protocolo Internet TCP/IP" y apreta el boton "propiedades" y describime que dice en la pestaña general ( es la primera que aparece ) si dice alguna informacion especifica o si esta simplemente pinchado donde dice "Obtener una direccion IP automaticamente"

---

### Post by NGP on 2009-10-28
[IMG]file:///C:/DOCUME%7E1/NOELIA%7E1/CONFIG%7E1/Temp/moz-screenshot.jpg[/IMG]Dice lo siguiente:

Conectar usando:
NIC Fast Ethernet PCI Familia RTL81

Esta conexión utiliza los siguientes elementos:

Clientes para redes Microsoft 
Compartir impresoras y archivos para clientes Microsoft 
Programador de paquete QoS 
NetBIOS de NWLink 
Protocolo de transferencia compatible con NWLink IPX... 
Protocolo Internet (TCO/IP)

---

### Post by anarko on 2009-10-28
La imagen no se ve porque pego el link en tu PC, volve a postearla pero anda donde dice "Advanced" y subila al foro con el "clip" el ganchito al lado de la carita blanca. Para que quede grabada en el foro.

Saludos

---

### Post by NGP on 2009-10-28
Ac.a va el print page

---

### Post by anarko on 2009-10-28
Ok, mandame lo mismo, pero ahora en la ventana que tiene por titulo "Esta de conexion de area local" apreta en la pestaña donde dice "soporte"

---

### Post by NGP on 2009-10-28
Ac.a va!!

---

### Post by anarko on 2009-10-28
Ok, ahora si estoy desconecrtado... la Pc con windows esta con IP automatica, lo mismo que configuramos recien en el ubuntu. Hace lo siguiente, si te animas, desconecta el cable de red de la PC que tiene windows, el que esta conectado el router, conectalo en la notebook y repeti el paso de "sudo /etc/init.d/networking restart" haber si es problema del cable o del router o de la pc.
Tambien puede ser que el router este configurado para solo aceptar las interfaces de red de las PC que ya tenes ahi. 
Una pregunta, el router cuantos enchufes para cable de red tiene?

---

### Post by NGP on 2009-10-28
Mas info:

Dirección física: 00-11-D8-CF-8A-BF
Dirección IP: 192.168.0.3
Máscara de subred: 255.255.255.0
Puerta de enlace predeterminada: 192.168.0.1
Servidor de DHCP: 192.168.0.1
Concesión obtenida: 28/10/2009 10:59:39 p.m.
La concesión caduca: 29/10/2009 10:59:39 p.m.
Servidores DNS: 200.42.0.111, 200.42.97.111, 200.42.97.110
Servidor WINS:

---

### Post by NGP on 2009-10-28
Tiene para enchufar 4 máquinas

---

### Post by anarko on 2009-10-28
Bien ahi te dio una IP y deberias poder navegar con el Ubuntu. El problema puede ser el cable con el que intentabas antes. Antes estabas intendo con otro cable o con el mismo cable?

---

