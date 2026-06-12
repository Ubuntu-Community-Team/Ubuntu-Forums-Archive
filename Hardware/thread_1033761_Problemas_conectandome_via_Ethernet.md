---
title: "Problemas conectandome via Ethernet"
date: 2009-01-07
forum: Hardware
---

### Post by Kabezon on 2009-01-07
Bueno, la hago lo más corta posible:

Instalé Windows XP en una partición aparte para jugar un par de juegos que me regalaron esta pasada Navidad. Instalé los drivers e iba todo muy lindo hasta que intentó conectar a internet, y me salió el mensajito ese de "limited or no connectivity" ("conexión limitada o inexistente" sería?) En ese momento no me importo, jugué al jueguito chocho, igual, para eso quería Windows, cierto? 

El problema es que al bootear a Ubuntu, si bien aparezco como conectado, no tengo conexión. Me fijé en "información de conexión" y me aparece lo que sale en la imagen adjunta al post. Desde entonces estoy conectado con el Wi-Fi

Esto ocurrió exactamente después de intentar conectarme en Windows. Pensé que era un problema de drivers, ya que los drivers de XP para mi PC los tuve que buscar individualmente. Entonces, decidí instalar Vista para sacar los drivers directamente desde la página de HP, pero al hacerlo siguió todo igual. 

Intenté las cosas más obvias, como apagar todo incluido el modem/router, esperar un tiempito, volver a conectar y... nada! Sigue igual :( Bajo Windows le puse a "reparar" a la conexión pero tampoco pasa nada u.u También intente configurar la conexión a mano, poniendo la IP, máscara, ruta predeterminada, DNS y todo eso... No sirve :S

Me dijeron que o se me hechó a perder el cable o la placa de ethernet, o que se desfiguró mi modem solamente para mi MAC o... algo por el estilo (No tengo idea qué quiera decir esta última) El cable funciona, lo probé con otro aparato y agarra lo más bien. Lo del modem, MAC, cosa rara, no sé que signifique, pero me dijeron que es muy poco probable ya que las otras PCs siguen conectándose sin dramas y es muy raro que sólo se desconfigure 1 máquina y no el resto.

Entonces, quedaríamos con que o se rompió la placa ethernet o que se desfiguró el MAC. Cómo puedo afirmar que la placa está dañada? Cómo puedo revisar si el MAC se desconfiguró? (de paso una breve explicación de qué es vendría bárbaro) O cuál otro podría ser el problema?

Desde ya, muchas gracias por al menos tomarse el tiempo leyendo. Ojalá me puedan ayudar :D

---

### Post by Hei Ku on 2009-01-07
Postea tu archivo /etc/network/interfaces
y el resultado del comando ifconfig

Tambien seria bueno saber qué es lo que tenes del otro lado. Es un router, es un cablemodem, un modem?

---

### Post by Kabezon on 2009-01-07
[QUOTE=/etc/network/interfaces]auto lo
iface lo inet loopback



[/QUOTE]

[QUOTE=ifconfig]kabezon@kabezon-desktop:~$ ifconfig
ath0      Link encap:Ethernet  direcciónHW 00:11:95:e7:64:12  
          inet dirección:192.168.1.66  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::211:95ff:fee7:6412/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:7348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5744 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:9111422 (8.6 MB)  TX bytes:695875 (679.5 KB)

eth0      Link encap:Ethernet  direcciónHW 00:1a:92:26:1c:f2  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10043 (9.8 KB)
          Interrupción:16 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:2666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2666 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:134548 (131.3 KB)  TX bytes:134548 (131.3 KB)

wifi0     Link encap:UNSPEC  direcciónHW 00-11-95-E7-64-12-00-00-00-00-00-00-00-00-00-00  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:13650 errors:0 dropped:0 overruns:0 frame:3660
          TX packets:5955 errors:2 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:199 
          RX bytes:10756943 (10.2 MB)  TX bytes:877727 (857.1 KB)
          Interrupción:21 

[/QUOTE]

Tengo este 2Wire [http://store.att.com/Catalog/ProductDetails.asp?ProductId=1000-401047-000&CategoryId=catMRG](http://store.att.com/Catalog/ProductDetails.asp?ProductId=1000-401047-000&CategoryId=catMRG)

---

### Post by Hei Ku on 2009-01-07
El problema en parte es que no tenes configurada la interfaz ethernet para que se configure por DHCP. Por que no probas de configurar con el Network Manager? Es la eth0
Si no te sale por ahí, vamos a traves del archivo interfaces.

---

### Post by Kabezon on 2009-01-07
Vayamos a través del archivo interfaces nomás :P

---

### Post by Hei Ku on 2009-01-07
Ok. Acá vamos:

```

sudo gedit /etc/network/interfaces

```

Agregá estas lineas:
```

auto eth0
iface eth0 inet dhcp

```

Y para restartear la red:

```

sudo /etc/init.d/networking restart

```

Probá si ahí anda. Si no, volvé a tirar el ifconfig y postealo.

---

### Post by Hei Ku on 2009-01-07
Ok. Acá vamos:

```

sudo gedit /etc/network/interfaces

```

Agregá estas lineas:
```

auto eth0
iface eth0 inet dhcp

```

Y para restartear la red:

```

sudo /etc/init.d/networking restart

```

Probá si ahí anda. Si no, volvé a tirar el ifconfig y postealo.

---

### Post by Kabezon on 2009-01-07
Cuando hago "sudo /etc/init.d/networking restart" me sale esto:

> kabezon@kabezon-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:1a:92:26:1c:f2
Sending on   LPF/eth0/00:1a:92:26:1c:f2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]


No funca :S 

El ifconfig ahora:

> kabezon@kabezon-desktop:~$ ifconfig
ath0      Link encap:Ethernet  direcciónHW 00:11:95:e7:64:12  
          inet dirección:192.168.1.66  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::211:95ff:fee7:6412/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:86506 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59637 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:119669888 (114.1 MB)  TX bytes:5116929 (4.8 MB)

eth0      Link encap:Ethernet  direcciónHW 00:1a:92:26:1c:f2  
          dirección inet6: fe80::21a:92ff:fe26:1cf2/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:26515 (25.8 KB)
          Interrupción:16 Dirección base: 0xe000 

eth0:avahi Link encap:Ethernet  direcciónHW 00:1a:92:26:1c:f2  
          inet dirección:169.254.6.219  Difusión:169.254.255.255  Máscara:255.255.0.0
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          Interrupción:16 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:2861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2861 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:157092 (153.4 KB)  TX bytes:157092 (153.4 KB)

wifi0     Link encap:UNSPEC  direcciónHW 00-11-95-E7-64-12-00-00-00-00-00-00-00-00-00-00  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:125698 errors:0 dropped:0 overruns:0 frame:38262
          TX packets:60324 errors:31 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:199 
          RX bytes:132799512 (126.6 MB)  TX bytes:6936427 (6.6 MB)
          Interrupción:21 

kabezon@kabezon-desktop:~$ 



---

### Post by Hei Ku on 2009-01-07
A que tenes conectada la placa ethernet? El router, modem o lo que sea tiene DHCP o tenes que tener IP fija?

---

### Post by Kabezon on 2009-01-07
> **Hei Ku said:**
> A que tenes conectada la placa ethernet? El router, modem o lo que sea tiene DHCP o tenes que tener IP fija?
Va al modem directamente ._. Y sí, es DHCP :S Es muy flashero todo esto, no? u.u El modem este es raro, onda que es como un modem y un router juntos...

---

### Post by Hei Ku on 2009-01-07
Pasa el modelo. Y como prueba, apaga la maquina, apaga el modem. Prende el modem y despues prende la maquina.

---

### Post by Kabezon on 2009-01-08
> **Hei Ku said:**
> Pasa el modelo. Y como prueba, apaga la maquina, apaga el modem. Prende el modem y despues prende la maquina.
Sí, sí, ya lo había hecho xD Me acabo de comprar otra placa de ethernet :P Si funca, me la quedo, si no funca, la devuelvo y a seguir batallando con la actual -.-

---

### Post by Kabezon on 2009-01-08
Aparentemente la vieja placa de ethernet habia muerto, la nueva conecto como si nada :D! Igualmente, gracias por toda la ayuda.

---

