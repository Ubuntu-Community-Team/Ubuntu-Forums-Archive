---
title: "Modem HUAWEI SmartAX MT880 y ubuntu 7.10"
date: 2008-05-02
forum: Hardware
---

### Post by cricri1991 on 2008-05-02
[SIZE="3"][FONT="Comic Sans MS"]Hola a todos.. solo quería asesorarme antes de hacerlo.
En este momento tengo un modem Speedtouch330 de **Speedy** conectado y funcionando. Pero estoy pensando en cambiarme a un **HUAWEI SmartAX MT880** para poder compartir internet con una maquina con Window$ XP asi puedo usar el ubuntu :) .

[CENTER][IMG]http://www.tomoyo.com.ar/imagenes/noganet-huawei/huawei.jpg[/IMG][/CENTER]

La pregunta es.... :confused:

**¿Como puedo configurar este Modem para conectarme a internet en ubuntu 7.10? ¿Es compatible? .. Me comentaron que tiene un firewall incorporado.. ¿Es verdad? ¿Como lo desactivo?**

Son varias preguntas pero, muy importanes, ya que con el ubuntu e internet.. no me hace falta nada :D

Saludos y espero que puedan ayudarme ;)

*Cris.*[/FONT][/SIZE]

---

### Post by _kAz_ on 2008-05-03
> **cricri1991 said:**
> Hola a todos.. solo quería asesorarme antes de hacerlo.
En este momento tengo un modem Speedtouch330 de **Speedy** conectado y funcionando. Pero estoy pensando en cambiarme a un **HUAWEI SmartAX MT880** para poder compartir internet con una maquina con Window$ XP asi puedo usar el ubuntu :) .
La pregunta es.... :confused:

**¿Como puedo configurar este Modem para conectarme a internet en ubuntu 7.10? ¿Es compatible? .. Me comentaron que tiene un firewall incorporado.. ¿Es verdad? ¿Como lo desactivo?**

Son varias preguntas pero, muy importanes, ya que con el ubuntu e internet.. no me hace falta nada :D

Saludos y espero que puedan ayudarme ;)

*Cris.*

Mira... yo **tengo exactamente el mismo modem** pero con Arnet. Nunca le toque nada y anda de maravillas, te lo reconoce incluso desde antes de instalarlo, desde el Live CD, así que no creo que tengas problemas.

---

### Post by cricri1991 on 2008-05-03
Pero yo tengo speedy, osea tengo que poner un usuario y contraseña para conectarme con mi actual modem USB.. como será con este modem?

---

### Post by _kAz_ on 2008-05-03
Exactamente igual.

A ver... el modem es una especie de minicomputadora que la única función que tiene es conectarse a internet. Si ya lo tenés configurado para esa tarea no importa que cambies el sistema operativo porque es algo totalmente independiente. Hace de cuenta que esa minicomputadora (el modem) tiene su SO propio. La única relación que tiene con tu PC es el cable USB o LAN para pasar los datos, de ahí no hay nada más que tenga incidencia.

---

### Post by cricri1991 on 2008-05-03
Osea que conectandolo teniendo ubuntu en la pC y como proveedor de internet Speedy vos decis que no va a haber drama?

---

### Post by faktorqm on 2008-05-03
Hola, lo que tenes que hacer es, conectar el modem al ubuntu, te lo reconoce todo ok, y cuando lo vas a configurar, aparte del usuario y la contraseña de speedy tenes que cambiar 2 valores más, estos se llaman VPI y VCI respectivamente. 
Para speedy estos valores son VCI: 8 y VPI: 35.
El firewall por que lo queres desactivar? sos una especie de suicida iraqui o te gusta el sado? Si tenes el hardware que te oficia de firewall, para que vas a tener 2 software's (uno en cada pc) gastandote recursos haciendo lo mismo que hace el modem? La verdad que no entiendo. Imagino que queres usar algo (sea programa, servicio) tal que necesites un firewall en tu pc. 
Espero que te haya servido. Salu2!!!!

---

### Post by cricri1991 on 2008-05-03
gracias loco.. y en que parte en el ubuntu configuro el modem? ^^ pasa que soy nuevo en esto :(

---

### Post by _kAz_ on 2008-05-03
Entras desde tu navegador web a la dirección 10.0.0.2, en configuración inicial vas a poder ingresar los datos de usuario, contraseña, etcétera.

Con respecto a lo del firewall yo lo dejaría. Pienso que quizás lo que vos querés es que "baje" cosas más rápido de algun programilla tipo torrent o mula. Para eso no tenes que sacar el firewall sino abrir puertos, pero ya son otras yerbas.

---

### Post by cricri1991 on 2008-05-03
Gracias loco.. para todos los modems es 10.0.0.2 ?? o para este en especial? :D

---

### Post by _kAz_ on 2008-05-03
Creo que para todos los de esa línea... yo tengo el 88**2**, deben ser iguales calculo. Fijate si anda y avisa cualquier cosa.

---

### Post by cricri1991 on 2008-05-03
Ah joya.. porque creo que me voy a comprar ese en deremate.com a $95 .. esta bien ese precio para el modem? andará con speedy y los demas servicios? te dejo el link del articulo para que lo veas.. a ver si me das tu opinion :D [http://oferta.deremate.com.ar/id=18982486_modem-adsl-huawei-smartax-mt882-rt-dual-nuevos]("http://oferta.deremate.com.ar/id=18982486_modem-adsl-huawei-smartax-mt882-rt-dual-nuevos")

Gracias :D

---

### Post by _kAz_ on 2008-05-03
El precio está relativamente bien, suelen andar entre los 70 y los 130 pesos los modems de ese tipo.

Si queres asegurarte podrías llamar a Speedy y preguntar si no tiene alguna *contraindicación*, lo cual no creo si es una conexion ADSL normal.

---

### Post by cricri1991 on 2008-05-03
Gracias loco.. cualquier cosa te vuelvo a molestar :D

---

### Post by pol666 on 2008-05-03
EH CRICRI que haces :D


 Yo tenia ese, andaba joya pero tuve un problema tocando el avhai eth0  desde ubuntu y lo queme (desconfigure) :roll:

---

### Post by cricri1991 on 2008-05-03
Pero lo tenias con Speedy? Como hiciste para configurarlo y poner internet? :D

---

### Post by pol666 on 2008-05-03
Antes que nada fijate si telefonica no te loc ambia gratuitamente o mas barato (LO DUDO pero proba antes asi no te comes un garron de pagar)

Si es muy facil, si tenes una pc hacelo mediante 

```
sudo pppoeconf
```

te sale en la misma consola un pequeño GUI, ahi te pide usuario, contraseña, y unas preguntas (dale a todo que si)


y listo, si todo sale bien tenes conectada a internet, a veces pasa que no conecta, o tiene conectividad nula, a veces apsa por los DNS (tenes que actualizarlos con un comando que no se como es), y a veces por el mismo modem, reseteas el modem y conectas de vuelta con

```
sudo pon dsl provider
```

para desconectar es 

```
sudo poff dsl provider
```

speedy es malo de por si asi que no te creas que vas a experimentar un super cambio.. pero mejor que un modem USB es.

---

### Post by cricri1991 on 2008-05-03
*_**[FONT="Arial Black"]Gracias loco ;)[/FONT]**_*

---

### Post by cricri1991 on 2008-05-07
> **pol666 said:**
> Antes que nada fijate si telefonica no te loc ambia gratuitamente o mas barato (LO DUDO pero proba antes asi no te comes un garron de pagar)

Si es muy facil, si tenes una pc hacelo mediante 

```
sudo pppoeconf
```

te sale en la misma consola un pequeño GUI, ahi te pide usuario, contraseña, y unas preguntas (dale a todo que si)


y listo, si todo sale bien tenes conectada a internet, a veces pasa que no conecta, o tiene conectividad nula, a veces apsa por los DNS (tenes que actualizarlos con un comando que no se como es), y a veces por el mismo modem, reseteas el modem y conectas de vuelta con

```
sudo pon dsl provider
```

para desconectar es 

```
sudo poff dsl provider
```

speedy es malo de por si asi que no te creas que vas a experimentar un super cambio.. pero mejor que un modem USB es.

No pude hacerlo.. no me reconoce el puerto USB. :(

---

### Post by cudjoe on 2008-06-18
Hola todos,

Acabo de hacer la configuracion de este modem HUAWEI MT880 para Speedy, con el cable ethernet. 

El asistante pppoeconf no me encontraba el modem en el puerto eth0. Asi que lo hice todo a mano con la interfaz web y telnet de este modem-router.

Esta configuracion deberia andar con cualquier sistema operativo (GNU/Linux o otro)

**1) Verificar que el modem te da una IP**
```

:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:Xxxxxxxxxxxx
          inet addr:192.168.1.33 

```

Sino, pedirla con la comanda :
```

:~$ sudo dhclient

```

Se debe alcanzar al modem :
```

:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=128 time=2.70 ms

```

**2) Editar los nodos remotos**

Connectarse con la interfaz web [http://192.168.1.1](http://192.168.1.1)

La contrasena por defecto es : admin / 1234

Ir en el menu *BASIC > WAN settings*

Hay 4 nodos remotos. Cuando uno usa el modem en modo router Ethernet, solamente se necesita un nodo PPPoE.

En mi caso, habia este : PVC-2 (SpeedyRo). 
Suprimir los 3 otros y editar este.

VPI/VCI :  8 / 35
Service Category : UBR without PCR
Protocol : PPPoE
Encapsulation : LLC/SNAP

Username : <telefono>@speedyplus
Password : <DNI>

Session Established : Always On
Default Route : [X]
NAT           : [X]
IGMP          : [ ]
MTU : 1492


Guardar los cambios : Apply, y buton Save All.

Mi interfaz web tenia un problema, cuando fui a ver de vuelta las valores, el usuario era <telefono>@speedyplusus, y no habia manera de sacar las 2 ultimas letras.
Entonces, las puse con telnet en una consola :
```

:~$ telnet 192.168.1.1
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
Huawei SmartAX
Login: admin
Password: ****
Login successful
-->
```
Entrar las comandas siguientes :
```

pppoe set transport PVC-2 username <telefono>@speedyplus
pppoe set transport PVC-2 password <DNI> 
system config save
```

**3) Verificar la configuration**

En el interfaz web : *Tools > Diagnostics > Apply*.
Todo es verde [COLOR="Green"]PASS[/COLOR], solamente los cuatro F4 y F5 son rojos FAILED, pero no importa.

**4) Acabar con el famoso test : [http://www.google.com](http://www.google.com) **
Anda !

---

### Post by --Lutari-- on 2008-06-24
Yo tengo el mismo modem pero con Arnet y no tuve ningún problema :)

---

### Post by faktorqm on 2008-06-25
Si tenes un problema, solo que no lo sabes... con la configuracion de él, estas haciendo que el modem de adsl se encargue del marcado de la conexión y del firewall. Con pppoeconf estas marcando vos y encima tu firewall es el que se "ve" desde afuera, por lo tanto, ante un descuido, estas teniendo puertos abiertos dejados a la "buena de Dios". 
No se desesperen que con la nueva ubuntu-ar faktorqm va a poner las cosas en su lugar :D Salu2!!

---

### Post by cricri1991 on 2008-06-25
pero.. conectaste el modem por usb o por cable ethernet?

---

### Post by jonafischer on 2008-06-26
> **cricri1991 said:**
> Gracias loco.. para todos los modems es 10.0.0.2 ?? o para este en especial? :D

en general es 192.168.1.1 para ese modem yo lo use 6 meses con speedy, fijate que lo podes hacer conectar an internet con el firmware que trae asi no te conectas desde linux y funcina como router... Es decir para que no uses el bendito pppoeconf y todo eso que trae mas dolores de cabeza que otra cosa!

---

### Post by fran88 on 2008-07-02
> **cricri1991 said:**
> [SIZE="3"][FONT="Comic Sans MS"]Hola a todos.. solo quería asesorarme antes de hacerlo.
En este momento tengo un modem Speedtouch330 de **Speedy** conectado y funcionando. Pero estoy pensando en cambiarme a un **HUAWEI SmartAX MT880** para poder compartir internet con una maquina con Window$ XP asi puedo usar el ubuntu :) .

[CENTER][IMG]http://www.tomoyo.com.ar/imagenes/noganet-huawei/huawei.jpg[/IMG][/CENTER]

La pregunta es.... :confused:

**¿Como puedo configurar este Modem para conectarme a internet en ubuntu 7.10? ¿Es compatible? .. Me comentaron que tiene un firewall incorporado.. ¿Es verdad? ¿Como lo desactivo?**

Son varias preguntas pero, muy importanes, ya que con el ubuntu e internet.. no me hace falta nada :D

Saludos y espero que puedan ayudarme ;)

*Cris.*[/FONT][/SIZE]

Hola, yo tengo el mismo modem y el mismo problema.. pero no se nada de ubuntu, no tengo idea de como instalar este modem... si alguien me podria explicar como hacerlo paso a paso me seria de mucha ayuda!
saludos

fran

---

### Post by cudjoe on 2008-07-04
chic@s,
fijense, lo hice aca:
[http://ubuntuforums.org/showpost.php?p=5211641&postcount=19](http://ubuntuforums.org/showpost.php?p=5211641&postcount=19)

es compatible !

---

### Post by fran88 on 2008-07-25
> **cudjoe said:**
> chic@s,
fijense, lo hice aca:
[http://ubuntuforums.org/showpost.php?p=5211641&postcount=19](http://ubuntuforums.org/showpost.php?p=5211641&postcount=19)

es compatible !

bien, te falto un detalle para ignorantes como yo :(
donde voy para ver si el modemo me da una ip y poner ese codigo q dice.??en terminal??
"Connectarse con la interfaz web http://192.168.1.1" esto donde lo hago??
disculpa mi ignorancia jajaja.. pero bueh.
saludos!!

---

### Post by Hei Ku on 2008-07-26
abris un navegador de internet y pones la direccion ahi. Firefox, Opera, el que sea.

---

### Post by marianogedisman on 2008-11-15
Hola gente, son las 6:03am y me pasé toda la madrugada intentando ver como puedo abrir el puerto 22 (SSH) en éste router. Les juro que hice las mil y unas y el nMap me sigue diciendo que el puerto 22 está cerrado, a pesar que lo forwardeé desde la interfaz web... ¿Alguna idea?

¡Muchas gracias!

---

### Post by marmax.cor on 2009-03-14
> **cudjoe said:**
> 
Mi interfaz web tenia un problema, cuando fui a ver de vuelta las valores, el usuario era <telefono>@speedyplusus, y no habia manera de sacar las 2 ultimas letras.
Entonces, las puse con telnet en una consola :
```

:~$ telnet 192.168.1.1
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
Huawei SmartAX
Login: admin
Password: ****
Login successful
-->
```
Entrar las comandas siguientes :
```

pppoe set transport PVC-2 username <telefono>@speedyplus
pppoe set transport PVC-2 password <DNI> 
system config save
```

**3) Verificar la configuration**

En el interfaz web : *Tools > Diagnostics > Apply*.
Todo es verde [COLOR="Green"]PASS[/COLOR], solamente los cuatro F4 y F5 son rojos FAILED, pero no importa.

**4) Acabar con el famoso test : [http://www.google.com](http://www.google.com) **
Anda !

yo tengo el mismo modem y el mismo problema de la interfaz que repite las dós últimas letras en donde se pone el nombre de usuario. Yo nunca manejé códigos en la consola, traté de poner lo que digiste, pero me dice error o algo así. Además, hay códigos raros que no sé como poner porque no me figuran en el teclado =/. 

Yo tambíen son nuevo en este tema, alguien me podría explicar bien detallado como hacer esa parte de los códigos? ^^

---

### Post by Thalskarth on 2009-03-16
> **marmax.cor said:**
> yo tengo el mismo modem y el mismo problema de la interfaz que repite las dós últimas letras en donde se pone el nombre de usuario. Yo nunca manejé códigos en la consola, traté de poner lo que digiste, pero me dice error o algo así. Además, hay códigos raros que no sé como poner porque no me figuran en el teclado =/. 

Yo tambíen son nuevo en este tema, alguien me podría explicar bien detallado como hacer esa parte de los códigos? ^^

Hola, como estás--- no se bien ya que nunca tuve speedy ni ninguno de estos problemas, pero por lo que dice Cudjoe en el tuto:
> Mi interfaz web tenia un problema, cuando fui a ver de vuelta las valores, el usuario era <telefono>@speedyplusus, y no habia manera de sacar las 2 ultimas letras.
Entonces, las puse con telnet en una consola :
```

:~$ telnet 192.168.1.1
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
Huawei SmartAX
Login: admin
Password: ****
Login successful
-->
```
Entrar las comandas siguientes :
```

pppoe set transport PVC-2 username <telefono>@speedyplus
pppoe set transport PVC-2 password <DNI> 
system config save
```

tenes que abrir una consola (o terminal). Ahi escribis "telnet 192.168.1.1"

y de apoco tendrias que obtener los textos como dice ahi arriba. Al final, te quedaría la ultima linea de la consola con este simbolo "-->" y te permitiria escribir. Entonces ahi es donde copias las comandas:
```
pppoe set transport PVC-2 username <telefono>@speedyplus
```
apretar enter y la otra comanda:
```
pppoe set transport PVC-2 password <DNI> 
```

y listo.


En lo de mi novia, que si tiene speedy y un modem ethernet, se lo configure con el pppoeconf directamente. Y resulto de 10 :)

---

### Post by Nikolopulus on 2009-03-18
> **faktorqm said:**
> Si tenes un problema, solo que no lo sabes... con la configuracion de él, estas haciendo que el modem de adsl se encargue del marcado de la conexión y del firewall. Con pppoeconf estas marcando vos y encima tu firewall es el que se "ve" desde afuera, por lo tanto, ante un descuido, estas teniendo puertos abiertos dejados a la "buena de Dios". 
No se desesperen que con la nueva ubuntu-ar faktorqm va a poner las cosas en su lugar :D Salu2!!


Entonces... ¿cual de las dos opciones tengo que usar para configurar el modem?
Por otro lado ¿la configuración desde navegador es igual para ubuntu y windows?
Gracias por la ayuda

---

