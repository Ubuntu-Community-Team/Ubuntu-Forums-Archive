---
title: "trafico en la red"
date: 2009-07-23
forum: Hardware
---

### Post by elgato_sec on 2009-07-23
Hola gente, soy nuevo en Ubuntu y también en el foro. he bajado todos los servicios que conozco que utilizan la red pero el trafico entrante o (de bajada o Rx) esta en una media de 13Kb constante en ningún momento deja de haber trafico. A alguien ya le pasó? saben que puede ser? yo estoy tratando de ver pero sigo sin saber porque tanto ancho de banda usado "pasivamente" instale ntop pero no veo mas que los proveedores de mi servicio. Aclaración no tengo router wireless. 
        saludos!

---

### Post by aledruetta on 2009-07-23
Quizá con nmap o zenmap podrías ver si hay algún puerto que no debería estar abierto. Como para ir descartando posibles intrusos.

---

### Post by aledruetta on 2009-07-23
Otra herramienta que podrías investigar es:

```
sudo aptitude install iptraf
```

---

### Post by guillermolisi on 2009-07-23
> **elgato_sec said:**
> Hola gente, soy nuevo en Ubuntu y también en el foro. he bajado todos los servicios que conozco que utilizan la red pero el trafico entrante o (de bajada o Rx) esta en una media de 13Kb constante en ningún momento deja de haber trafico. A alguien ya le pasó? saben que puede ser? yo estoy tratando de ver pero sigo sin saber porque tanto ancho de banda usado "pasivamente" instale ntop pero no veo mas que los proveedores de mi servicio. Aclaración no tengo router wireless. 
        saludos!

Danos algo de detalle respecto de que tipo de conexion a Internet estas usando y que tenes instalado en tu maquina. Por ejemplo, pusiste a funcionar algun servidor web, FTP, mail, etc. ?

Usas algun software para redes P2P como aMule, alguno para Torrents, etc. ?

Probar con nmap seria un buen comienzo para empezar a tener informacion.

---

### Post by elgato_sec on 2009-07-23
les cuento baje todos los servicios, tanto el apache, el mysql, cerre los torrents realize el nmap nuevamente y me sale estos errores, tampoco dejo de recibir kb, adjunto una imagen

-------
Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-07-23 19:41 ART
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
SCRIPT ENGINE: '/usr/share/nmap/scripts/skype_v2-version.nse' threw a run time error and could not be loaded.
SCRIPT ENGINE: '/usr/share/nmap/scripts/iax2Detect.nse' threw a run time error and could not be loaded.
SCRIPT ENGINE: '/usr/share/nmap/scripts/PPTPversion.nse' threw a run time error and could not be loaded.
All 1000 scanned ports on localhost (127.0.0.1) are closed
--------

Instale como recomendaron el iptraf y me sale esto, la media se mantiene en 0.8 aprox. 
Pregunra: puede que el monitor de sistema diga cualquier cosa??? de donde recoge la data para haber tanta diferencia??

 IPTraf
&#9484; Iface &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; Total &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; IP &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; NonIP &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; BadIP &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; Activity &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; lo                       0               0               0             0            0,00 kbits/sec                        &#9474;
&#9474; eth0                     0               0               0             0            0,00 kbits/sec                        &#9474;
&#9474; eth1                  2653            2653               0             0            1,40 kbits/sec                        &#9474;
&#9474;                                                                                                      


gracias por responder tan rápido!

---

### Post by guillermolisi on 2009-07-23
Por que nmap te dice que detecto dos IPs para el mismo host ?

Y los detalles de la conexion ?

Bajaste esos servidores, pero seguias con Skype ... no tendras algo mas funcionando y recibiendo paquetes desde Internet ?

nmap no te dio mas informacion que esa que mostras ?

---

### Post by elgato_sec on 2009-07-24
Solo eso, no el skype esta cerrado, no tengo nada de servicios en ese momento, ni firefox abiertos, nada de nada. la info completa del nmap es:

------
Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-07-24 01:31 ART
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
SCRIPT ENGINE: '/usr/share/nmap/scripts/skype_v2-version.nse' threw a run time error and could not be loaded.
SCRIPT ENGINE: '/usr/share/nmap/scripts/iax2Detect.nse' threw a run time error and could not be loaded.
SCRIPT ENGINE: '/usr/share/nmap/scripts/PPTPversion.nse' threw a run time error and could not be loaded.
All 1000 scanned ports on localhost (127.0.0.1) are closed

Service detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 0.40 seconds

------

Es completa la que dí, le faltaban las tres lineas de abajo. Lo que no entiendo porque iptraf da como maximo 1.4 KB y el monitor da minimo 11 KB. hace un rato había subido un poco más llego a picos de 21KB en el monitor mientras en el iptraf seguía en razón de 1.4,1.6 KB

de antemano gracias!!

---

### Post by guillermolisi on 2009-07-24
Como corriste nmap, con que opciones ?

Proba con ```
nmap -A <ip_del_host>
```Seria ideal que lo pudieras hacer desde otra maquina, fuera de tu red, donde deberias reemplazar <ip_del_host> por la IP publica que tengas asignada al momento del scanning.

Te deberia dar un aviso de cuantos puertos encuentra cerrados y una lista de los que encuentra abiertos.

---

### Post by Mister X on 2009-07-24
fijate que un core está constatemente al 100%, fijate que proceso esta comiendo procesador, tal vez sea el responsable del trafico de red

---

### Post by faktorqm on 2009-07-26
Para ver a quienes tenes escuchando y en que puerto, podes usar 

```
netstat -a
```

Para ver cuanto trafico estas consumiendo por interfaz, yo utilizo el comando "iftop", que es como el top pero para interfaces de red. El paquete se llama igual que el comando, si es que no lo tenes instalado.

Salu2!

---

### Post by sergiom99 on 2009-07-26
> **elgato_sec said:**
> 
Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-07-24 01:31 ART
Warning: *_**[COLOR="Red"]Hostname localhost resolves to 2 IPs[/COLOR]**_*. Using 127.0.0.1.


Esto que significa?
Con que parametros y opciones corres el nmap?

-Sergio

---

### Post by hictio on 2009-07-26
A mi personalmente para estos casos me gusta [iftop](http://www.ex-parrot.com/pdw/iftop/), te muestra (como netstat) qué es lo que está usando el ancho de banda, y además de eso, cuánto.

Acá hay un link con otras herramientas: [Bandwidth Monitoring Tools for Ubuntu Users](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html)

---

