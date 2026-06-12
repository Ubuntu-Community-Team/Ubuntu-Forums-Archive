---
title: "conexion telefonica a internet...como???"
date: 2009-10-18
forum: Hardware
---

### Post by dcorrea on 2009-10-18
Hola a todos!!
Estoy usando ubuntu 9.4 y tengo que hacer una conexion a internet via telefono. Es decir, con nombre de usuario, password y numero telefonico.
En que parte se configura esa conexion??
He buscado y no encuentro...
solo esta ethernet, adsl, inalambrica...eso...

gracias!!

---

### Post by moreback on 2009-10-18
Desconozco si hay algún plugin para el NM que permita hacer conexiones PPP con un módem, pero por lo menos hay un Applet para el panel que te permite usar un modem: "Monitor del modem". A lo mejor con ese puedes conectarte.

No sé si ese applet usa gnome-ppp para conectarse, pero si te falta lo puedes instalar desde Synaptic: [apt:gnome-ppp](apt:gnome-ppp)

Saludos.

---

### Post by gmunioz on 2009-10-18
Hola dco...:

Primero debes descargar desde este sitio:

[http://packages.ubuntu.com/jaunty/wvdial](http://packages.ubuntu.com/jaunty/wvdial)

Los siguientes paquetes, si no estan instalados

(esto lo puedes controlar desde synaptic)

```
wvdial  debconf libc6 libuniconf4.4 libwvstreams4.4-base libwvstreams4.4-extras libxplc0.3.13 ppp 
```
         
Una vez descargados los instalas ejecutando en el 

directorio donde se descargaron la orden en consola

```
sudo dpkg -i *.deb
```

Segundo debes configurar los servidores de nombres

Es necesario especificar los DNS (servidores de nombres) 

en el archivo /etc/resolv.conf. Si desconoces que DNS debe utilizar

puedes preguntar a tu proveedor de servicio de acceso a Internet (ISP). 

o utilizar los del ejemplo de opendns, el archivo que se abre con

la orden en consola

```
sudo gedit /etc/resolv.conf

```
debe contener estas lineas:

```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

Tercero debes tener un modem.

Se necesita un modem por hardware para poder conectarse a Internet. 
Estos son modems externos SERIALES, modems internos ISA que se configuran por Jumpers o US Robotics/3Com 56K FaxModem Modelo 561. 

La mayoría de los modems USB, los softmodems y winmodems NO SON COMPATIBLES con GNU/Linux. 

Deberas consultar a Linmodems.org para intentar hacerlos funcionar

Tratandose de modems compatibles se debe detectarlo y configurarlo. 

Ejecuta en consola siguiente comando:

```
sudo wvdialconf /etc/wvdial.conf
```

Este comando examina todos los puertos de comunicaciones existentes en el sistema 

enviando comandos ATT. Si el modem es compatible, será detectado sin problemas y 

determinará la cadena de inicialización de comandos ATT apropiados, 

Dando una salida en pantalla con lineas como las siguientes:

```
Found a modem on /dev/ttyS0.
ttyS0: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 S11=55 +FCLASS=0"

```
Ahora es necesario crear el enlace simbólico necesario para los programas 

y guiones que se utilizarán, para ello ejecutas en consola las ordenes:

```
cd /dev
sudo rm -f modem
sudo ln -s ttyS0 modem


```
[B]donde ttyS0 debe ser igual a la informada por wvdialconf
[/B]

Cuarto configurar la interfaz.

Considerando que en /etc/wvdial.conf se tendría algo como lo siguiente:

```
[Dialer Defaults]
Modem = /dev/ttyS0
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 S11=55 +FCLASS=0
SetVolume = 1
Dial Command = ATDT
Init4 = ATM1L3
; Phone = 
; Username = 
; Password = 
```

Debes añadir una interfaz o Dialer. Es conveniente utilizar como nombre para este Dialer el mismo que corresponde a la primera interfaz PPP, es decir ppp0. 
También será necesario especificar el nombre de usuario, contraseña y número telefónico al cual se deberá marcar para acceder a Internet. Será conveniente también habilitar el modo Stupid, a fin de que pppd se encargue de hacer toda la negociación de comandos ATT necesarios:

```
[Dialer ppp0]
Username = tu_nombre_de_usuario
Password = tu_contraseña
Phone = teléfono_de_tu_proveedor
Inherits = Dialer Defaults
Stupid mode = 1
```

Habiendo hecho lo anterior, /etc/wvdial.conf debe haber quedado del siguiente modo:

```
[Modem0]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 S11=55 +FCLASS=0
SetVolume = 1
Dial Command = ATDT
Init4 = ATM1L3

[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 S11=55 +FCLASS=0
SetVolume = 1
Dial Command = ATDT
Init4 = ATM1L3

[Dialer ppp0]
Username = tu_de_usuario
Password = tu_contraseña
Phone = teléfono_de_tu_proveedor
Inherits = Dialer Defaults
Stupid mode = 1

```

Debe editarse /etc/ppp/pap-secrets y /etc/ppp/chap-secrets a fin 
de especificar nuevamente el nombre de usuario y contraseña correspondientes, de acuerdo a como se hizo en /etc/wvdial.conf:

```
sudo gedit /etc/ppp/pap-secrets 
sudo gedit /etc/ppp/chap-secrets 
```

Y pones una línea en cada uno con lo siguiente

```
tu_nombre_de_usuario  *  tu_contraseña
```

quinto levantar y detener la interfaz.

Para conectarte a Internet ejecutas el siguiente comando:

```
sudo ifup ppp0
```

O con wvdial:

```
sudo wvdial ppp0
```

Para deconectarte, ejecutas este otro comando:

```
sudo ifdown ppp0
```

---

### Post by tetzauh on 2010-05-05
explanation seems clear enough, but what happens when the modem configuration you are trying to set up IS your only interet access? any additional steps one may have to follow if synaptic is not available?

---

