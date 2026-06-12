---
title: "wifi en kubuntu 9.04"
date: 2010-01-14
forum: Hardware
---

### Post by gustavo_ing on 2010-01-14
hola tengo una tarjeta wlan ralink2500 , instale kubuntu 9.04.
Cuando carga todo me detecta la tarjeta y hasta veo las redes, el problema es que no se conecta a ellas, no entiendo porque puede pasar, lo mismo con la tarjeta lan.
Ademas como que baja la sensibilidad de la tarjeta wifi.
Lo otro es que me anda lento, tengo un tarjeta de video intel, de la serie 945G o algo muy similar, y ya lei que tienen problemas con el render.

Primero me gustaria solucionar lo de la wifi para poder googlear tranquilo en el mismo linux y probar todo lo demas.



de antemano gracias!

pd: soy noob en linux

---

### Post by CdK1 on 2010-01-14
Usa Wicd para conectarte a Wifi y sobre tú tarjeta ya está en un post diferente con un xorg.conf de ejemplo...

---

### Post by gustavo_ing on 2010-01-14
> **CdK1 said:**
> Usa Wicd para conectarte a Wifi y sobre tú tarjeta ya está en un post diferente con un xorg.conf de ejemplo...

el wicd ya viene con los repositorios del kubuntu 9.04, lo pregunto porque como no tengo acceso a internet q no sea wifi, si entro debo tener ojala todo bien listo para probar comandos y configuraciones, por lo que si me pide una libreria u otra cosa estaria medio dificil seguirlo.

Saludos y gracias

---

### Post by CdK1 on 2010-01-14
En ese caso deberías hacerlo desde la consola, sería algo así:

sudo iwlist ethX scan
sudo ifconfig ethX up
sudo iwconfig ethX essid EscribeLaESSID
sudo iwconfig ethX key s:clave_wireless
sudo dhclient ethX

X es tu tarjeta... debería ser eth1 pero ahi pruebas...

---

### Post by gustavo_ing on 2010-01-14
> **CdK1 said:**
> En ese caso deberías hacerlo desde la consola, sería algo así:

sudo iwlist ethX scan
sudo ifconfig ethX up
sudo iwconfig ethX essid EscribeLaESSID
sudo iwconfig ethX key s:clave_wireless
sudo dhclient ethX

X es tu tarjeta... debería ser eth1 pero ahi pruebas...

gracias CDK1, estoy bajandome el ubuntu 9.10 por si acaso, y algunos cosas extra.
Ahi te cuento como me va, saludos! (=

---

### Post by CdK1 on 2010-01-14
Dale, si tienes algún error, postea para ver si podemos solucionarlo...

---

### Post by gustavo_ing on 2010-01-14
hice el sudo iwlist eht0, 1 y hasta 2 pero me dice qye la interface no soporta scaning...

y note que cuando intente la conexion con el kde se cae, pero es un problema al parecer del kde.


que mas puedo hacer, tambien probe instalar el wicd con apt-get install wicd pero no encuentra el paquete 


que mas podria hacer?

---

### Post by CdK1 on 2010-01-14
Es eth0 o eth1 no eht1 etc, y ya que recien instalaste, has un apt-get update luego apt-get upgrade && apt-get dist upgrade && apt-get install wicd suponiendo que estas conectado por cable...

---

### Post by CdK1 on 2010-01-14
Es wap o wep?

 [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)
[http://www.debianadmin.com/wicd-easy-network-connection-manager-in-debian.html](http://www.debianadmin.com/wicd-easy-network-connection-manager-in-debian.html)

---

### Post by gustavo_ing on 2010-01-14
> **CdK1 said:**
> Es eth0 o eth1 no eht1 etc, y ya que recien instalaste, has un apt-get update luego apt-get upgrade && apt-get dist upgrade && apt-get install wicd suponiendo que estas conectado por cable...

jeje vamos mejor, problema capa 8


ahora cuando puse sudo iwconfig wlan0 key s:mi_clave
me retorno
error for wireless request "Set encode" (8B2A)
SET failed on device wlan0 : Invalid argument

debe ir encodeada?


saludos

---

### Post by CdK1 on 2010-01-14
Tú interfaz no debería ser ra0?, partamos por configurarla...

[http://crysol.org/es/node/214](http://crysol.org/es/node/214)
[http://www.ubuntu-es.org/index.php?q=node/13998](http://www.ubuntu-es.org/index.php?q=node/13998)
[http://m3n3chm0.wordpress.com/2007/05/04/configuracion-tarjeta-inalambrica-ralink-ralink-rt2500-802/](http://m3n3chm0.wordpress.com/2007/05/04/configuracion-tarjeta-inalambrica-ralink-ralink-rt2500-802/)

---

### Post by gustavo_ing on 2010-01-14
> **CdK1 said:**
> Tú interfaz no debería ser ra0?, partamos por configurarla...

[http://crysol.org/es/node/214](http://crysol.org/es/node/214)
[http://www.ubuntu-es.org/index.php?q=node/13998](http://www.ubuntu-es.org/index.php?q=node/13998)
[http://m3n3chm0.wordpress.com/2007/05/04/configuracion-tarjeta-inalambrica-ralink-ralink-rt2500-802/](http://m3n3chm0.wordpress.com/2007/05/04/configuracion-tarjeta-inalambrica-ralink-ralink-rt2500-802/)

excelente y muchas gracias, tenia bajado el driver pero no he podido compilarlo, me faltan los paquetes necesarios para correr el make y todo eso.

a todo esto, en una de esas estaran en el cd de instalacion, o algo relacionado con el desarrollo y librerias?


de antemano muchas gracias!
ahi t cuento como me va!

saludos :popcorn:

---

### Post by CdK1 on 2010-01-14
apt-get install linux-headers-$(uname -r) make build-essential etc...

---

### Post by CdK1 on 2010-01-14
Has esto mejor:

    sudo apt-get install module-assistant linux-headers-$(uname -r) rt2500-source && cd /usr/src && tar zxvf rt2500.tar.gz && module-assistant prepare && module-assistant get rt2500 && module-assistant build rt2500 && modprobe rt2500


Pega todo eso en la consola...



Luego aplicas lo que sale acá...


[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)


Etc...

---

