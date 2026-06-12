---
title: "[SOLUCIONADO] Ayuda actualizaciones"
date: 2009-05-24
forum: Instalación y Actualización
---

### Post by Fisaulerod on 2009-05-24
Hola, tengo Ubuntu 8.10, y desde hace un tiempo no puedo actualizar, me dice primero que debo hacer una actualizacion parcial y luego que esta no se puede hacer..aquí imagenes:

[[IMG]http://img297.imageshack.us/img297/2770/pantallazoe.png[/IMG]]("http://img297.imageshack.us/my.php?image=pantallazoe.png")

_[IMG]http://img521.imageshack.us/img521/7677/pantallazo1a.png[/IMG]_

[IMG]http://img521.imageshack.us/img521/6948/pantallazo2.png[/IMG]

¿Cómo lo soluciono? Gracias de antemano.

---

### Post by Carlos C on 2009-05-24
creo que tienes repositorios que resultan incompatibles en este punto. Por favor pon acá el contenido de tu archivo sources.list. Lo &#7765;uedes ver escribiendo en el terminal:
```
gedit /etc/apt/sources.list
```

---

### Post by Fisaulerod on 2009-05-24
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

#Openoffice
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) romeo daryna
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main

---

### Post by Carlos C on 2009-05-24
> **Fisaulerod said:**
> 
#Openoffice
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) romeo daryna
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main
Creo que eso debieras comentarlo y probar nuevamente con tu actualización.
Saludos.

---

### Post by bichopro on 2009-05-24
Prueba a hacer lo siguiente:

```
# sudo mv /var/lib/dpkg/info/ /var/lib/dpkg/info_moved

```
```
# sudo mkdir /var/lib/dpkg/info

```

```
sudo apt-get update
sudo apt-get upgrade
```

```
# sudo mv /var/lib/dpkg/info/* /var/lib/dpkg/info_moved
```

```
# sudo rm /var/lib/dpkg/info

```
```
# sudo mv /var/lib/dpkg/info_moved /var/lib/dpkg/info
```

a mi me funciona siempre que hay un paquete rebelde... en vez de actualizar reinstalo el paquete y luego sigo los otros pasos y listo

---

### Post by EnriqueK on 2009-05-25
Creo que debes desactivar los backports, mejor entra a Synaptic --> Configuración --> Repositorios--> Actualizaciones y que queden desmarcadas las "aún no publicadas" y las "no soportadas"

---

### Post by Carlos C on 2009-05-25
> **EnriqueK said:**
> Creo que debes desactivar los backports, mejor entra a Synaptic --> Configuración --> Repositorios--> Actualizaciones y que queden desmarcadas las "aún no publicadas" y las "no soportadas"
Según entendí no los tiene activados ¿Por qué crees que están activados esos repositorios?
Saludos.

---

### Post by kamus on 2009-05-25
> **Fisaulerod said:**
> Hola, tengo Ubuntu 8.10, y desde hace un tiempo no puedo actualizar, me dice primero que debo hacer una actualizacion parcial y luego que esta no se puede hacer..aquí imagenes:

¿Cómo lo soluciono? Gracias de antemano.


Podrías poner una captura cuando aparece el error o si es posible revisar y pegar o adjuntar lo mas sospecho del archivo "/var/log/dpkg.log"?, segun entendí quieres solo actualizar tus paquetes NO una actualización de distribución, cierto?


Salu2

---

### Post by Fisaulerod on 2009-05-25
> **Carlos C said:**
>  					Originally Posted by **Fisaulerod** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7340933#post7340933") 				
 				[I]#Openoffice
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) romeo daryna
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main

[/I]
Creo que eso debieras comentarlo y probar nuevamente con tu actualización.
Saludos.
 
Gracias, hice eso y funciono. Gracias igual a los demás que postearon :P.

---

