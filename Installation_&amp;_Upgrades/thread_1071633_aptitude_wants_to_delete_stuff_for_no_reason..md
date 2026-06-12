---
title: "aptitude wants to delete stuff for no reason."
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by azzamite on 2009-02-16
Hi everyone.

Every time I try to install something from the console,
aptitude tries to delete stuff.

I allowed it to delet some packages that I thing I didn't
need, but this time it want's to delete packages that I
do need.

Any ideas what's wrong?

I'm using [COLOR="White"]Debian Sid[/COLOR]...


```
aptitude install macchanger
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho
Leyendo las descripciones de las tareas... Hecho
Se ELIMINARÁN los siguientes paquetes:
  comerr-dev{u} dhcdbd{u} kwalletmanager{u} libaudio-dev{u} libcups2-dev{u}
  libcupsys2-dev{u} libexpat1-dev{u} libfontconfig1-dev{u}
  libfreetype6-dev{u} libgcrypt11-dev{u} libgnutls-dev{u}
  libgpg-error-dev{u} libjpeg62-dev{u} libkadm55{u} libkrb5-dev{u}
  liblcms1-dev{u} libmng-dev{u} libnm-util0{u} libpkcs11-helper1{u}
  libpng12-dev{u} libpthread-stubs0{u} libpthread-stubs0-dev{u}
  libqt4-opengl{u} libqt4-sql{u} libqt4-sql-sqlite{u} libqt4-svg{u}
  libqt4-webkit{u} libqt4-xmlpatterns{u} libtasn1-3-dev{u} openvpn{u}
  openvpn-blacklist{u} resolvconf{u} vpnc{u} xtrans-dev{u} zlib1g-dev{u}
0 paquetes actualizados, 0 nuevos instalados, 35 para eliminar y 23 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se liberarán 40.7MB.
¿Quiere continuar? [Y/n/?] n

```

Eliminar = delete.

---

### Post by mc4man on 2009-02-16
This may be what's causing this for you.

Apt was changed in 8.10 to mark all packages acquired thru '*build-dep*' to "automatically installed'. This also marks them immediately for auto-remove which when you use aptitude, they will be removed. (rendering 'aptitude install' useless

If you were to use apt-get install you'll just get a list of what can be auto removed. (making 'autoremove' useless if you build apps

If you do use apt-get build-dep and don't want the packages marked this way then do like this

Ex. mplayer

```
sudo apt-get build-dep mplayer -o APT::Get::Build-Dep-Automatic=false
```

---

### Post by azzamite on 2009-02-16
Is there a way to mark the packages otherwise?

I tried with
aptitude markauto *
but it still wants to delete the packages

---

### Post by mc4man on 2009-02-17
> aptitude markauto *

I think you want the opposite.

To remove the autoinstalled flags (keep all your packages 
then run this

```
sudo aptitude unmarkauto --schedule-only '~i'
```

In the future use this. with your package of course (I always used apt-get but apt should be apt

```
sudo aptitude build-dep mplayer -o APT::Get::Build-Dep-Automatic=false
```

---

### Post by azzamite on 2009-02-17
Tanks, that did the trick. :D

> **mc4man said:**
> I think you want the opposite.

To remove the autoinstalled flags (keep all your packages 
then run this

```
sudo aptitude unmarkauto --schedule-only '~i'
```

hmmm, I think there's a bug in the documentation of aptitude.

```
mark_auto_     - marca paquetes como instalados _manualmente_
unmark_auto_   - desmarca paquetes como instalados _manualmente_

```

> **mc4man said:**
> In the future use this. with your package of course (I always used apt-get but apt should be apt

```
sudo aptitude build-dep mplayer -o APT::Get::Build-Dep-Automatic=false
```

I don't quite undestand what's that line for, while it's easier to write aptitude [--without-recommends] install something

):P

---

### Post by mc4man on 2009-02-17
you would only use this if you were getting build-dep's
o APT::Get::Build-Dep-Automatic=false
( I wasn't sure if you were, you did have a number of -dev's

Otherwise without the recommends I guess would work for normal package installs
> 
markauto     - marca paquetes como instalados manualmente
unmarkauto   - desmarca paquetes como instalados manualmente

 Don't quite know how to translate but in the reference manual it makes sense as is

worst case you can always  use the unmarkauto --schedule-only '~i' to set all as manually installed

---

