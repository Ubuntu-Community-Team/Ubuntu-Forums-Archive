---
title: "Compartir internet desde OS X a Xubuntu 8.10"
date: 2009-05-04
forum: Hardware
---

### Post by MrOSX on 2009-05-04
Hola a todos, es mi primer post y no encontre una solucion a mi problema especifico asi que aqui me explayo je!

Esto es así: 
* Tengo dos computadoras: una eMac G4 conectada a un PC con Xubuntu 8.10  y win XP por medio
    de un cable cruzado.
* La eMac recibe Internet por medio de la placa inalámbrica, la PC no tiene internet, por lo cual no
   puedo bajar ningun repositorio (quizas haya una manera de instalar repositorios sin coneccion a
   internet pero yo aun no la conozco)
* En OS X habilite las funciones "compartir Internet: desde: Airport, a pc conectadas por: Ethernet"
   (*Airport* es el nombre comercial de la tarjeta de red inalámbrica)

Y eso es todo hasta ahora, como es de esperarse la PC no tiene conexión a internet, en win tube algunos avances como ser llegar a compartir archivos, es decir, las 2 PCs estaban en la misma red y  podian compartir archivos entre ellas (o casi, ya que no pude entrar al recurso compartido de la mac por un problema de contraseñas).

He pedido ayuda también en el foro de Apple, si quieren checkear, el thread esta en (un mal) Ingles: [http://discussions.apple.com/thread.jspa?threadID=1994586&tstart=0](http://discussions.apple.com/thread.jspa?threadID=1994586&tstart=0)

Les agradezco toda la ayuda que me puedan dar, ya que, como se darán cuenta, de redes no entiendo mucho...
Saludos!

---

### Post by gmunioz on 2009-05-04
Hola mro....:

Desde ubuntu, no tienes que hacer nada, solo configurar la tarjeta de red

con una ip dentro del mismo rango que la de la mac y esta como gateway, 

esto lo haces con ifconfig o editando el archivo /etc/interfaces

Este archivo debe tener algo asi como

> 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0    (esta es tu tarjeta de red)
iface eth0 inet static
address 192.168.1.90  (la direccion ip de la tarjeta)
gateway 192.168.1.1    (la direccion ip de la tarjeta mac)
netmask 255.255.255.0  (máscara de red
network 192.168.1.0     (rango de la red)
broadcast 192.168.1.255  (dominio de difusión)


Respecto de osx, ignoro todo, deberias leer acerca de un proxy o

como hacer nat, en el.

Saludos.

---

### Post by hictio on 2009-05-04
MrOSX (que buen nick! :D )
Es como bien dice gmunioz, si en la Os X tenés habilitado el Internet Sharing, con usar en la Ubuntu la dirección IP del Os X como default gateway tendrías que, primero, ver las dos máquinas, y segundo, salir a internet a través de la Os X.
Un par de preguntas, con todo setteado:

- podés hacer ping desde la Os X a la Ubuntu (y viceversa)
- qué DNS estás usando en la Ubuntu?

Desde la Ubuntu, con todo setteado y conectado, probaste algo básico como un ping a algún servidor en internet? Para descartar problemas de DNS, probá con un ping a 74.125.79.83, que es uno de los IPs de gmail.com.

---

### Post by MrOSX on 2009-05-04
Hola y gracias por contestar, he aqui que no tengo ningun archivo en /etc que se llame interfaces...  
te paso lo que me tira el ifconfig:

> eth2     Link encap:Ethernet   direcciónHW  00:17:31:17:1f:ec
            inet direccion:192168.2.4   Difuision:192.168.2.255   Máscara: 255.255.255.0
            Dirección inet6: fe80: :217:31ff:fe17:1fec/64    Alcanze:Vínculo
            ARRIBA DIFUSION CORRIENDO MULTICAST     MTU:1500  Métrica:1
            RX packets:10  errors:0  dropped:0  overruns:0   frame:0
            TX packets:43  errors:0  dropped:0  overruns:0   carrier:0
            colisiones:0   txqueuelen:1000
            RX bytes:1712 (1.7 KB)  TX bytes:6131 (6.1 KB)
            Interrupción:22  Dirección base: 0x2000

lo        Link encap: Bucle local
           inet dirección:127.0.0.1   Máscara:255.0.0.0
           dirección inet6: ::17128  Alcance:Anfitrión
           ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:10  errors:0  dropped:0  overruns:0   frame:0
          TX packets:10  errors:0  dropped:0  overruns:0   carrier:0
          colisiones:0   txqueuelen:1000
          RX bytes:500  (500.0 B)  TX bytes:500 (500 B) 

y la pregunta es, creo un archivo en /etc que se llame interfaces con los datos que me pasas?
Muchas gracias

---

### Post by gmunioz on 2009-05-04
Hola mro...:

Aparentemente no necesitas hacer nada en Linux, ya que tu tarjeta, eth2

ya esta configurada:

eth2 Link encap:Ethernet direcciónHW 00:17:31:17:1f:ec

inet direccion:192.168.2.4 

Difusion:192.168.2.255 

Máscara: 255.255.255.0

Respecto de osx, del cual ignoro todo, segun este link:

[http://chilenomac.wordpress.com/2009/03/04/compartir-internet-mediante-un-cable-rj-45-cruzado/](http://chilenomac.wordpress.com/2009/03/04/compartir-internet-mediante-un-cable-rj-45-cruzado/)

Configurarlo es muy sencillo.

Saludos.

---

### Post by MrOSX on 2009-05-04
Espera que sin haber hecho nada, solito se conecto!!!
jua! estoy muy feliz :) !!
Pero x otro lado, si deja de funcionar no voy a saber arreglarlo... :(
Muchas gracias de todos modos.

---

### Post by DrKenobi on 2009-05-05
fijate si te sirve este link

[http://ubuntuforums.org/showthread.php?t=91370]("http://ubuntuforums.org/showthread.php?t=91370")

suerte

---

