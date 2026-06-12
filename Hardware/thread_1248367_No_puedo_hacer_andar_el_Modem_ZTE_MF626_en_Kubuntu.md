---
title: "No puedo hacer andar el Modem ZTE MF626 en Kubuntu 9.04"
date: 2009-08-24
forum: Hardware
---

### Post by pampero2814 on 2009-08-24
Hola, me llamo Julio y soy re novato.

Estoy tratando de hacer andar el modem ZTE MF626 en Kubuntu 9.04 pero no hay caso.

Este es el texto de mi archivo usb_modeswitch.conf así tal cual



```

ZTE MF628+ (tested version from Telia / Sweden)
ZTE MF626

Contributor: Joakim Wennergren

DefaultVendor=  0x19d2

DefaultProduct= 0x2000

TargetVendor=   0x19d2

TargetProduct=  0x0031

MessageEndpoint=0×01
MessageContent=”55534243123456782000000080000c85010101180101010101000000000000&#8243;

if that command doesn’t work, try the other (”eject”)
MessageContent=”5553424312345678000000000000061b000000030000000000000000000000&#8243;

```y me devuelve este error.




```
* usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7beta (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: /etc/usb_modeswitch.conf
DefaultVendor=0x0
DefaultProduct=0x0
TargetVendor=0x0
TargetProduct=0x0
TargetClass=0x0
DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint=0x0
MessageContent=""
Interface=0x0

Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 001
usb_os_find_busses: Found 002
usb_os_find_devices: Found 004 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 002 on 002
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device

No default vendor/product ID given. Aborting.
```
No sé si es importante pero Claro es el proveedor de internet.

Bueno, ojalá alguien pueda ayudar y gracias.

---

### Post by meirzbi on 2009-08-24
[LEFT]hola[/LEFT]
  [LEFT] [/LEFT]
  [LEFT]el problema es muy difundido en los distros ubuntu fedora linux mint y otros [/LEFT]
  [LEFT] [/LEFT]
  [LEFT]la solucion es muy simple cambia en cada pais de acuerdo al provedor de internet xdsl adsl dsl [/LEFT]
  [LEFT] [/LEFT]
  [LEFT]todos se conectan po medio de un router y cable en la tarjeta red [/LEFT]
  [LEFT] [/LEFT]
  [LEFT]por lo tanto nos conectamos con el router y no con fedora [/LEFT]
  [LEFT] [/LEFT]
  [LEFT]de acuerdo cada pais y tras consulta con el provedor de internet entramos en el router por ejemplo[/LEFT]
  [LEFT] [/LEFT]
  [LEFT].[http://10.0.0.138](http://10.0.0.138)[/LEFT]
  [LEFT] [/LEFT]
  [LEFT]y procedemos a definir nuestra cuenta usuario contrasena y activamos y cada vez que conectes el router [/LEFT]
  [LEFT] [/LEFT]
  [LEFT]estas en internet [/LEFT]
  [LEFT] [/LEFT]
  [LEFT]chau [/LEFT]
  [LEFT] [/LEFT]
  [LEFT]ricardo[/LEFT]

---

### Post by staar on 2009-08-24
el amigo no está hablando de ninguna conexión adsl, ni router, ni nada de eso, es una conexión por modem 3g...

julio, podrías postear la salida de ```
lsusb
```

saludos

---

### Post by pampero2814 on 2009-08-24
Bueno, revisando me di cuenta que me estaba olvidando de darle **sudo make install**, por eso me salian mal varios valores, pero seguimos en la misma. Marco con negrita los valores que cambiaron.

**Salida de lsusb**

```
Bus 001 Device 003: ID 19d2:2000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```El modem aparece (ID 19d2:2000)

```
* usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.7beta (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: /etc/usb_modeswitch.conf
[COLOR=Black][B]DefaultVendor=0x19d2
DefaultProduct=0x2000
TargetVendor=0x19d2
TargetProduct=0x31[/B][/COLOR]
TargetClass=0x0
DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint=0x0
MessageContent="”55534243123456782000000080000c85010101180101010101000000000000&#8243;"
Interface=0x0

Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 001
usb_os_find_busses: Found 002
**usb_os_find_devices: Found 003 on 001**
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 002 on 002
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device

Error: no MessageEndpoint given. Aborting.
```

---

### Post by gmunioz on 2009-08-24
Hola pam....:

Prueba con lo siguiente:

Constata que este instalado wvdial, si no lo esta

instalalo, puedes bajarlo desde packages.ubuntu.com

Con el modem desenchufado

Crea el archivo /etc/udev/rules.d/50-ztemf.rules

En consola, Aplicaciones - Accesorios - Terminal, ejecuta: 

[HTML]sudo gedit /etc/udev/rules.d/50-ztemf.rules
[/HTML]

Pega en su interior el siguiente contenido:

[HTML]ACTION!="add", GOTO="ZTE_End"# Is this the ZeroCD device?
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000",
SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"

# Is this the actual modem?
SUBSYSTEM=="usb", SYSFS{idProduct}=="0001",
SYSFS{idVendor}=="19d2", GOTO="ZTE_Modem"
LABEL="ZTE_ZeroCD"

# This is the ZeroCD part of the card, remove
# the usb_storage kernel module so
# it does not get treated like a storage device
RUN+="/sbin/rmmod usb_storage"
LABEL="ZTE_Modem"

# This is the Modem part of the card, let's
# load usbserial with the correct vendor
# and product ID's so we get our usb serial devices
RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0001",

# Make users belonging to the dialout group
# able to use the usb serial devices.
MODE="660", GROUP="dialout"
LABEL="ZTE_End"[/HTML]


Edita el archivo /etc/wvdial.conf

En consola, Aplicaciones - Accesorios - Terminal, ejecuta: 

[HTML]sudo gedit /etc/wvdial.conf
[/HTML]

Pega en su interior o edita para el siguiente contenido:

[HTML][Dialer Defaults]
Modem = /dev/ttyACM0
ISDN = off
Modem Type = USB Modem
Baud = 460800
Init = ATZ
Init2 = AT+CFUN=1
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1,"IP","internet.ctimovil.com.ar"
Init5 =
Init6 =
Init7 =
Init8 =
Init9 =
Phone = *99#
Phone1 =
Phone2 =
Phone3 =
Phone4 =
Dial Prefix =
Dial Attempts = 1
Dial Command = ATM1L3DT
Ask Password = off
Password = 3616
Username = ctigprs
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = off
Idle Seconds = 0
Auto DNS = off
[/HTML]

Enchufa el modem

Reinicia el sistema

Ejecuta en consola

[HTML]sudo wvdial[/HTML]

Si no conecta, ejecuta la orden reiteradas veces.

---

### Post by pampero2814 on 2009-08-24
> **gmunioz said:**
> Hola pam....:

Prueba con lo siguiente:

Constata que este instalado wvdial, si no lo esta

instalalo, puedes bajarlo desde packages.ubuntu.com




Cuando intento instalar wvdial me tira este error y no instala.

```
error: la dependencia no se puede satisfacer: libuniconf4.4
```

---

### Post by gmunioz on 2009-08-25
Hola: 

Desde aqui puedes bajar el paquete:

[http://packages.ubuntu.com/jaunty/libuniconf4.4](http://packages.ubuntu.com/jaunty/libuniconf4.4)

Lo copias a un directorio y lo instalas con

sudo dpkg -i *.deb

Ten presente que requiere tambien de:

libc6   libwvstreams4.4-base 

libwvstreams4.4-extras libxplc0.3.13

Desde aqui bajas wvdial

[http://packages.ubuntu.com/jaunty/wvdial](http://packages.ubuntu.com/jaunty/wvdial)

Ten presente que requiere además de:

debconf   ppp

---

### Post by pampero2814 on 2009-08-25
> **gmunioz said:**
> Hola pam....:

Prueba con lo siguiente:

En consola, Aplicaciones - Accesorios - Terminal, ejecuta: 

[html]sudo /etc/udev/rules.d/50-ztemf.rules
[/html]

cuando intento darle sudo /etc/udev/rules.d/50-ztemf.rules

me responde *command not found*.

---

### Post by gmunioz on 2009-08-25
Mil disculpas !!!!

Me comi un comando, gedit, ya esta corregido.

la orden es:

[HTML]sudo gedit /etc/udev/rules.d/50-ztemf.rules[/HTML]

Nuevamente, disculpas. 

*El Alzheimer me alcanzó* 8)

---

### Post by pampero2814 on 2009-08-25
> **gmunioz said:**
> Mil disculpas !!!!

Me comi un comando, gedit, ya esta corregido.

la orden es:

[html]sudo gedit /etc/udev/rules.d/50-ztemf.rules[/html]Nuevamente, disculpas. 

*El Alzheimer me alcanzó* 8)

Disculpas tengo que pedir yo que estoy rompiendo las guindas a lo loco. 

Va queriendo ser. gedit no anduvo pero kate si. 

Lo que sí, ahora me tira este error cuando le doy  *sudo wvdial*

```

--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory
```

---

### Post by gmunioz on 2009-08-25
Hola pam...:

Ejecuta en la consola la orden:

sudo wvdialconf

Y ve si no detecta el modem en otro /dev/tty

Puede ser /dev/ttyUSB0

Si fuera asi, cambia en el archivo

/etc/wvdial.conf

/dev/ttyACM0 por el que se haya encontrado

---

### Post by pampero2814 on 2009-08-26
> **gmunioz said:**
> Hola pam...:

Ejecuta en la consola la orden:

sudo wvdialconf

Y ve si no detecta el modem en otro /dev/tty

Puede ser /dev/ttyUSB0

Si fuera asi, cambia en el archivo

/etc/wvdial.conf

/dev/ttyACM0 por el que se haya encontrado

sudo wvdial conf devuelve

```
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial

If you still have problems, send mail to <wvdial-list@lists.nit.ca>
```

---

### Post by gmunioz on 2009-08-26
Hola:

Segun lsusb, tienes el modem en:

Bus 001 Device 003: ID 19d2:2000

Esto sería /dev/ttyUSB2

Edita el archivo /etc/wvdial.conf

sudo gedit /etc/wvdial.conf

Y cambia:

/dev/ttyACM0 

por

/dev/ttyUSB2

Guarda el archivo e insiste con

sudo wvdial

---

### Post by pampero2814 on 2009-08-26
:( Tira el mismo error

```
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB2: No such file or directory
--> Cannot open /dev/ttyUSB2: No such file or directory
--> Cannot open /dev/ttyUSB2: No such file or directory
```

---

### Post by staar on 2009-08-26
conectá el modem, y corré ```
ls /dev | grep tty
``` y fijate cuales salen (a los tty*X*, siendo *X* un número, no los tomes en cuenta), probablemente sea /dev/ttyUSB0 (en mi huawei es ese)

saludos

---

### Post by gmunioz on 2009-08-26
Hola pam....:

Volvamos a modeswitch, algunos pasos ya los has

hecho.

A)- Descargar el archivo usb_modeswitch-1.0.5.tar.bz2 o la versión más reciente del sitio:

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

B)- Descomprimir el archivo, cambiando al directorio (carpeta)
donde fue descargado, y ejecutar:

tar xvfj usb_modeswitch-1.0.5.tar.bz2

C)- Ingresar al directorio (carpeta) creada al descomprimir
y ejecutar :

sudo make install

D)- Editar el archivo usb_modeswitch.conf utilizando el editor 
de textos de la versión usada, en tu caso kate, en gnome gedit
en ambos nano:

sudo kate /etc/usb_modeswitch.conf

E)- Buscar la línea  MF626, borrar todas la almohadillas (#) y 
todos los punto y coma ; del comienzo de las líneas de
texto, para que quede mas o menos similñar a:


########################################################

ZTE MF628+ (tested version from Telia / Sweden)

ZTE MF626

Contributor: Joakim Wennergren

DefaultVendor= 0×19d2

DefaultProduct= 0×2000

TargetVendor= 0×19d2

TargetProduct= 0×0031

MessageEndpoint=0×01

MessageContent=&#8221;55534243123456782000000080000c85010101180101010101000000000000&#8243;

if that command doesn&#8217;t work, try the other (&#8221;eject&#8221;)

MessageContent=&#8221;5553424312345678000000000000061b000000030000000000000000000000&#8243;

Guardar el archivo

Cerrar el editor

F)- Recien ahora conectar este bendito? módem y controlar mediante
la orden:

sudo lsusb

Que esta reconocido con el ID 19d2:2000

G).- Ejecutar, siempre en la consola, (terminal) la orden:

sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf

Esta orden, se debe ejecutar después de enchufar el módem, para que sea reconocido como tal y cada vez que se quiera establecer la comunicación

H).- Ejecutar, siempre en consola, konsole en tu caso la orden:

sudo /sbin/modprobe usbserial vendor=0×19d2 product=0×0031

Si la respuesta es:

FATAL: Module usbserial not found.

H1) Debes editar el archivo  /boot/grub/menu.lst

sudo kate /boot/grub/menu.lst

Buscar la línea que dice:

kernel /vmlinuz-2.6.28-11-generic root=UUID=f2441938-7359-49d7-95eb-81f36a166757 ro quiet splash 

Y dejarla así

kernel /vmlinuz-2.6.28-11-generic root=UUID=f2441938-7359-49d7-95eb-81f36a166757 ro quiet splash usbserial.vendor=0x19d2 usbserial.product=0x0031

Guardar el archivo.

Esto lamentablemente se debe reiterar, cada vez que se actualice
el kernel.

I).- Controlar este instalado, sino instalar wvdial y editar
el archivo /etc/wvdial.conf

sudo apt-get install wvdial

sudo kate /etc/wvdial.conf

Este para el bendito? ISP Claro Argentina debe contener lo
siguiente:
 
[Dialer Defaults]
Modem = /dev/ttyUSB2
ISDN = off
Modem Type = USB Modem
Baud = 460800
Init = ATZ
Init2 = AT+CFUN=1
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1,"IP","internet.ctimovil.com.ar"
Init5 =
Init6 =
Init7 =
Init8 =
Init9 =
Phone = *99#
Phone1 =
Phone2 =
Phone3 =
Phone4 =
Dial Prefix =
Dial Attempts = 1
Dial Command = ATM1L3DT
Ask Password = off
Password = 3616
Username = ctigprs
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = off
Idle Seconds = 0
Auto DNS = off
 
Guardar el archivo.

J) Ejecutar en la terminal, consola / konsole la orden

sudo wvdial

Reiteradas veces.

Si conectó, bendito? Claro resta:

K).- Crear un archivo .fdi para que pueda ser reconocido por
 Network Manager. Para ello ejecutar en  consola:

sudo kate /usr/share/hal/fdi/information/20thirdparty/20-zte-mf626.fdi

Se abrirá un nuevo archivo en blanco, se debe agregar este contenido:

<!&#8211; -*- SGML -*- &#8211;>
<deviceinfo version=&#8221;0.2&#8243;>
<device>
<!&#8211; ZTE MF626 HSDPA USB Modem &#8211;>
<match key=&#8221;@info.parent:usb.vendor_id&#8221; int=&#8221;0×19d2&#8243;>
<match key=&#8221;@info.parent:usb.product_id&#8221; int=&#8221;0×0031&#8243;>
<match key=&#8221;@info.parent:usb.interface.number&#8221; int=&#8221;3&#8243;>
<append key=&#8221;modem.command_sets&#8221; type=&#8221;strlist&#8221;>GSM-07.07</append>
<append key=&#8221;modem.command_sets&#8221; type=&#8221;strlist&#8221;>GSM-07.05</append>
<append key=&#8221;info.capabilities&#8221; type=&#8221;strlist&#8221;>modem</append>
</match>
</match>
</match>
</device>
</deviceinfo>

Guardar el archivo

Cerrar el editor

Cerrar, por fin, la consola.


L) Pulsar en Sistema - Preferencias - Conexiones de Red - Pestaña
Banda ancha móvil - Editar la conexión Claro con los parámetros adecuados.

Intentar conectar desde el Network Manager

---

### Post by pampero2814 on 2009-08-27
[quote=staar]conectá el modem, y corré ```
ls /dev | grep tty
``` y fijate cuales salen (a los tty*X*, siendo *X* un número, no los tomes en cuenta), probablemente sea /dev/ttyUSB0 (en mi huawei es ese)

saludos[/quote]

Los únicos ttyX donde X no es un número son

ttyS0
ttyS1
ttyS2
ttyS3
ttyUSB0
ttyUSB1
ttyUSB2
ttyUSB3

Ahora me tira este error cuando mando el wvdial

```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

```

---

### Post by gmunioz on 2009-08-27
Hola pam....:

Aparentemente ya tu modem esta detectado como tal.

Falla algo en la configuración de wvdial.conf.

Ve variando estos parámetros:


[Dialer Defaults]

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Init3 =

New PPPD = yes

ISDN = off

Stupid Mode = on

Abort on No Dialtone = on


Ademas en el archivo /etc/ppp/options comenta la 
autenticacion con PAP y activa la conexion con CHAP.

sudo kate /etc/ppp/options

Lo dejas así:

# Require the peer to authenticate itself using PAP.
#+pap

    # Don’t agree to authenticate using PAP.
    #-pap

    # Require the peer to authenticate itself using CHAP [Cryptographic
    # Handshake Authentication Protocol] authentication.
    +chap

    # Don’t agree to authenticate using CHAP.
    #-chap

---

### Post by faktorqm on 2009-08-27
perdon por la intromision, pero le queria avisar a gabriel que le deje un pm. perdon y salu2! _muy_ interesante el thread.

---

### Post by pampero2814 on 2009-08-28
Efectuados los cambios sugeridos en tu último post gmunioz, sigue tirando el mismo error

```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

```

---

### Post by mama21mama on 2009-08-28
che miraste este [post de taringa]("http://www.taringa.net/posts/linux/2318037/Configurar-internet-en-Ubuntu-modem-ZTE-mf626.html")?

Saludos

---

### Post by pampero2814 on 2009-08-28
Si amigo lo mire, pero no me funca. Gracias por la buena onda, a todos los que ayudaron.

---

### Post by gmunioz on 2009-08-29
**Recapitulemos**

Hola Julio, no es posible darse por vencido !!!

Intenta:

1- Ve que exista el archivo y contenga esta información:

/etc/udev/rules.d/50-ztemf.rules 

ACTION!="add", GOTO="ZTE_End"# Is this the ZeroCD device?
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000",
SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"

# Is this the actual modem?
SUBSYSTEM=="usb", SYSFS{idProduct}=="0001",
SYSFS{idVendor}=="19d2", GOTO="ZTE_Modem"
LABEL="ZTE_ZeroCD"

# This is the ZeroCD part of the card, remove
# the usb_storage kernel module so
# it does not get treated like a storage device
RUN+="/sbin/rmmod usb_storage"
LABEL="ZTE_Modem"

# This is the Modem part of the card, let's
# load usbserial with the correct vendor
# and product ID's so we get our usb serial devices
RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0001",

# Make users belonging to the dialout group
# able to use the usb serial devices.
MODE="660", GROUP="dialout"
LABEL="ZTE_End"

Inicia el sistema, enchufa el modem, espera un tiempo
ejecuta.

sudo lsusb

Ve si el modem esta reconocido, si lo está

ejecuta 

sudo wvdial

2- Si sigue sin funcionar, edita el archivo
/etc/udev/rules.d/50-ztemf.rules  y cambia su
contenido por:


SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", RUN +="/usr/sbin/usb_modeswitch"
SUBSYSTEM=="usb", SYSFS{idProduct}=="0064", SYSFS{idVendor}=="19d2", RUN +="/sbin/modprobe usbserial vendor=0x19d2 product=0x0064"

Guarda el archivo

Edita el archivo /etc/usb_modeswitch.conf
y solo deja este contenido

########################################################
# ZTE MF628+ (tested version from Telia / Sweden) 
# ZTE MF626 
# 
# Contributor: Joakim Wennergren

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0064

MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"

Guarda el archivo

Reinicia, enchufa el modem, espera un tiempo

ejecuta.

sudo lsusb

Ve si el modem esta reconocido, si lo está

ejecuta 

sudo wvdial

Ve que el wvdial.conf 

[Dialer Defaults]
Modem = **/dev/ttyUSB2** ---* sea el que te informa sudo lsusb*
ISDN = off
Modem Type = USB Modem
Baud = 460800
Init = ATZ
Init2 = AT+CFUN=1
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1,"IP","internet.ctimovil.com.ar"
Init5 =
Init6 =
Init7 =
Init8 =
Init9 =
Phone = *99#
Phone1 =
Phone2 =
Phone3 =
Phone4 =
Dial Prefix =
Dial Attempts = 1
Dial Command = ATM1L3DT
Ask Password = off
Password = 3616
Username = ctigprs
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = off
Idle Seconds = 0
Auto DNS = off

Y hasta aqui llegue. (Por ahora)

---

### Post by bruno321 on 2010-11-06
Por qué será que la gente pide que otros le dediquen su tiempo a resolver sus problemas cuando ellos mismos no son capaces de perderlo en postear su solución o "el final" de la historia

---

### Post by gmunioz on 2010-11-08
Hola Bruno:
Actualmente este es el sistema que dicen hace funcionar
ese artefacto maligno:


a). Descargar el usb_modeswitch de este sitio:
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

b). Descomprimirlo, meterse desde consola al path del directorio
e intalar con el comando en consola:

sudo make install

c). Modificar el archivo usb_modeswitch.conf: 

sudo gedit /etc/usb_modeswitch.conf 

Para que quede asi:

########################################################
# ZTE MF628+ (tested version from Telia / Sweden)
ZTE MF626
# ZTE MF633
# ZTE MF636 (aka "Telstra / BigPond 7.2 Mobile Card")
#
# Contributor: Joakim Wennergren

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
;TargetProduct=  0x0031

# only for reference and 0.x versions
# MessageEndpoint=0x01

MessageContent="55534243123456782000000080000c85010101180101010101000000000000"

# if that command doesn't work, try the other ("eject")
;MessageContent="5553424312345678000000000000061b000000030000000000000000000000"


########################################################


d). Conectar el modem y verificar haciendo lsusb que esta
conectado, debería aparecer un dispositivo con el id: 

19d2:2000

e). Switchear para que ubuntu reconozca el modem como tal
ejecutando en consola: 

sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf

f). Una vez hecho esto esperar un poco a que lo reconozca como
tal, haciendo de nuevo lsusb, ahora debera aparecer como

19d2:0031

g). Crear una nueva conexion de banda ancha movil (puede ser 
con el network manager de ubuntu) con los parametros:

usuario: el_usuario
contraseña: la_contraseña
nombre de la conexion: movistar/claro/personal
apn: lo_que_corresponde_al _proveedor
en método de autenticacion debe ir solo: pap
en ajustes de ipv4 debera ir solo conexiones automaticas ppp, 
con dns: los que corresponden al proveedor

h)
Movistar
APN = internet.gprs.unifon.com.ar
Número = *99#
Usuario = internet
Password = internet
DNS:
200.49.193.140
200.49.206.140

Claro
APN = gprs.claro.com.ar
Número = *99#
Usuario = ctigprs
Password = ctigprs999
DNS:
170.51.255.100
170.51.242.18

Personal
APN = gprs.personal.com
Número = *99#
Usuario = gprs
Password = adgj
DNS:
172.25.7.6
172.25.7.7

Dado que me mudé y ahora sufro con Speedy, ya no testeo esos
artefactos denoníacos.

---

