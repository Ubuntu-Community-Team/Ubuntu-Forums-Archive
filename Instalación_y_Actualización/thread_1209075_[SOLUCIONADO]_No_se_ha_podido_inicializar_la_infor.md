---
title: "[SOLUCIONADO] No se ha podido inicializar la información de los paquetes"
date: 2009-07-09
forum: Instalación y Actualización
---

### Post by burdened on 2009-07-09
Saludos..

soy nuevo en ubuntu.. y tengo este problema cuando quiero añadir nuevas aplciaciones desde synaptic

Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Línea 57 mal formada en lista de fuentes /etc/apt/sources.list (análisis de dist), E:No se pudieron leer las listas de fuentes.'


como arreglo este error?

---

### Post by radixs on 2009-07-09
En la consola (Aplicaciones >> accesorios >> terminal) ejecuta lo siguiente:
```
sudo gedit /etc/apt/sources.list
```Lo que te muestre lo pegas aqui

> 'E:Línea 57 mal formada en lista de fuentes /etc/apt/sources.list (análisis de dist), E:No se pudieron leer las listas de fuentes.'

se refiere a que la linea 57 tiene error, debe de estar mas escrita la direccion de los repos en esa linea

---

### Post by burdened on 2009-07-09
Gracias, Radixs..

hice lo que me dijiste y me aparecio esto:
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ec.archive.ubuntu.com/ubuntu/](http://ec.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://ec.archive.ubuntu.com/ubuntu/](http://ec.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ec.archive.ubuntu.com/ubuntu/](http://ec.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://ec.archive.ubuntu.com/ubuntu/](http://ec.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ec.archive.ubuntu.com/ubuntu/](http://ec.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://ec.archive.ubuntu.com/ubuntu/](http://ec.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://ec.archive.ubuntu.com/ubuntu/](http://ec.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://ec.archive.ubuntu.com/ubuntu/](http://ec.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ec.archive.ubuntu.com/ubuntu/](http://ec.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://ec.archive.ubuntu.com/ubuntu/](http://ec.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://ec.archive.ubuntu.com/ubuntu/](http://ec.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://ec.archive.ubuntu.com/ubuntu/](http://ec.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ec.archive.ubuntu.com/ubuntu/](http://ec.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://ec.archive.ubuntu.com/ubuntu/](http://ec.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://ppa.launchpad.net/c-korn/vlc/ubuntudeb](http://ppa.launchpad.net/c-korn/vlc/ubuntudeb) [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu)

que hago ahora?

---

### Post by burdened on 2009-07-09
[SIZE=6]Solucionado mi problema..
Gracias.. [SIZE=2]borre la linea 57.. la que me causaba problemas.. talvez me puedas ayudar esto me paso porque intentaba instalar el VLC player., y segun parece no lo hice bien.. jeje.. como puedo instalarlo??
[/SIZE]
[/SIZE]

---

### Post by radixs on 2009-07-09
Compañero eso es facil y simple, en la consola tipee

```
sudo apt-get install vlc
```cuenta como te va.

---

### Post by burdened on 2009-07-10
[SIZE=4]asi de simple???[/SIZE]
jajaja..

wow..gracias.. ya empecé a bajarlo. desde la consola.. 

[SIZE=6]mil gracias!!!!!!!!!!!!!!!![/SIZE]

---

### Post by radixs on 2009-07-10
> **burdened said:**
> [SIZE=4]asi de simple???[/SIZE]
jajaja..

wow..gracias.. ya empecé a bajarlo. desde la consola.. 

[SIZE=6]mil gracias!!!!!!!!!!!!!!!![/SIZE]

uufff ... viendo tu sources.list asi pa ser sincero tienes la escoba. porque? tienes combinado repos de intrepid como de jaunty... wow jejeje adjunto mi sources.list para que veas como deberia ser:

```
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://cl.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://cl.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://cl.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://cl.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://cl.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://cl.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://cl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
```**Como consejo ten ojo con lo que agregas, puedes terminar con un dolor de cabeza muy grande ;)**

---

### Post by burdened on 2009-07-10
ok gracias.. seguire tu consejo.. y cualquier problema.. lo posteo por aca..

---

### Post by diemarsanlur on 2009-08-16
Hola radixs, si todavia estas por aqui te pido me ayudes ya que tengo el mismo que fue posteado con anterioridad, lo que pasa que al intentar borrar la linea me niega el permiso. El problema empezo al querer instalar el programa vlc.

En cualquier intento de instalar o desinstalar o actualizar me sale este error:

E: Línea 55 mal formada en lista de fuentes /etc/apt/sources.list (análisis de dist)
E: No se pudieron leer las listas de fuentes.

A continuacion pego la source list:

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://www.bashterritory.com/pytube/releases](http://www.bashterritory.com/pytube/releases) /
deb [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Por favor ayuda

Gracias

---

### Post by Carlos C on 2009-08-16
> **diemarsanlur said:**
> 
deb [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list


Si te fijas en el error verás que te dice que la linea 55 presenta problemas. Trataste de instalar los repositorios medibuntu y no lo hiciste bien. Borra esa linea y no tendrás más problemas.

Puedes mirar acá cómo añadir medibuntu a tu lista de repositorios:

[http://blockdeubuntu.blogspot.com/2008/07/cmo-aadir-medibuntu-la-lista-de.html](http://blockdeubuntu.blogspot.com/2008/07/cmo-aadir-medibuntu-la-lista-de.html)

En caso de que tengas dudas  por favor abre un thread nuevo, así evitamos mezclar temas diferentes.
Saludos.

---

### Post by diemarsanlur on 2009-08-16
Muchas gracias por la respuesta Carlos C, estoy empezando en Ubuntu y como debe ser: A los golpes!!!

Borre la linea y se soluciono el problema, ..... pero segui tocando y se me presento otro y estoy empantanado, siguiendo tu consejo lo voy a publicar como Tema nuevo.

Saludos y un abrazo

---

### Post by Heomar on 2012-09-29
Hola! :) También soy nueva en ubuntu 
Me gustaría saber qué debo hacer para solucionar el siguiente error: :confused:

No se ha podido inicializar la información de los paquetes
'E:No se pudo tratar el archivo de paquetes /var/lib/apt/lists/ve.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages (1), E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'

Les agradecería mucho la ayuda. Saludos!

---

### Post by overdrank on 2012-09-29
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

