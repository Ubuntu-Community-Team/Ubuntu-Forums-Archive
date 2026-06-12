---
title: "Problemas de audio y video"
date: 2008-12-14
forum: Hardware
---

### Post by nicolastroche on 2008-12-14
Les comento lo que me ha ocurrido: Habia descargado desde XP los iso de Ubuntu 8.10 y Ubuntu 8.04 (para probar Ubuntu, ya que es un sistema que siempre me pareció interesante, en un sistema busco que sea estable, confiable, rendimiento y apariencia, tal vez sea demasiado exigente, pero es lo que me gusta, y diria que la apariencia va en primer lugar y luego el rendimiento). Al grabar las imagenes, me tiraba errores en la instalación de ambos, por lo que use un viejo ISO que tenía de Ubuntu 6.06. Probe el Live CD y todavía me gustaba, asi que decidí instalarlo (previa descarga de un manual de Ubuntu, para que me sirva como guía rápida) y hasta ahi, todo iba de 10. Configure internet, deje todo funcionando al 100 %. Luego, no conforme con esto, y dado que el soporte para Ubuntu 6.06 estaba por caducar (son 3 años, y ya lleva su tiempo) decidi instalar todas las actualizaciones que me pedía (227 en total) y luego lo llevé a la version 8.04.1. Hasta aquí no había problemas, pero tengo una impresora Epson Photo Stylus R290 y precisaba hacer un trabajo, y no me dejaba configurar el tipo de papel y demás (tal vez sí aparecía, pero estaba muy cansado y no me fije mucho). Luego de intentar varias cosas, me decidí a probar Intrepid Ibex, y todo marchó de 10 durante la instalación. Reinicié la PC, y gran sorpresa me llevé al comprobar que no me tomaba mi tarjeta de audio (una VIA VT 1617, con controlador AC97). Me dije para mi mismo "no hay problema ... de última, encontraré una solución). Pero cuando quise ver los efectos de escritorio, tampoco me dejaba activarlos .... Probe desinstalar todos los controladores, y aquí tuve otro problema que lo pude solucionar entrando en modo de recuperación. Pero he aquí, que no me deja activarlos y solo me deja funcionar el sistema en modo de gráficos bajos (traducción literal del cartel que aparece). Mis preguntas son ¿Puedo activar mi tarjeta de audio para Ubuntu 8.10? ¿Cómo hago para activar nuevamente los efectos de escritorio? ¿Puedo eliminar la versión 8.10 y volver al anterior, donde todo funcionaba de 10?

Mi PC es AMD XP 2400+ 1.7 Ghz, 768 Mb de RAM, Mother VIA KT880, Audio VIA VT 1617, Ethernet VIA VT 6121, Video AGP NVIDIA Ge-Force FX 5500 de 256 Mb.

Les aviso, soy nuevo con Ubuntu (lo instalé hace una semana), así que cuanto más explicitos puedan ser, mejor. Desde ya, gracias por adelantado.

P.D. : Una cosa más ... en XP el monitor podía usarlo en resolución de 1280 x 1024, pero ahora no me deja más que 1024 x 768 ... ¿Se puede acomodar esto? Igual, no es algo que me vaya a cambiar demasiado, solo lo anterior es lo principal.

---

### Post by faktorqm on 2008-12-15
Hola, vamos por partes. Primero entra al sistema grafico en baja resolucion, e instala el envyng. (buscalo en el gestor de paquetes Synatic)
Si no tenes acceso al entorno grafico y solo al entorno de recuperacion, escribi

```
sudo apt-get install envyng-core
```

y luego

```
sudo envyng -t
```

(no me acuerdo el comando de memoria, si no es ese fijate de escribir sudo envyng y cuando estas exactamente en la g apretar dos veces la tecla tabulacion y te da las posibles opciones). Te va a aparecer un menu preguntandote que queres hacer, creo que es la opcion 1 :P

Una vez con el driver instalado y funcionando, arrancas el entorno grafico y desde una terminal pone

```
sudo displayconfig-gtk
```

y ahi seleccionas tu monitor, si no esta en la lista, podes ingresar a mano las frecuencias de actualizacion horizontal y vertical, o meter el cd que trae para win para que lea el .inf y extraiga la informacion automaticamente por vos.


Con el tema del sonido, primero tenes que pasearte por todas las opciones de volumenes que veas y levantarlos todos por que algunas veces aparecen todos los volumenes en cero, y mas cuando terminas de hacer una instalacion. Luego probar en sistema -> administracion -> sonidos que servidor de sonido es el que se escucha apretando los botones a la derecha para escuchar. Si tira un mensaje de error, postear cual. si no tira nada y no suena, cambiar de servidor de sonido (puede ser alsa, pulseaudio, etc).

Espero que te haya servido. Salu2!!!

---

### Post by Hadso on 2009-01-30
Hola. Yo tengo el mismo problema y estoy en busca de una solución. 
Intente entrar al administrador de paquetes, pero me dice que no tengo permisos suficientes para hacerlo. 
A la vez, tampoco entendí la explicación mas abajo, debo advertilrles que soy muy novato. 
Gracias por su ayuda.

---

### Post by guillermolisi on 2009-01-30
> **Hadso said:**
> Hola. Yo tengo el mismo problema y estoy en busca de una solución. 
Intente entrar al administrador de paquetes, pero me dice que no tengo permisos suficientes para hacerlo. 
A la vez, tampoco entendí la explicación mas abajo, debo advertilrles que soy muy novato. 
Gracias por su ayuda.
Como quisiste entrar al administrador de paquetes ?

Si fue a traves de una consola, tenes que usar 'sudo', por ejemplo:
```
sudo apt-get install <paquete>
```Despues del 'enter' te va a pedir la password del usuario que estas usando y cuando la digites no vas a ver que el cursor se mueva pero lo que digites ingresa en la terminal. Ese efecto es para preservar la password de ojos "metiches".

---

### Post by Hadso on 2009-01-31
He entrado al admin de paquetes y he instalado ya bastante software. 
Sucede que mi placa de video, que ahora no puedo decir cual es porque no se como se hace con el Xubuntu, andaba medio mal. 
Por ejemplo, los efectos funcionaban, pero a veces, distorcionaban un poco el area de la patalla donde debían aparecer. 
Entonces me decidí a instalarle drivers de video. Desde ahí que tengo este problema.

Gracias.

---

### Post by Hei Ku on 2009-01-31
Se mas concreto. Que error te tira? Ponelo exacto. O copia la pantalla y pega la imagen.
Sin eso, no podemos ayudarte.

Y para ver tu placa de video, pone lspci y pega el resultado aca.

---

### Post by Hadso on 2009-01-31
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
00:0a.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1




Este es el texto que me aparece. 
No hay cartel de error en Xubuntu. El tema es que, como decía, instale unos drivers de video para que mi placa "funcione mejor". 
Ahora me dice que tengo que entrar en modo "low graphic". 
Ya he probado, en el GRUB el modo recuperar y todo eso, peor no he logrado cambiar nada. Ademas, no tengo conocimiento como para editar el archivo del X. 

Que tengo que hacer?

Gracias!!!!

---

### Post by Hei Ku on 2009-01-31
Postea el contenido del archivo /etc/X11/xorg.conf, para ver qué driver estas usando ahora.

En el GRUB, al iniciar, apreta e para editar la linea de inicio, y agrega al final de la linea de kernel "irqpoll" sin las comillas.

Deberia quedarte algo asi:

```

kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash irqpoll

```

---

### Post by Hadso on 2009-01-31
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


Este es el contenido. Gracias por tu ayuda. Ahora voy a editar eso que me sugieres.

---

### Post by Hadso on 2009-01-31
Ya lo hice pero no cambió nada.... :(

---

### Post by Hei Ku on 2009-01-31
Esta es la guia para asegurarse que estas usando el driver Radeon, que es libre y deberia andar bien para tu placa.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

De ahi, segui estos pasos:

```

sudo apt-get remove --purge xorg-driver-fglrx
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

sudo nano /etc/X11/xorg.conf

```

En el xorg.conf, pone lo siguiente en la seccion Device:
```

Section "Device"
        Identifier      "Radeon Mobility"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

```
Y agrega estas dos secciones:

```

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

Graba el archivo y reinicia.

Despues postea el resultado de estos comandos:

```

glxinfo | grep vendor

glxinfo | grep "direct rendering"

```

---

### Post by Hadso on 2009-01-31
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/main libgl1-mesa-glx 7.2-1ubuntu2
  Could not connect to es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Connection refused)
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/main libgl1-mesa-dri 7.2-1ubuntu2
  Could not connect to es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Connection refused)
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-glx_7.2-1ubuntu2_i386.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-glx_7.2-1ubuntu2_i386.deb)  Could not connect to es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Connection refused)
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dri_7.2-1ubuntu2_i386.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dri_7.2-1ubuntu2_i386.deb)  Could not connect to es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


Esto fue lo que me apareció. No se ha bajado. Que debo hacer ahora?
Ademas, el archivo que me dijiste que edite, tenía datos totalmente diferentes. Lo edito igual aunque no haya bajado lo que me sugeriste? O lo dejo tal como está?

GRACIAS!!!

---

### Post by Hei Ku on 2009-01-31
Por ahora dejalo como esta, porque no te bajó los archivos necesarios.
Volvé a probar más tarde y si te baja los archivos, entonces sí hace los cambios.

---

### Post by Hadso on 2009-01-31
Hey :P... arrancó sin problemas como lo hacia antes. Pero creo que necesito configurar la placa de video. Puede ser que yo ya haya tenido los drivers en mi maquina? Porque el problema empezo desde que baje deliberadamente unos de internet pensando que sería mejor. 
Como puedo configurar mi placa? Si o si tengo que bajar esos drivs que me dijiste? Como puedo chequear si ya los tengo?

GRACIAS!!!

---

### Post by Hadso on 2009-01-31
Agrego que ya no lo uso en el modo Low graphics. Pero creo que mi placa necesitaria una ajustada. Dado que por ejemplo hace problemas para usar los efectos de las ventanas. Problemas que indican una falta de configuración, creo. 

GRACIAS por todo!

---

### Post by Hadso on 2009-01-31
Como puedo configurar mi placa? Si o si tengo que bajar esos drivs que me dijiste? Como puedo chequear si ya los tengo?

---

### Post by Hadso on 2009-01-31
Sigo sin poder bajar los archivos. Que puedo hacer? 
No hay otra manera? 

Gracias!

---

### Post by Hei Ku on 2009-01-31
Postea el resultado de estos comandos:

```

glxinfo | grep vendor

glxinfo | grep "direct rendering"

```

A partir de eso vemos.

---

### Post by Hadso on 2009-01-31
Hice lo que me dijiste y me indico que no está instalado. Pero me dio el comando para hacerlo así que lo hice. MI SER INTELIGENTE. 

adso@ubuntu:~$ glxinfo | grep "direct rendering"
direct rendering: Yes

Algo mas que daba hacer?
Gracias!

---

### Post by Hei Ku on 2009-01-31
Correr el primer comando, que nos va a dar la pista de qué drivers estas usando. ;)

glxinfo | grep vendor

---

### Post by Hadso on 2009-01-31
Esto es lo que me aparece:

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

---

### Post by Hei Ku on 2009-01-31
Ok. Pareciera que estás usando los drivers libres y tenés 3d. Una cosa menos.


Ahora te esta funcionando bien o seguis con problemas?

---

### Post by Hadso on 2009-02-01
Esta todo en orden. 

GRACIAS!

---

