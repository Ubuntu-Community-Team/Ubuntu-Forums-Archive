---
title: "Ubuntu 8.1 - Problema con la parte gráfica"
date: 2009-03-27
forum: Hardware
---

### Post by marmax.cor on 2009-03-27
Hola, les cuento ^^ 

Soy nuevo, hace unos días revisé el ubuntu iniciando desde el cd y me gustó mucho. Hoy lo instalé e hice las actualizaciones, y después noto que la parte gráfica me anda más lento que cuando lo había iniciado desde el cd. Antes le podía poner todos los efectos gráficos, pero ahora parece que con el formateo y la instalación completa que hice de ubuntu, como que perdí los drivers del mother que manejan la parte gráfica. Me pongo a ver un video y se me ven los frames por segundos, lo mismo con las animaciones del protector de pantalla, y en la resolución de la pantalla, me capta bien la resolución de 1280 x 1024, pero no me detecta la frecuencia de actualización que me indica 0 Ghz cuando tendría que ser de 60 Ghz, además me dice un cartel "Desconocido" que no lo detecta o no se qué.
Cuando iniciaba del cd, podía poner los efectos visuales en "normal" o "extra", y ahora me dice que no se puede y solo tengo la opción de "ninguno" en efectos visuales.

Traté de instalar los drivers del mother, pero creo que no me funciona con el ubuntu, porque en principio ya no me funciona el "autorun" y si exploro el cd y elijo instalar algo, me dice que no se puede, me pone error. Mi mother es un ASRock...

O sea, un ejemplo resumido, es como si hubiera instalado windows y lo estuviese usando sin haber instalado los drivers del mother que controlan la parte gráfica. ( No sé como explicarlo, espero que haya sido un ejemplo claro y no los confunda, y que mi interpretación del error sea correcta )

Cómo puedo solucionar el problema? alguien sabe? =/

---

### Post by pablo.s on 2009-03-27
Hola: En el menú Sistema - Administración clickeá en Controladores de Hardware. 
Ahi gestiona Ubuntu los drivers que necesita instalar cuando no trae incorporados. 
Por ejemp&#314;o: drivers de WiFi, drivers de tarjetas de video Nvidia o ATI, etc.
Si en la lista aparece el modelo del fabricante de tu tarjeta de video y una de ellas
figura como recomendada, clickea sobre la descripción y luego de un par de
autorizaciones después va a descargar el driver de internet.
Te sugiero que pruebes eso. Saludos.

---

### Post by marmax.cor on 2009-03-27
Si, había intentado clickeando ahí. Aparece una ventana con un mensaje que dice "No se están usando controladores privativos en este sistema", despues abajo casilleros vacíos, y solo la opción de cerrar esa ventana, o la de ayuda que no me ayuda mucho que digamos =/

---

### Post by pablo.s on 2009-03-27
Vamos a proceder sin mas al rito de iniciación de los novatos!

En una terminal escribí:

lspci

y después copia y pegá el texto que te devuelva en un mensaje nuevo.

---

### Post by marmax.cor on 2009-03-27
> **pablo.s said:**
> Vamos a proceder sin mas al rito de iniciación de los novatos!

jajjajajaaaa... xDDDDDDD ok ok XD

Me costó encontrar la terminal pero la encontré. Te paso los datos que me dió ^^

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:03.0 Communication controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by marcelo_bur on 2009-03-27
No se si tuve suerte o que, pero el Ubuntu 8.04 que yo estoy usando me ha descargado automáticamente drivers y codecs cada vez que los he necesitado, simplemente me aparece una ventana diciendome lo que me falta para que algo funcione y me pregunta si deseo descargarlo e instalarlo, digo que si, bajo, desbloqueo, y listo.
En esta pc tengo una particion con Windows XP, y fué justamente esa la que me dio más problemas, donde tuve que entrar a la mother e instalar desde el sofware de la misma muchos de los drivers para que funcionara todo bien.
Saludos y suerte.

---

### Post by Juanxho on 2009-03-27
> **marmax.cor said:**
> jajjajajaaaa... xDDDDDDD ok ok XD

Me costó encontrar la terminal pero la encontré...

Vamos a ver si te puedo ayudar.

Abre el terminal y escribe esto:

```
~$ gedit /etc/X11/xorg.conf
```

Se te abrirá un archivo de texo que es la configuracion de tu servidor gráfico o Servidor X (la gráfica en Linux). Copia el texto que ves y pégalo aquí para ver tu configuración.

Espero tu respuesta.

---

### Post by pablo.s on 2009-03-27
Abrite una terminal (:)) y escribí lo siguiente:

sudo apt-get install xserver-xorg-video-intel libdrm-intel1

Luego cerrá la sesión y volvé a entrar.

Espero que sirva muchacho! Saludos

---

### Post by marmax.cor on 2009-03-27
> **Juanxho said:**
> Vamos a ver si te puedo ayudar.

Abre el terminal y escribe esto:

```
~$ gedit /etc/X11/xorg.conf
```

Se te abrirá un archivo de texo que es la configuracion de tu servidor gráfico o Servidor X (la gráfica en Linux). Copia el texto que ves y pégalo aquí para ver tu configuración.

Espero tu respuesta.

Ok, lo hice y me aparece esto ^^

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
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

> **pablo.s said:**
> Abrite una terminal (:)) y escribí lo siguiente:

sudo apt-get install xserver-xorg-video-intel libdrm-intel1

Luego cerrá la sesión y volvé a entrar.

Espero que sirva muchacho! Saludos

ok, lo hice y me apareció esto

marmax@marmax-desktop:~$ sudo apt-get install xserver-xorg-video-intel libdrm-intel1
[sudo] password for marmax: 



Me pide el password, per en ese momento escribo y no aparece lo que escribo. Solo si pongo enter luego me deja escribir, pero en cuanto empiezo a escribir mi password (aquí lo puse con "x") me dice

marmax@marmax-desktop:~$ sudo apt-get install xserver-xorg-video-intel libdrm-intel1
[sudo] password for marmax: 
xxxxSorry, try again.
[sudo] password for marmax: 

O será que no tengo que poner mi password, solo cerrarlo y reiniciarlo? >_<

---

### Post by Hei Ku on 2009-03-27
Tenes que poner tu password, pero no te muestra mientras estas escribiendo.

Sólo escribilo y apreta Enter, y ya esta.

---

### Post by marmax.cor on 2009-03-27
ok, lo hice, me dice que no encuentra un paquete >_<

marmax@marmax-desktop:~$ sudo apt-get install xserver-xorg-video-intel libdrm-intel1
[sudo] password for marmax: 
Sorry, try again.
[sudo] password for marmax: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
xserver-xorg-video-intel ya está en su versión más reciente.
E: No se pudo encontrar el paquete libdrm-intel1
marmax@marmax-desktop:~$

---

### Post by infernus92 on 2009-03-28
intenta en el terminal

```
sudo aptitude update
```

te va a pedir la contraseña y va a actualizar la lista de paquetes para descargar

despues de eso intenta con el comando

```
sudo aptitude install xserver-xorg-video-intel libdrm-intel1
```

lo que hice ahi es cambiar apt-get por aptitude... es otro programa que tiene la misma funcion pero es un poco mas comleto... si neces itas descargar otro paquete para que el tuyo funcione te sugiere hacerlo y te pregunta si lo queres hacer...

espero que te sirva

Saludos

---

### Post by pablo.s on 2009-03-28
Hola: Quiero reconocer que te agregué un paquete en la lista de instalación
que no corresponde a Intrepid, sino que aparece recién en Jaunty. El paquete
aparece como libdrm-intel1 pero para versiones anteriores viene en una
variante que la instalás como:

sudo apt-get install libdrm2

Se me escapó. Perdón por la equivocación. Saludos.

---

