---
title: "Pedido - Como configuraron sus modem ADSL ?"
date: 2008-05-25
forum: Hardware
---

### Post by sajnox on 2008-05-25
Una de las secciones que seran incluidas en la pagina web de Ubuntu-ar es una seccion con los pasos para configurar los modems USB que proveen los distintos ISP, para ello solicitamos a todos los que tengan o hayan configurado algun modem ADSL en Ubuntu que nos comenten como lo hicieron.

Para esto le dejamos un cuestionario que les pedimos contesten.

Desde ya muchas gracias a todos los que deseen colaborar y en especial a faktor_qm que preparo el cuestionario.

[Cuestionario]

01)
a) ¿Qué empresa de ADSL tenés?
b) ¿Qué versión de Ubuntu tenés?
c) ¿Tenés más de una computadora interconectada al modem? Si es así, ¿Ubuntu funciona "repartiendo" la conexión o existe un hardware (switch/hub/router) que lo hace?
d) ¿Poseés placa de red por cable, inalámbrica, o ambas? (Adjuntar marca y modelo)
 
02) ¿Qué direcciones IP de DNS utilizás?
 
03) ¿Cuál es tu ubicación dentro de la Argentina?
 
04) ¿De qué marca y modelo es tu modem?
 
05) ¿Tiene conexión USB, Ethernet o ambas?
 
06) (Aquellos cuyo modem contenga conexión Ethernet o Ethernet y USB y lo estén usando con Ethernet pasar al paso 7)
     Si el modem es USB o lo estás usando bajo este tipo de conexión:
a) ¿Ubuntu te lo detectó cuando lo enchufaste? (Si esto es correcto pasar al paso 7)
b) Si no ocurrió a); ¿Tuviste que compilar un driver? Si es así, ¿cuál? ¿Qué guía seguiste para lograr instalarlo? (Poner TODOS los links visitados)
07) Para configurar tu modem, ¿Usas pppoeconf? Si es así, ¿Qué guía seguiste para lograr configurarlo? ¿Y con qué datos? (Poner TODOS los links visitados y también TODOS los datos; NO poner usuario y contraseña)
08 ) ¿Activaste el ufw? (Ubuntu FireWall) ¿Sabés lo que es Firestarter? e ¿IPTables?
09) ¿Comentarios? Algo más que quieras agregar o facilitar información, como por ejemplo links al manual del modem, o si lo tenés vos subilo, y poné el link. Nos será de gran ayuda. ¡¡Gracias por colaborar con Ubuntu-ar!!

[/Cuestionario]

---

### Post by User21 on 2008-05-25
01)
**a) ¿Qué empresa de ADSL tenés?**
ADSL Arnet 1 mbps via Telecom.

**b) ¿Qué versión de Ubuntu tenés?**
Ubuntu 8.04 LTS.

**c) ¿Tenés más de una computadora interconectada al modem? Si es así, ¿Ubuntu funciona "repartiendo" la conexión o existe un hardware (switch/hub/router) que lo hace?** 
Sí, mi PC "reparte" la conexion a otra con wxp.

**d) ¿Poseés placa de red por cable, inalámbrica, o ambas? (Adjuntar marca y modelo)**
Uso placas de red alambricas. Las mismas son, segun lspci:
- ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
- nVidia Corporation nForce2 Ethernet Controller (rev a1) (Mobo MSI K7N2 Delta)

**02) ¿Qué direcciones IP de DNS utilizás?**
200.3.60.13  (No estoy seguro)

**03) ¿Cuál es tu ubicación dentro de la Argentina?**
Ciudad de Santa Fe, Santa Fe, Argentina.
 
**04) ¿De qué marca y modelo es tu modem?**
Huawei SmartAX MT882
 
**05) ¿Tiene conexión USB, Ethernet o ambas?**
Tiene ambas conexiones. Uso Ethernet.
 
**07) Para configurar tu módem, ¿Usas pppoeconf? Si es así, ¿Qué guía seguiste para lograr configurarlo? ¿Y con qué datos? (Poner TODOS los links visitados y también TODOS los datos; NO poner usuario y contraseña)**

Puse la conexion en DHCP. Para configurarlo, inicié los seteos del módem desde 10.0.0.2 en el browser. 
Completé los datos de operador, nombre de usuario y contraseña. Clic a conectar. Conectó. Internet funcionando.

**08 ) ¿Activaste el ufw? (Ubuntu FireWall) ¿Sabés lo que es Firestarter? e ¿IPTables?**

Activé Firestarter para compartir la conexión con otra PC. El asistente es sencillo e intuitivo. No se usar UFW.

[B]09) ¿Comentarios?
[/B]Me fue MUY SENCILLO, y eso no significa que sea un usuario experimentado.

---

### Post by rojojuan on 2008-05-26
1)
a) ¿Qué empresa de ADSL tenés?
Fibertel

b) ¿Qué versión de Ubuntu tenés?
Ubuntu 8.04 LTS.

c) ¿Tenés más de una computadora interconectada al modem? Si es así, ¿Ubuntu funciona "repartiendo" la conexión o existe un hardware (switch/hub/router) que lo hace? 
No.

d) ¿Poseés placa de red por cable, inalámbrica, o ambas? (Adjuntar marca y modelo)
Uso placa pci Fast Ethernet 10/100 


02) ¿Qué direcciones IP de DNS utilizás?
Es automática. Se configura sola sin problemas.

03) ¿Cuál es tu ubicación dentro de la Argentina?
Capital Federal

04) ¿De qué marca y modelo es tu modem?
WebStar

05) ¿Tiene conexión USB, Ethernet o ambas?
Tiene Ethernet.

07) Para configurar tu módem, ¿Usas pppoeconf? Si es así, ¿Qué guía seguiste para lograr configurarlo? ¿Y con qué datos? (Poner TODOS los links visitados y también TODOS los datos; NO poner usuario y contraseña)
Se conectó automáticamente. Internet funcionando.

08 ) ¿Activaste el ufw? (Ubuntu FireWall) ¿Sabés lo que es Firestarter? e ¿IPTables?

Activé UFW. Lo dejé por defecto. Sé que Firestarter es un firewall e IPTables se usa para permitir o cerrar puertos, lo sé por haberlo leído.

09) ¿Comentarios?
Hasta ahora sin problemas.

---

### Post by faktorqm on 2008-05-26
**a) ¿Qué empresa de ADSL tenés?**
ADSL Speedy 1 Mbps via Telefónica.

**b) ¿Qué versión de Ubuntu tenés?**
Ubuntu 8.04 LTS.

**c) ¿Tenés más de una computadora interconectada al modem? Si es así, ¿Ubuntu funciona "repartiendo" la conexión o existe un hardware (switch/hub/router) que lo hace?** 
Si, ubuntu no reparte nada, tengo un switch de 8 bocas, con 3 compus conectadas, y el modem lo puse en modo router.

**d) ¿Poseés placa de red por cable, inalámbrica, o ambas? (Adjuntar marca y modelo)**
Uso placas de red por cable. Las mismas son:

- SiS 900 (Mother PC-CHIPS 810)
- nVidia Corporation nForce2 Ethernet Controller (rev a1) (Mother MSI K7N2G-L)
- Realtek 8139c (Mother PC-CHIPS A33G)

**02) ¿Qué direcciones IP de DNS utilizás?**
No lo sé por que como el router es el que se encarga de eso, yo solo me limito a poner DHCP y listo. Voy a intentar averiguarlo. 

**03) ¿Cuál es tu ubicación dentro de la Argentina?**
Ciudad Autónoma de Buenos Aires, Capital Federal, Argentina.
 
**04) ¿De qué marca y modelo es tu modem?**
Zyxel 610
 
**05) ¿Tiene conexión USB, Ethernet o ambas?**
Tiene sólo Ethernet.
 
**07) Para configurar tu módem, ¿Usas pppoeconf? Si es así, ¿Qué guía seguiste para lograr configurarlo? ¿Y con qué datos? (Poner TODOS los links visitados y también TODOS los datos; NO poner usuario y contraseña)**

NO, lo tengo en modo router.
Los dato sque utilicé para configurar mi modem fueron:

Encapsulacion: PPPoE
Multiplexacion: LLC
VPI: 8
VCI: 35
usuario: NO LO TENGO QUE PONER
contraseña: NO LO TENGO QUE PONER
IP: Automatica

**08 ) ¿Activaste el ufw? (Ubuntu FireWall) ¿Sabés lo que es Firestarter? e ¿IPTables?**

No activé UFW, por que mi modem trae firewall incorporado. Si sé lo que es, e iptables también.

**09) ¿Comentarios?**

Utilicé esta guia para ponerlo como modo router la primera vez:
[http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132](http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132)

El manual despues lo subo. Salu2!!

---

### Post by faktorqm on 2008-05-26
ROJOJUAN: Desde ya agradezco mucho tu colaboración, pero vos no tenés ADSL, tenés cablemodem, que es el servicio que da fibertel. Muchas gracias por responder igual :KS pero para la página lo que queremos hacer es poner la configuración de los modems de ADSL. Salu2!!

---

### Post by rojojuan on 2008-05-26
> **faktorqm said:**
> ROJOJUAN: Desde ya agradezco mucho tu colaboración, pero vos no tenés ADSL, tenés cablemodem, que es el servicio que da fibertel. Muchas gracias por responder igual :KS pero para la página lo que queremos hacer es poner la configuración de los modems de ADSL. Salu2!!

Ok. Lo envié por si servía. Más saludos y hasta la próxima!

---

### Post by euzkoarima on 2008-05-27
Yo me conecto desde mi empresa, asi que no aplico en este cuestionario, pero quería comentarles de este [instalador]("http://huawayes.wordpress.com/") que puede ser útil para incluir como información en la página de Ubuntu-ar.

---

### Post by atari130xe on 2008-05-27
01)
a) ¿Qué empresa de ADSL tenés?
ADSL Speedy 2,5 mbps via Telefonica.

b) ¿Qué versión de Ubuntu tenés?
Ubuntu 8.04 LTS.

c) ¿Tenés más de una computadora interconectada al modem? Si es así, ¿Ubuntu funciona "repartiendo" la conexión o existe un hardware (switch/hub/router) que lo hace?
Unica PC.

d) ¿Poseés placa de red por cable, inalámbrica, o ambas? (Adjuntar marca y modelo)
Uso placa de red (Cable)
- nVidia Corporation nForce Networking Controller
- Adaptador de red 1394 (asi lo identifica Ubuntu)

02) ¿Qué direcciones IP de DNS utilizás?
(No estoy seguro) son dinàmicas supongo.

03) ¿Cuál es tu ubicación dentro de la Argentina?
San Justo, Pcia. de Bs.As., Argentina.

04) ¿De qué marca y modelo es tu modem?
SpeedTouch ST510 v6.
05) ¿Tiene conexión USB, Ethernet o ambas?
Ethernet.

07) Para configurar tu módem, ¿Usas pppoeconf? Si es así, ¿Qué guía seguiste para lograr configurarlo? ¿Y con qué datos? (Poner TODOS los links visitados y también TODOS los datos; NO poner usuario y contraseña)
Utilicè la ayuda que trae el mismo CD de Ubuntu, pppoeconf ingresè el usuario y la contraseña, arrancò de una.

08 ) ¿Activaste el ufw? (Ubuntu FireWall) ¿Sabés lo que es Firestarter? e ¿IPTables?
No se usar UFW.

09) ¿Comentarios?
Muy facil, antes tenia dial up y usaba pppconfig ahora con adsl es màs facil aùn. :)

---

### Post by faktorqm on 2008-06-09
BUMPEO acá para que no se olviden :P

Recuerden, solo los que tienen adsl deben completar :P:P Salu2!

---

### Post by cudjoe on 2008-06-18
01)
**a) ¿Qué empresa de ADSL tenés?**
ADSL Speedy 2.5 mbps via Telefonica

**b) ¿Qué versión de Ubuntu tenés?**
Ubuntu 8.04 LTS.

**c) ¿Tenés más de una computadora interconectada al modem? Si es así, ¿Ubuntu funciona "repartiendo" la conexión o existe un hardware (switch/hub/router) que lo hace?** 
Tengo un portatil conectado al modem Ethernet, y comparto la conexion con el Wifi en modo Ad-Hoc.

**d) ¿Poseés placa de red por cable, inalámbrica, o ambas? (Adjuntar marca y modelo)**
La placa de red de mi portatil, segun lspci :
18:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

**02) ¿Qué direcciones IP de DNS utilizás?**
La de mi modem 192.168.1.1

**03) ¿Cuál es tu ubicación dentro de la Argentina?**
Capital Federal, Argentina.
 
**04) ¿De qué marca y modelo es tu modem?**
Huawei SmartAX MT880
 
**05) ¿Tiene conexión USB, Ethernet o ambas?**
Tiene Ethernet.
 
**07) Para configurar tu módem, ¿Usas pppoeconf? Si es así, ¿Qué guía seguiste para lograr configurarlo? ¿Y con qué datos? (Poner TODOS los links visitados y también TODOS los datos; NO poner usuario y contraseña)**

pppoeconf no me detecto el modem en eth0.
Hice esto : [http://ubuntuforums.org/showpost.php?p=5211641&postcount=19](http://ubuntuforums.org/showpost.php?p=5211641&postcount=19)

**08 ) ¿Activaste el ufw? (Ubuntu FireWall) ¿Sabés lo que es Firestarter? e ¿IPTables?**

Sé lo que es. No activé nada.

**09) ¿Comentarios?**
No me fue sencillo para nada, pero pusé todo el tutorial paso a paso en el foro.

---

### Post by gefarion on 2008-06-19
Buenas, este es mi apòrte.

01)
a) ¿Qué empresa de ADSL tenés?
Speedy
b) ¿Qué versión de Ubuntu tenés?
Kubuntu 8.04
c) ¿Tenés más de una computadora interconectada al modem? Si es así, ¿Ubuntu funciona "repartiendo" la conexión o existe un hardware (switch/hub/router) que lo hace?
Kubuntu lo tengo como servidor dhcp y estoy compartiendo internet usando Firestarter. Y tengo un router inalambrico D-Link 300 funcionando como switch.
d) ¿Poseés placa de red por cable, inalámbrica, o ambas? (Adjuntar marca y modelo)
Poseo solo una Placa de Red: SiS900 PCI Fast Ethernet.

02) ¿Qué direcciones IP de DNS utilizás?
Uso los DNS de speedy: 200.51.211.7  200.51.212.7

03) ¿Cuál es tu ubicación dentro de la Argentina?
Buenos Aires.

04) ¿De qué marca y modelo es tu modem?
SpeedTouch 330

05) ¿Tiene conexión USB, Ethernet o ambas?
USB 

06) (Aquellos cuyo modem contenga conexión Ethernet o Ethernet y USB y lo estén usando con Ethernet pasar al paso 7)
Si el modem es USB o lo estás usando bajo este tipo de conexión:
a) ¿Ubuntu te lo detectó cuando lo enchufaste?
No.
b)¿Tuviste que compilar un driver? 
No.
07) Para configurar tu modem, ¿Usas pppoeconf? Si es así, ¿Qué guía seguiste para lograr configurarlo? ¿Y con qué datos? (Poner TODOS los links visitados y también TODOS los datos; NO poner usuario y contraseña)
[http://www.linux-usb.org/SpeedTouch/ubuntu/index-es.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index-es.html)

08 ) ¿Activaste el ufw? (Ubuntu FireWall) ¿Sabés lo que es Firestarter? e ¿IPTables?
Uso Firestarter.
09) ¿Comentarios? 
Es una pena que speedy no de soporte para sus propios modem en linux.

---

### Post by faktorqm on 2008-06-20
Grosso, vos tenes el 330! estuve hace 2 semanas indagando como carancho instalar esa cosa..... finalice en un script que hace todo automaticamente. 
Lo que quiero saber es, primero, si estas dispuesto a probarlo (:KS) y segundo a soportar estar un par de horas sin internet si falla :P Es para la nueva página de Ubuntu-ar....

---

### Post by gefarion on 2008-06-20
Mira yo tambien use un script, que basicamente hace todo lo que dice la guia de manera automatica, y funciona bastante bien, digamos que en 10 seg, me dejo el modem funcionando, estaba pensando mejorarlo un poco y luego subirlo.
Igualmente tengo pensado llamar a speedy para pedir que me lo cambien por un modem ethernet para poder conectarlo directamente al router.
Pero sinceramente opino que no deberiamos pasar por esto, los proveedores deberian dar soporte al equipo que reparten, aunque sea para las distribuciones mas conocidos (debian,ubuntu,fedora,mandriva,etc). Pero les sale mas barato tener gente sin conocimientos que solo sigue un manual, que alguien que en verdad la tenga clara.
Con respecto a tu script, en unos dias tengo que migrar completamente mi maquina a linux (eliminar las particiones ntfs que quedan), asi que no tendria problemas en probar tu script antes de reinstalar todo.
Saludos.

---

### Post by faktorqm on 2008-06-21
Hola, antes de que borres todo me seria util tambien que me pases la configuracion que te anda, para eso posteame las salidas de estos comandos:

1) ```
cat /proc/bus/usb/devices
```

2) ```
ls -la /lib/firmware/
``` aca puede ser que encuentres un directorio o un archivo, si encontras un directorio, ls -la a ese directorio.

3) ```
cat /etc/ppp/peers/algo
```
donde dice algo puede ser que encuentres (o al menos deberias) un archivo. capaz se llama speedtch, pero no se. el contenido de ese archivo que a vos te ana es fundamental. 

Mil gracias y saludos!!!

---

### Post by gefarion on 2008-06-21
Aca te dejo los resultados q me pediste:

1) cat: /proc/bus/usb/devices: No existe el fichero ó directorio

2) drwxr-xr-x  3 root root   4096 2008-06-15 16:17 .
drwxr-xr-x 17 root root   4096 2008-06-17 22:32 ..
drwxr-xr-x  4 root root   4096 2008-06-15 16:02 2.6.24-18-generic
-rwxr-xr-x  1 root root    349 2008-05-29 11:58 speedtch
-rwxr-xr-x  1 root root    349 2008-05-29 11:58 speedtch~
-rwxr-xr-x  1 root root    935 2008-05-29 11:58 speedtch-1.bin
-rwxr-xr-x  1 root root 775545 2008-05-29 11:58 speedtch-2.bin

3)cat speedtch

noipdefault
defaultroute
user 'speedy@speedy'
noauth
updetach
usepeerdns
plugin rp-pppoe.so
nas0

Espero que te sean utiles, saludos.-

---

### Post by steve_ignorant on 2008-07-19
01)
a) ¿Qué empresa de ADSL tenés? 
TELEFONICA(TE-RE-FORNICAN)
b) ¿Qué versión de Ubuntu tenés?
 ubuntu 7.04
c) ¿Tenés más de una computadora interconectada al modem? Si es así, ¿Ubuntu funciona "repartiendo" la conexión o existe un hardware (switch/hub/router) que lo hace?
no, intente hacerlo conubuntu, pero termine renegandoc on windows xp hasta que me lleve la pc, y no comparto mas porq me mude, en su momento ruteaba la pc directo
 
d) ¿Poseés placa de red por cable, inalámbrica, o ambas? (Adjuntar marca y modelo)
usb 

02) ¿Qué direcciones IP de DNS utilizás?

los comunes de speedy

03) ¿Cuál es tu ubicación dentro de la Argentina?
buenos aires, berazategui
04) ¿De qué marca y modelo es tu modem?
zyxel 600, y antes speed touch 330.
05) ¿Tiene conexión USB, Ethernet o ambas?
USB

06) (Aquellos cuyo modem contenga conexión Ethernet o Ethernet y USB y lo estén usando con Ethernet pasar al paso 7)
Si el modem es USB o lo estás usando bajo este tipo de conexión:
a) ¿Ubuntu te lo detectó cuando lo enchufaste? (Si esto es correcto pasar al paso 7)
no
b) Si no ocurrió a); ¿Tuviste que compilar un driver? Si es así, ¿cuál? ¿Qué guía seguiste para lograr instalarlo? (Poner TODOS los links visitados)

no compile, simplemente baje los drivers, ya esta posteados por aca, de todas formas denme tiempoy despues les posteo los drivers. 

07) Para configurar tu modem, ¿Usas pppoeconf? Si es así, ¿Qué guía seguiste para lograr configurarlo? ¿Y con qué datos? (Poner TODOS los links visitados y también TODOS los datos; NO poner usuario y contraseña)

use el pppoeconf con el zyxel, con el speedtouch lo hice armando todo, el zyxel lo reconocio despues de instalar los drivers.

08 ) ¿Activaste el ufw? (Ubuntu FireWall) ¿Sabés lo que es Firestarter? e ¿IPTables?

no active firewall, no se lo que es el firestarter, y no pude usar IPtables para armar la red.

09) ¿Comentarios? Algo más que quieras agregar o facilitar información, como por ejemplo links al manual del modem, o si lo tenés vos subilo, y poné el link. 

esta es la guia solo resta cambiar los comandos ya que este es dintinto... en vez de sudo es su y asi... 

[http://lihuen.info.unlp.edu.ar/index.php/Como_instalar_el_modem_ZyXel_600_PRESTIGE%28usb%29_en_GNU/LINUX](http://lihuen.info.unlp.edu.ar/index.php/Como_instalar_el_modem_ZyXel_600_PRESTIGE%28usb%29_en_GNU/LINUX)

en este link esta la configuracion del zyxel 600.

 [http://www.linux-usb.org/SpeedTouch/ubuntu/index-es.html#pppoe](http://www.linux-usb.org/SpeedTouch/ubuntu/index-es.html#pppoe)  <------ en este esta la configuracion del SPEED TOUCH 330

---

### Post by pol666 on 2008-07-20
[Cuestionario]

01)
**a) ¿Qué empresa de ADSL tenés?**
Speedy ~ 512mb
**b) ¿Qué versión de Ubuntu tenés?**
Ubuntu 8.04[B]
c) ¿Tenés más de una computadora interconectada al modem? Si es así, ¿Ubuntu funciona "repartiendo" la conexión o existe un hardware (switch/hub/router) que lo hace?[/B]
1 sola por ahora
**d) ¿Poseés placa de red por cable, inalámbrica, o ambas? (Adjuntar marca y modelo)**
Tengo una placa PCI y otra onboard[B]

02) ¿Qué direcciones IP de DNS utilizás?[/B]
Use las de speedy pero como estan caidas uso estas:
216.244.192.2
216.244.192.3


**03) ¿Cuál es tu ubicación dentro de la Argentina?**
Banfield Oeste, Buenos Aires

**04) ¿De qué marca y modelo es tu modem?**
es un Zyxel p-600 antes tenia un Huawei MT880

[B]
05) ¿Tiene conexión USB, Ethernet o ambas?[/B]
Ethernet

[B]06) (Aquellos cuyo modem contenga conexión Ethernet o Ethernet y USB y lo estén usando con Ethernet pasar al paso 7)
Si el modem es USB o lo estás usando bajo este tipo de conexión:
a) ¿Ubuntu te lo detectó cuando lo enchufaste? (Si esto es correcto pasar al paso 7)
b) Si no ocurrió a); ¿Tuviste que compilar un driver? Si es así, ¿cuál? ¿Qué guía seguiste para lograr instalarlo? (Poner TODOS los links visitados)[/B]

[...]

**07) Para configurar tu modem, ¿Usas pppoeconf? Si es así, ¿Qué guía seguiste para lograr configurarlo? ¿Y con qué datos? (Poner TODOS los links visitados y también TODOS los datos; NO poner usuario y contraseña)**
si uso pppoeconf, no use ninguna guia, solo ejecute y segui el asistente.

[B]
08 ) ¿Activaste el ufw? (Ubuntu FireWall) ¿Sabés lo que es Firestarter? e ¿IPTables?[/B]
Si se pero no active nada de eso.

**09) ¿Comentarios? Algo más que quieras agregar o facilitar información, como por ejemplo links al manual del modem, o si lo tenés vos subilo, y poné el link. Nos será de gran ayuda. ¡¡Gracias por colaborar con Ubuntu-ar!!**

Ambos modem ethernet que tuve fueron muy faciles de configurar con pppoeconf, ningun problema, a veces no arranca la conexion al inicio y tengo que usar pon dsl-provider  y poff dsl-provider.

Saludos y suerte!

[/Cuestionario]

---

