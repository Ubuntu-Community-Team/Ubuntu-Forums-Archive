---
title: "No compilation of acerhk module"
date: 2011-07-08
forum: Hardware
---

### Post by OlmoLP on 2011-07-08
Hello All,

I have got an Acer Aspire 5630 since a while, I have always ran Kubuntu, but recently for a HD crash I reinstalled the OS swapping from Ubuntu 10.4 with KDE to Ubuntu 11, and I love it.

When trying to set everything up I found a problem which is driving me crazy. Installing the acerhk I followed my own post in this forum: 

[http://kubuntuforums.net/forums/index.php?topic=3112345.msg232551#msg232551](http://kubuntuforums.net/forums/index.php?topic=3112345.msg232551#msg232551)

As you can see the previous time I found the solution myself. However the problem which I am facing this time does not help. At first I installed the acerhk-source:

```

olmo@olmo-laptop:~$ sudo apt-get install acerhk-source
[sudo] password for olmo: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
acerhk-source ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
olmo@olmo-laptop:~$ sudo apt-get install acerhk-source
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
acerhk-source ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

```Afterwards I update the headers:

```

olmo@olmo-laptop:~$ sudo apt-get install build-essential linux-headers-$(uname -r)
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
build-essential ya está en su versión más reciente.
linux-headers-2.6.38-8-generic ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

```Now the problem, when trying to compile, it gets stuck no going further:

```

olmo@olmo-laptop:~$ cd /usr/scr
bash: cd: /usr/scr: No existe el fichero o el directorio
olmo@olmo-laptop:~$ cd /usr/src
olmo@olmo-laptop:/usr/src$ sudo tar -xvjf acerhk.tar.bz2
modules/
modules/acerhk/
modules/acerhk/debian/
modules/acerhk/debian/control.modules.in
modules/acerhk/debian/docs
modules/acerhk/debian/rules
modules/acerhk/debian/changelog
modules/acerhk/debian/copyright
modules/acerhk/debian/compat
modules/acerhk/acerhk.c
modules/acerhk/acerhk.h
modules/acerhk/README
modules/acerhk/NEWS
modules/acerhk/Makefile
modules/acerhk/doc/
modules/acerhk/doc/FAQ
modules/acerhk/doc/IOCTL
modules/acerhk/doc/acertm.def
modules/acerhk/doc/md95400.def
modules/acerhk/doc/keycodes
olmo@olmo-laptop:/usr/src$ cd modules/acerhk
olmo@olmo-laptop:/usr/src/modules/acerhk$ sudo make


```This matter is driving me crazy, I am not able to find anything on the web regarding similar issues. It is really frustrating.

Can anyone help me? I need I tip to follow in order solve this issue.

---

