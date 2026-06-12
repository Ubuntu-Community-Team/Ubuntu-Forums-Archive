---
title: "ZTE MF110 (Modem 3G) AYUDA..."
date: 2010-06-13
forum: Hardware
---

### Post by UbGooK on 2010-06-13
Buenas,

Debido a que estoy traumatizado con esto... paso a explicar que pasa.

Vivo en zona urbana pero NINGÚN ISP de ADSL esta disponible en mi barrio, investigue, pregunte, etc, etc. Recién dentro de 1 año harán las respectivas instalaciones...

Como tengo responsabilidades  por internet, **contrate un servicio 3G de Personal**... como leía que se conectaba automaticamente a **Ubuntu 10.04**... pero eso no era en **el modem ZTE MF110**, sino en otras "versiones"... entonces busque guiás... las hice... y sorpresa... ninguna funciona... el problema que me sucede **al parecer con el asistente de administrador de redes no toma la red inalambrica 3G, por que nunca aparece...**

[B]Las guías que seguí son:
[/B]
[https://zdes.wordpress.com/2010/02/11/modem-zte-mf110-en-ubuntu/](https://zdes.wordpress.com/2010/02/11/modem-zte-mf110-en-ubuntu/) (una de las primeras)
[http://blogdrake.net/documentacion/como-instalar-un-usb-modem-3g-utilizando-como-ejemplo-el-modem-zte-mf110](http://blogdrake.net/documentacion/como-instalar-un-usb-modem-3g-utilizando-como-ejemplo-el-modem-zte-mf110) (una de las ultimas)...

**Tampoco hacer que funcione en otras distros... basadas en ubuntu (ej Lubuntu) y demás...**

En Ubuntu me inicie hace 3 años o más pero no profundice mucho, en Windows llevo más de 15 años usándolo. Entonces si me quieren indicar paso a paso en Ubuntu me ayudarían mucho.

**AYUDA POR FAVOR.**

Muchisimas Gracias!

---

### Post by beren.olvar on 2010-06-13
El modem es detectado?? osea, aparece en el menu del NetworkManager??
si es asi podrias adjuntar el optput de dmesg (en un terminal escribe dmesg, y copia y pega lo ke salga)

Yo tuve una antena parecida a esa, y tambien tuve problemas. Normalmente lo solucionaba desconectando la antena e intentando los pasos de nuevo, hasta ke la reconocia y se conectaba. Es bueno ke esperes unos 30 segundos entre ke enchufas el modem e intentas conectarte.

suerte

---

### Post by UbGooK on 2010-06-13
El modem en el entorno "grafico" (administrador de redes) no lo toma, con los comandos lsusb si por ej... Tengo un HUB USB (Noganet) no se si eso cambia algo, de todas formas también probe ponerlo solo en el puerto usb y tampoco nada...

Aquí te adjunto todo lo que hice de las guias mencionadas + dmesg + lsusb... Hice lo que me dices del los 30 seg pero nada había sucedió...

Muchas Gracias por la mano,

---

### Post by beren.olvar on 2010-06-14
Bueno, al parece, tu problema es ke no esta funcionando el cambio de dispositivo de almacenamiento a modem. Mira, por ejemplo:

usb 1-4.3: usbfs: USBDEVFS_CONTROL failed cmd usb_modeswitch rqt 128 rq 6 len 255 ret -71

usb_modeswitch te esta tirando errores. Te recomiendo borrar cualkier regla ke hayas puesto en udev para ke no haga nada automaticamente. Solo despues de ke soluciones los problemas deberias activar la configuracion automatica.

Intenta haciendo lo siguiente:
-Conecta el modem y espera unos segundos, o hasta ke las luces dejen de parpadear.
-Escribe lo siguiente en un terminal:
```

sudo usb_modeswitch -W -c mi_conf.conf
sudo modprobe usbserial vendor=0x19d2 product=0x0031

```

donde el archivo mi_conf.conf es:
```

###################################################
# ZTE MF110 
#
# Contributor: Fernando Anthony Ristagno
###################################################

DefaultVendor=0x19d2
DefaultProduct=0x2000

TargetVendor=0x19d2
TargetProduct=0x0031

;MessageEndpoint=0x1
MessageContent="55534243b8fe6681000000000000061b000000020000000000000000000000"

```

Y es un archivo en el mismo directorio donde estas "parado".

El id del producto y del vendedor ke usas son los mismos ke he usado yo para otra antena, pero el messageContent es distinto. si no funciona con la configuracion como esta puesta mas arriba podrias intentar con 

MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
o
MessageContent="5553424312345678000000000000061b000000030000000000000000000000"

Te recomiendo ademas ke siempre desconectes y reconectes la antena entre intentos, para ke las configuraciones no choquen entre ellas.

buena suerte!

---

### Post by UbGooK on 2010-06-14
Lo intentare más tarde por que trabajo hasta la madrugada hoy. Muchisimas Gracias al fin una solución diferente.

Despues de la 02:00 te voy a dejar los resultados.

Un abrazo,

---

### Post by UbGooK on 2010-06-15
*#Frustración...#*

> **Intento 1:**

<<<<<<<<<<<<<<<<<<
kaiser@kaiser-desktop:~$ sudo usb_modeswitch -W -c mi_conf.conf

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: mi_conf.conf
Error: Could not find file mi_conf.conf

kaiser@kaiser-desktop:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031
kaiser@kaiser-desktop:~$ 
<<<<<<<<<<<<<<<<<<<<<<<<<

no encontro el archivo mi_config.config (o te referias al ya creado anteriormente?..) Entonces lo cree y puse el fragmento de codigo, lo guarde y probe lo que me dijiste... donde estaba parado no lo entiendo quizas,estaba en /etc/udev/rules.d/
> **Intento 2:**

<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
kaiser@kaiser-desktop:~$ usb_modeswitch -W -c usb_modeswitch.conf

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: usb_modeswitch.conf
Error: Could not find file usb_modeswitch.conf

kaiser@kaiser-desktop:~$ usb_modeswitch -W -c usb_modeswitch_config.conf

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: usb_modeswitch_config.conf
Error: Could not find file usb_modeswitch_config.conf

kaiser@kaiser-desktop:~$ 
<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

lo deje morir al intento dos...

> **Intento 3:**

<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
kaiser@kaiser-desktop:~$ sudo gedit /etc/usb_modeswitch.conf
[sudo] password for kaiser: 
<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

Pegue el codigo que me diste al final de archivo... con los distintos messagecontent... nada...
> **Intento 4:**

No seguí el log de lo que intente...
[B]
Por favor, teneme paciencia, ¿Que estoy haciedo mal...?[/B]

Por cierto, es verdad que lo toma como el disp de almacenamiento por que en nautilus me lo tomaba como disco externo. Entonces no esta pasando de alamac a modem...

Un abrazo groso,

---

### Post by beren.olvar on 2010-06-15
No te desesperes, en mi experiencia el soporte para estos dispositivos es bien precario, a si es que es natural que estes teniendo algunos problemas. Ademas, me disculpo por darte instrucciones imprecisas, ahora trato de hacerlo mejor:

Mi idea es tratar de empezar desde un ambiente lo mas "limpio" posible. Por eso te recomiendo borrar las reglas de udev que los tutoriales mencionan:
```

sudo rm /etc/udev/rules.d/55-ztemf110.rules
sudo rm /etc/udev/rules.d/91-usb_modeswitch.rules

```. 
Cuando este todo funcionando las podemos poner de nuevo.

Luego, ademas creo ke es mejor si usas un archivo de configuracion personal, en vez de editar el archivo /etc/usb_modeswitch.conf, ke esta lleno de configuraciones ke no son la ke necesitas. Para eso escribe en un terminal
```
gedit mi_conf.conf
``` y escribes
```
###################################################
# ZTE MF110 
#
# Contributor: Fernando Anthony Ristagno
###################################################

DefaultVendor=0x19d2
DefaultProduct=0x2000

TargetVendor=0x19d2
TargetProduct=0x0031

;MessageEndpoint=0x1
MessageContent="55534243b8fe6681000000000000061b000000020000000000000000000000"
``` 
Lo guardas, y luego ejecutas el modeswitch como:
```

sudo usb_modeswitch -W -c mi_conf.conf
sudo modprobe usbserial vendor=0x19d2 product=0x0031

```

A lo ke me referia a "donde estas parado" es el directorio en donde estas trabajando. Cuando abres un terminal, este esta siempre ubicado en el directorio ~ ke, en tu caso, es lo mismo ke /home/kaiser. Esto es importante por lo siguiente:

cuando haces "gedit mi_conf.conf", es como si escribieras "gedit /home/kaiser/mi_conf.conf", pq "estas parado" en el directorio /home/kaiser/. Entonces despues, al correr el usb_modeswitch, lo ke keremos es ke utilice ese mismo archivo como configuracion, por eso la opcion "-c mi_conf.conf" (el -W es paa ke imprima toda la informacion posible a la pantalla)

si despues de hacer esto, aun el networkmanager no reconoce tu modem, intenta cambiando la linea ke dice 
MessageContent="55534243b8fe6681000000000000061b000000020000000000000000000000"
por 
MessageContent="55534243123456782000000080000c8501 0101180101010101000000000000"
y si tampoco funciona intenta cambiandola por
MessageContent="5553424312345678000000000000061b00 0000030000000000000000000000"

Copia aca los mensajes de error ke obtengas para ir viendo donde esta el problema.
Recuerda desconectar el modem usb cada vez, para ke los intentos anteriores no interfieran, y esperar unos cuantos segundos antes de usar el comando usb_modeswitch.
Mucha suerte!

---

### Post by UbGooK on 2010-06-15
Por favor no te disculpes si me estas ayudando. Además de paso jugue un rato con la consola.

Al igual que ayer recien estoy en mi pc a la madrugada así que a las 2:00 o 3:00 publico los resultados. Que según veo puede funciona.

Gracias, un abrazo,

---

### Post by UbGooK on 2010-06-16
**Esto paso campeón... 0% conexión.**

> MessageContent="55534243b8fe6681000000000000061b000000020000000000000000000000"```
kaiser@kaiser-desktop:~$ gedit mi_conf.conf
kaiser@kaiser-desktop:~$ sudo usb_modeswitch -W -c mi_conf.conf
[sudo] password for kaiser: 

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: mi_conf.conf
DefaultVendor=  0x19d2
DefaultProduct= 0x2000
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint= not set
MessageContent="55534243b8fe6681000000000000061b000000020000000000000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 003
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 004 on 001
usb_os_find_devices: Found 003 on 001
usb_os_find_devices: Found 002 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 003 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
USB error: error submitting URB: Device or resource busy
 Could not get INQUIRY response (error -16)

Device description data (identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE WCDMA Technologies MSM
  Serial No.: P671A2PERD010000
-------------------------
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 Sending the message returned error -110. Trying to continue
-> Run lsusb to note any changes. Bye.

kaiser@kaiser-desktop:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031
```*******

> MessageContent="55534243123456782000000080000c85010101180101010101000000000000"```
kaiser@kaiser-desktop:~$ sudo usb_modeswitch -W -c mi_conf.conf

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: mi_conf.conf
DefaultVendor=  0x19d2
DefaultProduct= 0x2000
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint= not set
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 003
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 012 on 001
usb_os_find_devices: Found 011 on 001
usb_os_find_devices: Found 010 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 012 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
USB error: error submitting URB: Device or resource busy
 Could not get INQUIRY response (error -16)

Device description data (identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE WCDMA Technologies MSM
  Serial No.: P671A2PERD010000
-------------------------
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 Sending the message returned error -110. Trying to continue
-> Run lsusb to note any changes. Bye.

kaiser@kaiser-desktop:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031

```> MessageContent="5553424312345678000000000000061b000000030000000000000000000000"```
kaiser@kaiser-desktop:~$ sudo usb_modeswitch -W -c mi_conf.conf

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: mi_conf.conf
DefaultVendor=  0x19d2
DefaultProduct= 0x2000
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint= not set
MessageContent="5553424312345678000000000000061b000000030000000000000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 003
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 014 on 001
usb_os_find_devices: Found 013 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 No default device found. Is it connected? Bye.

kaiser@kaiser-desktop:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031
kaiser@kaiser-desktop:~$ clear

kaiser@kaiser-desktop:~$ sudo usb_modeswitch -W -c mi_conf.conf

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: mi_conf.conf
DefaultVendor=  0x19d2
DefaultProduct= 0x2000
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint= not set
MessageContent="55534243b8fe6681000000000000061b000000020000000000000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 003
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 020 on 001
usb_os_find_devices: Found 019 on 001
usb_os_find_devices: Found 018 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 020 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
USB error: error submitting URB: Device or resource busy
 Could not get INQUIRY response (error -16)

Device description data (identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE WCDMA Technologies MSM
  Serial No.: P671A2PERD010000
-------------------------
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 Sending the message returned error -110. Trying to continue
-> Run lsusb to note any changes. Bye.

kaiser@kaiser-desktop:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031
kaiser@kaiser-desktop:~$ sudo usb_modeswitch -W -c mi_conf.conf

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: mi_conf.conf
DefaultVendor=  0x19d2
DefaultProduct= 0x2000
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint= not set
MessageContent="55534243b8fe6681000000000000061b000000020000000000000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 003
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 025 on 001
usb_os_find_devices: Found 024 on 001
usb_os_find_devices: Found 023 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 025 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
USB error: error submitting URB: Device or resource busy
 Could not get INQUIRY response (error -16)

Device description data (identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE WCDMA Technologies MSM
  Serial No.: P671A2PERD010000
-------------------------
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 Sending the message returned error -110. Trying to continue
-> Run lsusb to note any changes. Bye.

```> Creo que este esta repetido...```
kaiser@kaiser-desktop:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031
kaiser@kaiser-desktop:~$ sudo usb_modeswitch -W -c mi_conf.conf

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: mi_conf.conf
DefaultVendor=  0x19d2
DefaultProduct= 0x2000
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint= not set
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 003
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 029 on 001
usb_os_find_devices: Found 028 on 001
usb_os_find_devices: Found 026 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 029 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
USB error: error submitting URB: Device or resource busy
 Could not get INQUIRY response (error -16)

Device description data (identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE WCDMA Technologies MSM
  Serial No.: P671A2PERD010000
-------------------------
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 Sending the message returned error -110. Trying to continue
-> Run lsusb to note any changes. Bye.

kaiser@kaiser-desktop:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031
kaiser@kaiser-desktop:~$ sudo usb_modeswitch -W -c mi_conf.conf

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: mi_conf.conf
DefaultVendor=  0x19d2
DefaultProduct= 0x2000
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint= not set
MessageContent="5553424312345678000000000000061b000000030000000000000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 003
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 033 on 001
usb_os_find_devices: Found 032 on 001
usb_os_find_devices: Found 031 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 033 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
USB error: error submitting URB: Device or resource busy
 Could not get INQUIRY response (error -16)

Device description data (identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE WCDMA Technologies MSM
  Serial No.: P671A2PERD010000
-------------------------
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 Sending the message returned error -110. Trying to continue
-> Run lsusb to note any changes. Bye.

kaiser@kaiser-desktop:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031
kaiser@kaiser-desktop:~$ sudo usb_modeswitch

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 033 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached

```

---

### Post by beren.olvar on 2010-06-16
Uff.. ke mala suerte,

lo primero ke se me ocurre ke puedes hacer es cambiar la linea ke dice:
;MessageEndpoint=0x1
a
MessageEndpoint=0x1
es decir, borrar el ; del inicio de la linea. Las lineas ke comienzan con ; son comentarios, es decir el programa no los lee. Asi lo tenia yo y funcionaba, por eso te recomende ke lo pusieras con comentarios, pero en la version ke tenias tu estaba sin el ; y no me fije. Intenta de nuevo con ese pequenho cambio, a ver ke pasa.

podrias tambien incorporar el output del comando lsusb, para ver si es ke hay algun cambio luego de correr el usb_modeswitch.

Viendo la ultima version del usb_modeswitch, parece ke los datos deberian ser:
```

########################################################
# ZTE MF110
#
# Contributor: Moritz Grosse-Wentrup

DefaultVendor=  0x19d2
DefaultProduct= 0x0053

TargetVendor=   0x19d2
TargetProduct=  0x0031

MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
########################################################

```

Si aun no funciona, podrias intentar una solucion ke encontre buscando en internet:
[http://taringa.net/posts/linux/4578132/modem-3g-Zte-mf110-personal-en-Ubuntu-kubuntu-xubuntu-9_10.html](http://taringa.net/posts/linux/4578132/modem-3g-Zte-mf110-personal-en-Ubuntu-kubuntu-xubuntu-9_10.html)

---

### Post by UbGooK on 2010-06-17
Genio =D. Con la ultima config al parecer el administrador de redes me habilita la pestaña de banda ancha movil. "Instalo" la red predeterminada donde me dan los numeros de personal, user, clave, etc. PERO nada..., luego probe la otra clave y tampoco nada... alguna sugerencia campeón? =S

> LOG LSUSB de config 1
```
kaiser@kaiser-desktop:~$ sudo usb_modeswitch -W -c mi_conf.conf
[sudo] password for kaiser: 

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: mi_conf.conf
DefaultVendor=  0x19d2
DefaultProduct= 0x2000
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint=0x01
MessageContent="55534243b8fe6681000000000000061b000000020000000000000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 003
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 011 on 001
usb_os_find_devices: Found 009 on 001
usb_os_find_devices: Found 008 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 011 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
USB error: error submitting URB: Device or resource busy
 Could not get INQUIRY response (error -16)

Device description data (identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE WCDMA Technologies MSM
  Serial No.: P671A2PERD010000
-------------------------
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 Sending the message returned error -110. Trying to continue
-> Run lsusb to note any changes. Bye.

kaiser@kaiser-desktop:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031
kaiser@kaiser-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 19d2:2000 ONDA Communication S.p.A. ZTE MF627/MF628/MF628+ HSDPA
Bus 001 Device 009: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 008: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

> LOG LSUSB de config 2
```
kaiser@kaiser-desktop:~$ sudo usb_modeswitch -W -c mi_conf.conf

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: mi_conf.conf
DefaultVendor=  0x19d2
DefaultProduct= 0x2000
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 003
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 010 on 001
usb_os_find_devices: Found 009 on 001
usb_os_find_devices: Found 008 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 010 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
USB error: could not get bound driver: No data available
 No driver found. Either detached before or never attached


```

> LOG LSUSB de config 3
```
kaiser@kaiser-desktop:~$ gedit mi_conf.conf
kaiser@kaiser-desktop:~$ sudo usb_modeswitch -W -c mi_conf.conf
[sudo] password for kaiser: 

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: mi_conf.conf
DefaultVendor=  0x19d2
DefaultProduct= 0x2000
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint=0x01
MessageContent="5553424312345678000000000000061b000000030000000000000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 003
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 007 on 001
usb_os_find_devices: Found 006 on 001
usb_os_find_devices: Found 005 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 007 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
USB error: error submitting URB: Device or resource busy
 Could not get INQUIRY response (error -16)

Device description data (identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE WCDMA Technologies MSM
  Serial No.: P671A2PERD010000
-------------------------
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 Sending the message returned error -110. Trying to continue
-> Run lsusb to note any changes. Bye.

kaiser@kaiser-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 19d2:2000 ONDA Communication S.p.A. ZTE MF627/MF628/MF628+ HSDPA
Bus 001 Device 006: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kaiser@kaiser-desktop:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031
kaiser@kaiser-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 19d2:2000 ONDA Communication S.p.A. ZTE MF627/MF628/MF628+ HSDPA
Bus 001 Device 006: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@


```


> LOG LSUSB de config NUEVO CODIGO
```
kaiser@kaiser-desktop:~$ sudo usb_modeswitch -W -c mi_conf.conf

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: mi_conf.conf
DefaultVendor=  0x19d2
DefaultProduct= 0x0053
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint= not set
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 003
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 009 on 001
usb_os_find_devices: Found 008 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 No default device found. Is it connected? Bye.

kaiser@kaiser-desktop:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031
kaiser@kaiser-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 008: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kaiser@kaiser-desktop:~$ sudo usb_modeswitch -W -c mi_conf.conf

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: mi_conf.conf
DefaultVendor=  0x19d2
DefaultProduct= 0x0053
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint= not set
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 003
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 009 on 001
usb_os_find_devices: Found 008 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 No default device found. Is it connected? Bye.

```

---

### Post by beren.olvar on 2010-06-20
Creo que eso mismo me ha pasaba a mi con mi antena. El networkmanager reconocia el modem, pero no podia conectarse a internet.
Lo que hacia para resolverlo era desenchufar y volver a enchufar el modem y rehacer los pasos, hasta que el network manager reconocia 2 interfaces. Una de ellas podia conectarse. Lamento no poder darte una ayuda mas concreta, pero en mi caso tambien tenia que depender bastante del azar.
Seria bueno que si encuentras alguna forma mas estable de hacer andar el dispositivo lo publicaras aca para poder ayudar a las personas que tengan este mismo problema. 
Yo voy a tratar de postearte mas informacion si es que logro descubrir algo.

Mucha suerte!

---

### Post by atari130xe on 2010-06-20
Mi hermana tiene el mismo modem pero con Claro, seguì este thread y funciona excelente, conseguì los datos de conexiòn de Personal y deberias obtener el mismo resultado:

[http://ubuntuforums.org/showthread.php?t=1391818&highlight=modem+zte+de+claro]("http://ubuntuforums.org/showthread.php?t=1391818&highlight=modem+zte+de+claro")

espero te sirva.

---

### Post by UbGooK on 2010-06-25
SOLUCIONADO. (...)

La solución quizás no les guste pero funciono y no creí que funcionara.

Instale Linux Mint 9 (Gnome) (DVD) se instalo muy rápido desde el pendriver de 8GB y solo por casualidad probe el asistente de conexión use todo standaar y lo tomo en 3 segundos!, no expulse nada, no hice nada de nada, solo eso. Funciona perfecto, mejor que en Windows que ahora descanse en paz.

De hecho ya me instale mi entorno preferido "LXDE" todo va perfecto!

Si quieres díganme que hago y les paso la configuración que tiene Linux Mint para tomarlo tan fácilmente.

¿Será por algún driver privativo?

Un abrazo genios!

---

