---
title: "Duda con modem"
date: 2007-10-25
forum: Hardware
---

### Post by atatiducken on 2007-10-25
[SIZE="2"]hola a todos soy nuevo en linux y en el foro,me alegro de haberme cambiado de xp, acabo de instalar gusty 7.10, este tema ya fue tratado y mucho por lo q veo pero mi duda es si los tutoriales de configurar el modem Huawei smart mt810 para arnet en feisty 7.04 sirven para gusty 7.10, o ya es soportado por el mismo? sino, me podrían ayudar?
gracias a todos y es un gusto ser parte de esta comunidad[/SIZE]

---

### Post by JoACoV on 2007-10-25
Hola, tengo el mismo modem..

para gutsy tenes que seguir cualquiera de los tutos para feisty y funca de 10

aca te dejo uno (tiene algunas modificaciones mias no recuerdo el autor original)
```

Configurar Modem Ueagle USB

Sirve para cualquier modem que tenga este chip (como el Huawei SmartAX MT 810)

Guia para Ubuntu 7.10 Gutsy Gibbon

1-PAQUETES NECESARIOS:

Antes que nada en caso  de no tenerlos, bajar estos paquetes:

rp-pppoe-3.8.tar.gz ( http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php )
br2684ctl.deb ( http://packages.ubuntulinux.org/feisty/net/br2684ctl bajen las dependencias que ahí les indican también)
ueagle-data-1.1.tar.gz ( http://eagle-usb.org/ueagle-atm/non-free/ )

2-PREPARAR TODO

Lo primero que hay que hacer es copiar todos los paquetes descargados en una carpeta  en una carpeta.

Ahora introducir el cd de ubuntu en la unidad.

Por ultimo abrir una terminal (esencial)

3-CONFIGURACION DEL SISTEMA:

Hay que instalar el paquete build-essential desde el cd:

$ sudo apt-get install build-essential

Nos pregunta si deseamos continuar, ponemos &#8220;s&#8221; y tecla enter. Si vuelve a pedirnos confirmación, nuevamente apretamos enter. También nos puede informar que ya lo tenemos en la versión mas reciente si es que ya lo instalamos anteriormente en otro proceso.

Ahora hay que instalar el firmware del módem, para eso vamos al directorio donde tenemos el paquete ueagle-data y hacemos lo siguiente:

$ tar xzf ueagle-data-1.1.tar.gz
$ cd ueagle-data-1.1

Lo que resta hacer es crear un directorio &#8220;ueagle-atm&#8221; dentro del directorio donde se almacenan los firmwares en el sistema, se hace de la siguiente manera:

$ sudo mkdir /lib/firmware/ueagle-atm

Y se copia todos los archivos del directorio &#8220;ueagle-data-1.1&#8221; al directorio que recién hemos creado:

$ sudo cp -a *.* /lib/firmware/ueagle-atm
$ cd ..

Muy bien!, hemos llegado a una parte de definiciones en todo este asunto, ahora debemos activar el driver:

$ sudo modprobe ueagle-atm

Si todo salió bien y no se ven errores, fíjense en el modem, verán que la lucecita de &#8220;link&#8221; al principio parpadea y luego queda definitivamente encendida, esa es la señal de que su alfajorcito está funcionando!. Si no enciende, reiniciar la PC y luego al entrar nuevamente a ubuntu, la luz del &#8220;link&#8221; deberá estar encendida.

4-CONFIGURACION DEL ISP:

Antes que nada debemos crear la internase de red para nuestro modem, para eso debemos hacer:

$ sudo dpkg -i br2684ctl_20040226-1_i386.deb (o el br2684ctl.deb que corresponda)
$ sudo modprobe br2684

Luego:

$ sudo br2684ctl -c 0 -b -a 0.33 (0.33 son los valores VPI y el VCI de arnet)

Y por último:

$ sudo ifconfig nas0 up

 A continuación hacen:

$ tar -zxvf rp-pppoe-3.8.tar.gz
$ cd rp-pppoe-3.8
$ sudo ./go

Va a iniciarse un asistente el cuál nos hará un par de preguntas referidas a nuestra conexión. Acá les paso lo que tienen que contestar, no anotar los paréntesis.

NOTA: Las IP de los DNS las extraje de OpenDNS que funcionan excelente y son libres. Sin embargo pueden buscar los DNS de Arnet o del ISP que dispongan. Ahora si:

1.Enter your PPPoE user name: (ej: micuenta@arnet-ciudad-apb)
2.Enter the Ethernet interface connected to the DSL modem: (nas0)
3.Enter the demand value: (no)
4.Enter the DNS information here: DNS primario (208.67.222.222)
5.Enter the secondary DNS server address here: DNS secundario (208.67.220.220)
6.Please enter your PPPoE password: (tu contraseña de internet)
Aclaración: Al entrar la contraseña el cursor no muestra nada ni se desplaza.
7.Please re-enter your PPPoE password: (de nuevo tu contraseña)
8.Choose a type of firewall (0-2): (1)
9.Accept these settings and adjust configuration files (y/n)? (y)

Una vez terminado esto, enemos que editar un par de ficheros, hacemos lo siguiente:

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

NOTA: Reemplazamos en donde dice "usuario@arnet" por nuestro usuario de Arnet (Sin las comillas) ej: micuenta@arnet-ciudad-apb. No se olviden de guardar y salir.

5-CONECTANDO A INTERNET (¡¡¡POR FIN!!!)

Esta es la parte más sencilla, solo tienen que hacer:

$ sudo pppoe-start

Ingresan el password de usuario de ubuntu y les aparecerá puntos (....) a modo de progreso (indica que esta intentando conectarse) y luego de un tiempo CONNECTED! lo cual indica que ya por fin estamos conectados.
Abran el navegador y voila!, a disfrutar de internet!.
NOTA: También es posible conectarse escribiendo en lugar de &#8220;sudo pppoe-start&#8221; escribiendo "sudo pppd call adsl" pero no nos indicará en qué momento el progreso de conexión termina y quedamos conectados.
NOTA: Cada vez que reiniciemos, para poder conectarnos deberemos escribir en la terminal:

$ sudo modprobe br2684
$ sudo br2684ctl -c 0 -b -a 0.33
$ sudo ifconfig nas0 up
$ sudo pppoe-start

6-AUTOMATIZANDO TODO

Escribir:

$ sudo gedit /etc/rc.local

En el final y antes de donde dice &#8220;exit 0&#8221; pegamos lo siguiente:

#------------------------Modem Huawei-------------------------.
modprobe br2684
br2684ctl -c 0 -b -a 0.33
ifconfig nas0 up
pppoe-start
#-----------------------/Modem Huawei-------------------------.

Reiniciamos la PC y ya estaremos conectados al entrar a Ubuntu. Para ver el estado de la conexión abrimos el terminal y escribimos:

$ sudo pppoe-status


```

En caso de que tu proveedor no sea Arnet, vas a tener que buscar los datos del ISP (elVPI y el VCI, los DNS no hacen falta porque son abiertos)

---

### Post by santiagoward2000 on 2007-10-25
> **atatiducken said:**
> [SIZE="2"]hola a todos soy nuevo en linux y en el foro,me alegro de haberme cambiado de xp, acabo de instalar gusty 7.10, este tema ya fue tratado y mucho por lo q veo pero mi duda es si los tutoriales de configurar el modem Huawei smart mt810 para arnet en feisty 7.04 sirven para gusty 7.10, o ya es soportado por el mismo? sino, me podrían ayudar?
gracias a todos y es un gusto ser parte de esta comunidad[/SIZE]

Hola atatiducken,
Estuve buscando info sobre tu modem en Google. ¿Se conecta por usb? Si es así te cuento que va a ser complicado. Yo todavía no pude configurar mi Arescom 1060usb de Speedy. Sé que se puede, pero soy muy vago, así que sigo usando el modem en Windows y armé una red inalambrica para poder conectarme con mi laptop.
Espero que alguien pueda ayudarte.

---

### Post by JoACoV on 2007-10-25
> **santiagoward2000 said:**
> Hola atatiducken,
Estuve buscando info sobre tu modem en Google. ¿Se conecta por usb? Si es así te cuento que va a ser complicado. Yo todavía no pude configurar mi Arescom 1060usb de Speedy. Sé que se puede, pero soy muy vago, así que sigo usando el modem en Windows y armé una red inalambrica para poder conectarme con mi laptop.
Espero que alguien pueda ayudarte.
Si ese modem (el MT810) se conecta por USB.

Fijate que chip tiene tu modem, si es el ueagle-atm, funciona con los mismos drivers (o sea misma guia), de no ser asi no puede ayudarte porque no tengo mucha idea de esto

---

### Post by santiagoward2000 on 2007-10-25
> **JoACoV said:**
> Si ese modem (el MT810) se conecta por USB.

Fijate que chip tiene tu modem, si es el ueagle-atm, funciona con los mismos drivers (o sea misma guia), de no ser asi no puede ayudarte porque no tengo mucha idea de esto

Hola JoACoV,
Según encontré en Google:
> Eagle-usb II chipset
¿Anda igual con esa guía?

---

### Post by atatiducken on 2007-10-26
[SIZE="2"]hola a todos, la verdad muchisimas gracias por todo, no hay dudas linux (queria decir ubuntu, pero esto es mas global jeje) es lo mejor no solo por su software sino por su comunidad, paso a contarles algo q para mi es increible porq soy noob en esto, estaba en lo de un amigo asi q corri el live cd desde su maquina con windows (tb tiene arnet) y configure el modem (tiene el mismo modem) siguiendo los pasos q me dieron sin casi ningun problema, despues de 10 min estaba conectado a internet desde el live cd no lo puedo creer todavia estoy feliz jeje.
gracias y perdon si me excedi

P/D: esto lo escribo desde el el live cd jeje [/SIZE]

---

### Post by leo_rockway on 2007-10-26
otro cliente satisfecho (?)

---

### Post by JoACoV on 2007-10-28
> **santiagoward2000 said:**
> 

¿Anda igual con esa guía?

perdon por no contestar antes.

Segun lei, si el chip es el mismo debería funcionar con esa guia, porque el firmware no es del modem sino del chip.

---

### Post by santiagoward2000 on 2007-10-28
> **JoACoV said:**
> perdon por no contestar antes.

Segun lei, si el chip es el mismo debería funcionar con esa guia, porque el firmware no es del modem sino del chip.

Hola JoACoV,
Gracias, no te preocupes por haber tardado. Apenas pueda voy a probarlo!!

---

### Post by coldplay15 on 2008-07-23
Hola, alguien sabe si con el Ubuntu 8.04 los pasos son los mismos?
Gracias a todos y abrazos.

---

### Post by faktorqm on 2008-07-24
Tenés que mirar la fecha de los posts la próxima....

[http://ubuntuforums.org/showthread.php?t=846069](http://ubuntuforums.org/showthread.php?t=846069)

---

