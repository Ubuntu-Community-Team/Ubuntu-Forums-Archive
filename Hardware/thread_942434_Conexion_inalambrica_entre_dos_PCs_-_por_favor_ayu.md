---
title: "Conexion inalambrica entre dos PCs - por favor ayuda"
date: 2008-10-09
forum: Hardware
---

### Post by devoriana on 2008-10-09
Hola! soy totalmente novata en el uso de Ubuntu y agradecería mucho vuestra ayuda: tengo instalado Ubuntu en una notebook HP 530 que tiene integrada una placa wi-fi Intel 802.11a/b/g con la que me conecto a internet en los lugares públicos, pero me gustaria crear una red inalámbrica con mi PC de escritorio que tiene WinXP y para eso quiero saber si puedo usar un chichecito que me regalaron llamado Wireless USB Adapter modelo TWL54U marca NogaNet.
La idea sería poder hacer la red inalámbrica entre la PC y la notebook, para poder compartir los archivos entre ellas, y, si es posible, la conexión internet que tiene la PC con WinXP de fibertel.
Tengo la versión Ubuntu 8.04 instalada en la notebook, y aún no he podido bajar todas las actualizaciones pues usando la conexión pública por wi-fi se está haciendo muy lento el proceso.  Alguien podría ayudarme? 
Perdón por mis términos poco técnicos y desde ya muchas gracias.:)

---

### Post by Hernán-Amaya on 2008-10-09
depende si las dos placas wifi te premiten establecer una red punto a punto, en casa tengo una red wifi pero con un AP

---

### Post by devoriana on 2008-10-09
> **Hernán-Amaya said:**
> depende si las dos placas wifi te premiten establecer una red punto a punto, en casa tengo una red wifi pero con un AP

Gracias Hernán! perdón por preguntar burradas, pero, ¿cómo sé si las dos placas wi-fi me permiten establecer una red punto a punto, y cuáles son los pasos a seguir para hacerlo?

---

### Post by gmunioz on 2008-10-09
Hola dev...:

Una de las tres formas de trabajo de las tarjetas wireless es la red ad-hoc.
Esta red se construye configurando a las pcs de la red para que trabajen par a par, recibiendo los paquetes de todas y envíando sus propios paquetes a todas los pcs de la red.
Para esto se necesita definir una red con un nombre (ESSID), y preferiblemente encriptar a 128 bits (con WEP).

La configuración se hace directamente en el archivo /etc/network/interfaces. 
Lo editas con:
sudo gedit /etc/network/interfaces 

Un ejemplo de su contenido sería para ip por dhcp:

auto eth1
# ejemplo con dhcp
 iface eth1 inet dhcp
 #address 192.168.0.2
 #netmask 255.255.255.0
 #network 192.168.0.0
 #gateway 192.168.0.1
 wireless_essid Nombre_de_red
 wireless_mode ad-hoc
 wireless_key s:tu_clave
 wireless_rate auto
 wireless_nick devo

Otro ejemplo de su contenido sería para ip estática:

auto eth1
# ejemplo con IP estática
 iface eth1 inet dhcp
 address 192.168.0.2
 netmask 255.255.255.0
 network 192.168.0.0
 gateway 192.168.0.1
 wireless_essid Nombre_de_red
 wireless_mode ad-hoc
 wireless_key s:tu_clave
 wireless_rate auto
 wireless_nick devo

O temporariamente, como prueba, ejecutando iwconfig e ifconfig con los parámetros:

sudo iwconfig eth1 mode ad-hoc essid Nombre_de_red channel 1
sudo ifconfig eth1 192.168.0.2 netmask 255.255.255.0 network 192.168.0.0 up

En Ubuntu se repite en ambas máquinas, cambiando obviamente las IP y poniendo como gateway la ip de la otra. Respecto de Windows lo lamento, lee la firma.

Saludos.Gabriel.

**Solo doy soporte a Ubuntu - 22** - ***Mad Intrepid User***.

---

### Post by devoriana on 2008-10-09
gracias Gabriel. anduve leyendo por ahí y dicen que la conexión podría hacerse con un programa llamado ndiswrapper. ¿es posible? porque todas esas indicaciones que me proponés me resultan imposibles (he reconocido ser una absoluta novata en linux)
:( que pena que no puedas ayudarme a instalar toda la red con la otra PC en la que tengo winXP...

---

### Post by gmunioz on 2008-10-09
Hola dev...:
No, ndiswrapper es una aplicación destinada a instalar drivers originales Windows de tarjetas de red, en Linux, y lograr que las tarjetas funcionen cuando no existen drivers Linux. Este no es tu caso, pues informas que te conectas a redes sin problemas.

La configuración en modo grafico, puedes intentarla pulsando:
Sistema - Administración - Red - Desbloquear - Conexión inalambrica - Propiedades

Saludos.Gabriel.

**Solo doy soporte a Ubuntu **- *22 - Mad Intrepid User.*

---

### Post by devoriana on 2008-10-10
Hola Gabriel, aún sigo sin entender si es que puedo conectar mi PC con mi notebook sólo teniendo en la PC una wi-fi adapter y en la notebook la tarjeta integrada. ¿Necesito comprar un router para hacer la red entre ambas? Si no lo necesito, ¿puedo compartir la conexion a internet (Fibertel) que está en la PC con mi notebook?. Desde ya muchas gracias.
Dev

---

### Post by faktorqm on 2008-10-10
Pones las dos wi-fi en ad-hoc, y es como si tuvieras dos placas de red "comunes" con un cable cruzado, y ahi te comunicas de pc a pc inalambricamente. 
A parte, una de las pc tiene otra placa, que es la que se conecta a fibertel, que esa la dejas como esta. Luego de hacer lo que te dijo Gabriel, hacés esto para compartir internet:

> **gmunioz said:**
> 
Primero habilita definitivamente el forwarding en el kernel, ejecutando en consola:
sudo gedit /etc/sysctl.conf

Buscas las líneas que dicen:
# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

Y la dejas asi:
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

Guardas el archivo.

(Esta modificación es definitiva, no degrada el sistema y si no se usa no afecta el uso ni el funcionamiento de la pc.)

Pulsas en nuevo, en el archivo que se abre pegas el siguiente contenido:


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
iptables -A INPUT -i eth1 -j ACCEPT
iptables -t nat -A POSTROUTING -s eth1 -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth0 -j ACCEPT


Lo guardas en /etc/init.d/ con el nombre firewall, aceptando sobrescribir el archivo creado anteriormente.
Cierras gedit

Ejecutas
sudo chmod +x /etc/init.d/firewall
sudo ln -s /etc/init.d/firewall /etc/rc2.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc3.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc4.d/S99firewall
sudo ln -s /etc/init.d/firewall /etc/rc5.d/S99firewall



Esto de acuerdo a que la salida a internet es por eth0 y eth1 es tu placa wi-fi (Igual esto lo puso Gabriel en otro post, me tome el atrevimiento de quotearlo no mas) y el ubuntu hace el ruteo de internet para las dos computadoras. Espero que te haya servido. Salu2!!!

---

### Post by gmunioz on 2008-10-10
Hola fak....:
La usuaria tiene dos impedimentos importantes:
1) No se anima a la consola, esto es solucionable, si lee y se anima a usar la consola o si intenta configurar la conexión de su tarjeta en modo gráfico.
2) Insoluble para mi, **tiene Windows en la pc desktop**. Es insoluble para mi, pues como estimo que si nos hubieramos abstenido de piratear los productos Microsoft y de dar soporte y soluciones gratuitas a los incontables fallos de sus productos, estos no tendrian la difusión que hoy tienen, decidí hace tiempo que Microsoft debe ocuparse de dar soporte, si puede, a sus usuarios y hacerse cargo de sus errores.
Saludos.de Gabriel.
[B]Solo doy soporte para Ubuntu: Un sistema operativo superior, moderno, optimizado, seguro, racional,y evolutivo.
[/B]

---

### Post by Mauro22 on 2008-10-10
Para la red interna, lo mas practico seria un router wifi... 

*Te ahorras el encender la PC con wXP para compartir internet y ademas, al usarla como puente para compartir una conexion, la vas a hacer mas lenta y que consuma mas recursos, ya que el ruteo de los paquetes lo hace por software (y mas, todos los problemas que tiene win en cuanto a la administracion de los recursos, el asunto se vuelve engorroso), Lo peor? que pierdas internet en la notebook porque el XP se colgo o de la noche a la mañana no cargue mas :)

* Lo mejor es tener un aparato diseñado 100% para eso y te ahorras un monton de dolores de cabeza *




Saludos!

---

### Post by devoriana on 2008-10-10
> **faktorqm said:**
> Pones las dos wi-fi en ad-hoc, y es como si tuvieras dos placas de red "comunes" con un cable cruzado, y ahi te comunicas de pc a pc inalambricamente. 
A parte, una de las pc tiene otra placa, que es la que se conecta a fibertel, que esa la dejas como esta. Luego de hacer lo que te dijo Gabriel, hacés esto para compartir internet:



Esto de acuerdo a que la salida a internet es por eth0 y eth1 es tu placa wi-fi (Igual esto lo puso Gabriel en otro post, me tome el atrevimiento de quotearlo no mas) y el ubuntu hace el ruteo de internet para las dos computadoras. Espero que te haya servido. Salu2!!!

Gracias en primer lugar, pero creo que nadie de los que generosamente se han molestado en contestarme han entendido que soy novatísima en esto de Ubuntu, y no sé hacer todo eso de los comandos para poder hacer la red punto a punto.  A duras penas aprendí lo que es la red "ad-hoc". ¿se entiende? Soy abogada, y si yo le digo a un cliente que le deben de un contrato que puede ejercer la exceptio non adimpleti contractus, no va a entender un jora.. Ahora si le digo que como no le pagaron por lo que está haciendo, puede dejar de hacerlo, estoy segura que me comprenderá...
Por favor chicos, sé que para Uds. tal vez esto se haga con los ojos cerrados, pero estoy sin conexión a internet en la notebook y no puedo acceder todo el tiempo a la pc de escritorio a la que quiero conectarme inalámbricamente en red. A ver si alguno se apiada un poquito y me explica cómo puedo hacer, en interfaz gráfica para conectar mi PC con win XP con adaptador usb w-fi a la notebook con su placa w-fi, y luego compartir la conexión de la pc de escritorio con la notebook desde la red.
Muchichísimas gracias!!

---

### Post by santiagofrias on 2008-10-11
Devo: me parece que la solución más rápida y fácil para vos, sería lo que te dice Mauro22:

> **Mauro22 said:**
> Para la red interna, lo mas practico seria un router wifi... 

*Te ahorras el encender la PC con wXP para compartir internet y ademas, al usarla como puente para compartir una conexion, la vas a hacer mas lenta y que consuma mas recursos, ya que el ruteo de los paquetes lo hace por software (y mas, todos los problemas que tiene win en cuanto a la administracion de los recursos, el asunto se vuelve engorroso), Lo peor? que pierdas internet en la notebook porque el XP se colgo o de la noche a la mañana no cargue mas :)

* Lo mejor es tener un aparato diseñado 100% para eso y te ahorras un monton de dolores de cabeza *




Saludos!


Te quedaría una conexión similar a esta:

[IMG]http://fdntga.bay.livefilestore.com/y1pgSUUm3R7P-8ntAlp0rmQgAl9--JuJh_kI3ZirED5Tff6ZRpge0rPVBU5cLJ5oi_FUJ8o7rXFPFc/Red.png[/IMG]

El caso es que tenés que preguntar a Fibertel si te pueden proporcionar este tipo de "modem-router" (el mío es de Arnet).
Como dice Mauro22 con este tipo de conexión no necesitás tener prendida la PC ya que el modem-router se encarga de distribuir la conexión (ya sea que tengas WinXP o Ubuntu)(al modem no le interesa el Sistema Operativo que estes utilizando).
Actualmente en el caso tuyo, el modem que te conecta a Internet debe ser USB por lo que necesitas tener prendida la PC con WinXP; lo cual cualquier falla influye en tu conexión sumado a que: llega tu señal de Internet por el modem, luego debe pasar a la placa Wi-Fi y recién transmitir a tu Laptop, todo ello mediante software Windows, lo que es bastante engorroso.
Consejo, tratá de conseguir un Modem-Router y creo que tu problema se solucionaría.
Saludos

---

### Post by gmunioz on 2008-10-11
Hola dev....:
En principio gracias por lo de chicos, mas ya voy por mi vuelta número 58 alrededor del sol.
Aqui dos sitios con indicaciones para sistemas operativos Microsoft:
[http://piezas.bandaancha.st/docs/compartirconexionxp.html](http://piezas.bandaancha.st/docs/compartirconexionxp.html)
[http://www.microsoft.com/spain/technet/recursos/articulos/wifisoho.mspx](http://www.microsoft.com/spain/technet/recursos/articulos/wifisoho.mspx)
Una vez que configures tu pc de escritorio debes pulsar en la notebook:
Sistema - Administración - Redes - Elegir tu tarjeta inalambrica y configurarla segun los parámetros establecidos en la desktop
[B]Saludos.
Gabriel[/B].
**Solo doy soporte para Ubuntu: Un sistema operativo superior, moderno, optimizado, seguro, racional,y evolutivo.**

---

### Post by majatu on 2008-10-12
yo te diria que ahora que tenes dos maquinas con capacidad para conectarte pro Wireless, te compres un router WiFi y vas a tener internet en cualquiera de las pc, sin necesidad del punto a punto (mas que nada porque si es punto a punto necesitas si o si que las dos pcs esten encendidas para que la segunda tenga internmet)

un saludo!

---

### Post by devoriana on 2008-10-20
> **gmunioz said:**
> Hola dev....:
En principio gracias por lo de chicos, mas ya voy por mi vuelta número 58 alrededor del sol.
Aqui dos sitios con indicaciones para sistemas operativos Microsoft:
[http://piezas.bandaancha.st/docs/compartirconexionxp.html](http://piezas.bandaancha.st/docs/compartirconexionxp.html)
[http://www.microsoft.com/spain/technet/recursos/articulos/wifisoho.mspx](http://www.microsoft.com/spain/technet/recursos/articulos/wifisoho.mspx)
Una vez que configures tu pc de escritorio debes pulsar en la notebook:
Sistema - Administración - Redes - Elegir tu tarjeta inalambrica y configurarla segun los parámetros establecidos en la desktop
[B]Saludos.
Gabriel[/B].
**Solo doy soporte para Ubuntu: Un sistema operativo superior, moderno, optimizado, seguro, racional,y evolutivo.**

:)Gracias Gabriel, por tu ayuda, imagino lo que habrá significado para vos poner esos links del sistema "innombrable".
Lo cierto es que, como por ahí se me ocurrió explicar, la PC que tiene el S.O. que no se nombra no es mía, es de mi mamá y allí es donde está la conexión fiber que quiero compartir con la notebook. No quiero ni imaginar lo que sería para ella meterle mano a su computadora, en donde aún cree hay enanos trabajando todo el día....
Bueno, traté de seguir las directivas que daban esos links, y lo posteado aquí, y sólo logré que en el listado de conexiones inalámbricas de la notebook con Ubuntu aparezca la red con la PC, pero está ahí, sin ningún grado de conectividad.
Tal vez haya hecho algo mal, quien sabe, en mi oficina puse solita la red y comparto internet sin problemas, en mi casa estoy volviéndome un poco loca.
Saludos
Devo

---

### Post by devoriana on 2008-10-20
> **majatu said:**
> yo te diria que ahora que tenes dos maquinas con capacidad para conectarte pro Wireless, te compres un router WiFi y vas a tener internet en cualquiera de las pc, sin necesidad del punto a punto (mas que nada porque si es punto a punto necesitas si o si que las dos pcs esten encendidas para que la segunda tenga internmet)

un saludo!

Gracias Majatu por tu consejo, pero lamentablemente para comprarme la notebook estuve 4 años y junté peso sobre peso, y ahora no puedo darme el lujo de comprarme un router Wi-Fi, cuyo precio (estuve averiguando) no baja de los 200, y que por añadidura algunos vendedores me dijeron no me servirá si tengo conexión por fibertel, pues habrá conflictos con la MacAdress, o como se llame.
Así que seguiré peleando con lo que tengo, hasta que logre dar con la solución, y si es así la postearé aquí para que otros usuarios que tengan la misma necesidad/problema puedan usarla.
saludos
Devo

---

### Post by devoriana on 2008-10-20
> **santiagofrias said:**
> Devo: me parece que la solución más rápida y fácil para vos, sería lo que te dice Mauro22:
.....

Consejo, tratá de conseguir un Modem-Router y creo que tu problema se solucionaría.
Saludos

Gracias Santiago, pero fijáte lo que le contesto a Majatu.  Ya no llego a comprar nada más, primero tengo que terminar de pagar las cuotas de la notebook.  Además, fiber te da otro modem,y para compartir con otras pcs te cobra cargos adicionales.  No puedo darme el lujo de seguir pagando, pagando y pagando....
Saludos,
Devo

---

### Post by gmunioz on 2008-10-20
Hola dev...:
Evidentemente el conflicto está en la pc de tu mamá.
También puede que este en fibertel, no es legal ni ético pero puede que este limitado a monousuario. Esto surge de lo que dices:
"...en mi oficina puse solita la red y comparto internet sin problemas..."
Para saber donde está la falla conecta directamente tu portatil al cable de fibertel, si te conectas el problema esta en la configuración de la pc Windows.
Respecto del router, compras barato, en general un linksys esta cerca de los $300 y es el más recomendable, tiene un soporte excelente las 24 horas del día, con otra marca no me arriesgaría, sin embargo fibertel puede no funcionar.
Saludos y suerte.
Gabriel.
**Solo doy soporte para Ubuntu.**

---

### Post by gmunioz on 2008-10-20
Hola dev...:
Estuve investigando y:
En general los modems de Fibertel  disponen de solo una placa de red y por lo tanto solo disponen de una MAC, esta MAC es la que habilita Fibertel para que todo funcione.
Si se pone un HUB $40 o un SWITCH $70 no se podra compartir la conexion y solo funcionara la primera que solicite una ip.
La solucion a esto es un Router Linksys $300, que hace que el prestador siga viendo solo la MAC de modem y siga funcionando la conexion, el resto del trabajo lo hace router que se debe poner despues del modem. 
Esto me cuesta horrores, :) 
Si tienes Windows XP en la máquina a la que le llega el Fibertel, (la de tu mamá) tienes que ir a:
Conexiones de red y en el dibujo del adaptador de red, pulsas Propiedades, luego en Avanzadas y debes tildar en conexion compartida a internet las dos opciones, y el sistema hace el resto solo. Luego pulsas ejecutar cmd y en la consola de Windows, si Windows tiene consola, escribes ipconfig /all así sabrás los parámetros de ambas interfaces de la pc, usas los de la inalambrica como puerta de enlace para tu Ubuntu.
Saludos.

---

### Post by Ligero on 2008-10-20
Utilice el cable, allí sea un montón de anchura de banda. Su ISP proporcionará un módem pero un ranurador será necesario, comprueba el Internet. Usted puede ir estación al statio o a la radio.

Suerte

---

### Post by chalito on 2008-10-22
Devo,

No creo que tengas problemas con un router wifi (especialmente con un linksys), pero si se te va de presupuesto, podes empezar haciendo lo que decian mas arriba, habilitar la conexion compartida de internet en windows.

Para ello, podés seguir los pasos que se detallan -->[aquí]("http://support.microsoft.com/kb/306126/es")<-- en la parte que dice "En el equipo host".

Una vez que hayas hecho esto, tenés que habilitar tu adaptador wifi en windows para que forme una red Ad-Hoc. Para eso, podés seguir -->[estas instrucciones]("http://www.configurarequipos.com/doc331.html")<--.

En esas instrucciones fijate que en un momento cerca del final, definen una dirección IP "192.168.1.50". Esa dirección IP es la que vas a tener que configurar en tu notebook para que ésta sepa que tiene que salir a internet a través de la pc de tu madre.
También fijate, y esto es MUY importante, que en el documento menciona en un momento el cifrado de datos como "deshabilitado". Es enormemente recomendable que lo habilites, y de las opciones que te ofrece podes usar WPA o WEP (WPA Personal es mejor) y definirle la clave que mas te guste. NI SE TE OCURRA usar algun sitio tipo pagomiscuentas.com o tu home banking via wifi si no usas una conexion cifrada.

Habiendo aclarado eso, solo resta configurar ubuntu para que use esa conexión. Si tu placa wifi fue reconocida correctamente por Ubuntu, con sólo hacer clic en el icono de redes en tu escritorio debería figurar una lista de redes inalámbricas, entre las cuales debe estar la que creaste en los pasos anteriores. Si seguiste las instrucciones al pie de la letra, tu red se llama "Red Wifi" (te recomendaría que le pongas algo mas personal, pero lo importante es que puedas identificarla en la lista). Si tu red figura en la lista, vamos bien.
Clickeá abajo de todo donde dice "Configuración Manual".
Te va a aparecer una ventana desde donde podes configurar tu red. Para eso primero tenés que desbloquearla (click en el botón de abajo, al lado de "cerrar", te va a pedir tu contraseña). 
Una vez desbloqueada la configuración, hacé clic en la configuración inalámbrica, y despues clic en el botón de "propiedades". En la ventana que aparece, hacé lo siguiente:
***** Destildá la opción de roaming (no se como figura en castellano, alguien puede ayudar con una traducción?)
***** Ingresá los siguientes datos:
**Network**: Red Wifi (o el nombre que hayas usado para la red, podes incluso desplegar la lista y seleccionarla directamente).
**Password type**: el que hayas elegido cuando creaste la red en windows. recomendable usar WPA Personal (es necesario usar el mismo tipo en las dos maquinas. Puede que el nombre varíe ligeramente entre windows y ubuntu, en ubuntu se llama WPA Personal, en windows no estoy seguro pero debería ser evidente cual es.. de ultima proba con todos :) )
**Network Password**: el mismo que pusiste en la red en windows.
**Configuration**: Static IP Address.
**IP Address**: 192.168.1.51 (asumiendo que en windows pusiste 192.168.1.50)
**Subnet Mask**: 255.255.255.0
**Gateway Address**: 192.168.1.50 (asumiendo, de nuevo, que ésta es la direccion que pusiste como IP Address en windows).

Ya casi estamos! Hacé clic en OK.
Lo único que resta, es indicar los servidores DNS que vas a usar. Deberías encontrarte de nuevo en la ventana de Configuración de Red. Fijate que tenés varias solapas "Conexiones, General, DNS ...".
Seleccioná la solapa "DNS", y hacé clic en el botón con el signo "+" (agregar). Ahí tenes que poner los DNS de fibertel (osea, este paso lo tenes que hacer una vez para cada DNS):
24.232.0.17
24.232.0.18

(Yo hace poco me pasé de Fiber a Telecentro, asi que si alguno es cliente de fiber y puede corroborar esas IP, se lo agradecería).

Listo! una vez que te figuren esos dos DNS en la lista, podes hacer clic en close y deberías tener la conexión funcionando.

Creo que no me olvidé de nada...
Espero que te salga todo derecho, y sino, avisá con que tenés problemas y vemos como lo solucionamos.

salu2

---

### Post by devoriana on 2008-10-22
gracias chalito! gracias gabriel! miles de gracias a los dos por la ayuda que me están dando! en cuanto llegue a casa y logre "apoderarme" un rato de la PC de mi madre intento lo que me proponen y después cuento aquí cómo me fue.
salu2 para los 2

---

### Post by devoriana on 2008-10-23
[QUOTE=chalito;6012510]Devo,

No creo que tengas problemas con un router wifi (especialmente con un linksys), pero si se te va de presupuesto, podes empezar haciendo lo que decian mas arriba, habilitar la conexion compartida de internet en windows.

Para ello, podés seguir los pasos que se detallan -->[aquí]("http://support.microsoft.com/kb/306126/es")<-- en la parte que dice "En el equipo host".

una vez más gracias chalito. te cuento que seguí todos los pasos pero igual no pude conectar la PC con la notebook.  En la notebook con ubuntu aparece la conexión de red (que configuré manualmente siguiendo tus pacientes explicaciones y agregándole las DNS que saqué de la conexión area local de fiber - tenía 4 pero ubuntu sólo me dejó agregar dos- ).
el tema es que si hago ping desde la notebook a la pc en terminal sale host unreacheable, y ping de la pc a la notebook sale que no pudo enviar ningún paquete.
te aclaro que puse una contraseña WEP hexadecimal porque WAP no estaba disponible al hacer la conexión desde Win Xp.
lo unico que me ocurre es que no puedan conectarse por el firewall de win xp que está activado. ¿qué opinás? ¿te parece que sea eso? ¿lo desactivo? gracias de nuevo
salu2
Devo

---

### Post by chalito on 2008-10-23
Es posible, proba con el firewall desactivado un momento al menos para ver, y despues activalo de nuevo. Si resulta ser eso, podemos ver como lo confguramos para que deje pasar esa conexion. Si aun asi no funciona, configurá todo y dejalo como "deberia andar" y por favor posteate por aca el resultado de los comandos:
route -n
ifconfig -a

y en la maquina windows, desde una ventana de comandos:
ipconfig /all
(ojo: en windows es ipconfig, en linux es ifconfig)

Y una pregunta más, cuando conectas las dos maquinas por wifi, la conexión wifi funciona? osea, olvidandonos de que no podes hacer ping de una a otra, los iconitos verdes en ambas maquinas de la fuerza de la señal, se ven? figuran conectadas con buena señal?

---

### Post by devoriana on 2008-10-23
> **chalito said:**
> Es posible, proba con el firewall desactivado un momento al menos para ver, y despues activalo de nuevo. Si resulta ser eso, podemos ver como lo confguramos para que deje pasar esa conexion. Si aun asi no funciona, configurá todo y dejalo como "deberia andar" y por favor posteate por aca el resultado de los comandos:
route -n
ifconfig -a

y en la maquina windows, desde una ventana de comandos:
ipconfig /all
(ojo: en windows es ipconfig, en linux es ifconfig)

Y una pregunta más, cuando conectas las dos maquinas por wifi, la conexión wifi funciona? osea, olvidandonos de que no podes hacer ping de una a otra, los iconitos verdes en ambas maquinas de la fuerza de la señal, se ven? figuran conectadas con buena señal?

Hola Chalito! Bueno, aquí va:
En la PC:
Configuración IP de Windows
        Nombre del host . . . . . . . . . : USER13
        Sufijo DNS principal  . . . . . . :
        Tipo de nodo . . . . . . . . . .  : desconocido
        Enrutamiento IP habilitado. . . . : Sí
        Proxy WINS habilitado. . . . .    : No
Adaptador Ethernet Conexión de área local          :
        Sufijo de conexión específica DNS :
        Descripción. . . . . . . . . . .  : NVIDIA nForce Networking Controller
        Dirección física. . . . . . . . . : 00-18-F3-53-CC-94
        DHCP habilitado. . . . . . . . .  : No
        Autoconfiguración habilitada. . . : Sí
        Dirección IP. . . . . . . . . . . : 190.16.190.190
        Máscara de subred . . . . . . . . : 255.255.255.0
        Puerta de enlace predeterminada   : 190.16.190.1
        Servidor DHCP . . . . . . . . . . : 172.20.2.12
        Servidores DNS . . . . . . . . . .: 200.49.130.23
                                            200.49.130.22
                                            200.49.130.32
                                            172.20.2.12
        Concesión obtenida . . . . . . .  : Jueves, 23 de Octubre de 2008 11:02:
14 p.m.
        Concesión expira . . . . . . . . .: Viernes, 24 de Octubre de 2008 05:02
:14 a.m.

Adaptador Ethernet Conexiones de red inalámbricas          :
        Estado de los medios. . . .: medios desconectados
        Descripción. . . . . . . . . . .  : 802.11b/g USB Wireless LAN Adapter
        Dirección física. . . . . . . . . : 00-E0-2A-4D-04-BA

En la Notebook:
Tabla de rutas IP del núcleo
Destino		Pasarela	Genmask	Indic	Metric	Ref	Uso Interfaz
192.168.1.0		0.0.0.0		255.255.255.0	  U	0	0	0 wlan0
169.254.0.0		0.0.0.0		255.255.255.0	  U	1000	0	0 wlan0
0.0.0.0		   192.168.1.50	0.0.0.0              UG     100    	0	0 wlan0

eth0	Link encap: Ethernet  direcciónHw 00:1e:ec:71:b2:04
	ARRIBA DIFUSION MULTICAST MTU: 1500 Métrica:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	colisiones:0 txqueuelen:1000
	RX bytes: 0 (0.0 B)  TX Bytes:0 (0.0 B)

lo	Link encap: Bucle local
	inet dirección: 127.0.0.1	Máscara:255.0.0.0
	dirección inet6: ::1/128 Alcance: Anfitrión
	ARRIBA LOOPBACK CORRIENDO MTU: 16346 Métrica:1
	RX packets:2094 errors:0 dropped:0 overruns:0 frame:0
	TX packets:2094 errros:0 dropped:0 overruns:0 carrier:0
	colisiones:0 txqueuelen:0
	RX bytes:119548 (116.7 KB) TX bytes:119548 (116.7 KB)

wlan0	Link encap: Ethernet  direcciónHW 00:1f:3c:60:90:de
	Inet dirección:192.168.1.51 Difusión 192.168.1.255 Máscara:255.255.255.0
	ARRRIBA DIFUSION MULTICAST  MTU:1500  Métrica:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	colisiones:0 txqueuelen:1000
	RX bytes: 0 (0.0 B)  TX Bytes:0 (0.0 B)

Con o sin firewall sigo sin conectar ambas. 
En cuanto a si funciona la conexión wi-fi cuando están las 2 máquinas conectadas, en win xp te digo que sí, pero en ubuntu no sé como verlo. no tengo ese iconito verde (qué burra soy!)
Gracias mil. Salu2
Devo

---

### Post by chalito on 2008-10-24
El burro soy yo, el iconito en Ubuntu es azul :) 
Es como una escalerita que sube de izquierda a derecha.
De todos modos lo raro es que ahi dice:

Adaptador Ethernet Conexiones de red inalámbricas :
Estado de los medios. . . .: medios desconectados
Descripción. . . . . . . . . . . : 802.11b/g USB Wireless LAN Adapter
Dirección física. . . . . . . . . : 00-E0-2A-4D-04-BA

Osea que sería como que no está conectada la placa Wifi en windows.. raro que tampoco tiene IP.
Estás segura de que le configuraste la IP a mano como dice [acá]("http://www.configurarequipos.com/doc331.html")? ( en la parte que dice "Aparece una nueva ventana y pulsamos sobre la opción Usar la siguiente dirección IP. Es aquí donde pondremos nuestra dirección IP y la máscara de subred tal y como se ve en la figura."

---

### Post by devoriana on 2008-10-24
> **chalito said:**
> El burro soy yo, el iconito en Ubuntu es azul :) 
Es como una escalerita que sube de izquierda a derecha.
De todos modos lo raro es que ahi dice:

Adaptador Ethernet Conexiones de red inalámbricas :
Estado de los medios. . . .: medios desconectados
Descripción. . . . . . . . . . . : 802.11b/g USB Wireless LAN Adapter
Dirección física. . . . . . . . . : 00-E0-2A-4D-04-BA

Osea que sería como que no está conectada la placa Wifi en windows.. raro que tampoco tiene IP.
Estás segura de que le configuraste la IP a mano como dice [acá]("http://www.configurarequipos.com/doc331.html")? ( en la parte que dice "Aparece una nueva ventana y pulsamos sobre la opción Usar la siguiente dirección IP. Es aquí donde pondremos nuestra dirección IP y la máscara de subred tal y como se ve en la figura."

gracias chalito:)
juro que seguí paso a paso las indicaciones del link, y le puse la IP estática y la máscara de subred.
en cuanto al ícono de Ubuntu, este aparecía cuando tenía la conexión inalámbrica configurada itinerante y se conectaba con algún wi-fi sin clave WAP. después de que configuré conexión manual no aparece más, ni tampoco las redes wifi cercanas, sólo aparecen los dos monitores como cuando estás en red.
salu2
Devo

---

### Post by chalito on 2008-10-24
Que macana :(

En definitiva no está conectando la red inalámbrica, osea, las dos máquinas no se ven en modo ad-hoc. Me llama mucho la atención que en windows ni siquiera muestre la IP. La verdad no se bien como seguir, si tuviese la máquina enfrente me fijaría a ver si tiene algún parámetro que pasamos por alto pero hace mucho que no uso windows. A lo mejor alguien en el foro que tenga dos maquinas win/linux con wifi pueda hacer unas pruebitas y experimentar un poco ..

edit: que bobo ahora que lo pienso, en esta notebook (la del laburo) tengo windows, y en una pc de casa tengo ubuntu con wifi, aunque no está configurado (la armé hace poco y me dio fiaca =P). Después en casa voy a ver si puedo conectarlas y te comento que ondas, a lo mejor encuentro algo interesante que te pueda ayudar.

edit2: Antes de que se pongan a gastarme, tengo windows en la notebook del laburo solo para usarlo una vez al mes para correr un programita que no anda del todo bien con wine, el resto del tiempo uso un ubuntu customizado para funcionar acá! :)

---

### Post by pablo atheist on 2008-11-05
yo tengo una hp 530 y en una maquina con xp que se conecta mediante un usb inalambrico y estas maquinas se conectan a Internet con un router 
[belkin]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id=136493") y por ahora no he tenido ningún problema , y lo que tuve que configurar fue mínimo

saludos

---

