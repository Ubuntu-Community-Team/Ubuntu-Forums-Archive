---
title: "red e internet"
date: 2009-01-27
forum: Hardware
---

### Post by seserpic on 2009-01-27
Hola a todos, antes que nada quiero agradecer las respuestas a mi consulta anterior: pude instalar ubuntu.
Ahora tengo otro problemita: no puedo no puedo acceder a la red.
Tengo un modem router y otra Pc conectada, probé con todas las posibilidades que da la ayuda pero no pude conectarme. Si alguien tiene alguna sugerencia  lo voy a agradecer mucho.

---

### Post by lncoll on 2009-01-27
Bueno, para empezar hace falta algo de información.
De momento supongo que tienes una (uno en España ;) ) PC con tarjeta Ethernet, conectado a un router.
Lo primero es ver como está configurada la tarjeta ethernet, para ello en una consola ( Aplicaciones -> Accesorios -> Terminal ) teclea:

```
alguien@la_pc:~$ ifconfig
```

Y postea los resultados, con esto ya podemos hacernos una idea de lo que pasa.

---

### Post by seserpic on 2009-01-27
> **lncoll said:**
> Bueno, para empezar hace falta algo de información.
De momento supongo que tienes una (uno en España ;) ) PC con tarjeta Ethernet, conectado a un router.
Lo primero es ver como está configurada la tarjeta ethernet, para ello en una consola ( Aplicaciones -> Accesorios -> Terminal ) teclea:

```
alguien@la_pc:~$ ifconfig
```

Y postea los resultados, con esto ya podemos hacernos una idea de lo que pasa.

muchas gracias Incoll, aqui la configuracion de la tarjeta ethernet:
eth0      Link encap:Ethernet  direcciónHW 00:15:f2:45:8f:05  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:64  Métrica:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:7985 (7.9 KB)  TX bytes:2630 (2.6 KB)
          Interrupción:22 Dirección base: 0x2000 
lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

---

### Post by lncoll on 2009-01-27
> **seserpic said:**
> muchas gracias Incoll, aqui la configuracion de la tarjeta ethernet:
```

eth0      Link encap:Ethernet  direcciónHW 00:15:f2:45:8f:05  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:64  Métrica:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:7985 (7.9 KB)  TX bytes:2630 (2.6 KB)
          Interrupción:22 Dirección base: 0x2000 
lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

```

Bueno, ya sabemos que tu Ethernet está reconocida y activada. Como suele ocurrir se llama **eth0** y puedes ver que aparece su dirección hw. y está arriba (activada).
El problema es que todavía no tiene dirección IP asignada. La dirección IP se puede asignar manualmente u obtenerla de un servidor DHCP. Para comprobar si tienes servidor DHCP en tu red (suele ser un servicio del router) has de ejecutar desde consola:

```
alguien@la_pc:~$ sudo dhclient

[sudo] password for alguien: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/vmnet8/00:50:56:c0:00:08
Sending on   LPF/vmnet8/00:50:56:c0:00:08
Listening on LPF/vmnet1/00:50:56:c0:00:01
Sending on   LPF/vmnet1/00:50:56:c0:00:01
Listening on LPF/eth0/00:19:d1:81:7d:48
Sending on   LPF/eth0/00:19:d1:81:7d:48
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.0.2 from 192.168.0.1
DHCPREQUEST of 192.168.0.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.2 from 192.168.0.1
bound to 192.168.0.2 -- renewal in 1143 seconds.

```
  La primera línea es el comando, las siguientes es el resultado en mi PC, verás que el las ultimas líneas se puede leer un DHCPACK que indica una aceptación por parte de la PC al servidor y luego bound to 192.168.0.2 indicando la IP asignada.
  Si en tu caso el resultado es parecido (la IP puede ser completamente distinta) te diré como hacer esto automáticamente con el NetworkManager.
  Pero me temo que no, si es lo que me temo necesitarás o bien arrancar en otro sistema operativo que si te funcione o bien con otra PC que funcione y apuntar la configuración de red para luego introducirla en el NetworkManager.
  Pendona si me extiendo mucho, pero como creo que no tienes mucha experiencia procuro aclarártelo todo.

---

### Post by seserpic on 2009-01-27
Efectivamente no tengo mucha experiencia, agradezco tu dedicación; volviendo al problema, no pude comprobar el servicio DHCP al llegar al password no pude tipear mas nada.
Tengo instalado otro SO (windows) y alli la reconoce automáticamente. La pregunta: que datos tengo que apuntar de la configuración de red para introducirlos luego en el NetworkManager?
gracias por tu paciencia

---

### Post by guillermolisi on 2009-01-27
> **seserpic said:**
> Efectivamente no tengo mucha experiencia, agradezco tu dedicación; volviendo al problema, no pude comprobar el servicio DHCP al llegar al password no pude tipear mas nada.
Tengo instalado otro SO (windows) y alli la reconoce automáticamente. La pregunta: que datos tengo que apuntar de la configuración de red para introducirlos luego en el NetworkManager?
gracias por tu paciencia

Cuando ingresas la password el cursor no se mueve y parece que no te toma el tipeo pero vos dale para adelante y cuando termines de ingresarla presiona <enter>, luego pasa el resultado del comando.

---

### Post by lncoll on 2009-01-27
Vale, por mucho que he intentado explicarme, siempre me olvido de algo.
Cuando ejecutas "sudo dhclient" (sin comillas) te pide un password, es el mismo que utilizas para ingresar al sistema pero al teclear no sale nada en pantalla, ni lo que tecleas ni asteriscos ni el numero de la loteria del proximo sorteo :) 
  A pesar de eso estás ingresando el password, luego pulsas enter y ya está. Esto es para evitar que nadie vea el password por encima de tu hombro.
  Aparte de la explicación. Necesitarás saber varios datos que puedes extraer de otro sistema que si funcione, estos son:
[LIST]
[*]Dirección IP.
[*]Máscara de red.
[*]Gateway o puerta de enlace por defecto.
[*]Servidor(es) DNS
[/LIST]

  Si la información obtenida es del mismo PC en Güindo$ te servirá tal cual, si es de un PC distinto hay que cambiar la dirección IP por una que se suponga libre.
  Por ejemplo; en el otro PC:
[LIST]
[*]Dirección IP = 192.168.0.99
[*]Máscara = 255.255.255.0
[*]Gateway = 192.168.0.100
[*]DNS = 88.88.88.88 y 99.99.99.99
[/LIST]
  Has de buscar una IP libre, generalmente se suma 1 al ultimo numero de los 4, en este caso no es posible ya que seria 192.168.0.100 que es la dirección del Gateway entonces puedes escoger otro numero entre 1 y 254 incluidos que supongas libre, escogemos en el 192.168.0.50.
  Así quedará para nuestro PC en Linux
[LIST]
[*]Dirección IP = 192.168.0.50
[*]Máscara = 255.255.255.0
[*]Gateway = 192.168.0.100
[*]DNS = 88.88.88.88 y 99.99.99.99
[/LIST]

  Te voy preparando un par de capturas de pantalla de como configurar el network manager y envio el mensaje en unos minutos.

---

### Post by lncoll on 2009-01-27
Para acceder a la configuración de red con el NetworkManager has de hacer click en el icono del networkmanager, por si no sabes cual es mira el fichero pantallazo.png.
  En el desplegable que salga escoges "configuración manual" y te saldrá una ventana como la de pantallazo1.png.
  Si pulsas en el boton desbloquear, podrás ingresar tu contraseña para poder modificar los valores, una vez aceptada la contraseña selecciona "red cableada" y pulsa en propiedades pantallazo3.png
  Aquí es donde has de entrar los datos de configuración, para ello has de desactivar la casilla de modo itinerante. En la imagen pantallazo4.png verás los datos segun el ejemplo del mensaje anterior.

---

### Post by seserpic on 2009-01-28
> **lncoll said:**
> Para acceder a la configuración de red con el NetworkManager has de hacer click en el icono del networkmanager, por si no sabes cual es mira el fichero pantallazo.png.
  En el desplegable que salga escoges "configuración manual" y te saldrá una ventana como la de pantallazo1.png.
  Si pulsas en el boton desbloquear, podrás ingresar tu contraseña para poder modificar los valores, una vez aceptada la contraseña selecciona "red cableada" y pulsa en propiedades pantallazo3.png
  Aquí es donde has de entrar los datos de configuración, para ello has de desactivar la casilla de modo itinerante. En la imagen pantallazo4.png verás los datos segun el ejemplo del mensaje anterior.

de vuelta en el frente, gracias de nuevo. segui las instrucciones y lo primero que encontre es diferencias entre las ventanas y opciones, adjunto unas imágenes para que vean. Luego no se pudo conectar a internet.

---

### Post by lncoll on 2009-01-28
> **seserpic said:**
> de vuelta en el frente, gracias de nuevo. segui las instrucciones y lo primero que encontre es diferencias entre las ventanas y opciones, adjunto unas imágenes para que vean. Luego no se pudo conectar a internet.

Hola perdona el retraso pero la diferencia horaria se ha de notar de alguna manera.

Segun las capturas que me enseñas parece que tengas la red bien configurada, siempre que la IP no esté utilizada por otro PC.

Pruebas que puedes hacer: 
Comando "ifconfig eth0" (sin comillas claro), aquí veremos si realmente está configurada la terjeta y el trafico que ha tenido.

Comando "ping 10.0.0.2", este comando envia un paquete a la IP indicada y espera una respuesta, como si fuese un sonar, así veremos si el router está en esa dirección y si hay conexión con este.

Si el anterior da resultados, comabdo "ping google.com", para ver si 
hay conexion con servidores externos a tu red.

Todos estos comandos desde consola claro. Si los dos ultimos comandos no te dan resultados correctos puedes hacer dos cosas:
Primero, no es abitual que un router tenga IP 10.0.0.2, lo más normal es 10.0.0.1, cambialo y haz la prueba.
Segundo, cabria la posibilidad, si hay mas PCs en tu red, que la IP 10.0.0.14 esté ocupada por otro, cambiala y prueba otra vez :-\"

Si puedes envia el resultado de los comandos para que tengamos mas pistas.

P.D.  Tu NetworkManager es distinto al mio porque yo todavia uso Ubuntu 8.04 y veo que tu 8.10.

---

### Post by seserpic on 2009-01-28
> **lncoll said:**
> Hola perdona el retraso pero la diferencia horaria se ha de notar de alguna manera.

Segun las capturas que me enseñas parece que tengas la red bien configurada, siempre que la IP no esté utilizada por otro PC.

Pruebas que puedes hacer: 
Comando "ifconfig eth0" (sin comillas claro), aquí veremos si realmente está configurada la terjeta y el trafico que ha tenido.

Comando "ping 10.0.0.2", este comando envia un paquete a la IP indicada y espera una respuesta, como si fuese un sonar, así veremos si el router está en esa dirección y si hay conexión con este.

Si el anterior da resultados, comabdo "ping google.com", para ver si 
hay conexion con servidores externos a tu red.

Todos estos comandos desde consola claro. Si los dos ultimos comandos no te dan resultados correctos puedes hacer dos cosas:
Primero, no es abitual que un router tenga IP 10.0.0.2, lo más normal es 10.0.0.1, cambialo y haz la prueba.
Segundo, cabria la posibilidad, si hay mas PCs en tu red, que la IP 10.0.0.14 esté ocupada por otro, cambiala y prueba otra vez :-\"

Si puedes envia el resultado de los comandos para que tengamos mas pistas.

P.D.  Tu NetworkManager es distinto al mio porque yo todavia uso Ubuntu 8.04 y veo que tu 8.10.

Amigo no hay caso, probé con todas las variantes y siempre me dió el resultado que se ve en el pantallazo. Gracias de nuevo

---

### Post by guillermolisi on 2009-01-28
> **seserpic said:**
> Amigo no hay caso, probé con todas las variantes y siempre me dió el resultado que se ve en el pantallazo. Gracias de nuevo
Esa placa de red, eth0, sigue sin tener una direccion IP asignada.

Serias tan amable de pegar en un mensaje nuevo el contenido del archivo /etc/network/interfaces ?

Podrias confirmar si esa PC con Ubuntu esta conectada al modem y no al router ?

---

### Post by seserpic on 2009-01-29
> **guillermolisi said:**
> Esa placa de red, eth0, sigue sin tener una direccion IP asignada.

Serias tan amable de pegar en un mensaje nuevo el contenido del archivo /etc/network/interfaces ?

Podrias confirmar si esa PC con Ubuntu esta conectada al modem y no al router ?

buenas, continúo con el aprendizaje. empiezo por lo último: la PC está conectada por cable de  red a un modem router encore de 4 puertos cuyas especificaciones son las siguientes:

Especificaciones  	 
Standards:
• IEEE 802.3 y 802.3u
• USB 2.0
• ANSI T1.413 issue 2
• ITU G.dmt (G.992.1)
• ITU G.lite (G.992.2)
• G.994.1 (G.hs, Multimode)
• ADSL over POTS (Annex A) o ADSL over ISDN (Annex B / UR2)
• ATM Forum UNI 3.1/4.0 PVC
• RFC 2516 (PPP over Ethernet)
• RFC 2364 (PPP over ATM)
• RFC 1577 (Classical IP over ATM)
• RFC 1483 BPDU (Bridge Ethernet over ATM)

Protocolos soportados:
• Ruteo de IP estática
• DHCP (Dynamic Host Configuration Protocol) Servidor y Cliente
• IP routing-RIPv2 (compatible con RIPv1)
• NAPT (Network Address and Port Translation)
• NAT (Network Address Translation)
• PAT (Port Address Translation)
• ICMP (Internet Control Message Protocol)
• IGMP (Internet Group Management Protocol)
• PAP (Password Authentication Protocol)
• CHAP (Challenge Authentication Protocol)

Tasa de transferencia de datos:
• Bajada maxima hasta 8 Mbps
• Subida maxima hasta 1 Mbps

Consumo de energia:
• entrada 220 5 VAC
• salida 9VAC, 1000mA

Dimensiones y peso:
• 125mm(length) x 88mm (width) x 27mm (height)
• 140 gramos 

segundo: el contenido del archivo /etc/network/interfaces lo busco en la terminal?
sepan disculpar a uno que está verde

---

### Post by sajnox on 2009-01-29
Podes ir a buscar el archivo en la direccion indicada o ejecutar

```
cat /etc/network/interfaces
```

---

### Post by guillermolisi on 2009-01-29
> **seserpic said:**
> buenas, continúo con el aprendizaje. empiezo por lo último: la PC está conectada por cable de  red a un modem router encore de 4 puertos cuyas especificaciones son las siguientes:

Especificaciones  	 
Standards:
&#8226; IEEE 802.3 y 802.3u
&#8226; USB 2.0
&#8226; ANSI T1.413 issue 2
&#8226; ITU G.dmt (G.992.1)
&#8226; ITU G.lite (G.992.2)
&#8226; G.994.1 (G.hs, Multimode)
&#8226; ADSL over POTS (Annex A) o ADSL over ISDN (Annex B / UR2)
&#8226; ATM Forum UNI 3.1/4.0 PVC
&#8226; RFC 2516 (PPP over Ethernet)
&#8226; RFC 2364 (PPP over ATM)
&#8226; RFC 1577 (Classical IP over ATM)
&#8226; RFC 1483 BPDU (Bridge Ethernet over ATM)

Protocolos soportados:
&#8226; Ruteo de IP estática
&#8226; DHCP (Dynamic Host Configuration Protocol) Servidor y Cliente
&#8226; IP routing-RIPv2 (compatible con RIPv1)
&#8226; NAPT (Network Address and Port Translation)
&#8226; NAT (Network Address Translation)
&#8226; PAT (Port Address Translation)
&#8226; ICMP (Internet Control Message Protocol)
&#8226; IGMP (Internet Group Management Protocol)
&#8226; PAP (Password Authentication Protocol)
&#8226; CHAP (Challenge Authentication Protocol)

Tasa de transferencia de datos:
&#8226; Bajada maxima hasta 8 Mbps
&#8226; Subida maxima hasta 1 Mbps

Consumo de energia:
&#8226; entrada 220 5 VAC
&#8226; salida 9VAC, 1000mA

Dimensiones y peso:
&#8226; 125mm(length) x 88mm (width) x 27mm (height)
&#8226; 140 gramos 

segundo: el contenido del archivo /etc/network/interfaces lo busco en la terminal?
sepan disculpar a uno que está verde

Bueno, ahora deberiamos saber si ese modem/router tiene habilitado el servicio DHCP para que le asigne una IP dinamica a la placa de red.

En caso que no este habilitado, se pueden hacer por lo menos dos cosas, habilitarlo y configurarlo para que funcione adecuadamente (sera necesario manual del modem/router y acceder a su setup via un navegador) o asignarle una IP fija que se encuentre en el mismo bloque de IPs, en la misma red, que el modem/router.

Ese modem router esta conectado a Internet o a algun otro aparato que a su vez si se conecta directamente a Internet (tipo cablemodem o modem ADSL) ?

---

### Post by seserpic on 2009-01-29
> **guillermolisi said:**
> Bueno, ahora deberiamos saber si ese modem/router tiene habilitado el servicio DHCP para que le asigne una IP dinamica a la placa de red.

En caso que no este habilitado, se pueden hacer por lo menos dos cosas, habilitarlo y configurarlo para que funcione adecuadamente (sera necesario manual del modem/router y acceder a su setup via un navegador) o asignarle una IP fija que se encuentre en el mismo bloque de IPs, en la misma red, que el modem/router.

Ese modem router esta conectado a Internet o a algun otro aparato que a su vez si se conecta directamente a Internet (tipo cablemodem o modem ADSL) ?

este modm/router está conectado a internet y puedo navegardesde windows

---

### Post by seserpic on 2009-01-29
> **seserpic said:**
> este modm/router está conectado a internet y puedo navegardesde windows

va un pantallazo de el estado de conexion

---

### Post by guillermolisi on 2009-01-29
> **seserpic said:**
> este modm/router está conectado a internet y puedo navegardesde windows

Podrias pasar la informacion que tiene la placa de red cuando te conectas a internet con Windows (IP, marcara de red, gateway, dns) ? (o sea, el contenido que te muestra cuando presionas el boton Detalles)

Cuando enviaste las muestras de pantalla con la direccion IP de la maquina con Ubuntu en 10.0.0.14, la otra PC con Win estaba conectada a la red al mismo tiempo ?

Si abris un navegador web en Ubuntu y pones [http://209.85.195.99](http://209.85.195.99), que sucede ?

---

### Post by seserpic on 2009-01-29
> **guillermolisi said:**
> Podrias pasar la informacion que tiene la placa de red cuando te conectas a internet con Windows (IP, marcara de red, gateway, dns) ?

van los detalles de conexion de red

---

### Post by seserpic on 2009-01-29
> **guillermolisi said:**
> Podrias pasar la informacion que tiene la placa de red cuando te conectas a internet con Windows (IP, marcara de red, gateway, dns) ? (o sea, el contenido que te muestra cuando presionas el boton Detalles)

Cuando enviaste las muestras de pantalla con la direccion IP de la maquina con Ubuntu en 10.0.0.14, la otra PC con Win estaba conectada a la red al mismo tiempo ?

Si abris un navegador web en Ubuntu y pones [http://209.85.195.99](http://209.85.195.99), que sucede ?

1 si la otra PC estaba conectada
2 me da el mensaje: no se puede establecer la conexion

---

### Post by guillermolisi on 2009-01-29
> **seserpic said:**
> 1 si la otra PC estaba conectada
2 me da el mensaje: no se puede establecer la conexion
Entonces si le pones una direccion IP estatica, como te sugirieron, ponele 10.0.0.20 o 10.0.0.50 (o sea, una que estes seguro que no tenes ocupada) porque la 10.0.0.14 ya esta ocupada por la maquina Windows y eso genera conflicto en la red. Esto a partir de la informacion que acabas de mostrar.

---

### Post by seserpic on 2009-01-30
> **guillermolisi said:**
> Entonces si le pones una direccion IP estatica, como te sugirieron, ponele 10.0.0.20 o 10.0.0.50 (o sea, una que estes seguro que no tenes ocupada) porque la 10.0.0.14 ya esta ocupada por la maquina Windows y eso genera conflicto en la red. Esto a partir de la informacion que acabas de mostrar.

Buenas, sigo intentando. Puse las direcciones con otros números pero tampoco dió resultado.
Buscando fui a herramientas de red y me encontré con datos que no se de dónde salen ni cómo interpretar. (ver pantallazos).Un número de IP 127.0.0.0 que cuando lo coloco en la solapa ping me da resultados como que está funcionando. En fin no le encuentro la punta al ovillo.

---

### Post by seserpic on 2009-01-30
> **seserpic said:**
> Buenas, sigo intentando. Puse las direcciones con otros números pero tampoco dió resultado.
Buscando fui a herramientas de red y me encontré con datos que no se de dónde salen ni cómo interpretar. (ver pantallazos).Un número de IP 127.0.0.0 que cuando lo coloco en la solapa ping me da resultados como que está funcionando. En fin no le encuentro la punta al ovillo.

Corrección es 127.0.0.1, y entré a la configuración del router y lo encontré en route table (ver pantallazo)

---

### Post by Hei Ku on 2009-01-30
127.0.0.1 es el localhost. Es la misma maquina. Es una direccion que se usa para referirse a si misma.

---

### Post by seserpic on 2009-01-31
bueno, no hay caso, no me puedo conectar. Sospecho que debe ser algo simple pero no lo descubro. Tendría que ponerme a estudiar, pero no tengo tiempo. Muchas gracias a todos

---

