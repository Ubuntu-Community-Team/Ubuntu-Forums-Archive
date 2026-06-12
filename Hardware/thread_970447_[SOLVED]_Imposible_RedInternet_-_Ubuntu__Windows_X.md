---
title: "[SOLVED] Imposible Red/Internet - Ubuntu / Windows XP"
date: 2008-11-04
forum: Hardware
---

### Post by fedeavila on 2008-11-04
Buen día... Bueno... Paso a comentar un poco mi situación a ver si me pueden ayudar.

Hace algún tiempo contraté Speedy 1MB. Me trajeron el modem ethernet e hice la conexión.

Antes tenía XP y esperando a que salga Intrepid, me lo bajé e instalé hace poquito.

El problema es que yo comparto Internet con una vecina a través de un cable de red, cruzado.

Y no sé como configurarlo. Es decir, busqué, googleé, todo... 

Encontré demasiada info, demasiados tutoriales (que por cierto no me funcionó ninguno).

Ayer, el último que hice, fue un script... En la compu de mi vecina (que tiene XP), cuando intenta abrir una página se queda "resolviendo host....." y pasados unos segundos me salta el error de que no encontró el servidor.

Lo aún mas extraño es que a mi, en mi compu, con Intrepid; no me aparece ningún ícono de conexión, o sea en la barra superior aparece la lista de redes cableadas y otras, y aparecen las 2 (la ethernet de la red y la del modem que me brinda Internet) pero las dos desconectadas.

Yo para hacer la conexión usé "pppoeconf" y seguí el asistente de Ubuntu...

Así aparece cuando hago un clic sobre el icono en la barra superior:

[I][B]---------------------------------------------------------------------------------------------------
Red cableada (Elitegroup Computer Systems MCP61 Ethernet)
Ifupdown (eth1)
Red cableada (Realtek RTL-8029 AS))
El dispositivo no está gestionado.
---------------------------------------------------------------------------------------------------[/B][/I]

La verdad ni idea que puede ser. En realidad toda la vida tuve problemas con esto...

El tema es que antes era mi vecina la que me daba Internet, entonces yo no tenía problemas porque Ubuntu lo detectaba al toque.

Ahora no sé qué hacer, ella está esperando que lo resuelva y la verdad ni ganas de ponerme XP de vuelta.

Bueno, si alguien desea ayudarme, muchas gracias.

Aunque seguro me voy a tener que comprar un router o alguno de esos aparatos...

Bueno, un saludo y gracias!

_PD:_ Si necesitan alguna info avisenme que estoy al ped* en el laburo... Aviso que ya probé Firestarter también y nada...

---

### Post by faktorqm on 2008-11-04
Faltaria que pongas no mas que modem adsl es el que te dio speedy, marca y modelo de ser posible, asi vemos bien que paso. Una vez que conectes internet en tu maquina, podes ver que Gmunioz publico aca [http://ubuntuforums.org/showthread.php?t=942434](http://ubuntuforums.org/showthread.php?t=942434) unos scripts para eso que funcionan 100%, fijate. Tambien hizo otros por el foro, si ese no te es claro. Salu2!!

---

### Post by mhoyos on 2008-11-04
hola fedeavila:...

viendo tu post (y muy similar a una consulta que hicieron el la lista de correo) lo que vos necesitas el que tu intrepid, se "haga router" ...!!??

en tal caso, necesitas (te paso los ingredientes).. jejeje:

- desconfigurar toda placa de red (sin valor alguno)...
- configurar el pppoeconf (conexion a inet) y que funcione.
- configurar la 2da placa de red (donde NO esta el modem) con una IP interna.
- armar o hacer un script, que haga lo siguiente:

```
echo 1 > /proc/sys/net/ipv4/ip_forward
``` (este paso es para que puedas forwardear entre placas de red)
- desactivar el firewall 
- configurar la pc de la vecina, con datos "a mano"...

- opcional: configurar el servicio DHCP en el intrepid.

de esta manera, tu ubuntu pasara a ser un router... :)

tene en cuenta, que si apagas tu maquina, la vecina se queda sin internet.. y todo lo que conlleva a que la conexion sea compartida desde tu ubuntu..

espero te sirva..

salu2

---

### Post by fedeavila on 2008-11-04
> **mhoyos said:**
> hola fedeavila:...

viendo tu post (y muy similar a una consulta que hicieron el la lista de correo) lo que vos necesitas el que tu intrepid, se "haga router" ...!!??

en tal caso, necesitas (te paso los ingredientes).. jejeje:

- desconfigurar toda placa de red (sin valor alguno)...
- configurar el pppoeconf (conexion a inet) y que funcione.
- configurar la 2da placa de red (donde NO esta el modem) con una IP interna.
- armar o hacer un script, que haga lo siguiente:

```
echo 1 > /proc/sys/net/ipv4/ip_forward
``` (este paso es para que puedas forwardear entre placas de red)
- desactivar el firewall 
- configurar la pc de la vecina, con datos "a mano"...

- opcional: configurar el servicio DHCP en el intrepid.

de esta manera, tu ubuntu pasara a ser un router... :)

tene en cuenta, que si apagas tu maquina, la vecina se queda sin internet.. y todo lo que conlleva a que la conexion sea compartida desde tu ubuntu..

espero te sirva..

salu2

mhoyos, desde ya GRACIAS jaja

un par de preguntontas:

- como hago para "desconfigurar toda placa de red" ?
en la lista me aparece un "ifupdown" que dice al lado "nunca" y no puedo borrarlo... me dice "read only"

- esos datos a mano son algunos en especial? o tengo que inventarlos yo?

- respecto a lo de apagar mi maquina tambien lo medite y quizas necesite un aparato para que quede la conexion activa y yo poder apagar mi compu... que me tendria que comprar?

gracias señor #-o

---

### Post by mhoyos on 2008-11-04
> **fedeavila said:**
> mhoyos, desde ya GRACIAS jaja

un par de preguntontas:

- como hago para "desconfigurar toda placa de red" ?
en la lista me aparece un "ifupdown" que dice al lado "nunca" y no puedo borrarlo... me dice "read only"

- esos datos a mano son algunos en especial? o tengo que inventarlos yo?

- respecto a lo de apagar mi maquina tambien lo medite y quizas necesite un aparato para que quede la conexion activa y yo poder apagar mi compu... que me tendria que comprar?

gracias señor #-o

- edita (con permisos de root) el archivo /etc/network/interfaces y solo te tiene que quedar:

```
auto lo
iface lo inet loopback
```

borra todo lo demas, graba, y ejecuta:

```
/etc/init.d/networking restart
```

y asi queda todo "limpio"

- por el tema para apagar tu pc, te recomiendo que te compres un router (hay varios de varios tipos y marcas en el mercado) que tendras que elegir..

en base a mi experiencia, no te recomiendo los noganet (se calientan y se cuelgan) los d-link (despues de 1 año se ponen inestables)..

te recomendaria los edimax, los cnet y los linksys ...

espero te sirva...

---

### Post by fedeavila on 2008-11-04
> **faktorqm said:**
> Faltaria que pongas no mas que modem adsl es el que te dio speedy, marca y modelo de ser posible, asi vemos bien que paso. Una vez que conectes internet en tu maquina, podes ver que Gmunioz publico aca [http://ubuntuforums.org/showthread.php?t=942434](http://ubuntuforums.org/showthread.php?t=942434) unos scripts para eso que funcionan 100%, fijate. Tambien hizo otros por el foro, si ese no te es claro. Salu2!!

Hola **faktorqm**, te comento, el modem es [**_ZTE ZXDSL 831_**]("http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=214&root=132") Va, ahora que veo la foto no es "exactamente" el mismo, pero de la lista que muestra la pagina web, es el unico de esa marca...

Gracias

---

### Post by fedeavila on 2008-11-04
> **mhoyos said:**
> - edita (con permisos de root) el archivo /etc/network/interfaces y solo te tiene que quedar:

```
auto lo
iface lo inet loopback
```

borra todo lo demas, graba, y ejecuta:

```
/etc/init.d/networking restart
```

y asi queda todo "limpio"

- por el tema para apagar tu pc, te recomiendo que te compres un router (hay varios de varios tipos y marcas en el mercado) que tendras que elegir..

en base a mi experiencia, no te recomiendo los noganet (se calientan y se cuelgan) los d-link (despues de 1 año se ponen inestables)..

te recomendaria los edimax, los cnet y los linksys ...

espero te sirva...

Muchas gracias, y si, lo más seguro es que me lo compre, mas por un tema de no dejar mi maquina encendida todo el dia, todos los dias, espero que luego no haya que configurar nada con el router :|

Salu2 :rolleyes:

---

### Post by fedeavila on 2008-11-04
Bueno, decidí seguir los pasos de este chico "gmunioz" que por cierto está recontra claro... y... me funcionó al 50%

> Paso a paso:
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

Pero con la diferencia de que la otra PC tiene XP y no Ubuntu, aunque no sé si dará igual... Mi pregunta es: en XP tengo que configurar algo? Dejo las IP y DNS tal como están (automáticas) o les tengo que poner un valor específico?

Porque en XP el icono de red está como "limitado o nulo"...

Muchas gracias!

---

### Post by faktorqm on 2008-11-05
Aca tenes para configurar el modem de adsl en modo router [http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=214&root=132](http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=214&root=132), pero para las dos compus necesitarias un switch. de este modo no tenes que tener ninguna de las pc's prendida las 24hs. Sale 50 pesos uno de 8 bocas noganet (mas no necesitas). 

Si queres dejar esa configuracion, tenes que fijarte que ip tenes vos, y ponerla como puerta de enlace en el xp, y ponerle otra ip a esa compu, dentro de la misma subred. cualquier cosa postea ifconfig. Salu2!

---

### Post by fedeavila on 2008-11-05
> **faktorqm said:**
> Aca tenes para configurar el modem de adsl en modo router [http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=214&root=132](http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=214&root=132), pero para las dos compus necesitarias un switch. de este modo no tenes que tener ninguna de las pc's prendida las 24hs. Sale 50 pesos uno de 8 bocas noganet (mas no necesitas). 

Si queres dejar esa configuracion, tenes que fijarte que ip tenes vos, y ponerla como puerta de enlace en el xp, y ponerle otra ip a esa compu, dentro de la misma subred. cualquier cosa postea ifconfig. Salu2!

Ja! Es exactamente el mismo link que yo te pasé a vos...

Te comento que ya encargué el Router, es uno marca D-LINK, me salió $90 y el chabón del local me dijo que SÍ FUNCIONA PARA LINUX... Parece que es PRO-Linux también. No dudaría en que esté registrado en este foro...

Bueno, cuando llegue a casa, tipo 20hs lo conecto y veo si funcó o si tiré la plata a la basura.

Si no escribo nada, es porque no me funcionó. ](*,) ](*,) ](*,)

---

### Post by fedeavila on 2008-11-05
Listoo!!

Me trajeron el router, lo conecté con un asistente, a través del Firefox

Yendo como a una página web pero en vez de escribir "www..." escribí 19.168.1.1 (creo, no me acuerdo)

Taba todo en inglés pero deducís todo al toque :p quedó pipí cucú ;)

Lo podría haber hecho mi abuela tranquilamente ahahaha :p

Pero lo más **[SIZE="4"]extraordinario[/SIZE]** aún es que no sólo andubo Internet sino que también andubo la **[SIZE="5"]Red[/SIZE]** :-D:-D:-D

Pego una captura de pantalla y una foto del susodicho y del modem que quedó en la mesita de luz(?) por cuestiones de organizar un poco mi habitación... 

Son demasiadas cosas positivas en un lapso de tiempo tan corto jaja y encima con este calor que no ayuda...

Y pensar que ahora yo voy a poder seguir con **Ubuntu** que ya me lo re amoldé a mi personalidad(?) y la otra guachita con su **Windows XP** jeje

Saludos y muchiiiisimas gracias por la ayuda ;)

---

