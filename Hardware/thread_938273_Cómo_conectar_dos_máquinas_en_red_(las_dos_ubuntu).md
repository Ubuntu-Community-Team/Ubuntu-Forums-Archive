---
title: "Cómo conectar dos máquinas en red (las dos ubuntu)"
date: 2008-10-04
forum: Hardware
---

### Post by erdosain9 on 2008-10-04
HOla. Pues eso... tengo las dos máquinas con ubuntu 8.04 y quería saber cómo conectarlas en red... para compartir la conexión a internet (primero y principal)... y luego para compartir archivos...
El modem está conectado a la placa interna de red de la mother... y la otra computadora esta conectada por otra placa de red...

Aún no tengo conocimientos sobre linux por lo que si me dan una explicación detallada se agradece...

Saludos y gracias

---

### Post by gmunioz on 2008-10-04
Hola erd....:
Lo más practico es que te compres un router, alrededor de $90, conectes el modem a la entrada wlan y las pcs a las salidas del router mediante cables directos.
Al router lo configuras segun su manual entrando al mismo, en general su dirección es 192.168.1.1, mediante un navegador desde cualquiera de las pcs, su usuario y contraseña suele ser admin admin ó admin 123456, el router con tu nombre de usuario y contraseña se encarga de comunicarse a internet automáticamente a traves del modem y por dhcp te administra las ips de las pcs, las conecta en red y les da acceso a internet.
En las pcs te instalas samba, samba-common y smbclient, cargas nautilus desde una consola con la orden 
sudo nautilus
navegas hasta /media o hasta /home/usuario/carpeta-a-compartir y en ambas pcs, luego de crear los directorios, carpetas, o ya creados pulsando el boton derecho eliges opciones de compartición y le das compartir carpetas acceso invitado y ya estarian listas para ser accedidas.

Si no quieres comprar el router, deberás tener siempre encendida la pc conectada al modem para conectarte a internet con la otra, deberás conectarlas entre si mediante un cable cruzado a traves de sus tarjetas de red y habilitar compartir internet mediante alguno de los siguientes procedimientos:

Para compartir la conexión a internet tenemos muchas formas distintas, aqui tienes tres:
A) Mediante el uso de squid.
B) Mediante el uso de iptables. 
C) mediante el uso de un bridge

Compartir la conexión con un proxy Squid

Instalas squid desde synaptic
Para configurar squid, basta configurar el fichero "squid.conf" 
sudo gedit /etc/squid.conf
Suponiendo tu red local es del tipo 192.168.1.0/255.255.255.0
Debes prestar atención a los siguientes items:

http_port 3128 
(este es el puerto por el que escuchara squid)
cache_mem 16 
(tamaño máximo que pueden alcanzar los objetos cacheados).
acl all src 0.0.0.0/0.0.0.0 
(creas una lista de acceso con todas las redes)
acl localhost src 127.0.0.1/255.255.255.255 
(creas una lista de acceso con
la propia maquina)
acl mired src 192.168.1.0/255.255.255.0 
(creas una lista de acceso con tu red)
http_access allow localhost 
(permites el acceso a la propia maquina)
http_access allow mired 
(permites el acceso a tu red local)
http_access deny all 
(deniegas el acceso al resto de la red)
httpd_accel_host virtual
httpd_accel_port 0 
(habilitas cache acelerada para cualquier puerto)
http_accel_with_proxy on


Y todas las demás opciones las dejaos como vienen por defecto. 
En los clientes, solo comentar que en cada una de las aplicaciones que utilices de cara a internet habrá que configurar como proxy el que acabas de configurar. 

En el firefox sería:

Edición - Preferencias - Avanzadas - Proxies
Aquí, marcas la casilla de "Configuración manual del proxy" y en la casilla
"Proxy HTTP" pones la dirección IP y como puerto el 3128 


B)Compartir la conexión con Iptables
Iptables funciona de forma parecida a las reglas de acceso del proxy squid, para compartir la conexión a internet debes "Hacer NAT de tu red local", 

Hacer NAT/MASQUERADE de una red, es simplemente enmascarar las ip's de dicha red con otra diferente, es decir, imaginemos una maquina cuya ip es 192.168.1.1 que sirve de pasarela de otra maquina cuya ip es 192.168.1.2. Hacer NAT de esta última maquina, significa que de cara al exterior las conexiones las estará haciendo 192.168.1.1, aunque sea 192.168.1.2, la que esté accediendo al exterior.


La forma de utilizar iptables, es ir escribiendo regla por regla, recordando la misma limitación del orden de las reglas que tenías en el proxy. 
Como estas reglas se guardan en memoria, perdiéndose cuando apagas el ordenado, para evitarlo, lo que puedes hacer es escribir en orden las reglas en un script, el cual puedes ejecutar en el inicio del sistema
Para ello, editamos un fichero de texto, por ejemplo, "/etc/init.d/firewall", donde pondras esto 
Suponiendo que tu red local es del tipo 192.168.1.0 y sales a Internet a traves de la interfaz eth0. 

modprobe iptable_nat 
iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
Hay otra forma de hacerlo, podemos editar el fichero /etc/sysctl.conf y descomentar o añadir (segun este o no) la linea:
# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1
Acto seguido, reiniciamos el equipo y tendremos el NAT masquerading siempre activado por defecto.

Tambien se pueden activar entre otras cosas:
#net/ipv4/icmp_echo_ignore_broadcasts=1
# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1
# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

Una vez lo tenemos, le damos permisos de ejecución:

sudo chmod +x /etc/init.d/firewall
Y lo pones en el arranque del sistema:
sudo ln -s /etc/init.d/firewall /etc/rc2.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc3.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc4.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc5.d/S99firewall

Configuración de los clientes
En los clientes de tu red local, lo único que tendrás que hacer es poner como puerta de enlace predeterminada (o gateway), la ip de la maquina que acabas de configurar.

C) Mediante el uso de un bridge

El primer paso para crear un bridge es instalar el paquete bridge-utils.
sudo apt-get install bridge-utils
Luego, se inicializan las interfaces de red

sudo ifconfig eth0 0.0.0.0
sudo ifconfig eth1 0.0.0.0
sudo brctl addbr br0
sudo brctl addif br0 eth0
sudo brctl addif br0 eth1
sudo ifconfig br0 up
Opcionalmente puede ser deseable que el bridge tenga una IP, se puede hacer así:
sudo ifconfig br0 192.168.0.2 netmask 255.255.255.0 up
sudo route add default gw  192.168.0.1 dev br0
La IP del bridge sería 192.168.0.2
La IP del gateway se encuentra en uno de los segmentos configurados en el bridge, eth0 o eth1

Una vez se tiene el bridge con IP, se puede hacer un brouter, que es un bridge + un router.
Con las IPs del ejemplo:
sudo echo "1" > /proc/sys/net/ipv4/ip_forward
sudo iptables -t nat -A POSTROUTING --source 192.168.0.0/24 -j SNAT --to-source 192.168.0.2

Para desconfigurar el bridge:
# Descomentar si el bridge tiene IP
#
#route del default gw 192.168.0.1 dev br0
#ifconfig br0 down
brctl delif br0 eth0
brctl delif br0 eth1
ifconfig eth0 down
ifconfig eth1 down
brctl delbr br0

Saludos. Gabriel.
Solo doy soporte para Ubuntu. - 6666 - Mas malo que el diablo.

---

### Post by WanderingKnight on 2008-10-04
Ehm, me parece que tal vez gmunioz (aunque en toda buena voluntad) la complicó demasiado con el tema del squid y del bridge... honestamente no le veo la utilidad para un seteo hogareño de dos máquinas. Lo único que necesitás es un router. El router lo conectás al módem en el puerto que dice WAN, y después conectás cada máquina a los otros puertos del router. Linux por defecto cuando estás detrás de un router (al menos en mi experiencia) genera una IP estática mientras que la IP al mundo exterior (que esa, a menos que tengas una conexión empresarial, sí o sí es dinámica) la maneja el router mismo.

Lo que vas a tener cuando las tengas en red es que cada máquina va a tener una IP de "intranet" asignada (192.168.1.xxx). Luego el tema de compartir archivos se realiza mediante samba como lo explicó gmunioz... aunque nunca lo intenté, es muy posible también que haya formas más directas, pero la del samba me parece la más sencilla.

---

### Post by pol666 on 2008-10-04
osea vos decis que unas vez que la red esta lista, se comparte internet automaticamente?

---

### Post by WanderingKnight on 2008-10-04
> osea vos decis que unas vez que la red esta lista, se comparte internet automaticamente?

Eeh, sí, es la principal función del router... routear internet. El aparatito se encarga de realizar DHCP y conseguirse una IP exterior para sí mismo, y luego asigna una IP interna a cada máquina que tiene conectada. Cuando te lleguen requests a tu máquina, en realidad están llegando requests a la IP externa asignada al router, y el router simplemente las redirecciona a la máquina correcta.

BTW, "la interné" no "la tiene" una máquina, sino que les llega a ellas... el router lo que hace es que les llegue a las dos al mismo tiempo.

PD: Cualquiera que tiene un router puede hacer la prueba e ir a una de esas páginas tipo [www.whatismyip.com](http://www.whatismyip.com) y va a notar que la IP que le tira es distinta a la que tiene asignada internamente.

---

### Post by pol666 on 2008-10-05
aaaah gracias, nunca me quedo claro como era lo de las redes.

---

### Post by erdosain9 on 2008-10-05
Hola gmunioz... gracias por tu extensa respuesta.  Te comento que no tiene interés para mi perder la conexión a internet al apagarse alguna de las máquina... y que la conexión de cable ya la tengo hecha... El proveedor que tengo es Fibertel...
Cómo se haría en ese caso la conexión... y de los tres métodos que me recomendás cuál es el que menos recursos gasta... por ejemplo quisiera evitar la instalación de un firewall...
Saludos y gracias de vuelta
Erdosain9

---

### Post by santiagofrias on 2008-10-05
Sin desvirtuar el tema, tuve un inconveniente entre mis dos máquinas en red; hasta ayer, ambas máquinas (una PC y una Laptop), se comunicaban entre las dos y compartían internet y una pequña red hogareña mediante un router con una conexión inalámbrica para la laptop. Todo perfecto hasta que por un problema ajeno se corto en mi edificio el cable de telefono (adsl de Arnet) y el día de hoy ya no pude ver mediante la red ninguna de las dos máquinas.
El hecho que no tenga la conexion adsl, tiene algo que ver a pesar que el router esta prendido y que puedo ver las maquinas en Windows?
Gracias desde ya.

---

### Post by erdosain9 on 2008-10-05
Todo bien santiagofrias... no tengo idea sobre lo que preguntás, como verás soy muuuuy nuevo, yo no puedo ayudarte...
Ya que vos tenés conectado:
Sabés cómo lograr la conexión sin router... En windows hay que toquetear en las dos máquinas...
Según lo que me escribieron parece que acá (en ubuntu) sólo una::::

Lo que hice fue esto:

modprobe iptable_nat
iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o eth1 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

Acto seguido, reiniciamos el equipo y tendremos el NAT masquerading siempre activado por defecto.

sudo chmod +x /etc/init.d/firewall
Y lo pones en el arranque del sistema:
sudo ln -s /etc/init.d/firewall /etc/rc2.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc3.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc4.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc5.d/S99firewall

Configuración de los clientes
En los clientes de tu red local, lo único que tendrás que hacer es poner como puerta de enlace predeterminada (o gateway), la ip de la maquina que acabas de configurar.

Ahí fui a Sistema/Administración/Red/
Solapa /anfitriones y agregué con anfitrión la ip 192.168.1.0

Pero no conecta... qué estoy haciendo mal
Por cierto... mi conexión a internet sale por el eth1


ayuda!!!!

---

### Post by erdosain9 on 2008-10-05
Me voy a ir ahora por esta respuesta:
sudo apt-get install bridge-utils
sudo ifconfig eth0 0.0.0.0
sudo ifconfig eth1 0.0.0.0
sudo brctl addbr br0
sudo brctl addif br0 eth0
sudo brctl addif br0 eth1
sudo ifconfig br0 up
sudo ifconfig br0 dhcp start

es necesario algo más??? lo tengo que hacer también en la otra máquina??

Saludos y gracias por contestarme.

P.d:: tengo que deshacer de alguna manera los cambios que hice al seguir la opción anterior...¿?¿?¿?

---

### Post by erdosain9 on 2008-10-05
pues cuando realizo esto del bridge me quedo sin conexión, por suerte al reiniciar ya vuelvo a tener!! qué puedo hacer???
dónde dice 0.0.0.0 tengo que poner un valor como el de 192.168.0.1???

---

### Post by faktorqm on 2008-10-06
No se si Gabriel lo nombro pero con Firestarter la conexion de hace en 1-2-3 al mejor estilo sig sig sig. Busca en el gestor de paquetes firestarter e instalatelo, te comparte internet en 2 minutos. Salu2!

---

### Post by gmunioz on 2008-10-06
Hola erd...:
Paso a paso:
Primero habilita definitivamente el forwarding en el kernel, ejecutando en consola:
sudo gedit /etc/sysctl.conf

Buscas las líneas que dicen:
# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

Y la dejas asi:
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

Guardas el archivo.

Pulsas nuevo y le pegas este contenido:


#!/bin/sh
# Script para habilitar conexión compartida de internet

# Limpieza de las reglas

iptables -F
iptables -X
iptables -Z
iptables -F -t nat
iptables -X -t nat
iptables -Z -t nat
iptables -F -t mangle
iptables -X -t mangle
iptables -Z -t mangle
iptables -F -t filter
iptables -X -t filter
iptables -Z -t filter

# Habilitación de compartición

iptables -A INPUT -i eth0 -j ACCEPT
iptables -t nat -A POSTROUTING -s eth0 -o eth1 -j MASQUERADE
iptables -A FORWARD -i eth0 -j ACCEPT


Lo guardas en /etc/init.d con el nombre firewall, aceptando sobrescribir el archivo creado anteriormente.
Cierras gedit
Ejecutas
sudo chmod +x /etc/init.d/firewall

Cierras la consola y reinicias, los enlaces ya fueron creados en tus otros procedimientos, eth1 segun dices es la conexión al cablemodem y eth0 a la otra pc, que ya estan configuradas y funcionando.

Saludos. Gabriel.

---

### Post by erdosain9 on 2008-10-06
Hola  faktorqm te comento que probé con el Firestarter... y el resultado es este:

No se pudo arrancar el cortafuegos
El dispositivo eth0 no está preparado.
Compruebe la configuración de su dispositivo de red y asegúrese de que su conexión a internet está disponible

Pues está disponible porque te estoy escribiendo desde la máquina...

Luego Gabriel te comento que seguí al pie de la letra todo... excepto que cambié lo de eth0 por eth1 y viceversa... porque me había equivocado... mi conexión a internet SI sale por eth0 (el tema es que en administración/red el orden no es 0 1 sino que es  1 0... y evidentemente estuve medio quemado y no ví los números sólo el orden...

Pues no logro que se conecte...

Cuando decís "cierras la consola y reinicias, los enlaces ya fueron creados en tus otros procedimientos" con "en tus otros procedimientos" te referís a lo del bridge o los iptables... porque tal vez se desconfiguró algo de eso porque le vengo metiendo mano a cada rato... 

No me decís nada para poner en la otra máquina (es que no hace falta??? (acostumbrado a xp))

Se me acaba de ocurrir algo... que tal vez no tenga nada que ver pero no sé... Pues que la otra máquina (cliente ahora) cuando yo le instalé el ubuntu lo hice con conexión a internet... es decir, estaba conectada a internet directamente... puede ser que algo haya quedado configurado de tal manera que al ponerla como cliente en este momento ya no lo acepte... Tal vez lo que planteo es una tontería... pero se entiende lo que digo, tendré que reconfigurar algo en esa también???

Por favor, tenés idea qué puedo hacer???  (te voy a seguir por este foro porque el -es es muy lento...

Mil gracias, por prestarme atención (ni yo ya soporto esto)...

Saludos erdosain9

---

### Post by erdosain9 on 2008-10-07
Alguien puede ayudarme???

---

### Post by faktorqm on 2008-10-07
si capo, estoy siguiendo tu thread, pero si el firestarter te tira error y seguiste la/las soluciones de gabriel (que estan muy bien por cierto) mejor que el te conteste por que la verdad que ya tocaste mucho y estoy mareado, asi que poco te puedo recomendar. (incluso, y sin levantar flame por esto, si el resto de las cosas no te andan del todo bien, podrias pensar en reinstalar, si es por esto solo, dejao asi, no lo hagas.)
Salu2!

---

### Post by gmunioz on 2008-10-07
Hola erd...:
Soy partidario de que lo que no anda se arregla y al contrario de windows, reinstalar solo si el sistema de archivos se inutilizó.
Recapitulando:
===========================================================================

Primero habilita definitivamente el forwarding en el kernel, ejecutando en consola:
sudo gedit /etc/sysctl.conf

Buscas las líneas que dicen:
# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

Y la dejas asi:
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

Guardas el archivo.

*(Esta modificación es definitiva, no degrada el sistema y si no se usa no afecta el uso ni el funcionamiento de la pc.)*

Pulsas en  nuevo, en el archivo que se abre pegas el siguiente contenido:


#!/bin/sh
# Script para habilitar conexión compartida de internet

# Limpieza de las reglas
iptables -F
iptables -X
iptables -Z
iptables -F -t nat
iptables -X -t nat
iptables -Z -t nat
iptables -F -t mangle
iptables -X -t mangle
iptables -Z -t mangle
iptables -F -t filter
iptables -X -t filter
iptables -Z -t filter

# Habilitación de compartición
iptables -A INPUT -i eth1 -j ACCEPT
iptables -t nat -A POSTROUTING -s eth1 -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth0 -j ACCEPT


Lo guardas en /etc/init.d/ con el nombre firewall, aceptando sobrescribir el archivo creado anteriormente.
Cierras gedit

Ejecutas
sudo chmod +x /etc/init.d/firewall
sudo ln -s /etc/init.d/firewall /etc/rc2.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc3.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc4.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc5.d/S99firewall

*(Esto de acuerdo con los nuevos datos, la salida a internet es por eth0)*

Configuración de los clientes

En los clientes de tu red local, lo único que tendrás que hacer es poner como puerta de enlace predeterminada (o gateway), la ip de la maquina que acabas de configurar.

Saludos. Gabriel. Intrepid *(Mad)* User

---

### Post by erdosain9 on 2008-10-07
Gracias Gabriel, seguí todo nuevamente paso a paso...
Pero tengo una duda, cuando ponés esto:

"Configuración de los clientes

En los clientes de tu red local, lo único que tendrás que hacer es poner como puerta de enlace predeterminada (o gateway), la ip de la maquina que acabas de configurar".

Bueno, para conocer la ip toqué en el ícono de dos monitores con el botón derecho y puse "información de la conexión".  Anoté la ip, la difusión, máscara de subred, ruta predeterminada, dns primario, dns secundario (por si acaso) en un papel...
Pues bien al ir a la máquina cliente, fui a Sistema/Administración/Red... ahí desbloquee y hice click en propiedades... pues bien, puse en "configuración" Dirección ip estática... 

Se supone que en "Dirección de puerta de enlace" tengo que poner la ip de la máquina servidor??? y qué pongo que las demás casillas: "Dirección ip", "Máscara de subred" ????? (puse un número cualquiera y no funcionó)

P.D.: y por cierto, esto sólo lo hago en la máquina cliente y no también en la conexión eth1 de la máquina servidor??? (la cual figura en modo itinerante)

Saludos y gracias nuevamente.

---

### Post by erdosain9 on 2008-10-07
Pues cansado de no poder poner la red... reinstalé el S.O.  y me fui por la opción fácil: firestarter... pues me dice estas características ahora:

eth0 local
eth1 internet ... y aparecen los megas recibidos, enviados, y la actividad que en eth0 es nula, por lo pronto...

Al poner iniciar cortafuegos, me da este error:
"el dispositivo eth1 no está preparado, compruebe la configuración de su dispositivo de red y asegurese de que su conexión a internet está disponible"

¿por qué?

¿Debo hacer algo en la máquina cliente??? ¿hay que hacer algo más en la máquina servidor???

Saludos

Por cierto, en el asistente en la pantalla de activar la conexión de compartición a internet... las opciones de "activar dhcp para red local" y los "detalles del servidor dhcp" aparecen grisados... será eso???

---

### Post by Hei Ku on 2008-10-07
El firestarter en la version de Hardy tiene un bug.

Para solucionarlo:
abrí una terminal y escribi

```

 sudo gedit /etc/firestarter/firestarter.sh

```

después tenes que cambiar la linea

```

MASK=`/sbin/ifconfig $IF | grep Mas | cut -d : -f 4`

```
le tenes que agregar el tilde al mas o sea que quede

```

MASK=`/sbin/ifconfig $IF | grep Más | cut -d : -f 4`

```

---

### Post by erdosain9 on 2008-10-07
jaja, si lo acabo de encontrar...

[http://www.n0xtrum.com/2008/04/error-al-iniciar-firestarter-en-ubuntu.html](http://www.n0xtrum.com/2008/04/error-al-iniciar-firestarter-en-ubuntu.html)

el tema es que al cambiarlo que por cierto, hay otro un poco más abajo... al volverlo a abrir el asistente vuelve a estar cambiado... vuelve a cambiar el archivo por el anterior... 
¿Cómo se hace para que no lo renueve?
Y el asistente lo reinicio para poder activar las opciones grisadas que parece son importantes... tal vez no, si es así... me pasarías tu archivo así lo copio entero o me dirías qué tengo que cambiar para tener las opciones grisadas sin ejecutar el asistente!!

Y si pongo iniciar el cortafuegos sin volver a pasar por el asistente me dice:

El dispositivo eth0 no está preparado, etc. etc.

---

### Post by Hei Ku on 2008-10-07
Postea el archivo aca asi lo vemos

---

### Post by erdosain9 on 2008-10-07
Acá pego todo el archivo... por cierto ahora reinstalé todo nuevamente y me toma a eth0 como internet...

#!/bin/bash
#-----------( Firestarter Control Script )-----------#

# Load Configuration
source /etc/firestarter/configuration 2>&1

# --(Set program paths)--

IPT=/sbin/iptables
IFC=/sbin/ifconfig
MPB=/sbin/modprobe
LSM=/sbin/lsmod
RMM=/sbin/rmmod


# --(Extract Network Information)--

# External network interface data
IP=`/sbin/ifconfig $IF | grep inet | cut -d : -f 2 | cut -d \  -f 1`
MASK=`/sbin/ifconfig $IF | grep Más | cut -d : -f 4`
BCAST=`/sbin/ifconfig $IF |grep Bcast: | cut -d : -f 3 | cut -d \  -f 1`
NET=$IP/$MASK

if [ "$NAT" = "on" ]; then
	# Internal network interface data
	INIP=`/sbin/ifconfig $INIF | grep inet | cut -d : -f 2 | cut -d \  -f 1`
	INMASK=`/sbin/ifconfig $INIF | grep Más | cut -d : -f 4`
	INBCAST=`/sbin/ifconfig $INIF |grep Bcast: | cut -d : -f 3 | cut -d \  -f 1`
	INNET=$INIP/$INMASK
fi

if [ "$MASK" = "" -a "$1" != "stop" ]; then
	echo "External network device $IF is not ready. Aborting.."
	exit 2
fi

if [ "$NAT" = "on" ]; then
	if [ "$INMASK" = "" -a "$1" != "stop" ]; then
		echo "Internal network device $INIF is not ready. Aborting.."
		exit 3
	fi
fi


# --(Helper Functions)--

# Scrub data parameters before use
scrub_parameters () {
	target=`echo $target | sed 's/ //'g`
	port=`echo $port | sed 's/ //'g |  sed "s/-/:/"`
	ext_port=`echo $ext_port | sed 's/ //'g |  sed "s/-/:/"`
	int_port_dashed=`echo $int_port | sed 's/ //'g |  sed "s/:/-/"`
	int_port=`echo $int_port | sed 's/ //'g |  sed "s/-/:/"`
	if [ "$target" == "everyone" ]; then target=0/0
	else if [ "$target" == "firewall" ]; then target=$IP
	else if [ "$target" == "lan" ]; then target=$INNET
	fi fi fi
}


# --(Control Functions)--

# Create Firestarter lock file
lock_firestarter () {
	if [ -e /var/lock/subsys ]; then
		touch /var/lock/subsys/firestarter
	else
		touch /var/lock/firestarter
	fi
}

# Remove Firestarter lock file
unlock_firestarter () {
	if [ -e /var/lock/subsys ]; then

		rm -f /var/lock/subsys/firestarter
	else
		rm -f /var/lock/firestarter
	fi
}

# Start system DHCP server
start_dhcp_server () {
	if [ "$DHCP_DYNAMIC_DNS" = "on" ]; then
		NAMESERVER=
		# Load the DNS information into the dhcp configuration
		while read keyword value garbage
			do
			if [ "$keyword" = "nameserver" ]; then
				if [ "$NAMESERVER" = "" ]; then
					NAMESERVER="$value"
				else
					NAMESERVER="$NAMESERVER, $value"
				fi
			fi
			done < /etc/resolv.conf

		if [ "$NAMESERVER" != "" ]; then
			if [ -f /etc/dhcpd.conf ]; then
				sed "s/domain-name-servers.*$/domain-name-servers $NAMESERVER;/" /etc/dhcpd.conf > /etc/dhcpd.conf.tmp
				mv /etc/dhcpd.conf.tmp /etc/dhcpd.conf
			fi
			if [ -f /etc/dhcp3/dhcpd.conf ]; then
				sed "s/domain-name-servers.*$/domain-name-servers $NAMESERVER;/" /etc/dhcp3/dhcpd.conf > /etc/dhcp3/dhcpd.conf.tmp
				mv /etc/dhcp3/dhcpd.conf.tmp /etc/dhcp3/dhcpd.conf
			fi
		else
			echo -e "Warning: Could not determine new DNS settings for DHCP\nKeeping old configuration"
		fi
	fi

   if [ -e /etc/init.d/dhcp3-server ]; then
		/etc/init.d/dhcp3-server restart > /dev/null
	elif [ -e /etc/init.d/dhcpd ]; then
		  /etc/init.d/dhcpd restart > /dev/null
	elif [ -e /etc/init.d/dnsmasq ]; then
		  /etc/init.d/dnsmasq restart > /dev/null
	else
		/usr/sbin/dhcpd 2> /dev/null
	fi

	if [ $? -ne 0 ]; then
		echo Failed to start DHCP server
		exit 200
	fi
}

# Start the firewall, enforcing traffic policy
start_firewall () {
	lock_firestarter
	source /etc/firestarter/firewall 2>&1
	retval=$?
	if [ $retval -eq 0 ]; then
		echo "Firewall started"
	else
		echo "Firewall not started"
		unlock_firestarter
	exit $retval
fi
}

# Stop the firewall, traffic flows freely
stop_firewall () {
	$IPT -F
	$IPT -X
	$IPT -Z
	$IPT -P INPUT ACCEPT
	$IPT -P FORWARD ACCEPT
	$IPT -P OUTPUT ACCEPT
	$IPT -t mangle -F 2>/dev/null
	$IPT -t mangle -X 2>/dev/null
	$IPT -t mangle -Z 2>/dev/null
	$IPT -t nat -F 2>/dev/null
	$IPT -t nat -X 2>/dev/null
	$IPT -t nat -Z 2>/dev/null
	retval=$?
	if [ $retval -eq 0 ]; then
		unlock_firestarter
		echo "Firewall stopped"
	fi
	exit $retval
}

# Lock the firewall, blocking all traffic
lock_firewall () {
	$IPT -P INPUT DROP
	$IPT -P FORWARD DROP
	$IPT -P OUTPUT DROP
	$IPT -F;
	$IPT -X
	$IPT -Z
	retval=$?
	if [ $? -eq 0 ]; then
		echo "Firewall locked"
	fi
	exit $retval
}

# Report the status of the firewall
status () {
	if [ -e /var/lock/subsys/firestarter -o -e /var/lock/firestarter ]; then
		echo "Firestarter is running..."
	else
		echo "Firestarter is stopped"
	fi
}

case "$1" in
start)
	start_firewall
 	if [ "$NAT" = "on" -a "$DHCP_SERVER" = "on" ]; then
		start_dhcp_server
	fi
;;
stop)
	stop_firewall
;;
lock)
	lock_firewall
;;
status)
	status
;;
reload-inbound-policy)
	source /etc/firestarter/inbound/setup 2>&1
;;
reload-outbound-policy)
	source /etc/firestarter/outbound/setup 2>&1
;;
*)
	echo "usage: $0 {start|stop|lock|status}"
	exit 1
esac
exit 0

---

### Post by erdosain9 on 2008-10-07
Por cierto al reiniciar el ubuntu hay un mensaje de algo failed... y me parece que dice algo de network; cómo puedo hacer para leer qué es?? porque pasa demasiado rápido, y el botón pausa no lo para... habrá algo de volcado...
saludos

---

### Post by Hei Ku on 2008-10-07
Fijate en /var/logs/boot

---

### Post by erdosain9 on 2008-10-07
Perdón me expresé mal al reiniciar quise decir al poner reiniciar salta mientras se apaga... mientras finaliza...
donde me dijiste que me fijara no aparece nada pero supongo porque es el boot... y yo quería decir al apagar, finalizar (disculpá)

por cierto, lo poco que pude leer dice algo de network manager... varios failed y un bus connection failed, también algo así como nm_dbus_signal_device... y si no me equivoco también failed por ahí

---

### Post by Hei Ku on 2008-10-07
Fijate en /var/log/messages o daemon.log
Puede ser que algo aparezca ahi.

---

### Post by erdosain9 on 2008-10-07
mirá en el daemon encontré esto, al final:

NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

lo demás, si bien no sé... me parece bien...

y en message encontré esto:
Oct  8 00:37:15 computadora dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Oct  8 00:37:15 computadora dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct  8 00:37:15 computadora dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct  8 00:37:15 computadora dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct  8 00:37:16 computadora kernel: [   39.485416] NET: Registered protocol family 10
Oct  8 00:37:16 computadora kernel: [   39.485634] lo: Disabled Privacy Extensions
Oct  8 00:57:07 computadora -- MARK --
Oct  8 01:17:07 computadora -- MARK --
Oct  8 01:37:07 computadora -- MARK --

En user.log aparece esto:

Oct  7 22:59:30 computadora dhcdbd: Started up.
Oct  7 22:59:32 computadora dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct  7 22:59:37 computadora dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Oct  7 22:59:37 computadora dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct  7 22:59:37 computadora dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct  7 22:59:37 computadora dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu


ni idea... 

Luego veo si puedo llegar a anotar algo de lo que pasa al apagarla...

Por cierto, no tengo que hacer nada en la otra máquina (cliente) con este método (firestarter).

Saludos

---

### Post by faktorqm on 2008-10-08
pero te conectaste al final?

---

### Post by erdosain9 on 2008-10-08
pues no.  El firestarter me sigue tirando el error...!

¿tengo que hacer algo en la otra máquina (cliente) con este método (firestarter)???? ¿tendré que instalarlo también en la otra máquina??? algo habrá que hacer en la otra... O algo en la que es servidor en la solapa de sistema/administración/red

La cliente está en modo itinerante... tengo que cambiarle algo?? tal vez es eso...

Saludos

---

### Post by faktorqm on 2008-10-08
Si capo, te lo puso Gabriel en su ultimo post:

"En los clientes de tu red local, lo único que tendrás que hacer es poner como puerta de enlace predeterminada (o gateway), la ip de la maquina que acabas de configurar."

Eso es lo que hay que hacer, te fijas que ip le pusiste a tu "server" (ejemplo: 192.168.0.1) y vas a la cliente y le pones de IP otra distinta a esa (ejemplo: 192.168.0.15) y en donde dice puerta de enlace y dns le pones 192.168.0.1 (siguiendo con el ejemplo claro). Las mascaras las tenes que poner iguales en los dos, de lo contrario no anda.
Espero que te ande, sino volve a preguntar. Salu2!

---

### Post by erdosain9 on 2008-10-08
Veamos: supongo que ya casi (tengo esperanzas).

Máquina servidor:
   -voy a sistema/administración/red

   Allí me encuentro con: 
    -cableada eth1
    -cableada eth0

internet sale por eth0

qué hago?

mi ip es 190.19.105.197
máscara de subred: 255.255.255.0

le puse esta información a eth0 y la conexión no me funca... me refiero a la máquina servidor... qué hago?

Saludos

---

### Post by faktorqm on 2008-10-08
En el server deja eth0 como esta, si esa es la conexion a internet. 
En eth1 pone:

direccion ip: 192.168.0.1
mascara de subred: 255.255.255.0
puerta de enlace: VACIO

Quiero creer que eth1 tiene un cable cruzado hasta la otra computadora.
Configuracion para la computadora cliente:

direccion ip: 192.168.0.2
mascara de subred: 255.255.255.0
puerta de enlace: 192.168.0.1
DNS: 192.168.0.1

Salu2!

---

### Post by ramiro_md on 2008-10-08
Gente, tengo dos pc con internet mediante router. NO me queda claro como compartir archivos aun.
Instale los paquetes samba samba-common smbclient en ambas maquinas (desktop-laptop). Configure la compartición de mis carpetas, ahora como accedo a ellas desde la lap ? UN saludo.

---

### Post by erdosain9 on 2008-10-08
Pues tengo que decirle a todos MUCHAS GRACIAS!!!!!!!!!!!!!!!!!!!!!!!!
Ya tengo internet en red!!!!!!
Ah! Gracias por guiarme, la verdad que excelente su ayuda.
Saludos, por un tiempo.

Erdosain9

---

### Post by faktorqm on 2008-10-08
> **ramiro_md said:**
> Gente, tengo dos pc con internet mediante router. NO me queda claro como compartir archivos aun.
Instale los paquetes samba samba-common smbclient en ambas maquinas (desktop-laptop). Configure la compartición de mis carpetas, ahora como accedo a ellas desde la lap ? UN saludo.

Lee mi tutorial de samba: [http://ubuntuforums.org/showthread.php?t=940579](http://ubuntuforums.org/showthread.php?t=940579)
Salu2!

---

### Post by erdosain9 on 2008-10-08
Quería preguntar algo más... la velocidad en la máquina cliente es bastante lenta... (sin que la servidor este funcionando)... se puede hacer algo para que tenga más ancho de banda?

La servidor va más o menos en 70kb
La cliente sin estar en uso la servidor es muyyy oscilante... y va de 7 a 30kb...
es así o se puede mejorar... porque cuando tuve windows en red, la máquina cliente funcaba a buenas velocidades (las mismas que la servidor).

Tendrá que ver con Firestarter... no creo pero...

por cierto es natural que firestarter muestre actividad en eth0 aunque no haya ningun tipo de "navegación" en internet por la máquina servidor??????, me refiero a que si miro... ehhh, un ejemplo sería con la máquina servidor sin uso:

dispositivo tipo     recibido enviado actividad
eth0       internet  121,2mb   3.0mb      50kb/s     
eth1         local   2.0mb     59.2mb     30kb/s

El eth0 siempre tiene aún sin uso una velocidad "actividad" mayor a la de cliente...
¿por qué?

---

### Post by ramiro_md on 2008-10-09
Gracias faktorqm, lo solucionè...no preste atencion a "servidores de red" en nautilus. Un saludo. Graciias

---

### Post by proferrb on 2008-10-16
Saludos, quería saber si es posible y si es posible como hacerlo… quiero conectarme a Internet desde mi portátil utilizando WIRLESS pero utilizando otra portátil que se conecta através de una tarjeta gíreles 3GPASSPORT de KYOCERA.

Alguien me dijo que creara un “BRIDGE”  en la portátil que posee la tarjeta de KYOCERA y que de esa forma podía entrar al Internet desde mi portátil.

Espero puedan ayudarme, si es posible

---

