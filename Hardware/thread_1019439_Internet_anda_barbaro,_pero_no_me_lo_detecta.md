---
title: "Internet anda barbaro, pero no me lo detecta :\"
date: 2008-12-23
forum: Hardware
---

### Post by sanflores on 2008-12-23
Hola gente, que tal, necesito que me tiren una mano... tengo IPLAN como proveedor, por lo que configuro la IP manual, esto lo hice en la instalación y todo andubo bien, pero tengo un problema ya que el Network Manager no me lo detecta, es como si pensara que no tengo internet, pero en realidad si tengo :\

Y necesito que el Network manager se de cuenta de que todo anda bien para poder utilizar la vpn.

Muchas gracias.

---

### Post by Hei Ku on 2008-12-23
postea el resultado del comando ifconfig

---

### Post by sanflores on 2008-12-23
> **Hei Ku said:**
> postea el resultado del comando ifconfig

sanflores@SILVER:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:19:66:53:3f:e2  
          inet dirección:2XX.XXX.XXX.XXX  Difusión:2XX.XXX.XXX.XXX  Máscara:255.255.255.252
          dirección inet6: fe80::XXX:XXXX:XXXX:XXXX/XX Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:16722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14819 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:18083905 (18.0 MB)  TX bytes:2123491 (2.1 MB)
          Interrupción:220 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

sanflores@SILVER:~$ 


Este es el resultado, todo normal me parece... lo que no me anda es el icono de internet por asi decirlo

---

### Post by Hei Ku on 2008-12-23
Cuando querés abrir el Network Manager qué es lo que te dice?

---

### Post by sanflores on 2008-12-23
Cuando pongo Información de la conexión me sale:

Ha ocurrido un error al mostrar información de conexión:

No se encontró ninguna conexión activa válida


Si activo o desactivo la red... es indiferente, queda siempre activa   <--- Error
CORRIJO: Si desactivo, SI deja de funcionar internet

---

### Post by mhoyos on 2008-12-23
hola..

la conexion de iplan, va "directo" en el linux ?? o estaras detras de un router ??

si va directo, vas a tener que configurar "a mano" con los valores fijos para la IP, la mascara de subred, la puerta de enlace y los DNS.

proba primero hacerlo en el network-manager, sino modifica lo siguiente:

/etc/network/interfaces :

```
auto eth0 
iface inet eth0 static
    address IP_fija
    netmask mascara_subred
    gateway puerta_enlace
```


y los dns, en /etc/resolv.conf:

```
nameserver ip_dns1
nameserver ip_dns2
```

espero te sirva..

---

### Post by sanflores on 2008-12-23
> **mhoyos said:**
> hola..

la conexion de iplan, va "directo" en el linux ?? o estaras detras de un router ??

si va directo, vas a tener que configurar "a mano" con los valores fijos para la IP, la mascara de subred, la puerta de enlace y los DNS.

proba primero hacerlo en el network-manager, sino modifica lo siguiente:

/etc/network/interfaces :

```
auto eth0 
iface inet eth0 static
    address IP_fija
    netmask mascara_subred
    gateway puerta_enlace
```


y los dns, en /etc/resolv.conf:

```
nameserver ip_dns1
nameserver ip_dns2
```

espero te sirva..

Gracias, pero no creo que esto me sea de ayuda, te paso a explicar un poco mejor como es la mano, la conexión va a un modem cisco 575 (Long Reach Ethernet). Eso de configurar a mano con los valores fijos, ya lo hice (en la instalación) e internet anda perfecto, no tiene ningun drama, igual que los DNS que andan fantasticos los dos. El único drama que tengo, es que el icono del Network Manager (el que esta arriba a la derecha, cerca del reloj) no me muestra que esta activada la conexión, se queda permanentemente con:

Ha ocurrido un error al mostrar información de conexión:

No se encontró ninguna conexión activa válida

Ah, también dicho sea de paso, cuando pongo para monitorear los recursos, el de la red funca sin ningun drama, o sea, me muestra todo como debe ser, pero lo que no me anda es el icono solamente, es decir, cuando pongo para configurar la red, y vuelvo a poner los valores para que me tome la conexión, es como si no guardara... y no puedo configurar la conexión, por consiguiente, tampoco puedo configurar VPN

---

### Post by mhoyos on 2008-12-23
por lo que entiendo:

- configuraste a mano la conexion y anda OK.
- el networkmanager no informa lo que es real (es decir: estas conectado, pero para el network manager "no lo interpreta".
- salvo lo del network manager, el resto anda todo: lan, wan, etc.. 

si tu problema es SOLO lo de la vpn... porque no lo instalas a mano ?? es decir, no dependas del network manager para armar la vpn.. !!

en el caso que necesites o sea impresindible usar el networkmanager, lo recomendable es que configures la red a traves de esa aplicacion, pero en tu caso, no lo recomiendo, dado que la aplicacion (nm) es util para conexiones simples (dhcp, wireless, etc) pero se "atonta" cuando son valores fijos..

esperamos tu respuesta..

salu2

---

### Post by sanflores on 2008-12-23
Entendistes barbaro, lo de la vpn, es la unica forma que conocía :(
Me podrías decir de alguna otra vpn? Yo necesito conectarme a la vpn de mi trabajo, que es de cisco. Asi que me imagino que debería tener algun tipo de compatibilidad con eso.

Muchas gracias loco

---

### Post by mhoyos on 2008-12-23
;)

lo de la vpn sabes como funciona ??
que version de cisco estan usando ??
alguna vez usaste y/o configuraste una vpn en un linux ??

en el caso de que tus respuestas no sean favorables, revisa estos links:

[http://www.blog.arun-prabha.com/2008/05/01/cisco-vpn-installation-issue-with-ubuntu-804-hardy-heron/](http://www.blog.arun-prabha.com/2008/05/01/cisco-vpn-installation-issue-with-ubuntu-804-hardy-heron/)

[http://www.noseque.net/wordpress/2008/05/11/howto-cisco-vpn-client-en-ubuntu-804-hardy-heron/](http://www.noseque.net/wordpress/2008/05/11/howto-cisco-vpn-client-en-ubuntu-804-hardy-heron/)

[http://thoughtworker.in/2008/11/19/ubuntu-cisco-vpn-client-installation-on-intrepid/](http://thoughtworker.in/2008/11/19/ubuntu-cisco-vpn-client-installation-on-intrepid/)

espero te sirva..

P.D: un "click en thanks" no me viene nada mal.. jejeje.... :P

salu2

---

### Post by sanflores on 2008-12-23
A leer entonces :)
Y dejo abierta la pregunta por si a alguien se le ocurre alguna idea :)

Gracias

---

