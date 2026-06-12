---
title: "problema tarjeta red conceptronic c100i chip (realtek 8139)"
date: 2009-06-25
forum: Hardware
---

### Post by sitodonosti on 2009-06-25
hola a todos hace un año que me pasé a ubuntu, y hace un mes me compre una tarjeta de red de conceptronic el c100i, e instalado ubuntu con lxde en esa maquina antes tenia una tarjeta wifi e iba perfectamente pero ahora me e cambiado a una tarjeta de red, la conceptronic.

El caso es que nunca me he conectado a internet por red cableada y nose que tengo que hacer y que no tengo que hacer si alguien me hehca una mano estaría muy agradecido, que nose si es por mi incompetencia o que este chip da problemas en linux

He buscado por internet pero no he conseguido que me funcione...

un saludo y gracias

---

### Post by guillermolisi on 2009-06-25
Ese placa tiene chip Realtek, asi que deberia salir funcionando sola.
> 
This card is supporting Wake up On Lan and low power management. The Realtek chipset ensures high performance and compatibility.
Mas info en:

[http://conceptronic.net/site/desktopdefault.aspx?tabindex=1&tabid=222&cid=20&gid=2070&pid=C100i](http://conceptronic.net/site/desktopdefault.aspx?tabindex=1&tabid=222&cid=20&gid=2070&pid=C100i)

En base a esto, asumo que el trabajo a realizar viene por el lado del software, asi que muevo el thread a esa seccion.

---

### Post by sitodonosti on 2009-06-25
en la pagina de concpetronic ya me he metido y ya e visto que se supone que debería de ir y en la de realtek pone que los drivers están en el kernel pero el caso es que ubuntu me lo reconoce que está pero no llega a conectarse, cuando pincho en el networkmanager me pone como que esta desactivado

He mirado en algunos post de ubuntu-es pero ninguno me da solución, y nose que hacer. He probado con insmod ./8139too.ko y me sale un erro de que no encuentra el archivo(ahora mismo no encuentro lo que ponia). Ponia algo como no search directory o algo asi

sabrias porque puede darse?

---

### Post by guillermolisi on 2009-06-25
> **sitodonosti said:**
> en la pagina de concpetronic ya me he metido y ya e visto que se supone que debería de ir y en la de realtek pone que los drivers están en el kernel pero el caso es que ubuntu me lo reconoce que está pero no llega a conectarse, cuando pincho en el networkmanager me pone como que esta desactivado

He mirado en algunos post de ubuntu-es pero ninguno me da solución, y nose que hacer. He probado con insmod ./8139too.ko y me sale un erro de que no encuentra el archivo(ahora mismo no encuentro lo que ponia). Ponia algo como no search directory o algo asi

sabrias porque puede darse?
No creo que haga falta usar los drivers del sitio del fabricante. El link lo puse a titulo informativo.

Entiendo que los drivers para la linea Realtek ya estan incluidos en el kernel.

En base a esto es necesario algo mas de informacion, a saber:

Que version de Ubuntu estas usando ?

En una consola/terminal, ingresa el comando lspci y mostra su salida, asi vemos como la reconoce literalmente el SO.

Luego ingresa, tambien en consola/terminal, el comando ifconfig y mostra su resultado.

---

### Post by Hei Ku on 2009-06-25
Podes poner el resultado de poner ifconfig en la consola? Con eso vemos si reconoce tu placa o no.

---

### Post by fmsismo on 2009-06-25
En consola pone los siguientes comandos sin el # y lo que viene atrás que explico que hace

ifconfig -a           #lista todos los dispositivos de red que tengas.
lspci |grep Ethernet  #lista 

y si ves que tenes uno o más dispositivos ethx (donde x es 0,1,2,etc)

sudo ethtool eth0     #informa que velocidades soporta la placa y si tiene link o no fijate de adaptar el eth0 a la interface que detecte tu equipo

Probaste esa placa en otro lado?  No vas a ser el primero al que le venden una placa que no anda :-P

---

### Post by sitodonosti on 2009-06-25
Bueno lo primero agredeceros la rapidez jeje
@guillermolisi, Hei Ku:
os dejo la salida de lspci y de ifconfig
sito@sitotorre:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
[B]00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)[/B]
00:0f.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)
sito@sitotorre:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:07:95:2f:7a:55  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:11 Dirección base: 0xd400 

eth1      Link encap:Ethernet  direcciónHW 00:80:5a:78:02:27  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:11 Dirección base: 0xd000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

@fmsismo
la primera salida es lo mismo que en lspci solo que me da eso asique copi y pego lo anterior 
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

y el ifconfig -a esta salida:
sito@sitotorre:~$ ifconfig -a
eth0      Link encap:Ethernet  direcciónHW 00:07:95:2f:7a:55  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:11 Dirección base: 0xd400 

eth1      Link encap:Ethernet  direcciónHW 00:80:5a:78:02:27  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:11 Dirección base: 0xd000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  direcciónHW fa:19:58:fa:55:9c  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

en cuanto a lo de ethtool:
sito@sitotorre:~$ sudo ethtool eth0(00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90))
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x000000c5 (197)
	Link detected: no
sito@sitotorre:~$ sudo ethtool eth1(00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10))
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: no


A más información:
utilizo ubuntu 9.04 con lxde y el kernel mas nuevo que a sacado canonical
el procesador es un amd ahtlon de 1,16ghz 1g de ram tarjeta nvidia(sale en el lspci) y muy vieja ya que es una de la universidad...

Antes de que se me olvide en window$ si que funciona con sus respectivos drivers claro

---

### Post by guillermolisi on 2009-06-25
Y como te conectas a la red o a Internet con el cable de red ? ADSL, router, Cablemodem, switch, firewall en el medio ?

Como habras podido apreciar, la placa de red alambrica esta bien reconocida por el SO, asi que ahora es cuestion de probar configuracion de red y deberia salir funcionando.

---

### Post by sitodonosti on 2009-06-25
sí, ya se que la reconoce bien pero nose porque aparece como desconectado. Pero como nunca lo he hecho por cable...pos nose.

Es un router de telfonica, con adsl 1mb

---

### Post by guillermolisi on 2009-06-25
> **sitodonosti said:**
> sí, ya se que la reconoce bien pero nose porque aparece como desconectado. Pero como nunca lo he hecho por cable...pos nose.

Es un router de telfonica, con adsl 1mb
Ok. Fijate si en el contenido de /etc/network/interfaces eth1 figura de esta forma:
# The primary network interface
```
auto eth1
iface eth1 inet dhcp
```
Si no hay contenido, agrega lo que te puse asi la placa sale de la administracion del Network Manager y levanta en cuanto le pones el cable de red.

SI ya tiene ese contenido, la otra prueba seria asignarle un aIP fija en la misma red que maneja el router.

Por ejemplo, si el router es 192.168.1.1 el contenido podria ser:
```
iface eth1 inet static
        address 192.168.0.5
        netmask 255.255.255.0
        gateway 192.168.1.1
```

---

### Post by sitodonosti on 2009-06-25
a que te refieres con que la levante¿

---

### Post by guillermolisi on 2009-06-25
> **sitodonosti said:**
> a que te refieres con que la levante¿
A que quede operativa y funcional para la red y para Internet (if up)

---

### Post by sitodonosti on 2009-06-25
no tengo la de eht1 me sale esto:
auto lo
iface lo inet loopback

escribo debajo lo que me has puesto o es lo borro y escribo lo que me aspuesto¿

---

### Post by guillermolisi on 2009-06-25
> **sitodonosti said:**
> no tengo la de eht1 me sale esto:
auto lo
iface lo inet loopback

escribo debajo lo que me has puesto o es lo borro y escribo lo que me aspuesto¿
Deja una linea de separacion y agrega lo que envie en el mensaje anterior.

Esa configuracion le esta diciendo al SO que cuando inice los servicios de red, esa placa usara IP dinamica asignada por un servidor DHCP, en este caso tu router, fuera de la administracion del Network Manager.

Para no reiniciar toda la PC, luego de editar podes hacer en consola
```
sudo /etc/init.d/networking restart
```

Para editar el archivo usa sudo antes de invocar al editor.

---

### Post by sitodonosti on 2009-06-25
Bueno como no tengo problemas jejeje a ver te digo las pautas que he seguido por si he hecho algo mal 

tipear sudo gedit /etc/network/interfaces

agregar lo que me habías escrito y queda así:

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

una vez guardado he escrito en la terminal:
sudo /etc/init.d/networking restart
El resultado en la terminal a sido este:
sito@sitotorre:~$ sudo gedit /etc/network/interfaces
sito@sitotorre:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:80:5a:78:02:27
Sending on   LPF/eth1/00:80:5a:78:02:27
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

Si ahora voy al applet de networkmanager sigue como desconectado. Reinicio el sistema por si acaso.

---

### Post by guillermolisi on 2009-06-25
> **sitodonosti said:**
> Bueno como no tengo problemas jejeje a ver te digo las pautas que he seguido por si he hecho algo mal 

tipear sudo gedit /etc/network/interfaces

agregar lo que me habías escrito y queda así:

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

una vez guardado he escrito en la terminal:
sudo /etc/init.d/networking restart
El resultado en la terminal a sido este:
sito@sitotorre:~$ sudo gedit /etc/network/interfaces
sito@sitotorre:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:80:5a:78:02:27
Sending on   LPF/eth1/00:80:5a:78:02:27
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

Si ahora voy al applet de networkmanager sigue como desconectado. Reinicio el sistema por si acaso.
El router no tiene habilitado el servicio DHCP, o esta desconectado de la PC o la placa no funciona fisicamente hablando, por eso no recibio ninguna asignacion de IP.

Cuando le pones el cable de red con la PC encendida y el otro extremo conectado al router, se enciende algun LED que indique presencia/deteccion de portadora ?

Si posee un LED para esto y no se enciende, o el cable esta mal o la placa esta quemada (a menos que sepas que funciona porque la probaste en otra maquina con el mismo cable).

---

### Post by sitodonosti on 2009-06-25
si vale cierto no habia conectado el cable #-o

Bueno ahora lo he conectado, lo conecto y alprincipio si que va aparece como se conecta pero de repente se desconecta y no puedo conectarme, de hecho la luz de la placa de red se apaga

Puede ser por la contraseña?El DHCP del router esta bien porque en los ordenadores con wifi lo tengo así.

---

### Post by guillermolisi on 2009-06-25
> **sitodonosti said:**
> si vale cierto no habia conectado el cable #-o

Bueno ahora lo he conectado, lo conecto y alprincipio si que va aparece como se conecta pero de repente se desconecta y no puedo conectarme, de hecho la luz de la placa de red se apaga

Puede ser por la contraseña?El DHCP del router esta bien porque en los ordenadores con wifi lo tengo así.
El cable esta colocado en alguna de las bocas LAN del router, si es que tiene mas de una) ?

Se puede aseverar que el cable funciona correctamente ? Probaste con otro ?

Reiniciaste los servicios de red luego de conectar el cable ?

Que contraseña ? Si te referis a la de la red WiFi olvidate porque para la redes con cable eso no existe.

---

### Post by sitodonosti on 2009-06-25
Pues creo que probe el cable pero en windows y creo que si iba, aunque no esto 100% seguro. Antes cuando tenia esta tarjeta en windows con otra cable si que me iba asique probaré con ese para ver si es el cable u es otra cosa. Si si tranquilo el cable esta puesto en 1 lan, no creo que vuelva a cometer ese tipo de error garrafal!jej(que vergüenza!!)

pero e probado el conectar con el cable al portatil desde donde escribo y tampoco me funciona asique igual si es el cable...ahora probare con el otro cable en este laptop y mañana te comento como fue la cosa que ya son las 12 de la mañana y hay que descansar.

Muchisimas gracias por la ayuda!!

---

### Post by sitodonosti on 2009-06-26
Bueno ya he comprobado con otro cable y la configuración va bien, por lo que el cable no estará bien, lo malo es que el cable con el que he probado no llega desde donde tengo el router hasta mi cuarto así que tendré que llamar a mi tio el electricista para que me lo arregle ejjeje

Bueno muchas gracias guillermolisi estaba a punto de darme por rendido, pondré esta solución en ubuntu-es por si alguno en España tiene el mismo problema. Espero tener internet en este ordenador pronto y GRACIAS otra vez.

Un saludo desde Donosti(Gipuzkoa)

---

### Post by guillermolisi on 2009-06-26
> **sitodonosti said:**
> Bueno ya he comprobado con otro cable y la configuración va bien, por lo que el cable no estará bien, lo malo es que el cable con el que he probado no llega desde donde tengo el router hasta mi cuarto así que tendré que llamar a mi tio el electricista para que me lo arregle ejjeje

Bueno muchas gracias guillermolisi estaba a punto de darme por rendido, pondré esta solución en ubuntu-es por si alguno en España tiene el mismo problema. Espero tener internet en este ordenador pronto y GRACIAS otra vez.

Un saludo desde Donosti(Gipuzkoa)
La solucion, en definitiva, era probar con otro cable antes de modificar la configuracion de la placa de red.

Me alegro que ya funcione. Saludos.

Edit: Al final termino siendo un problema de hardware.

---

### Post by sitodonosti on 2009-07-31
hola, vuelvo a las andadas, resulta que el cable ahora lo conecto al portatil y funciona por lo que sospecho que el cable no es...estoy escribiendo conectado a traves de cabel y va perfectamente, sin embargo cuando lo enchufo a la torre no se conecta.

El led de latarjeta de red se pone en verde pero no consigo tener internet, ademas en el applet para conectarme a internet en nombre de la conexión pone esto:

nombre:eth1:avahi
estado:error

el cable no es por que lo estoy utilizando además cuando hago ifconfig me da esto, lo que pongo en rojo es lo que no entiendo que hace ay:
sito@sitotorre:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:07:95:2f:7a:55  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:11 Dirección base: 0xd400 

eth1      Link encap:Ethernet  direcciónHW 00:80:5a:78:02:27  
          dirección inet6: fe80::280:5aff:fe78:227/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:484 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:37408 (37.4 KB)
          Interrupción:11 Dirección base: 0xd000 

[COLOR="Red"]eth1:avahi Link encap:Ethernet  direcciónHW 00:80:5a:78:02:27  
          inet dirección:169.254.3.104  Difusión:169.254.255.255  Máscara:255.255.0.0
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          Interrupción:11 Dirección base: 0xd000 [/COLOR]

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:266 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:24355 (24.3 KB)  TX bytes:24355 (24.3 KB)

ahora si tecleo esto si me pone  que detecta el cable:
sito@sitotorre:~$ sudo ethtool eth1
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: yes

que hago alguien sabe porque?

---

### Post by guillermolisi on 2009-07-31
Me llama la atencion que eth1 tenga dos instancias, una discreta (que para mi es la correcta aunque no tenga asignada ninguna IP) y una vinculada con avahi (que para mi esta mal y la IP asociada es la que generalmente se pone cuando falla la asignacion dinamica de direccion).

Estas usando un servidor DHCP3 en esa instalacion ? (disculpame si esto ya se toco en este thread pero sinceramente me dio fiaca releerlo desde el principio, my fault).

Si no es asi y utilizan direcciones estaticas, podrias asignarle una libre a eth1 para probar ?

---

### Post by sitodonosti on 2009-07-31
no el servidor no es dhcp3 es sin el tres o eso tengo pueso en el router

a mi la verda me parece muy extraño lo del avahi y nose lo que es la verda...yo creo que eso se tendria que kitar no?

podria poner una dinamica a este ordenadro, pero esque tengo lxde y nose como hacerlo, en ubuntu con gnome si pero en lxde sigo sin encontrarlo...

---

### Post by guillermolisi on 2009-07-31
Dinamica no, estatica habras querido decir, y para hacerlo solo necesitas un editor de texto (nano o equivalente) y la IP estatica que tengas libre en tu red.

El archivo que tenes que editar es el /etc/network/interfaces. Te paso uno para que lo tomes como ejemplo y modifiques las IPs por la que usaras en tu caso:
```
iface eth1 inet dhcp
auto eth1

iface eth0 inet static
address 90.0.0.1
netmask 255.255.255.0
gateway 90.0.0.2
network 90.0.0.0
dns-nameservers 90.0.0.2
dns-search unimix
auto eth0
```
En el ejemplo veras que eth1 esta definida para que tome una IP en forma dinamica desde un servidor DHCP (lo del 3 es anecdotico para el caso). Si esto es lo que queres obtener para tu maquina, deberia estar definida de igual forma (salvo la identificacion de la placa, claro esta).

En el caso de eth0 del ejemplo, esa placa posee una direccion estatica (que le asigne editando el archivo luego de determinar cual estaba libre en mi red), con su mascara de red, en que direccion esta la maquina que oficia de gateway/pasarela, en que red operara, que servidor DNS interno le prestara servicio y en que dominio/zona trabajara.

Todo eso lo defini a mano con un editor.

---

### Post by sitodonosti on 2009-07-31
he puesto el ejemplo que me has puesto en el, solo que en vez de eth0 e puesto eth1 y eth0 como dhcp bueno mejor te pongo como lo he peusto jiji:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iface eth1 inet static
address 192.168.1.54
netmask 255.255.255.0
gateway 90.0.0.2
network 90.0.0.0
dns-nameservers 90.0.0.2
dns-search unimix
auto eth1

estoy enrando al router para ver lo de el gateway si es ese o no

cambiando esto en las opciones para conectarme me aparece esto
eth1
eth0:avahi
lo

si pongo nm-applet me aparece el mismo icono que en gnome, y el red cableada me pone lo siguiente:
red cableada (realtek trl-8139/8139c/8139c+)
el dispositivo no está gestionado

---

### Post by guillermolisi on 2009-07-31
> **sitodonosti said:**
> he puesto el ejemplo que me has puesto en el, solo que en vez de eth0 e puesto eth1 y eth0 como dhcp bueno mejor te pongo como lo he peusto jiji:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iface eth1 inet static
address 192.168.1.54
netmask 255.255.255.0
gateway 90.0.0.2
network 90.0.0.0
dns-nameservers 90.0.0.2
dns-search unimix
auto eth1

estoy enrando al router para ver lo de el gateway si es ese o no

cambiando esto en las opciones para conectarme me aparece esto
eth1
eth0:avahi
lo
Te falta cambiar las otras IPs que dejaste como las que te pase en el ejemplo y que no corresponden a tu red (las que son del bloque 90.x.x.x) y el dominio/zona del DNS (que podes descartar eventualmente, no es una declaracion obligatoria para que funcione la conexion de red).

En direccion IP funciona el servidor DHCP ?

---

### Post by sitodonosti on 2009-07-31
> **guillermolisi said:**
> 

En direccion IP funciona el servidor DHCP ?

no enteidno lo que me kieres decir con direccion ip funciona el servido dchp
nose que me keires decir :$

estado mirando en el router y no encontrado nada de lo que me has dicho esto e econtrado
las dns de mi compañia telefónica
y default gateway que ponia :mylsp

---

### Post by guillermolisi on 2009-07-31
> **sitodonosti said:**
> no enteidno lo que me kieres decir con direccion ip funciona el servido dchp
nose que me keires decir :$

estado mirando en el router y no encontrado nada de lo que me has dicho esto e econtrado
las dns de mi compañia telefónica
y default gateway que ponia :mylsp
Disculpame, omiti una palabra (me falto una taza mas de cafe para despertarme).

Lo que te preguntaba es si sabes en que direccion IP esta el servidor DHCP, si tenes uno.

Luego, y leyendo lo ultimo que pusiste, como es la red que estas utilizando ? Es una PC conectada directamente a Internet via ADSL, Cable o similar ?
Hay otras maquinas, firewall, proxy, etc. ?
Hay un router ?

---

### Post by sitodonosti on 2009-07-31
pos aer yo tengo un router adsl, wifi marca zyxel contratado con telefonica españa la ip se que es 192.168.1.33-192.168.1.230 y tengo la dns

no, no tengo ni firewal,ni proxy ni na esta directamente coenctado a internet

---

### Post by guillermolisi on 2009-07-31
> **sitodonosti said:**
> pos aer yo tengo un router adsl, wifi marca zyxel contratado con telefonica españa la ip se que es 192.168.1.33-192.168.1.230 y tengo la dns

no, no tengo ni firewal,ni proxy ni na esta directamente coenctado a internet
A ver ... esta claro que tenes una PC conectada directamente a un modem/router ADSL via cable Ethernet y con la posibilidad de WiFi.

Ahora y a efectos de aclarar algunos puntos, las direcciones IP que mencionas a que corresponden exactamente, cual es la del modem/router de las dos que decis conocer ?

La que corresponda al modem/router es la que va como gateway/pasarela y con eso ya deberias poder poder obtener la direccion IP del resto de los servidores de Telefonica (siempre que el modem/router este bien configurado).

---

### Post by sitodonosti on 2009-08-01
pues a ver para entrar a la configuración del router es 192.168.1.1
y el router te da estas ip por dhcp de 192.168.1.33 hasta 192.168.1.230

el gateway me pone mylsp, entrado en el router y no me pone nada mas...

---

### Post by guillermolisi on 2009-08-01
> **sitodonosti said:**
> pues a ver para entrar a la configuración del router es 192.168.1.1
y el router te da estas ip por dhcp de 192.168.1.33 hasta 192.168.1.230

el gateway me pone mylsp, entrado en el router y no me pone nada mas...
Proba con esta configuracion:
```
iface eth0 inet static
address 192.168.1.32
netmask 255.255.255.0
gateway 192.168.1.1
auto eth0
```

La IP que le di esta fuera del rango que asigna el DHCP del router.

Proba y comenta que resulto.

---

### Post by sitodonosti on 2009-08-01
Bueno e vuelto a reinstalar ubuntu y ahroa si que me reconoce la tarjeta de red solo que no se conecta....creo que voya ***** la tarjeta wifi del otro ordenador y cambiarlo, poner wifi a este y ethernet al de mis papas con windows...

---

### Post by guillermolisi on 2009-08-01
O sea, mas o menos estas como al principio, aun despues de reinstalar, o no ?

---

### Post by sitodonosti on 2009-08-01
bueno no del todo antes no me aparecia para poder conectarme a eth1 ahroa si me parece sol oque no se conectar...

---

