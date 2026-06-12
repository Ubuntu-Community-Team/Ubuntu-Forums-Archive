---
title: "Problemas con el gestor de actualizaciones"
date: 2009-10-04
forum: Instalación y Actualización
---

### Post by darkimedez on 2009-10-04
hola a todos. Eso, cuando aparece el icono de actualizaciones disponibles, hago click para que ubuntu haga lo suyo pero me manda un error en una ventana emergente que versa en español:

[COLOR=Red][I]No se han podido descargar todos los índices de los repositorios

El repositorio puede no estar disponible, o no se ha podido conectar con él debido a algún problema con la red. Si está disponible, se usará una versión anterior del índice erróneo. En caso contrario, el repositorio será ignorado. Compruebe la conexión de su red y verifique que la dirección del repositorio en las preferencias es la correcta.[/I][/COLOR]

luego en la misma ventana más abajo, dice en ingles:

[COLOR=Red]*Problem executing scripts APT::Update::Pre-Invoke 'fi”'Sub-process returned an error code*[/COLOR]

No se que puedo hacer, ojala puedan ayudarme.

Saludos.

---

### Post by Patriciologico on 2009-10-05
Hola darkimedez, bienvenido al foro.

 Para una correcta participación en el foro debes leer las normas (esta el enlace en mi firma) y ver en cada sección el aviso sobre que puedes publicar en cada lugar) En este caso tu problema va claramente en la sección "Instalación y Actualización" por lo que ha sido movido.

 Todo esto en favor del orden y una mas pronta respuesta a tu problema.

Saludos.

---

### Post by themasterdark on 2009-10-05
Hola

quizás este caído algún repositorio, en un terminal 

escribe:

> sudo apt-get update

en caso de haber alguno caído, te dirá que no pudo descargar el índice de paquetes, para que no siga buscando en ese repositorio debes o comentarlo o eliminarlo de sources.list (el archivo donde se guardan las direcciones de cada uno de los repositorios de tu sistema) se puede hacer de esta forma:

> sudo gedit /etc/apt/sources.list

fijate en las direcciones que estaban caidas, y elimina la linea completa ó comentala poniendo delante un #, luego guarda el archivo y repite en un terminal


> sudo apt-get update

con eso se debería solucionar.

Saludos =D

---

### Post by darkimedez on 2009-10-05
cuando hago eso, me parece en el codigo:
[COLOR=Red]Already have key E2314809 for archive ppa by ~bjfs
DONE
sh: fi”: not found
E: Problem executing scripts APT::Update::Pre-Invoke 'fi”'
E: Sub-process returned an error code
[/COLOR]
que es mas o menos lo mismo q me aparecia denante pero en la terminal.

se supone que aqui es donde debia haber chillado por un repositorio??

gracias por las posibles respuestas.

---

### Post by themasterdark on 2009-10-05
por lo que entiendo del ingles xD

> Already have key E2314809 for archive ppa by ~bjfs

dice que ya tienes la clave tanto E2314809 .... mmm...
postea tu sources.list para ver que le pasa al endemoniado jaja
(esa es la key del repositorio emesene en ppa creo...)

---

### Post by darkimedez on 2009-10-05
aca te mando el sources.list de mi compu:
[I][COLOR=Red]
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) jaunty main
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse[/COLOR][/I]

gracias por la lata xD.

---

### Post by themasterdark on 2009-10-05
mmmmmm... al parecer no tiene nada pero... prueba 

comentado 

> deb [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) jaunty main


que quede asi

> #deb [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) jaunty main
#deb-src [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) jaunty main

y luego haz sudo apt-get update

Saludos

---

### Post by darkimedez on 2009-10-05
no paso nada :(

---

### Post by Carlos C on 2009-10-06
Cuando dices que no paso nada ¿qué significa? Luego de comentar y hacer el "sudo apt-get update" ¿te sigue saliendo el mismo error? ¿Estás seguro que comentaste esas dos lineas? No deberías tener el mismo error si el repositorio ya no está en tu sources.list

---

### Post by darkimedez on 2009-10-06
al parecer el cambio q debia efectuar era anteponer gato en ambas lineas. pues lo hice y me manda el mismo error.

pdta: que significa exactamente "comentar"?

---

### Post by themasterdark on 2009-10-06
comentar significa poner un # delante de la linea, de esa forma no es tomada en cuenta, se toma solo como un comentario... 
que extraño que el problema persista, veré algo escribo mas tarde que ahora estoy en la U. 

Saludos.

---

### Post by darkimedez on 2009-10-07
vale gracias!

---

### Post by themasterdark on 2009-10-07
Hola... leia informacion y al parecer es un bug en apt-get
bueno... mira te paso el link de un script que se encarga de solucionar los problemas de los repositorios ppa.

[http://www.mediafire.com/download.php?wmyjzfdqfgy](http://www.mediafire.com/download.php?wmyjzfdqfgy)

ejecutalo... con un 

> chmod +x launchpad-update
> sudo ./launchpad-update

espera que termine el proceso, y haz un 

> sudo apt-get update

y vee que pasa, espero funcione, saludos =)

---

### Post by darkimedez on 2009-10-08
mira, pasa q soy igual nuevo en ubuntu y no entiendo todo el modo de operar sobretodo en la terminal, intente hacer lo que me dijiste pero se quedo pensando mas de tres horas asi q decidi suspender el proceso. quizas no hice bien algo, creo que no se que hacer con lo que baje del link q me mandaste del posteo anterior porque luego de descargarlo, no hice nada con el.

saludos y muchas gracias.

---

### Post by themasterdark on 2009-10-08
aaa mira te cuento...
el archivito q te pase, comprueba que esten bien todas las llaves de autentificacion de los repositorios ppa.. como el que tienes tu, que mencione comentaras... 

el archivo primero que nada debes darle permsisos de ejecucion, es decir con el comando "chmod" cambias que es lo hace el archivo, que sea ejecutable, quienes lo leen etc... 
para esta ocasion solo importa darle los permisos de ejecucion asi:
> chmod +x launchpad-update

luego, para ejecutar un archivo en una terminal se escribe:

> sh nombre_del_archivo ó ./nombre_del_archivo

bueno, lo que te menciono es que lo ejecutes con privilegios de administrador, por ello el comando sudo, que realiza la peticion de esos privilegios, para el archivo que te deje seria:

> sudo ./launchpad-update

dejarlo que termine el proceso por si solo... y luego de eso realizar una actualizacion de los paquetes de tus repositorios (saber que hay en tus repositorios y ver si tienes las llaves de autentificacion) con:

> sudo apt-get update


pd: todo lo antes mencionado en un terminal/consola, espero me entendieras mejor, también menciones si el problema persiste
Saludos

---

### Post by darkimedez on 2009-10-09
mismo error :confused:

---

### Post by Carlos C on 2009-10-10
Ahora que tienes esas lineas comentadas, ¿podrías copiar acá el error exacto que te está dando?

Te sugiero que trates de dar más información cuando respondas, escribir que te da el mismo error no dice mucho, siempre debes decir lo que hiciste y cualquier respuesta o mensaje del sistema (incluso si no hay respuesta alguna también debes decirlo), ya que eres el único frente al computador y los demás necesitan comprender lo que está pasando gracias a lo que informas.

---

### Post by darkimedez on 2009-10-15
Gracias por la recomendacion, pero es q crei q quedaba claro que seguia ocurriendo el mismo problema q origino el tema en el foro.

Aca mando el error que me sigue molestando:
[COLOR=Red]
Problem executing scripts APT::Update::Pre-Invoke 'fi”'Sub-process returned an error code[/COLOR]

Saludos.

---

### Post by lobosorno on 2009-11-01
amigos....sou nuevo en ubuntu, y por lo mismo creo ke la embarré en forma grave....cuando kise actualizar al karmic, me decía ke me faltaba espacio....y por tratar de hacer otras cosas después, me metí en el siguiente forro...necesito de su ayuda:

[IMG]file:///home/juanubuntu/Escritorio/Pantallazo.png[/IMG]"error al comprobar las aplicaciones instaladas y disponibles

este es un fallo importante en su sistema de gestion de software. por favor, compruebe si existen paquetes rotis con synaptic, compruebe los permisos y la corrección del archivo "/etc/apt/sources.list" y vuelva a cargar la informacion del software con "sudo apt-get update" y "sudo apt-get install-f"

el problema es ke ahora no puedo actualizar paquetes ni acceder a synaptic...

saludos, y gracias desde ya

---

### Post by Carlos C on 2009-11-02
> **lobosorno said:**
> amigos....sou nuevo en ubuntu, y por lo mismo creo ke la embarré en forma grave....cuando kise actualizar al karmic, me decía ke me faltaba espacio....y por tratar de hacer otras cosas después, me metí en el siguiente forro...necesito de su ayuda:

[IMG]file:///home/juanubuntu/Escritorio/Pantallazo.png[/IMG]"error al comprobar las aplicaciones instaladas y disponibles

este es un fallo importante en su sistema de gestion de software. por favor, compruebe si existen paquetes rotis con synaptic, compruebe los permisos y la corrección del archivo "/etc/apt/sources.list" y vuelva a cargar la informacion del software con "sudo apt-get update" y "sudo apt-get install-f"

el problema es ke ahora no puedo actualizar paquetes ni acceder a synaptic...

saludos, y gracias desde ya
Estimado, tengo la impresión de que tu problema es diferente al del amigo que inició este thread. Te pido que abras un thread nuevo en el sub foro adecuado, en donde des toda la información necesaria para poder ayudarte.

En caso de dudas puedes leer [aquí]("http://ubuntuforums.org/showthread.php?t=1162750").

Saludos.

---

### Post by VonlisT on 2009-11-02
No sé exactamente a que se debe, pero intenta lo siguiente:
Ve a Sistema - Orígenes del software. y anda a la ficha Autenticación, busca la llave [COLOR=Red]E2314809 [COLOR=Black]y quítala, luego haz un: sudo apt-get update
No creo que sea problema con los repositorios, la cosa va por la autentificación de un paquete.

Espero haberte ayudado, saludos.
[/COLOR][/COLOR]

---

### Post by darkimedez on 2009-11-22
Puues ya estaba harto del problema, tenia 100 dias sin poder actualizar y tampoco me dejaba avanzar al karmic koala. consulte a un amigo y formatie mi compu instalando otra version de linux llamada mint, me va muy bien con ella y no he tenido absolutamente ningun problema.

Saludos, dario

---

### Post by javierfigueroa on 2012-02-14
Cuando quiero ir al gestor de actualizaciones o gestor de paquetes synaptic me aparece el siguiente error:

No se ha podido inicializar la información de los paquetes

Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Línea 1 mal formada en lista de fuentes /etc/apt/sources.list.d/pidgin-ppa.list (análisis de dist)'


Alguien me puede ayudar?

He copiado en la terminal algunos comandos, y también me aparecen errores:

323 actualizados, 0 se instalarán, 0 para eliminar y 5 no actualizados.
Se necesita descargar 101MB/320MB de archivos.
Se utilizarán 11,4MB de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libfreetype6 amd64 2.4.2-2ubuntu0.2
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main sysvinit-utils amd64 2.87dsf-4ubuntu19.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main sysv-rc all 2.87dsf-4ubuntu19.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libpam0g amd64 1.1.1-4ubuntu2.3
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libpam-modules amd64 1.1.1-4ubuntu2.3
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main initscripts amd64 2.87dsf-4ubuntu19.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main language-pack-es all 1:10.10+20101204
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main language-pack-gnome-es all 1:10.10+20101204
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libxml2 amd64 2.7.7.dfsg-4ubuntu0.2
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main apt amd64 0.8.3ubuntu7.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libssl0.9.8 amd64 0.9.8o-1ubuntu4.4
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libpam-runtime all 1.1.1-4ubuntu2.3
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main apt-utils amd64 0.8.3ubuntu7.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main dhcp3-client amd64 3.1.3-2ubuntu6.2
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main dhcp3-common amd64 3.1.3-2ubuntu6.2
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libk5crypto3 amd64 1.8.1+dfsg-5ubuntu0.7
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libgssapi-krb5-2 amd64 1.8.1+dfsg-5ubuntu0.7
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libkrb5-3 amd64 1.8.1+dfsg-5ubuntu0.7
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libkrb5support0 amd64 1.8.1+dfsg-5ubuntu0.7
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libldap-2.4-2 amd64 2.4.23-0ubuntu3.5
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libcurl3-gnutls amd64 7.21.0-1ubuntu1.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main apt-transport-https amd64 0.8.3ubuntu7.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main dnsutils amd64 1:9.7.1.dfsg.P2-2ubuntu0.4
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main bind9-host amd64 1:9.7.1.dfsg.P2-2ubuntu0.4
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libisc60 amd64 1:9.7.1.dfsg.P2-2ubuntu0.4
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libdns66 amd64 1:9.7.1.dfsg.P2-2ubuntu0.4
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libisccc60 amd64 1:9.7.1.dfsg.P2-2ubuntu0.4
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libisccfg60 amd64 1:9.7.1.dfsg.P2-2ubuntu0.4
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main liblwres60 amd64 1:9.7.1.dfsg.P2-2ubuntu0.4
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libbind9-60 amd64 1:9.7.1.dfsg.P2-2ubuntu0.4
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main update-manager all 1:0.142.23
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main update-manager-core amd64 1:0.142.23
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main app-install-data-partner all 12.10.10.3
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libwebkit-1.0-common all 1.2.5-0ubuntu0.10.10.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libwebkit-1.0-2 amd64 1.2.5-0ubuntu0.10.10.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libcups2 amd64 1.4.4-6ubuntu2.3
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main cups-common all 1.4.4-6ubuntu2.3
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main cups-bsd amd64 1.4.4-6ubuntu2.3
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libcupsimage2 amd64 1.4.4-6ubuntu2.3
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main cups-client amd64 1.4.4-6ubuntu2.3
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libnss3-1d amd64 3.12.9+ckbi-1.82-0ubuntu0.10.10.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main nautilus-sendto-empathy amd64 2.32.1-0ubuntu1.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main empathy amd64 2.32.1-0ubuntu1.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main empathy-common all 2.32.1-0ubuntu1.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libevdocument3 amd64 2.32.0-0ubuntu1.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libevview3 amd64 2.32.0-0ubuntu1.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main evince-common all 2.32.0-0ubuntu1.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main evince amd64 2.32.0-0ubuntu1.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main firefox-gnome-support amd64 3.6.18+build2+nobinonly-0ubuntu0.10.10.2
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main firefox-branding amd64 3.6.18+build2+nobinonly-0ubuntu0.10.10.2
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main firefox amd64 3.6.18+build2+nobinonly-0ubuntu0.10.10.2
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main gdb amd64 7.2-1ubuntu3
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libcupscgi1 amd64 1.4.4-6ubuntu2.3
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libcupsdriver1 amd64 1.4.4-6ubuntu2.3
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libcupsmime1 amd64 1.4.4-6ubuntu2.3
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libcupsppdc1 amd64 1.4.4-6ubuntu2.3
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libcurl3 amd64 7.21.0-1ubuntu1.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libpurple-bin all 1:2.7.3-1ubuntu3.2
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main libxml2-utils amd64 2.7.7.dfsg-4ubuntu0.2
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-firmware all 1.38.6
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-libc-dev amd64 2.6.35-1030.56
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main xulrunner-1.9.2 amd64 1.9.2.18+build2+nobinonly-0ubuntu0.10.10.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main icedtea6-plugin amd64 6b20-1.9.9-0ubuntu1~10.10.2
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main icedtea-6-jre-cacao amd64 6b20-1.9.9-0ubuntu1~10.10.2
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main openjdk-6-jre-lib all 6b20-1.9.9-0ubuntu1~10.10.2
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main openjdk-6-jre-headless amd64 6b20-1.9.9-0ubuntu1~10.10.2
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main openjdk-6-jre amd64 6b20-1.9.9-0ubuntu1~10.10.2
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main openssl amd64 0.9.8o-1ubuntu4.4
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main python-libxml2 amd64 2.7.7.dfsg-4ubuntu0.2
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main python-papyon all 0.5.1-0ubuntu2
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main software-center all 3.0.9
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main xul-ext-ubufox all 0.9~rc2-0ubuntu5.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main ubufox all 0.9~rc2-0ubuntu5.1
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main xserver-common all 2:1.9.0-0ubuntu7.3
  404  Not Found
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main xserver-xorg-core amd64 2:1.9.0-0ubuntu7.3
  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.4.2-2ubuntu0.2_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.4.2-2ubuntu0.2_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/sysvinit-utils_2.87dsf-4ubuntu19.1_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/sysvinit-utils_2.87dsf-4ubuntu19.1_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/sysv-rc_2.87dsf-4ubuntu19.1_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/sysv-rc_2.87dsf-4ubuntu19.1_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-4ubuntu2.3_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-4ubuntu2.3_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-4ubuntu2.3_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-4ubuntu2.3_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.87dsf-4ubuntu19.1_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.87dsf-4ubuntu19.1_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-es/language-pack-es_10.10+20101204_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-es/language-pack-es_10.10+20101204_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-es/language-pack-gnome-es_10.10+20101204_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-es/language-pack-gnome-es_10.10+20101204_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.7.7.dfsg-4ubuntu0.2_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.7.7.dfsg-4ubuntu0.2_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.8.3ubuntu7.1_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.8.3ubuntu7.1_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8o-1ubuntu4.4_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8o-1ubuntu4.4_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-4ubuntu2.3_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-4ubuntu2.3_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.8.3ubuntu7.1_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.8.3ubuntu7.1_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-client_3.1.3-2ubuntu6.2_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-client_3.1.3-2ubuntu6.2_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-common_3.1.3-2ubuntu6.2_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-common_3.1.3-2ubuntu6.2_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libk5crypto3_1.8.1+dfsg-5ubuntu0.7_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libk5crypto3_1.8.1+dfsg-5ubuntu0.7_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libgssapi-krb5-2_1.8.1+dfsg-5ubuntu0.7_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libgssapi-krb5-2_1.8.1+dfsg-5ubuntu0.7_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-3_1.8.1+dfsg-5ubuntu0.7_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-3_1.8.1+dfsg-5ubuntu0.7_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5support0_1.8.1+dfsg-5ubuntu0.7_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5support0_1.8.1+dfsg-5ubuntu0.7_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/o/openldap/libldap-2.4-2_2.4.23-0ubuntu3.5_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/o/openldap/libldap-2.4-2_2.4.23-0ubuntu3.5_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3-gnutls_7.21.0-1ubuntu1.1_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3-gnutls_7.21.0-1ubuntu1.1_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.8.3ubuntu7.1_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.8.3ubuntu7.1_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.7.1.dfsg.P2-2ubuntu0.4_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.7.1.dfsg.P2-2ubuntu0.4_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.7.1.dfsg.P2-2ubuntu0.4_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.7.1.dfsg.P2-2ubuntu0.4_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc60_9.7.1.dfsg.P2-2ubuntu0.4_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc60_9.7.1.dfsg.P2-2ubuntu0.4_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns66_9.7.1.dfsg.P2-2ubuntu0.4_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns66_9.7.1.dfsg.P2-2ubuntu0.4_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc60_9.7.1.dfsg.P2-2ubuntu0.4_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc60_9.7.1.dfsg.P2-2ubuntu0.4_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg60_9.7.1.dfsg.P2-2ubuntu0.4_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg60_9.7.1.dfsg.P2-2ubuntu0.4_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres60_9.7.1.dfsg.P2-2ubuntu0.4_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres60_9.7.1.dfsg.P2-2ubuntu0.4_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-60_9.7.1.dfsg.P2-2ubuntu0.4_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-60_9.7.1.dfsg.P2-2ubuntu0.4_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.142.23_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.142.23_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.142.23_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.142.23_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-partner/app-install-data-partner_12.10.10.3_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-partner/app-install-data-partner_12.10.10.3_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/w/webkit/libwebkit-1.0-common_1.2.5-0ubuntu0.10.10.1_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/w/webkit/libwebkit-1.0-common_1.2.5-0ubuntu0.10.10.1_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/w/webkit/libwebkit-1.0-2_1.2.5-0ubuntu0.10.10.1_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/w/webkit/libwebkit-1.0-2_1.2.5-0ubuntu0.10.10.1_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.4.4-6ubuntu2.3_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.4.4-6ubuntu2.3_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.4.4-6ubuntu2.3_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.4.4-6ubuntu2.3_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.4.4-6ubuntu2.3_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.4.4-6ubuntu2.3_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.4.4-6ubuntu2.3_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.4.4-6ubuntu2.3_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.4.4-6ubuntu2.3_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.4.4-6ubuntu2.3_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.9+ckbi-1.82-0ubuntu0.10.10.1_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.9+ckbi-1.82-0ubuntu0.10.10.1_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.32.1-0ubuntu1.1_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.32.1-0ubuntu1.1_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.32.1-0ubuntu1.1_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.32.1-0ubuntu1.1_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_2.32.1-0ubuntu1.1_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_2.32.1-0ubuntu1.1_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevdocument3_2.32.0-0ubuntu1.1_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevdocument3_2.32.0-0ubuntu1.1_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevview3_2.32.0-0ubuntu1.1_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevview3_2.32.0-0ubuntu1.1_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince-common_2.32.0-0ubuntu1.1_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince-common_2.32.0-0ubuntu1.1_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_2.32.0-0ubuntu1.1_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_2.32.0-0ubuntu1.1_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_3.6.18+build2+nobinonly-0ubuntu0.10.10.2_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_3.6.18+build2+nobinonly-0ubuntu0.10.10.2_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_3.6.18+build2+nobinonly-0ubuntu0.10.10.2_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_3.6.18+build2+nobinonly-0ubuntu0.10.10.2_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_3.6.18+build2+nobinonly-0ubuntu0.10.10.2_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_3.6.18+build2+nobinonly-0ubuntu0.10.10.2_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/g/gdb/gdb_7.2-1ubuntu3_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/g/gdb/gdb_7.2-1ubuntu3_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupscgi1_1.4.4-6ubuntu2.3_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupscgi1_1.4.4-6ubuntu2.3_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsdriver1_1.4.4-6ubuntu2.3_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsdriver1_1.4.4-6ubuntu2.3_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsmime1_1.4.4-6ubuntu2.3_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsmime1_1.4.4-6ubuntu2.3_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsppdc1_1.4.4-6ubuntu2.3_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsppdc1_1.4.4-6ubuntu2.3_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.21.0-1ubuntu1.1_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.21.0-1ubuntu1.1_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple-bin_2.7.3-1ubuntu3.2_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple-bin_2.7.3-1ubuntu3.2_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.7.7.dfsg-4ubuntu0.2_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.7.7.dfsg-4ubuntu0.2_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.38.6_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.38.6_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1030.56_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1030.56_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.18+build2+nobinonly-0ubuntu0.10.10.1_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.18+build2+nobinonly-0ubuntu0.10.10.1_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea6-plugin_6b20-1.9.9-0ubuntu1~10.10.2_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea6-plugin_6b20-1.9.9-0ubuntu1~10.10.2_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea-6-jre-cacao_6b20-1.9.9-0ubuntu1~10.10.2_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea-6-jre-cacao_6b20-1.9.9-0ubuntu1~10.10.2_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-lib_6b20-1.9.9-0ubuntu1~10.10.2_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-lib_6b20-1.9.9-0ubuntu1~10.10.2_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b20-1.9.9-0ubuntu1~10.10.2_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b20-1.9.9-0ubuntu1~10.10.2_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre_6b20-1.9.9-0ubuntu1~10.10.2_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre_6b20-1.9.9-0ubuntu1~10.10.2_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8o-1ubuntu4.4_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8o-1ubuntu4.4_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.7.7.dfsg-4ubuntu0.2_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.7.7.dfsg-4ubuntu0.2_amd64.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/p/papyon/python-papyon_0.5.1-0ubuntu2_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/p/papyon/python-papyon_0.5.1-0ubuntu2_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_3.0.9_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_3.0.9_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/u/ubufox/xul-ext-ubufox_0.9~rc2-0ubuntu5.1_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/u/ubufox/xul-ext-ubufox_0.9~rc2-0ubuntu5.1_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/u/ubufox/ubufox_0.9~rc2-0ubuntu5.1_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/u/ubufox/ubufox_0.9~rc2-0ubuntu5.1_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.9.0-0ubuntu7.3_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.9.0-0ubuntu7.3_all.deb)  404  Not Found
Imposible obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.9.0-0ubuntu7.3_amd64.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.9.0-0ubuntu7.3_amd64.deb)  404  Not Found
E: No se pudieron obtener algunos archivos, ¿quizás deba ejecutar
apt-get update o deba intentarlo de nuevo con --fix-missing?
javier@ubuntu:~$ 

son muchos!!!!! hay alguna solución para esto?

---

