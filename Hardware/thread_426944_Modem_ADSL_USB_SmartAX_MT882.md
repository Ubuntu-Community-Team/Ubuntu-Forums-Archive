---
title: "Modem ADSL USB SmartAX MT882"
date: 2007-04-29
forum: Hardware
---

### Post by DuckMan on 2007-04-29
Asi es, necesito ayuda con este modem, una conocida quiere tener ubuntu porq el windows no para de morirse, pero tiene ese modem : Modem ADSL USB SmartAX MT882

encontre unos drivers q dejo adjuntos, la verdad no soy amigo de compilar, o lo q haya q hacer, si alguien me comenta q onda genial :O

y si no le digo q llame y pida uno con salida ethernet como me dijeron los pebetes en la flisol :O

saludos

---

### Post by sebas.rhcp on 2007-04-29
La marca es huawei?

---

### Post by DuckMan on 2007-04-29
exacto! :O

---

### Post by Gideon26 on 2007-04-29
Hola duckman yo encontre como configurarlo en la pagina ubuntu de españa te copio el How to aca para que pruebes lo que si donde dice br2684ctl -c 0 -b -a 0.33 (modifiques el 0.33 a 8.35 ese es el parametro de telefonica de argentina) bueno espero que te sirva acordate de cambiar esos parametros sino no vas a poder conectarte yo no lo puedo probar porque no tengo ese modem tengo un  zyxel p630-c1 pero por lo que pude ver trabaja muy similar bueno espero que sirva.

Buenas usuarios de Ubuntu!, como lo prometido es deuda voy a publicar el mini how to para configurar el modem usb adsl Huawei SmartAX MT810 (si el alfajorcito de luces verdes!) de TELECOM ARGENTINA (ojo que para otros ISP en la página [http://eagle-usb.org](http://eagle-usb.org) se detalla los valores que deben ir solo tienen que buscar el suyo) , tengan en cuenta que este how to es una combinación de dos how to que a mi me funcionaron perfectamente, bueno paso a contar detalladamente como se hace:

1-Paquetes necesarios:
rp-pppoe-3.8.tar.gz ( [http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php](http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php) )
br2684ctl.deb ( [http://packages.ubuntulinux.org/hoary/net/br2684ctl](http://packages.ubuntulinux.org/hoary/net/br2684ctl) bajen las dependencias que ahí les indican también)
ueagle-atm-1.3.tar.gz ( [http://download.gna.org/ueagleatm/ueagle-atm-1.3.tar.gz](http://download.gna.org/ueagleatm/ueagle-atm-1.3.tar.gz) )
ueagle-data-1.1.tar.gz ( [http://eagle-usb.org/ueagle-atm/non-free/](http://eagle-usb.org/ueagle-atm/non-free/) )

2-Configurar el sitema:
Bien paso a explicar algo que se debe entender bien, el driver incluido en UBUNTU 6.06 LTS es el eagle-usb, dicho driver es obsoleto a partir de la rama 2.6.10 del kernel, este es reemplazado entonces por el nuevo driver “ueagle-atm”. Para hacerlo funcionar primero debemos compilarlo, por eso instalaremos las herramientas esenciales, inserten el cd o dvd de ubuntu, abran una terminal (de paso no la cierren porque la vamos a necesitar en casi todo el proceso) y tipeen:

$ sudo apt-get install build-essential linux-headers-'uname -r'

NOTA: reemplazen el 'uname-r' por su version del kernel. Ej: en mí caso es: 2.6.15-23
Si quieren comprobar si el viejo driver está instalado en sus sistemas tipeen:

$ sudo lsmod | grep eagle

Si les sale algo referido al “eagle-usb”, para descargarlo tipeen:

$ sudo modprobe -r eagle-usb

Ahora hay que remover los módulos de la memoria, para eso:

$ sudo rm /lib/modules/'uname -r'/kernel/drivers/usb/atm/usbatm.ko
$ sudo rm /lib/modules/'uname -r'/kernel/drivers/usb/net/eagle/eagleusb.ko

3-Instalación del driver:
Bien, ahora es el turno de instalar el driver para eso vamos al directorio donde descargamos el paquete ueagle-atm, tipeamos:

$ tar -xvzf ueagle-atm-1.3.tar.gz
$ cd ueagle-atm-1.3
$ sudo make
$ sudo make install

Para terminar con la instalación hay que instalar también el firmware del módem, para eso vamos al directorio donde descargamos el paquete ueagle-data y hacemos lo siguiente:

$ tar xzf ueagle-data-1.1.tar.gz
$ cd ueagle-data-1.1
Lo que resta hacer es crear un directorio “ueagle-atm” dentro del directorio donde se almacenan los firmwares en el sistema, en Dapper se hace de la siguiente manera:

$ sudo mkdir /lib/firmware/ueagle-atm

Y se copia todos los archivos del directorio “ueagle-data-1.1” al directorio que recién hemos creado:

$ sudo cp -a *.* /lib/firmware/ueagle-atm

Muy bien!, hemos llegado a una parte de definiciones en todo este asunto, ahora debemos activar el nuevo driver, cruzen los dedos y buena suerte, pero antes tipeen:

$ sudo modprobe ueagle-atm

Si todo salió bien y no se ven errores, fijense en el modem, verán que la lucecita de “link” al principio parpadea y luego queda definitivamente encendida, esa es la señal de que su alfajorcito está funcionando!.
Para confirmar realmente esto, si quieren pueden tipear:

$ dmesg | grep ueagle

Les tiene que salir algo como esto:

usb 1-2: [ueagle-atm] modem operational
usb 1-2: [ueagle-atm] ATU-R firmware version : 44e2ea17

4-Configurando el ISP:
Algo que tengo que aclarar antes de continuar, mi conexión utiliza PPPoE, aquellos que tengan una conexión mediante PPPoA les recomiendo que busquen en los foros de ubuntu sobre todos en aquellos que esten en inglés en el buscador de dicho foro tipeen “ Sagem Fast 800 with Ueagle-Atm in Dapper” (si es uno de los how to en los que me basé para este!). Bueno los que tengan el mismo tipo de conexión sigan conmigo, antes que nada debemos crear la interface de red para nuestro modem, para eso debemos hacer:

$ sudo modprobe br2684

Luego:

$ sudo br2684ctl -c 0 -b -a 0.33

NOTA: los parámetros 0 y 33 corresponden al VPI y el VCI de mi ISP, ustedes deberán adaptarlo al suyo.

Si todo está bien, les saldrá esto:

RFC1483/2684 bridge: Interface "nas0" created sucessfully
RFC1483/2684 bridge: Communicating over ATM 0.0.33, encapsulation: LLC
RFC1483/2684 bridge: Interface configured

Y por último:

$ sudo ifconfig nas0 up

A continuación vayan al directorio donde se encuentra el paquete rp-pppoe-3.8.tar.gz y hacen:

$ tar -zxvf rp-pppoe-3.8.tar.gz
$ cd rp-pppoe-3.8
$ sudo ./go

Va a iniciarse un asistente el cuál nos hará un par de preguntas referidas a nuestra conexión, acá les paso lo que tienen que contestar, ah! las respuestas están entre parentesis:

1.Enter your PPPoE user name: (ej: micuenta@arnet-ciudad-apb)
2.Enter the Ethernet interface connected to the DSL modem: (nas0)
3.Enter the demand value: (no)
4.Enter the DNS information here: DNS primario (200.45.191.35)
5.Enter the secondary DNS server address here: DNS secundario (200.45.191.40)
6.Please enter your PPPoE password: (tu contraseña de internet)
7.Please re-enter your PPPoE password: (de nuevo tu contraseña)
8.Choose a type of firewall (0-2): (1)
9.Accept these settings and adjust configuration files (y/n)? (y)

Una vez terminado esto, tenemos que editar un par de ficheros, vamos que falta poco!. Para editar el primero es:

$ sudo gedit /etc/resolv.conf

NOTA: en este fichero tienen que fijarse que los números de los DNS primario y secundario coincidan con lo que contestaron en el asistente, si son los numeros correctos no toquen nada, o sea:

nameserver 200.45.191.35
nameserver 200.45.191.40

Luego hacemos lo siguiente:

$ sudo gedit /etc/ppp/peers/adsl

y pegamos:

# example configuration for the kernel space PPP over Ethernet driver
#
# See the manual page pppd( for information on all the options.

# MUST CHANGE: replace myusername@realm with the PPP login name given to
# your by your provider.
# There should be a matching entry with the password in /etc/ppp/pap-secrets
# and/or /etc/ppp/chap-secrets.
user "usuario@arnet"

# Load the PPPoE plugin.
plugin rp-pppoe.so

# Ethernet interface to which the modem is connected.
nas0

# Assumes that your IP address is allocated dynamically by the ISP.
noipdefault
# Try to get the name server addresses from the ISP.
usepeerdns
# Use this connection as the default route.
defaultroute

# Makes pppd "dial again" when the connection is lost.
persist

# Do not ask the remote to authenticate.
noauth

NOTA: en el parametro user va el usuario de internet, ej: “micuenta@arnet-ciudad-apb”, no se olviden de guardar y salir.

Los ultimos dos archivos hay que verificar si el nombre de usuario y contraseña estan correctamente cargados, para ver eso hacemos:

$ sudo gedit /etc/ppp/pap-secrets

Saldrá algo asi:

#Secrets for authentication using PAP
# client server secret IP addresses
"usuario@proveedor" * "password"

y

$ sudo gedit /etc/ppp/chap-secrets

Van a ver algo como esto:

# Secrets for authentication using CHAP
# client server secret IP addresses

# Secrets for authentication using CHAP
# client server secret IP addresses

# OUTBOUND CONNECTIONS
# Here you should add your PPP Login and PPP password to connect to your
# provider via pap. The * means that the entry(login and passoword may be
# used for ANY host you connect to.
# Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
#hostname * password

# PREDIFINED CONNECTIONS
# These are user and password entries for publically accessible call-by-call
# Internet providers in Germany. If they confict with your config, remove them.
# READ_IN_CALLBYCALL_SECRETS

# INBOUND CONNECTIONS
#client hostname 192.168.1.1

"usuario@proveedor" * "password"

5-Conectando a internet (¡¡¡POR FIN!!!)
Esta es la parte mas sencilla, solo tienen que hacer:

$ sudo pppd call adsl

y les aparecerá esto:

Plugin rp-pppoe.so loaded.

Abran el navegador y voila!, a disfrutar de internet!.

6-Automatizando todo
Listo? y más o menos, si tienen en cuenta que van a tener que tipear todos los comandos una y otra vez cuando inicien la pc, así que les recomiendo que hagan lo siguiente:

$ sudo gedit /etc/rc.local

y al final del archivo peguen lo siguiente:

modprobe br22684
br2684ctl -c 0 -b -a 0.33
ifconfig nas0 up

Listo!, ahora si!, cuando inicien su pc lo único que tendrán que hacer es abrir una terminal y tipear:

$ sudo pppd call adsl

Y se conectarán a internet. Bueno eso es todo espero que les salga como a mí, se que parece complicado pero no se desesperen, si algo sale mal vuelvan hacía atrás e intentenlo de nuevo, no se salteen nada porque es impotante que todo este a punto. Un abrazo

---

### Post by DuckMan on 2007-04-29
gracias, la mina esta tiene speedy, sera telefonica??

---

### Post by Gideon26 on 2007-04-29
si es speedy jaja probalo te tiene que funcionar en edgy 6.10 no estoy seguro que necesites el rp-pppoe-3.8.tar.gz 
creeria que desde segun como figura en el how to 

"A continuación vayan al directorio donde se encuentra el paquete rp-pppoe-3.8.tar.gz y hacen:"

no hagas esa parte y sigas con 
Paso procederemos a configurar nuestra conexión.

Escribimos en nuestra Terminal 

sudo gedit /etc/ppp/peers/dsl-provider



(en mi caso como tengo Ubuntu con interfaz grafica Gnomo uso gedite pero si tienen interfaz grafica KDE usen kwrite)

Bueno el procesador de texto que acabamos de abrir pegamos el siguiente contenido




noipdefault 
defaultroute 
replacedefaultroute 
hide-password 
noauth 
persist 
usepeerdns 
plugin rp-pppoe.so nas0 
user "xxxxxxx" 
password "xxxxxx"










 Bueno donde dice User ponemos el user que tenemos en el isp de Speedy, y bueno en password (bueno esta demas aclarar no?? ;) ) guardamos el archivo y cerramos el gedit.
La terminal la cerramos escribiendo exit.
Luego abrimos de nuevo el gedit y pegamos el contenido a continuacion.


#!/bin/bash 

sudo br2684ctl -b -c 0 -a 8.35
sudo ifconfig nas0 up
pon dsl-provider



Lo guardamos en el escritorio y luego pulsamos el boton derecho del mouse sobre el y vamos a propiedades, una vez en la ventana de propiedades nos dirigimos a la pestaña de permisos y seleccionamos la casilla de verificacion de ejecucion (permitir ejecutar el archivo como un programa) 


Hacemos doble click sobre el y saldra un cartel y pedimos ejecutar en terminal nos preguntara seguramente nuestra contraseña root la ingresamos y tendremos conexion a internet si a la primera no conecta esperemos unos segundos  y lo volvemos intentar que seguro tendremos conexion.


bueno esas serian las modificaciones que le haria yo para probar en edgy eft saludos proba la forma que te puse primero y  si no funciona proba con la mia. ok?? saludos.

---

### Post by sebas.rhcp on 2007-04-29
Si es speedy necesitas otra configuracion de VCI y VPI

---

### Post by DuckMan on 2007-04-29
y si es feisty fawn?!?!?!?!11111oneoneone

la pucha es larguito...

y como instalo build-essentials si no tengo internet :/

EDIT: chicos, el modem es ethernet! no es mas facil asi? :O

---

### Post by Gideon26 on 2007-04-29
y si si es ethernet no hay que hacer nada de eso jaja. a  y el 8.35 es el valor VCI y VPI, el build-essential lo haces con el cd o dvd de la distro de ubuntu que tengas si no tenes internet carga los que tiene el cd o dvd.

---

### Post by DuckMan on 2007-04-29
che pero instale, tiene por ethernet y no lo detecto, preciento q tiene q usar algo para marcar o algo asi :S como hago? :O

---

### Post by sebas.rhcp on 2007-04-29
pppoeconf proba si te lo detecta

---

### Post by Gideon26 on 2007-04-30
no ya se que tipo de modem es es un  modem router dual osea tiene usb y ethernet si no me equivoco, ahora te posteo como hacer vas a tener que entrar al router.

Para comenzar con la configuración accedemos al router poniendo la puerta de enlace predeterminada en el navegador: [http://192.168.1.1](http://192.168.1.1)
Despues nos pide usuario y contraseña el usuario es admin y contraseña admin (por lo menos esos son los de fabrica)(sino responde la contraseña y user presiona el boton reset del router e intenta de nuevo)
Bueno cuando entre te aparece una pantalla con todo un menu desplegable a tu izquierda y elegis  ATM Settings.

eso que estas viendo es la pantalla WAN y tenes que asignar estos valores:

VPI 8 el VCI 35

Active Yes

Mode Routing

Encapsulation PPPoE

Multiplex VC

User: "usuario de speedy"
Password: "Contraseña"

Default Router: elegi ENABLE

Luego elegi la opcion Obtain an IP Adress Automatically

luego elegy apply y listo ya esta cerra la ventana de navegador y tenes conexion a internet!!


Espero que te sirva (los datos que te di son los que se usan para speedy de aca Argentina)

saludos postea para saber si funciono

---

### Post by DuckMan on 2007-04-30
gracias maestro! me voy a fijar si funciona, no sabias q funcionaba como un router.. si, tiene las 2 salidas, usb y ethernet, usa la ethernet por suerte xD

---

### Post by sxxs on 2007-08-14
Yo tengo un problema que me vuelve locooooo!!! lo mismo me paso siempre que quise instalar el Huawei.
Luego de instalar el build-essential y el linux-header "correctamente" por medio de la Terminal al momento de hacer la compilacion de Ueagle-atm_1.3.... con: $ sudo make, en este comando me salta un error "2" y no puedo continuar.
a si que si alguien save como puedo solucionar ese problema de build-essential o de lo que sea que me diga., Por favor se los ruegoo!!!!!!!!!!!!

Desde ya Muchas Gracias!!!:confused::confused::confused:

---

### Post by Hei Ku on 2007-08-15
postea el error completo. probablemente te falte algun paquete para poder compilarlo.

---

### Post by sxxs on 2007-08-19
No postie el error por que ya lo solucione., El error era que estaba intentado compilar el ueagle-atm_1.3 con el comando Make en Ubuntu 7.04, cosa que no hay que hacer., solamente tenia que copiar firmware y listo. jajaja. Me paso por que crei que para instalarlo tenia que hacer lo mismo que con el ubuntu 6.10.

Gracias igual

](*,)
](*,)

---

### Post by Hex_Mandos on 2007-10-13
Buenas! Estoy tratando de configurarle este modem (MT882, dual, no el MT810 alias "alfajor del diablo") a mi abuela. Le armé una máquina dual boot Ubuntu - XP (XP sólo por si se retobaba el modem, precisamente). Ahora estoy en XP y el modem anda perfecto, pero en Ubuntu no puedo ni cargar la configuracion del bicho en 10.0.0.2. Está conectado vía Ethernet, así que me sorprende bastante. Alguien sabe cual puede ser el tema y/o como seguir? Nunca antes tuve problemas con ningún modem o router que tenga conexión Ethernet, así que me sorprende un poco el tema.

---

### Post by JoACoV on 2007-10-14
> **Hex_Mandos said:**
> Buenas! Estoy tratando de configurarle este modem (MT882, dual, no el MT810 alias "alfajor del diablo") a mi abuela. Le armé una máquina dual boot Ubuntu - XP (XP sólo por si se retobaba el modem, precisamente). Ahora estoy en XP y el modem anda perfecto, pero en Ubuntu no puedo ni cargar la configuracion del bicho en 10.0.0.2. Está conectado vía Ethernet, así que me sorprende bastante. Alguien sabe cual puede ser el tema y/o como seguir? Nunca antes tuve problemas con ningún modem o router que tenga conexión Ethernet, así que me sorprende un poco el tema.
pero si en xp te anda y lo enchufas por ethernet, teoricamente ubuntu lo detecta solo porque es red. ahora si es po usb tendrias que ver el tema de los drivers....

mas no te puedo decir por que yo tengo el mt810 (el alfajor), pero si el chip el mismo (ueagle-atm) la guia que dejaron un par de posts atras a mi me funciono

---

### Post by mauro80m on 2008-12-16
para el rp-pppoe-3.8.tar.gz es otro link ahora

[http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz](http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz)

---

### Post by mauro80m on 2008-12-16
la del br2684ctl
[http://packages.ubuntu.com/dapper/br2684ctl](http://packages.ubuntu.com/dapper/br2684ctl)

---

### Post by tonyhanna on 2009-02-13
guys, does anybody knows why the hell i can't change the Lan ip of the modem smartAX mt882 ?
everytime i change it , i do save and i save everything and i reboot ... and i discover that i still have the same ip : 192.168.1.1.
does anybody knows a way to change this ip to : 192.168.2.2 for example ?? please it's urgent.

---

### Post by Hei Ku on 2009-02-13
First, post on an English forum where more people will look at your request. This is the Argentina forum, and we speak Spanish here.
Second, if it is really urgent, then go into IRC and contact someone, don't post in a forum.

---

### Post by Hei Ku on 2009-02-13
First, post on an English forum where more people will look at your request. This is the Argentina forum, and we speak Spanish here.
Second, if it is really urgent, then go into IRC and contact someone, don't post in a forum.

---

### Post by faktorqm on 2009-02-14
Basta de hablar en ingles aca. respondele en castellano y si no sabe español que se curta.

---

