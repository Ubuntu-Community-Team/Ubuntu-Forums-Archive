---
title: "Problema con configuracion de red"
date: 2009-10-10
forum: Hardware
---

### Post by canariopdu on 2009-10-10
Buenas... Antes que nada, soy nuevo en linux, es la primera vez que instalo un ubuntu. Es la version 8.10 Estoy tratando de configurarle a la pc una ip estatica pero no me deja. Ya he mirado varios foros y hecho lo que dicen pero sigue sin funcionar. 

Lo que hice fue ejecutar este comando en la terminal:

sudo nano /etc/network/interfaces

y luego modificar el archivo para que me quede de esta forma:

auto eth0
iface eth0 inet static
address 192.168.1.219
netmask 255.255.255.0
gateway 192.168.1.1

pero al hacer eso lo único que logro es que no me reconozca la tarjeta de red.

Muchas gracias.

---

### Post by guillermolisi on 2009-10-10
> **canariopdu said:**
> Buenas... Antes que nada, soy nuevo en linux, es la primera vez que instalo un ubuntu. Es la version 8.10 Estoy tratando de configurarle a la pc una ip estatica pero no me deja. Ya he mirado varios foros y hecho lo que dicen pero sigue sin funcionar. 

Lo que hice fue ejecutar este comando en la terminal:

sudo nano /etc/network/interfaces

y luego modificar el archivo para que me quede de esta forma:

auto eth0
iface eth0 inet static
address 192.168.1.219
netmask 255.255.255.0
gateway 192.168.1.1

pero al hacer eso lo único que logro es que no me reconozca la tarjeta de red.

Muchas gracias.
La IP 192.168.1.1 a que dispositivo corresponde ?
Que tipo de conexion a Internet tenes ?

Esa maquina esta en una LAN o sale directo a Internet, sin router ni nada que se le parezca ? Si esta en una LAN cn otras maquinas, que IPs y mascara de red (netmask) tienen esas otras ?

El cable que estas usando funciona bien con otras maquinas ?

Probaste iniciando con el LiveCD a ver si la interface la reconoce bien y conecta ?

De paso, postea la salida de "lspci" y "lsusb" (sin las comillas) corridos en una terminal/consola.

---

### Post by canariopdu on 2009-10-10
ya quedo, el problema era que me desaparecía el icono de conexión de red, pero en realidad estaba conectada a la red. 

Muchas Gracias, 

saludos.

---

### Post by staar on 2009-10-10
cuando configurás la conexión desde ese archivo, network-manager (el programa que te pone el icono en el panel, al lado del reloj) se desactiva, ya que para funcionar necesita ese archivo vacio, ambas formas de configuración de la red son incompatibles...

saludos

---

