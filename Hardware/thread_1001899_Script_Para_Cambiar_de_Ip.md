---
title: "Script Para Cambiar de Ip"
date: 2008-12-04
forum: Hardware
---

### Post by NickCis on 2008-12-04
Bueno, antes en Xp yo usaba un archivo BAT, para que me cambie la ip de internet (para seguir bajando archivos que alojados en sitios como Rapidshare, megaupload, etc)

El comando de este bat es este
```

@echo off

ipconfig/release

netsh interface IP set address "Conexion de area local" static 1.2.3.4 255.0.0.0 1.3.4.5 0

netsh interface IP set address "Conexion de area local" dhcp

ping www.google.com

ping www.taringa.net

ping www.hotmail.com

close

```

Creo que lo que hace basicamente es, cambiar la configuracion de la placa de red (qe esta por dhcp) a estatica, dsp devuleta a dhcp y los ultimos pings, me parece que son para poner un delay o probar si hay internet.

Es posible hacer uno para linux?, como lo hago?.

Saludos.

---

### Post by rodolfojavier1982 on 2008-12-04
Bueno, te cuento lo que yo hago, no es muy cool pero funciona, cada vez que termino de descargar algo de alguno de esos sitios me desconecto y me vuelvo a conectar a internet, y ya se me cambio el ip.
Si a alguien le sirve, bienvenido sea...

---

### Post by Applelnx on 2008-12-04
La IP no depende de tu ISP? Solo si tenes IP dinamica la podrias llegar a cambiar, yo nunca pude.

---

### Post by c4d0rn4 on 2008-12-04
vos tenías que windows marcaba por ppoe o algo así no?

en realidad el secreto del bat es ipconfig/release
 y lo más común después es ipconfig/renew

[www.techtalkies.com/2006/06/27/rapidshare-hacking-rapidshare-tips-and-tricks-2/](www.techtalkies.com/2006/06/27/rapidshare-hacking-rapidshare-tips-and-tricks-2/)

En una busqueda rápida de cual sería el equivalente en linux encontré esto, por ahí para comenzar sirve
[http://blogs.pingpoet.com/overflow/archive/2005/12/04/15739.aspx](http://blogs.pingpoet.com/overflow/archive/2005/12/04/15739.aspx)
[http://sidewynder.blogspot.com/2005/08/linux-equivalent-of-ipconfig-release.html](http://sidewynder.blogspot.com/2005/08/linux-equivalent-of-ipconfig-release.html)

Vislumbro que podrías a llegar a tener problema con el tema de ser root, lo cual para automatizar podría, como última solución, usar sudoers, pero ya escapa a mis conocimientos.


@ Applelnx, es cierto, depende del isp; pero es MUY raro tener una conexión de ip fija. Pero si ya hizo eso en xp, es evidentemente tiene una ip dinamica.

---

### Post by hictio on 2008-12-04
> **NickCis said:**
> Bueno, antes en Xp yo usaba un archivo BAT, para que me cambie la ip de internet (para seguir bajando archivos que alojados en sitios como Rapidshare, megaupload, etc)

El comando de este bat es este
```

@echo off

ipconfig/release

netsh interface IP set address "Conexion de area local" static 1.2.3.4 255.0.0.0 1.3.4.5 0

netsh interface IP set address "Conexion de area local" dhcp

ping www.google.com

ping www.taringa.net

ping www.hotmail.com

close

```

Creo que lo que hace basicamente es, cambiar la configuracion de la placa de red (qe esta por dhcp) a estatica, dsp devuleta a dhcp y los ultimos pings, me parece que son para poner un delay o probar si hay internet.

Es posible hacer uno para linux?, como lo hago?.

Saludos.

Que ISP tenes? Normalmente, por mas que la desconectes/ apagues, si la volves a conectar la maquina va a seguir usando el mismo IP porque el DHCP que lo asigna va a ver el mismo MAC address de tu tarjeta de red.
La solucion es apagarla un rato, y volver a conectarla, pero nuevamente, depende de que cuantos requests hubo en el servidor DHCP que te asigna IP, quizas te toca la misma.

De todas formas, los sitios de descargas que vos decis no bloquean todo el segmento del pais? Por mas que te obtengas un IP nuevo, sigue siendo de Argentina.

---

### Post by c4d0rn4 on 2008-12-04
Para nada hictio, con rapidshare se puede bajar cuanto uno quiera.

En lo personal tengo un router muy comun, que está dentro los que ofrece jdownloader. Cada vez que me desconecto me da un ip nueva y descargo un archivo tras otro y sin preocuparme de nada

---

### Post by NickCis on 2008-12-07
La verdad no se como hacia con Xp, pero la explicacion, segun lo que tengo entendido, es que cuando reinicias el modem o reconectas, este guarda que ip tenias antes, y le pide la misma al Dhcp (o algo por el estilo). Pero al desconectar (ipconfig /release), configurar la ip por una estatica, y despues volver a pedir la ip, se te asigna una nueva. Muy seguro no estoy de esto,,, es solo una teoria de alguna pagina.

Encontre info de esto en Taringa ( [http://taringa.net/posts/linux/1645302/Descargar-de-Rapidshare-y-Megaupload---Ubuntu.html](http://taringa.net/posts/linux/1645302/Descargar-de-Rapidshare-y-Megaupload---Ubuntu.html) ), mañana pruebo eso a ver que onda, si alguien qiere adelantarse, cuenteme sus experiencias.

Saludos.

P.D.: Mi ISP es multicanal, (creo que estan trabajando Flash, o Fiberterl, ni idea bien cual). Tengo cablemodem, y si es dinamica, la cambia cuando quiere, pero es dinamica xD.

---

### Post by c4d0rn4 on 2008-12-08
> Ahora creamos un "lanzador" o "Enlace a aplicación" en el escritorio, en orden ponemos jdownloader, y en opciones avanzadas (esto es en KUbuntu, no recuerdo como era en Ubuntu) eligen ejecutar como otro usuario y le ponen root. Esto es para que el programa pueda ejecutar sin problemas el cambio de IP, ya que se necesitan permisos de superusuario para realizarlo. 

Me suena a que los archivos que bajes van a ser del root y para manejarlos vas a tener que cambiarles los permisos.

igual eso soluciona el problema de ejecutar ese script y tener que poner el pass siempre. Tengo entendido que algo más exquisito sería crear una excepción para ese bash y que se ejecute como root.

---

### Post by faktorqm on 2008-12-09
Yo conozco el macchanger, no se que tanto les sirva... capaz a los de fibertel no les sirve tanto...

[http://www.alobbs.com/macchanger/](http://www.alobbs.com/macchanger/)

```
faktorqm@the-edge:~$ apt-cache search macchanger
macchanger - utility for manipulating the MAC address of network interfaces
macchanger-gtk - a GTK+ interface for GNU/MACchanger
faktorqm@the-edge:~$
```

Salu2!!!

---

### Post by User21 on 2008-12-09
Yo uso el macchanger, y acto seguido reinicio el servidor de red y voilá!
Sino, simplemente renovar IP desde el control web del modem que estes usando.

---

### Post by guisheca on 2008-12-09
Verán, este es el que usaba para un modem huawei smartax mt882, lo cree yo mismo y no se nada de scripting, así que el que sepa lo puede mejorar ya que tiene algunas limitaciones que no supe sobrellevar.

```
#!/bin/bash
firefox "http://10.0.0.2/GenAction?MacWanUsrName=******%40arnet-res-glc&MacWanPasswd=********&ex_param1=8&MacWanBdgEn=0&MacWanIgmpEn=1&MacWanUseDns=1&MacWanGwIp=0.0.0.0&MacWanNetMask=0.0.0.0&MacWanIpAddr=0.0.0.0&prim_serv=0.0.0.0&sec_serv=0.0.0.0&MacWanVcEn=1&MacWanEncaps=3&sec_proto=0&MacWanVci=33&MacWanVpi=0&MacWanDhcpClEn=0&MacWanDefRtEn=1&MacWanNatEn=1&mtu=1492&trf_index=0&id=13&b2"
firefox "http://10.0.0.2/GenAction?MacWanUsrName=******%40arnet-res-glc&MacWanPasswd=*********&ex_param1=8&MacWanBdgEn=0&MacWanIgmpEn=1&MacWanUseDns=1&MacWanGwIp=0.0.0.0&MacWanNetMask=0.0.0.0&MacWanIpAddr=0.0.0.0&prim_serv=0.0.0.0&sec_serv=0.0.0.0&MacWanVcEn=1&MacWanEncaps=3&sec_proto=0&MacWanVci=33&MacWanVpi=0&MacWanDhcpClEn=0&MacWanDefRtEn=1&MacWanNatEn=1&mtu=1492&trf_index=0&id=12&b1"
```

Paso a explicar como lo hice:
Existe una extensión para firefox (cuando no) llamada tamper data, cuando se la activa lo que hace es tirarte el enlace de lo que sea que aprietes en el firefox, quiere decir, que nos tira el enlace del botón "desconectar" del panel de control del modem-router. Con lo cual resta colocar ese enlace en la barra de direcciones para que el modem corte la señal de internet. Lo mismo hacemos para el boton "conectar".
Al final del proceso obtendremos sendos enlaces que colocados en un navegador cualquiera nos conectará o desconectará de internet según necesitemos. Con esa información elaboré el rudimentario script que puse arriba. 

Cuando hablaba de limitaciones me refería a que es necesario mantener abierto firefox para que sea automático, de otra forma el script se ejecuta a medias y necesita atención del usuario.

Hay tutoriales acerca de como usar el tamper data para estos fines.

Al principio dije que este script es el que "usaba" porque ahora creo que ya no hace falta, además ya no tengo mas el modem huawei jejeje y me da fiaca repetir el proceso para el router que tengo ahora.

Saludos

---

### Post by Hernán-Amaya on 2008-12-11
Si querés renovar la ip para bajar cosas de rapishare, megaupload y sitios similares te conviene usar el jdownloader anda de lujo. Si no es para esto ignorá lo anterior.

---

### Post by NickCis on 2008-12-22
La solucion qe se posteo en taringa [http://taringa.net/posts/linux/1645302/Descargar-de-Rapidshare-y-Megaupload---Ubuntu.html](http://taringa.net/posts/linux/1645302/Descargar-de-Rapidshare-y-Megaupload---Ubuntu.html)
Anda perfecto, claro nececitas tener permisos de root. Pero, si lo que nececitas es que un programa lo ejecute, la solucion esta en abrir el programa con privilegios de root y listo.

Ahora lo que estaria buscando es como hacer para cambiar la ip, estando conectado a internet atraves de router.
La internet es DHCP, como es eso de cambiarle el mac addres??, se lo tendria que cambiar al modem o al router?.

Saludos.

---

