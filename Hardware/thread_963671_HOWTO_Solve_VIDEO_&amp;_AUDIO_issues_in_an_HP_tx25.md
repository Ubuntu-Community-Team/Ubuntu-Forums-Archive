---
title: "HOWTO: Solve VIDEO &amp; AUDIO issues in an HP tx2500 series (Intrepid Ibex) [ESPAÑOL]"
date: 2008-10-30
forum: Hardware
---

### Post by AlfredoZ on 2008-10-30
Me la he pasado como loco buscando soluciones a mis problemas de ubuntu y porfin los encontré. Haciendo un recuento de tutoriales sacados de muchos lados, los junté y los puse todos aqui. Esta probado que funcionan en una TX2525nr con Intrepid Ibex de 32-bits instalado.

PROBLEMAS DE AUDIO

1) Instalar version reciente de ASLA DRIVERS
 
-Actualizamos e instalamos los headers del Kernel

```

$ sudo apt-get update
$ sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic

```

Instalamos las siguientes librerias para poder compilar

```
$ sudo apt-get install libncurses5-dev
```

Ya que esto esta hecho, vamos a la pagina oficial de ALSA [/]("http://www.alsa-project.org/") y bajamos los siguientes archivos más recientes
 
Driver * 1.0.# 
Library * 1.0.#
Utilities * 1.0.#
OSS Compat. Library * 1.0.#

Y los guardamos.
**Sugerencia: guarden en /home/"usuario"/ALSA/ porque así se va a explicar. (donde "usuario" es tu nombre de usuario .. duh!)

Despues, detenemos Alsa Utilities para poder actualizarlo

```
sudo /etc/init.d/alsa-utils stop
```

Ahora hay que descomprimir los 4 archivos que bajamos y que estan en nuestra carpeta que creamos.

PARA EL CASO SERIA ASI: 

```
cd /home/"usuario"/alsa
```


Luego decomprimimos,
**Sugerencia: pueden escribir las primeras 2 palabras despues de tar xvf y luego pulsar [TAB] para que se autocomplete.

```
tar xvf alsa-driver-1.0.#.tar.bz2
tar xvf alsa-lib-1.0.#.tar.bz2
tar xvf alsa-utils-1.0#.tar.bz2
tar xvf alsa-oss-1.0.#.tar.bz2
```


Ahora ya que estan descomprimidos los archivos vamos a configurar el Alsa Driver

Entramos a la carpeta de driver

```
$ cd alsa-driver-1.0.14 
```

Ahora a compilar e instalar,

```
$ sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-oss=yes 
$ sudo make
$ sudo make install
```

Despues se hace, otra vez, (nose porque) este:

```
$ sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-oss=yes
```


Despues se va a compilar e instalar los otros archivos. Es importante hacer en el orden mostrado:


Entramos a la carpeta de librería:

```
$ cd ..
$ cd alsa-lib-1.0.#
```

Y ejecutamos

```

$ sudo ./configure
$ sudo make
$ sudo make install
```

Lo mismo hacemos con las utilities.

```
$ cd ..
$ cd alsa-utils-1.0.#
```

Y ejecutamos

```
$ sudo ./configure
$ sudo make
$ sudo make install 
```

Y por ultimo lo hacemos con OSS

```
$ cd ..
$ cd alsa-oss-1.0.#
```

Y ejecutamos

```
$ sudo ./configure
$ sudo make
$ sudo make install
```

Despues se reinicia el equipo.

Ahora, se van a agregar 2 líneas al archivo alsa-base.

Lo abrimos,

```
$ sudo gedit /etc/modprobe.d/alsa-base
```

Agregar al final (donde estan todos los options... ; antes de los comentarios)

options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel index=0 model=toshiba position_fix=1

Reiniciar y LISTO!!

PROBLEMAS CON VIDEO

1) Para habilitar pantalla externa

instalar catalyst control center de ATI para Linux desde página de ATI, y moverle.


2) Para resolver el blinking en videos con compiz habilitado

Abrir un Terminal y escribir (así pelón)

```
gstreamer-properties 
```

Pulsa [Enter]

Vete a la pestaña de Video, y pica "test", veras que la prueba de video parpadea. Ahora, en el Drop Down Menu, cambia el Default y escoge:

“X Window System (No Xv)"

Pulsa "Test" y debe de dejar de parpadear.

Cierra.


Para usuarios de VLC

Inicia VLC y vete a "Herramientas > Preferencias"

Expande el menu de Video y luego en el apartado Output, Escoge:

"X11 video output"

Pulsa Salvar y Listo!
------------------------------------------------------

Espero que les haya servido de algo.
Ahora, si alguien tiene la versión de 64-bits y esto les funcionó, favor de postearlo, porque pienso cambiarme a 64-bits pero no se si me convenga. Si no les funciona algo, no me pregunten, no voy a saber, solo soy un novato.

Para bajar programas para ubuntu métanse a [http://www.getdeb.net]("http://www.getdeb.net") está bastante buena para novatos que no saben compilar y cosas así. Son puros .deb fáciles de instalar, y muy útiles.

---

### Post by bapoumba on 2008-11-02
The IP is from Mexico, so is the IP from another closely related account: alfredozendejas with zero posts. I suppose the user has lost the login and/or password or something..
Anyway, there is no Mexico team, and I do not know how the user would feel about moving the post to the Argentina team for ex.

May be send a PM or an email and suggest the moving? (English is the language on the main forums etc..).

---

