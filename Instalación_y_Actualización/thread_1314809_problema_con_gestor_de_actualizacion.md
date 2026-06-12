---
title: "problema con gestor de actualizacion"
date: 2009-11-04
forum: Instalación y Actualización
---

### Post by lobosorno on 2009-11-04
holaaaa...soy nuevo y creo ke cometí un error grave...esto me sale:

E: Línea 57 mal formada en lista de fuentes /etc/apt/sources.list (análisis de dist)
E: No se pudo leer la lista de fuentes.
Vaya al diálogo del repositorio para corregir el problema.
E: _cache->open() failed, please report.

espero me ayuden 

gracias desde ya


lobosorno

---

### Post by Carlos C on 2009-11-04
Hola. Te sugiero que hagas lo siguiente: escribe en el terminal:
```
gedit /etc/apt/sources.list
```
con ese comando se abrirá un editor de texto en donde verás el contenido del archivo sources.lst. La idea es que copies el contenido de la linea 57 (gedit te muestra siempre en qué linea estás parado) y lo pegues acá. Seguramente modificaste tu lista de repositorios y por ahí tienes un problema.
Saludos.

---

### Post by moreback on 2009-11-05
La mayoría de los problemas con los sources.list provienen de usuarios poco experimentados que lo modifican manualmente siguiendo guías de dudosa procedencia.

Mejor es con Sistema -> Administración -> Orígenes del software

Saludos.

---

### Post by lobosorno on 2009-11-07
> **Carlos C said:**
> Hola. Te sugiero que hagas lo siguiente: escribe en el terminal:
```
gedit /etc/apt/sources.list
```con ese comando se abrirá un editor de texto en donde verás el contenido del archivo sources.lst. La idea es que copies el contenido de la linea 57 (gedit te muestra siempre en qué linea estás parado) y lo pegues acá. Seguramente modificaste tu lista de repositorios y por ahí tienes un problema.
Saludos.


esto me sale en la línea 57:
deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main

---

### Post by themasterdark on 2009-11-08
Mejor sube tu sources.list completo, asi podremos ver donde esta la falla, ya que a veces no suele estar en la linea que indica el error.

Saludos

---

### Post by lobosorno on 2009-11-08
> **themasterdark said:**
> Mejor sube tu sources.list completo, asi podremos ver donde esta la falla, ya que a veces no suele estar en la linea que indica el error.

Saludos


Esto me sale amigo...a ver si me puedes ayudar...gracias desde ya:

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
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
##Themes du ZgegBlog: Project Bisigi
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/jaunty](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/jaunty) main
deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main

---

### Post by moreback on 2009-11-08
> **lobosorno said:**
> ```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/jaunty main
deb http://ppa.launchpad.net/fta/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/fta/ppa/ubuntu jaunty main
```


La primera línea es la que está mal escrita y por eso da error en la siguiente. Debiera ser:
```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
```

Y yo tenía razón. Un usuario poco experimentado como tú debiera usar **Sistema -> Administración -> Orígenes del software** para agregar fuentes. Con eso te evitas dolores de cabeza como los causados por esto.

Saludos.

---

### Post by lobosorno on 2009-11-08
> **moreback said:**
> La primera línea es la que está mal escrita y por eso da error en la siguiente. Debiera ser:
```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
```Y yo tenía razón. Un usuario poco experimentado como tú debiera usar **Sistema -> Administración -> Orígenes del software** para agregar fuentes. Con eso te evitas dolores de cabeza como los causados por esto.

Saludos.

y qué hago ahora? al tratar de editar, me sale esto:

No se puede guardar el archivo /etc/apt/sources.list.
No tiene los permisos necesarios para guardar el archivo. Compruebe que ha tecleado el lugar correctamente y pruebe de nuevo.

---

### Post by MDK2000 on 2009-11-08
Prueba colocando en una consola
 
```
sudo gedit /etc/apt/sources.list
```

---

### Post by Carlos C on 2009-11-08
lobosorno, la razón de que no tengas permisos es que estás tratando de modificar un archivo que únicamente puede ser alterado por un administrador del sistema. Para eso se usa el comando "sudo". Te sugiero que averigües en qué consiste "sudo" y la manera en que funciona el sistema de permisos, propietarios y grupos en linux, para que evites mayores problemas en el futuro. A continuación te sugiero un par de enlaces que te pueden resultar muy útiles:

[http://www.guia-ubuntu.org/index.php?title=Sudo](http://www.guia-ubuntu.org/index.php?title=Sudo)

[http://www.guia-ubuntu.org/index.php?title=Sistema_de_ficheros](http://www.guia-ubuntu.org/index.php?title=Sistema_de_ficheros)

Espero que te sirvan.

Saludos.

---

