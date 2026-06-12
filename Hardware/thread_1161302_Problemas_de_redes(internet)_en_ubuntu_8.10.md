---
title: "Problemas de redes(internet) en ubuntu 8.10"
date: 2009-05-16
forum: Hardware
---

### Post by Polacko85 on 2009-05-16
Hola, soy nuevo en el foro ):P,les comento mis problemas:
Desde que me convencieron (unos compañeros a instalar ubuntu) ,me a surgido los siguientes problemas relacionados con la red, mas precisamente con internet:

**1º problema **: A la semana mas o menos de haber instalado ubuntu  8.10 en mi pc, note que habia desaparecido el icono de red ( ese q´tiene 2 computadoras, q esta al lado de la hora en la barra) justo cuando me decidi a instalar speedy para poder a navegar.

**2º problema**: No tengo idea de como instalar speedy en ubuntu, en realidad ya prove todas las formas que encontre en internet (prove con el sudo pppoeconf en la consola y nada, prove desde network configuration y nada) ademas como desaparecio el icono de red de la barra, mas estoy perdido  :confused:.
Ademas por otros datos creo que el sistema rechazo la placa de red y ya no la detecta.

pd: El 1º problema perciste ya que desinstale el S.O y el icono vuele a parecer pero luego cuando reinicio o vuelvo prender el sistema desaparece otra vez.:cry: ](*,)](*,).

Version de Ubuntu : 8.10 , 386!
Placa de red : NIC Fast Ethernet PCI Familia RTL8139 de Realtek 
Servicio de internet: speedy duo (modem huawei smartAX MT880)
Instalacion de ubuntu con windows xp sp2 ( por medio de wubi), osea como una aplicacion con arranque dual.
No tengo router ni una red.
No quiero volver al windows ](*,):cry: Por favor espero que me ayuden [-o< 
Gracias.

---

### Post by emiliano_raso on 2009-05-16
Que modem es? Ethernet o USB?
Porque si no te funcionó el pppoeconf es que seguramente es un USB y es un bardo configurarlos (al menos era un bardo 2 años atras xD)

---

### Post by Polacko85 on 2009-05-16
No es ethernet , ese es el problema, quizas pueda ser algun problema con la placa de red:confused::confused::frown:.
Lei por hay  que habia un tipo de placas de red con casi el mismo nombre que la mia q tenia, un problema parecido al no poder conectarse. Con el pppoeconf prove y  al final decia que estaba todo bien instalado y q ya estaba conectado a internet y bla bla, pero yo entro al mozilla y no de respuesta " SERVIDOR NO ENCONTRADO" y el luces (led) del modem se comportan diferente a windows xp.

---

### Post by emiliano_raso on 2009-05-16
> **Polacko85 said:**
> No es ethernet , ese es el problema, quizas pueda ser algun problema con la placa de red:confused::confused::frown:

Por ahi sigue vigente el problema de configurar modems usb en Linux u.u

---

### Post by Hei Ku on 2009-05-16
Lo tenes puesto como ruteable al modem? Si no, tenes que fijarte en los posts en este mismo foro sobre ese modem (bien llamado el alfajor del diablo, si no estoy confundido)

---

### Post by Polacko85 on 2009-05-16
Por hay me exprese mal xD es ethernet quise decir, perdon por si no entendieron.
Mi modem es ethernet, y creo q no es este "el alfajor del diablo" el que dicen ustedes

---

### Post by Hei Ku on 2009-05-16
Ok. Lo tenes en modo router? Funciona por DHCP o con un discador?

Deberias configurarlo como router y DHCP, y ahi te andaria sin problemas.

Podrias postear la configuracion que tenes en windows, que eso nos ayudaria a saber en que modo esta andando ahora.

---

### Post by Polacko85 on 2009-05-16
ok, aca va esta es la d la placa de red :
 
Tipo de direccion: Asignada por DHCP.
Direccion de ip : xxx.xxx.xxx.x
Mascarasubred: xxx.xxx.xxx.x
Puerta de enlace predeterminada: xxx.xxx.x.x

No creo q sea conveniente poner la ip y eso , por eso no lo puse.

Estado de Speedy:
Nombre de dispositivo : Minipuerto WAN (PPPOE)
Tipo de dispositivo: PPPOE
Tipo de servidor: PPP
Transportes :TCP/IP
Auntenticacion: PAP
Compresion: -
Entramado de vinculo: ninguno
ip del servidor :xxx.xx.xxx.xxx
ip del cliente: xxx.xxx.xx.xxx

Como dije antes no tengo router ni una red , solamente modem (Huawei SmartAX MT880 y placa de red NIC Fast Ethernet PCI Familia RTL81

Creo que te referis a ese tipo de info sino avisame :p

---

### Post by Polacko85 on 2009-05-16
Podrian dejarme algun link o guia de como rutearlo??

---

### Post by Hei Ku on 2009-05-16
Como dije, en este mismo foro hay varios threads de ese mismo modem/router.

Aca explica como ponerlo en modo router.
[http://ubuntuforums.org/showpost.php?p=5211641&postcount=19](http://ubuntuforums.org/showpost.php?p=5211641&postcount=19)

---

### Post by Polacko85 on 2009-05-18
Hay alguna manera de configurar la conexion de speedy sin necesidad de andar cambiandole la configuracion al modem?

---

### Post by dirty fingers on 2009-05-18
si no queres tocar el modem tenes que establecer una conexión pppoe desde el sistema. en ubuntu 9.04 lo encontras en "conexiones de red" -> "dsl".

---

### Post by Polacko85 on 2009-05-23
Ya solucione algunos problemas instalando el ubuntu 9.04.
El unico problema que tengo ahora es el de la coneccion que sigo sin poder usarla , este ubuntu me vino ,ya puesta una coneccion "auto eth0" que esta configurada como DCHP, pero aun no puedo navegar: al abrir el firefox me aparece "SERVIDOR NO CONECTADO" o algo similar.

---

### Post by guillermolisi on 2009-05-23
> **Polacko85 said:**
> Ya solucione algunos problemas instalando el ubuntu 9.04.
El unico problema que tengo ahora es el de la coneccion que sigo sin poder usarla , este ubuntu me vino ,ya puesta una coneccion "auto eth0" que esta configurada como DCHP, pero aun no puedo navegar: al abrir el firefox me aparece "SERVIDOR NO CONECTADO" o algo similar.
Si tenes red y no podes navegar te estan faltando las IPs de los DNSs.

Proba poniendo en el navegador web esta IP 64.233.169.104 y si te aparece el sitio de Google es que la conexion funciona pero no tenes servicio de DNS (que traduce la URL en una IP)

---

### Post by Polacko85 on 2009-05-24
No nada mira :icon_frown: : 

Este es la info de la conexion en un pantalllaso: [http://ubuntuforums.org/attachment.php?attachmentid=114933&stc=1&d=1243171529](http://ubuntuforums.org/attachment.php?attachmentid=114933&stc=1&d=1243171529)

Aca el FIREFOX : [http://ubuntuforums.org/attachment.php?attachmentid=114934&stc=1&d=1243150077](http://ubuntuforums.org/attachment.php?attachmentid=114934&stc=1&d=1243150077)

[http://ubuntuforums.org/attachment.php?attachmentid=114935&stc=1&d=1243150077](http://ubuntuforums.org/attachment.php?attachmentid=114935&stc=1&d=1243150077)

Y aca la config de la conexion : [http://ubuntuforums.org/attachment.php?attachmentid=114936&stc=1&d=1243150077](http://ubuntuforums.org/attachment.php?attachmentid=114936&stc=1&d=1243150077)

---

### Post by guillermolisi on 2009-05-24
> **Polacko85 said:**
> No nada mira :icon_frown: : 

Este es la info de la conexion en un pantalllaso: [http://ubuntuforums.org/attachment.php?attachmentid=114933&stc=1&d=1243171529](http://ubuntuforums.org/attachment.php?attachmentid=114933&stc=1&d=1243171529)

Aca el FIREFOX : [http://ubuntuforums.org/attachment.php?attachmentid=114934&stc=1&d=1243150077](http://ubuntuforums.org/attachment.php?attachmentid=114934&stc=1&d=1243150077)

[http://ubuntuforums.org/attachment.php?attachmentid=114935&stc=1&d=1243150077](http://ubuntuforums.org/attachment.php?attachmentid=114935&stc=1&d=1243150077)

Y aca la config de la conexion : [http://ubuntuforums.org/attachment.php?attachmentid=114936&stc=1&d=1243150077](http://ubuntuforums.org/attachment.php?attachmentid=114936&stc=1&d=1243150077)
Mmmm ... me parece que algo falta ...
Como sabes que la conexion a Internet se establece bien ?

La asignacion de IPs en eth0 parece correcta pero como asegurar/saber que el modem se conecto a Internet ?

Te fijaste en la pantalla de monitoreo del modem (tenes que entrar con un web browser segun te indique su manual). Ahi deberia decirte si se conecto o no a su red (externa) o si hubo algun problema (usuario / password incorrectos).

---

### Post by josecuervo86 on 2009-05-24
Yo tengo exactamente ese mismo modem (y no, no es el alfajor del diablo, ese es el MT810) y lo configure siempre exitosamente con pppoeconf. Proba hacerlo nuevamente.

---

