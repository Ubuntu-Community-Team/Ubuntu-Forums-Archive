---
title: "Rutear modem Thomson Speedtouch 510, ¿Como?"
date: 2008-07-13
forum: Hardware
---

### Post by atari130xe on 2008-07-13
Como ruteo un modem Ethernet Thomson Speedtouch s510?:confused:

PD: Quisiera conectarme directamente desde el modem (evitando pppoe)

---

### Post by [P]oli on 2008-07-13
Yo prefiero cliente-servidor, es decir, que una pc se conecte al módem, y que esa pc sea servidor en el router, yo tengo la conexión de mi casa así, ya que desde 1 pc se puede controlar el modem

---

### Post by faktorqm on 2008-07-14
> **'[P]oli said:**
> Yo prefiero cliente-servidor, es decir, que una pc se conecte al módem, 

¿por qué?

> **'[P]oli said:**
> y que esa pc sea servidor en el router, 

¿Cómo? No entendi...

> **'[P]oli said:**
> yo tengo la conexión de mi casa así, ya que desde 1 pc se puede controlar el modem

y por qué así? sabías de algo que se llama "modo router" en lugar de modo "bridge" o modo "puente"?

atari130xe: Lee la página 17 del manual que te adjunte. Es un manual de la propia de gente de Speedtouch en castellano. Salu2!!

---

### Post by atari130xe on 2008-07-14
> **faktorqm said:**
> ¿por qué?



¿Cómo? No entendi...



y por qué así? sabías de algo que se llama "modo router" en lugar de modo "bridge" o modo "puente"?

atari130xe: Lee la página 17 del manual que te adjunte. Es un manual de la propia de gente de Speedtouch en castellano. Salu2!!

Seguí tus pasos desde Ubuntu y nada... (no conecta con el navegador, dice servidor no encontrado), como tengo dual boot, ingresé por Firefox en XP y pude hacerlo pero... cuando quiero entrar a configuracion para hacer las modificaciones y setearlo como router me pide usuario y contraseña que según el manual es Administrator y el pass en blanco, pero nada, una y otra vez me pide (a partir de ese momento) el usuario y contraseña esta vez para ingresar al sitio, o sea se me complicó un poco, estoy googleando a ver si se puede de otra manera y encontré algo en psicofx pero de unos usuarios de Colombia con servidores y configuraciones de allá. alguna sugerencia?

---

### Post by [P]oli on 2008-07-14
**faktorqm**, te explico cómo tengo Internet en mi pc:

Internet llega mediante Cablemodem. Ése modem lo conecté a una PC (con WinXP, que no viene al caso.). En casa tengo otras 2 PC, conectadas mediante un router cableado. La PC que recibe Internet, está configurada como servidor (IP fija,), la mía y la de mi hermano, son cliente (Ip dinámica con puerta de enlace a la IP fija). Yo creo que es mejor éste método, ya que puedo administrar el módem desde una única pc (habilitarlo, deshabilitarlo, etc etc)

Espero que conteste tus preguntas :D

---

### Post by Hei Ku on 2008-07-14
> **'[P]oli said:**
> **faktorqm**, te explico cómo tengo Internet en mi pc:

Internet llega mediante Cablemodem. Ése modem lo conecté a una PC (con WinXP, que no viene al caso.). En casa tengo otras 2 PC, conectadas mediante un router cableado. La PC que recibe Internet, está configurada como servidor (IP fija,), la mía y la de mi hermano, son cliente (Ip dinámica con puerta de enlace a la IP fija). Yo creo que es mejor éste método, ya que puedo administrar el módem desde una única pc (habilitarlo, deshabilitarlo, etc etc)

Espero que conteste tus preguntas :D

En cuanto a diseño de red, esa configuración tiene varios problemas, asumiendo que el router tiene todo lo necesario para conectarse al modem directamente.

Primero, tenés un punto de falla adicional.
Segundo, te obliga a tener una PC prendida sí o sí si queres navegar desde las otras. Desde el punto de vista energético, eso te puede sumar.
Tercero, en general, los routers también tienen opciones para habilitar/deshabilitar la conexion
Cuarto, sobrecargas la PC que hace de router, y eso te puede complicar si por ejemplo estas jugando en esa maquina y otra PC esta bajando y subiendo cosas a full. El router esta pensado especialmente para ese proposito y es mucho mas dificil que lo sobrecargues. En todo caso, en vez del router te hubieras comprado un hub de $20 y era lo mismo.
Quinto, exponer un XP a internet es una invitacion a problemas.

---

### Post by faktorqm on 2008-07-15
> **atari130xe said:**
> Seguí tus pasos desde Ubuntu y nada... (no conecta con el navegador, dice servidor no encontrado), como tengo dual boot, ingresé por Firefox en XP y pude hacerlo pero... cuando quiero entrar a configuracion para hacer las modificaciones y setearlo como router me pide usuario y contraseña que según el manual es Administrator y el pass en blanco, pero nada, una y otra vez me pide (a partir de ese momento) el usuario y contraseña esta vez para ingresar al sitio, o sea se me complicó un poco, estoy googleando a ver si se puede de otra manera y encontré algo en psicofx pero de unos usuarios de Colombia con servidores y configuraciones de allá. alguna sugerencia?

Reiniciaste el modem a valores de fábrica antes de hacer eso? que raro que en ubuntu no pudiste, ¡es lo mismo que en win! pero bue... 

Las contraseñas que recolecte durante años de soporte técnico son, 1234, 12345, 123456, tecoteco (si tenes telecom), tasatasa (si tenes telefonica), admin, <nada> (como dice el manual), tomenague, pass y password. Son las que mas uso y las que mas me acuerdo. Capaz me olvide de alguna. Pero si lo reinicias a valores de fabrica, la contraseña es la que te dice el manual digamos, no hay otra.

[P]oli: Es lo mismo solo que yo pense que tenias adsl... hacele caso a Hei Ku, cuando tengas tiempo/ganas arma la red de vuelta con un router y un switch o con el router solo si tenes 4 bocas y lo configuras bien y suficiente. Salu2!!

---

### Post by atari130xe on 2008-07-15
> **faktorqm said:**
> Reiniciaste el modem a valores de fábrica antes de hacer eso? que raro que en ubuntu no pudiste, ¡es lo mismo que en win! pero bue... 

Las contraseñas que recolecte durante años de soporte técnico son, 1234, 12345, 123456, tecoteco (si tenes telecom), tasatasa (si tenes telefonica), admin, <nada> (como dice el manual), tomenague, pass y password. Son las que mas uso y las que mas me acuerdo. Capaz me olvide de alguna. Pero si lo reinicias a valores de fabrica, la contraseña es la que te dice el manual digamos, no hay otra.

[P]oli: Es lo mismo solo que yo pense que tenias adsl... hacele caso a Hei Ku, cuando tengas tiempo/ganas arma la red de vuelta con un router y un switch o con el router solo si tenes 4 bocas y lo configuras bien y suficiente. Salu2!!

> que raro que en ubuntu no pudiste, ¡es lo mismo que en win! pero bue... La verdad ni idea, pero desde Ubuntu no pude entrar por la web, "time out" despuès de un largo rato esperando. En cuanto al reseteo del modem no lo hice (perdòn no sabìa que habìa que hacerlo antes del procedimiento), hoy voy a intentarlo de esa manera y despuès les cuento.

---

### Post by faktorqm on 2008-07-23
y? salu2!

---

### Post by atari130xe on 2008-08-07
Bueno acà estoy de nuevo con este tema, despuès de un tiempo vuelvo a la carga. Logrè setear el modem de fàbrica al menos eso parece porque para entrar a la configuraciòn del modem no me pide màs contraseña. El tema està en que cuando intento ir a "configurar" se abre una ventana pero VACIA :confused: es como si no terminara de cargar o como si hubiera sido "deshabilitada" por Speedy no lo sè. Alguna sugerencia? hago una impresion de pantalla desde XP (si, desde ubuntu sigo sin poder ingresar al modem, creo que es algo de la config. DHCP).

---

### Post by sergiom99 on 2008-08-07
proba de abrirlo con el iexplorer.
Hay cosas que aun estan mal hechas y por algun motivo no funcionan en firefox.
Para esos casos tengo IEtab: [https://addons.mozilla.org/en-US/firefox/addon/1419](https://addons.mozilla.org/en-US/firefox/addon/1419)

---

### Post by atari130xe on 2008-08-07
> **sergiom99 said:**
> proba de abrirlo con el iexplorer.
Hay cosas que aun estan mal hechas y por algun motivo no funcionan en firefox.
Para esos casos tengo IEtab: [https://addons.mozilla.org/en-US/firefox/addon/1419](https://addons.mozilla.org/en-US/firefox/addon/1419)

No tuve èxito, es raro :confused:

---

### Post by sergiom99 on 2008-08-07
MUY raro.
pero fijate que tampoco te carga las imagenes de los botones de la izq, por lo que veo en la captura.
en google no encontraste nada descripto para este modelo?

---

### Post by pol666 on 2008-08-07
Iba a brir un tema pero este es el momento justo para preguntarles...

Si routeo mi modem Zyxel 600 de esta forma

[http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132]("http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132")

Osea con Telnet desde XP, en Ubuntu me va a andar bien? la verdad no se si esa forma es la correcta, diganme

---

### Post by atari130xe on 2008-08-07
Estoy en eso pero no encuentro nada del porque aparece la ventana de configuracion en blanco. :confused:

---

### Post by sergiom99 on 2008-08-07
> **atari130xe said:**
> Estoy en eso pero no encuentro nada del porque aparece la ventana de configuracion en blanco. :confused:

upgrades de firmware?

---

### Post by atari130xe on 2008-08-07
> **sergiom99 said:**
> upgrades de firmware?

No estoy seguro pero no creo que sea necesario, los "entendidos" lo diràn.

La opcion "configurar" como figura en la imagen no despliega nada màs que una imagen en blanco. No comprendo.

---

### Post by faktorqm on 2008-08-08
> **pol666 said:**
> Iba a brir un tema pero este es el momento justo para preguntarles...

Si routeo mi modem Zyxel 600 de esta forma

[http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132]("http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132")

Osea con Telnet desde XP, en Ubuntu me va a andar bien? la verdad no se si esa forma es la correcta, diganme

No seas marica! Hacelo desde el telnet de ubuntu! ;) naa en serio, tenes el mismo modem que yo, si haces lo que dice en ese tuto salis andando para win y para ubuntu. lo que te recomiendo de hacer es: a tu(s) pc(s) ponele IP fija, y dejar un pool DHCP de 4, por ejemplo del 192.168.1.6 al 192.168.1.10. para que haces esto? para que cuando quieras usar el emule, reenvies los puertos a tu ip por ejemplo, (o el programa p2p q + t guste), y no tenes drama (eso con dhcp no lo podes hacer).
En cambio cuando x ejemplo queres hacer un net install de debian, mientras corre la instalacion y SIN TOCAR NADA, te autodetecta que tenes un server dhcp, te asigna una direccion y salis con internet de una. y cuando digo sin tocar nada es posta eh! te quedas mirando la pantalla y continua la instalacion... hasta que te pregunta por el espejo debian para bajar los paquetes (a proposito, no uses el de la uba). 
Cualquier cosa pregunta. Salu2!

atari130xe: que bueno que esta tu avatar :D 
con respecto a lo del modem es la primera vez que lo veo :S pero bueno, no se, la verdad lo unico que hubiera probado asi de manotazo de ahogado es sacarle el punto a la direccion ip del final. viste q dice 192.168.1.254./algo.... bueno, sacale el ultimo punto de la direccion ip, te deberia quedar [http://192.168.1.254/ewizard.htm](http://192.168.1.254/ewizard.htm)
Sino la otra que te queda es hacer upgrade de firmware, t acordas que x msn te habia pasado una pagina (un foro si mal no recuerdo) al respecto? Salu2!

---

### Post by pol666 on 2008-08-08
> pol@pol-desktop:~$ telnet 192.168.1.1
Trying 192.168.1.1...



parece que no responde, Sera por que esta en modo itinerante :o?

---

### Post by atari130xe on 2008-08-08
Muchachos no hay caso me sigue saliendo la ventana de configuración en blanco, esta vez y luego de modificar la conexión (aparentemente habia un problema con DHCP) logré hacerlo en ubuntu! Faktorqm -El avatar me gusto y decidí cambiarlo :lolflag: ahora puedo desde Ubuntu pero sigo sin poder acceder a la configuración. me sugieren actualizar el Firmware pero resulta que buscando en Google, el que ya tiene el modem parece ser la última version porque las que encontré son del 2004/5, los detalles de lo que tiene ahora son los siguientes:

> Información del sistema	

En esta página se resume la información importante relativa a su SpeedTouch. Es posible que necesite esta información cuando contacte con el servicio de atención al cliente.
	
			
Nombre del producto:	ST510
Número de serie:	CP0741DTBK1
[COLOR="Red"]**Versión de software:	6.2.15.7**[/COLOR]
Variante del software:	CA
Versión del cargador de inicio:	1.0.8
Código de producto:	3594261A
Nombre de tarjeta:	BANT-U

¿Alguna otra sugerencia?
¿Me parece a mí o me toca todo lo complejo para hacer? jajaja ¡quieren que aprenda eso pasa! :lolflag:

---

### Post by faktorqm on 2008-08-08
pol: modo itinerante? tenes uno wireless? capaz entendi mal. O sea, lo que tenes que hacer basicamente es resetear el modem a valores de fabrica y poner tu placa en dhcp o itinerante no se si es lo mismo o no que dhcp. (de paso me podes aclarar esa pequeña duda).

atari: mañana busco y te digo si es un bug o algo. Salu2!!

---

### Post by pol666 on 2008-08-08
ni idea tampoco que es, asi me lo deja ubuntu default ahora lo cambie a DHCP  y telnet responde

---

### Post by pol666 on 2008-08-08
mmm Parece que ya esta routeado... tan facil era, pero no dice lo que dice la pag de telefonica, supuestamente se tienen que cambiar las luces a naranja/amarillo y estan en verde, nada ams que se prendio otra que antes no se prendia la que dice Internet


Listo, quedo routeado excelente :D

me falta saber si quedo listo en win

---

### Post by atari130xe on 2008-08-09
¡Gracias Amigo Faktorqm!

Buscando encontré el significado de DHCP:

[http://docs.info.apple.com/article.html?artnum=58507-es&coll=wp]("http://docs.info.apple.com/article.html?artnum=58507-es&coll=wp")

Lo que sí me día cuenta es que por ejemplo, al instalar Ubuntu y al ejecutar pppoeconf todo se hacé de manera "automática" (salvo el usuario y la clave de conexión). Yo no podía ingresar al setup de mi modem en Ubuntu evidentemente si antes dejar la configuración de la conexíon en DHCP que aparentemente es lo que permite entrar en el setup del modem via navegador, ahora sí puedo hacerlo y al principio cuando modifiqué ese parámetro no me dejaba si quiera conectarme a Internet, pero bueno aprendí algo más. :)

---

### Post by pol666 on 2008-08-09
Yo necesito saber como puedo abrir los puertos por que no anda el Utorrent ni el amule :(

---

### Post by faktorqm on 2008-08-10
> **pol666 said:**
> Yo necesito saber como puedo abrir los puertos por que no anda el Utorrent ni el amule :(

No les des bola a las lucecitas, mi zyxel me tira las que se le canta. A veces me tira 4, a veces dos, a veces titilan, a veces no.... y la conexion nunca se corta asi que....

Para abrir los puertos entra al modem desde el navegador y anda a "nat", en la pagina que se te abre elegi "SUA only" y apreta en "edit details" y en la pagina que se te abre modificas las que te gustan. (JAMAS MODIFIKES LA ENTRADA UNO POR QUE NO VA A ANDAR NADA y vas a tener que resetear a valores de fabrica y configurar todo de vuelta).
ahi pones puerto a puerto que queres que reenvie y apretas "save" y listo.

En windows lo unico que tenes que hacer es poner la misma configuracion que en ubuntu, asi te andan los programas p2p y listo.

atari: claro, te quedas sin internet por que lo que estas haciendo en realidad es cambiar de red. No importa eso, lo pudiste configurar? salu2!

---

### Post by pol666 on 2008-08-10
> (JAMAS MODIFIKES LA ENTRADA UNO POR QUE NO VA A ANDAR NADA

poquito tarde, busque en un tutorial decia eso, lop hice y anda todo jej.

---

### Post by faktorqm on 2008-08-10
mmm posteame un screenshot que quiero ver que hiciste. y cuantas pc's tenes en tu casa? imagino que solo una. salu2!

---

### Post by atari130xe on 2008-08-11
> **faktorqm said:**
> No les des bola a las lucecitas, mi zyxel me tira las que se le canta. A veces me tira 4, a veces dos, a veces titilan, a veces no.... y la conexion nunca se corta asi que....

Para abrir los puertos entra al modem desde el navegador y anda a "nat", en la pagina que se te abre elegi "SUA only" y apreta en "edit details" y en la pagina que se te abre modificas las que te gustan. (JAMAS MODIFIKES LA ENTRADA UNO POR QUE NO VA A ANDAR NADA y vas a tener que resetear a valores de fabrica y configurar todo de vuelta).
ahi pones puerto a puerto que queres que reenvie y apretas "save" y listo.

En windows lo unico que tenes que hacer es poner la misma configuracion que en ubuntu, asi te andan los programas p2p y listo.

atari: claro, te quedas sin internet por que lo que estas haciendo en realidad es cambiar de red. No importa eso, lo pudiste configurar? salu2!

No pude amigo, sigo con el mismo problema del popup (ventana en blanco) :confused: puede ser posible que el modem me haya sido enviado desde Speedy con alguna configuración "especial" para no poder ser modificado el setup?

---

### Post by faktorqm on 2008-08-11
Si realmente lo reseteaste a valores de fabrica, no. 
Tenes el cd que te vino con el modem ese? en la seccion soporte tecnico de speedy explican como configurarlo en modo router mediante la utilizacion de ese cd... sino se consigue, no creo que sea tan dificil... salu2!

---

### Post by pol666 on 2008-08-11
[[img]http://i38.tinypic.com/rvko47_th.png[/img]](http://i38.tinypic.com/rvko47.png)

ahi esta, no se si hice bien pero por lo menos el amuel y utorrent empesaron a andar

---

### Post by faktorqm on 2008-08-12
Exactamente lo que pensaba... ya podes empezar a insultar el que escribio eso en el blog...
Vos ahi lo que estas haciendo, es saltear el firewall que trae el mismo router, redireccionando todos los puertos de la conexion de internet a tu pc. Lo que tenes que hacer, es, la primera linea, ponerla a 0.0.0.0 y abajo en la columna de la izquierda, el puerto que queres redireccionar, en la columna del medio el mismo puerto, y a la derecha de todo tu ip.
Te tiene que quedar algo parecido a esto:

all ports - all ports - 0.0.0.0
1234 - 1234 - 192.168.1.10

siendo 1234 el puerto que uses vos. Te tenes que fijar en tu programa que puertos esta usando, y abrirlos a todos. cuando llego a casa te posteo mi tabla nat asi la tenes de referencia. Salu2!!

---

### Post by pol666 on 2008-08-12
Y esta mal que me saltee el firewall ?

---

### Post by faktorqm on 2008-08-12
No es que esta mal, pero te obliga a tener uno vos por software, (a menos que no te caliente tener firewall) entendes? vos asi como estas ahora, el que se ve desde afuera es el firewall de tu SO, el que hayas arrancado. Y si no tenes ninguno te cuento que estas sin proteccion jajaja (suena a male y fleco) 

Aca te dejo mi tabla, la ip 2 soy yo y la 3 la otra compu. me redirecciono un par de puertos para emule y otros para torrent para cada una. el resto de las appz que no necesitan tener abiertos puertos desde afuera, funcionan perfecto. Espero que te haya aclarado un poco el panorama, sino pregunta. [http://xs130.xs.to/xs130/08332/tabla413.jpg](http://xs130.xs.to/xs130/08332/tabla413.jpg)

Salu2!

---

### Post by pol666 on 2008-08-12
Gracias   peeero ....

* ¿Que riesgo corro en Linux sin firewall?

( que incha que soy)

---

### Post by faktorqm on 2008-08-12
y... un ejemplo puede ser que vos levantes una ssh para tu red local por ejemplo, y como no tenes firewall venga uno de afuera y se conecte... obviamente sin el password no puede, pero esta abierta la posibilidad. Lo mimso con un ftp, o smb (aunque menos probable por que los proveedores bloquean los puertos) o no se, siempre mejor estar seguro que no estarlo. Aparte ya tengo la paranoia de tantos años de windows, asi que de alguna manera es como que ""ayudo"" a la seguridad de mi pc, ya ayudada en un 99% por gnu/linux. Salu2!

---

### Post by pol666 on 2008-08-12
ah listo, no me afecta mucho. No tengo el firestarter ni ningun firewall, tengo una sola PC  sin red local, lo que si tengo una carpeta compartida en Samba.

---

### Post by Hei Ku on 2008-08-12
el puerto de samba, que es el mismo que para los shares de windows, es el primero que prueban cuando te hacen un escaneo de puertos. Definitivamente te conviene usar un firewall.

---

### Post by atari130xe on 2008-08-15
Bueno logrè entrar al setup del modem via telnet en XP:
User: Administrator
Password: (en blanco)
Luego queda en "Administrator" con el cursor titilando pero no se como seguir, intentè: setup y configurar pero nada me dice que el comando no es correcto... :confused:

---

### Post by atari130xe on 2008-08-16
> **atari130xe said:**
> Bueno logrè entrar al setup del modem via telnet en XP:
User: Administrator
Password: (en blanco)
Luego queda en "Administrator" con el cursor titilando pero no se como seguir, intentè: setup y configurar pero nada me dice que el comando no es correcto... :confused:

PD: luego de poder "rutearlo" serìa màs que interesante saber que debo hacer en el OS para poder usar el modem en modo router, o sea si hay que modificar paràmetros, etc.

---

### Post by faktorqm on 2008-08-18
aca tenes todos los comandos: [http://www.speedtouch.com/pdf/ST500%20CLI%20Reference%20Guide%20R4.2.pdf](http://www.speedtouch.com/pdf/ST500%20CLI%20Reference%20Guide%20R4.2.pdf) salu2!

---

### Post by atari130xe on 2011-03-04
Revivo el post luego de tanto tiempo porque jamás lo cerré! Ayer volví a tener en mis manos el bendito modem ethernet Thomson Speedtouch ST510v6, debido que a pedido de una amiga de mi hna que cansada de tanto virus con XP le instale Ubuntu. Averigué todo y le pregunté que modem estaba usando ella con su conexion SION 1 mega, me dijo Zyxel Prestige 600 series (USB), dije con ese modem me vá a sacar canas verdes y llevé mi Speedtouch que tenia arrumbado por tener otra linea y otro modem. Intenté configurarlo nuevamente como router y fué imposible, probé con casi todo lo que conozco y no hubo manera, evidentemente tiene algún defecto. Por web, logro entrar al setup pero no a la configuración en sí (ventana en blanco), por Telnet no realiza los cambios (se cuelga), así que desistí en cuanto a rutearlo pero igual reemplacé el Zxel de esta chica por el Speedtouch que para pppoe funciona bién. No pude hacer que Ubuntu 10.04.2 pueda conectarse desde Network manager (DSL, user, pass, etc.) así que tuve que crearle un lanzador con sudo pon dsl-provider "SION conectarse", y sudo poff dsl-provider "SION desconectarse" es un poco molesto pero es lo más práctico que se me ocurrió en ese momento, si alguien sabe de un único lanzador o como conectarse con el bendito Network manager, bienvenido. En resumen, cambiar el modem es mi única solucion. gracias por leerme!

---

