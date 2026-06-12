---
title: "problemas wifi adaptador"
date: 2010-11-08
forum: Hardware
---

### Post by maximo68 on 2010-11-08
Como instalo un  adaptador wifi usb tp-link 722n
no se por donde arrancar??:confused:

---

### Post by hectorivand on 2010-11-08
> **maximo68 said:**
> Como instalo un  adaptador wifi usb tp-link 722n
no se por donde arrancar??:confused:

Hola Máximo.

¿Cuál es el problema? te la reconoce Ubuntu? no lo hace? tenes problemas de calidad de enlace? explayate un poco más, así hay más chance de que te podamos dar una mano.

Saludos
Nacho

---

### Post by maximo68 on 2010-11-08
> **hectorivand said:**
> Hola Máximo.

¿Cuál es el problema? te la reconoce Ubuntu? no lo hace? tenes problemas de calidad de enlace? explayate un poco más, así hay más chance de que te podamos dar una mano.

Saludos
Nacho

nacho

tengo ubuntu 10.04 en conexiones de red no la reconoce, tambien tengo instalado el wifiradar no la reconoce. En un lsusb si aparece el dispositivo  Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc.

---

### Post by maximo68 on 2010-11-08
> **maximo68 said:**
> nacho

tengo ubuntu 10.04 en conexiones de red no la reconoce, tambien tengo instalado el wifiradar no la reconoce. En un lsusb si aparece el dispositivo  Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc.

nacho
Tengo tambien instalados el controlador para redes inhalambricas que toma un driver de windows pero para mi no la reconoce, tiene que crear un wlan o algo por el estilo para mi no lo crea, pero no tengo idea porque? Soy nuevo en linux me esta costando el concepto

saludos
maximo

---

### Post by biale on 2010-11-09
La salida de lsusb indica que reconoció al adaptador y que tiene chipset atheros. O sea que lo reconoce...

Fijate que dice "lshw" relacionado con el adaptador y también la salida del "dmesg".

"iconfig" muestra alguna interface wlan0, wlan1, o lo que sea?

Trataría provisoriamente de retirar lo que has instalado, especialmente el driver de windows, es muy probable que todo eso este trayendo interferencias (?)

---

### Post by maximo68 on 2010-11-09
Tenes razon hay problemas con los archivos de win sale todo lo siguiente, ahora que hago reemplazo con otros driver (estan de xp, vista y otras)  la ventana del ndis dice que es correcto, lo puedo desintalar a este progs, como lo haces con remove o algo asi. Con el ifconfig no sale el wlan.
saludos maximo
[ 8052.698719] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'RtlIsServicePackVersionInstalled'
[ 8052.698756] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[ 8052.698773] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[ 8052.698789] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[ 8052.698947] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 8052.698967] ndiswrapper (import:242): unknown symbol:

---

### Post by biale on 2010-11-10
Sin instalar nada especial, Ubuntu tendría que tomarlo de una con el driver ath9k_htc 

Esto de acuerdo con  [http://linuxwireless.org/en/users/Devices/USB](http://linuxwireless.org/en/users/Devices/USB)

O sea que el primer paso es sacar los drivers de windows y correr los comandos que te pase.

Para facilitar el comando dmesg, cuando ubuntu ya arranco, conectas al dongle USB y las últimas lineas que salgan del dmesg van a referir al dispositivo.

Lo que no se es como sacar el driver de win. Alguien mas por ahi?

---

### Post by maximo68 on 2010-11-10
> **biale said:**
> Sin instalar nada especial, Ubuntu tendría que tomarlo de una con el driver ath9k_htc 

Esto de acuerdo con  [http://linuxwireless.org/en/users/Devices/USB](http://linuxwireless.org/en/users/Devices/USB)

O sea que el primer paso es sacar los drivers de windows y correr los comandos que te pase.

Para facilitar el comando dmesg, cuando ubuntu ya arranco, conectas al dongle USB y las últimas lineas que salgan del dmesg van a referir al dispositivo.

Lo que no se es como sacar el driver de win. Alguien mas por ahi?

Voy a probar lo que dice la pagina que recomendas, me queda la duda cuando dice el Kernel, se refiere tambien a un archivo del nucleo del s.o? los de mas archivos los busco los edito y modifico

saludos

---

### Post by biale on 2010-11-11
Si, son modulos auxiliares que el kernel activa segun necesidad. En mi caso el ar9170usb.ko.

La idea es tratar de volver a la situación original (un arranque live de Maverick funcionaria) y correr los comandos para ver como se comporta.

Y si hay suficiente señal, network-manager tendría que "saltar" pidiendo los datos del router que encontro para conectarse.

Fijate también que provisoriamente el router al que te vas a conectar haga las cosas mas fáciles.

---

### Post by biale on 2010-11-19
Buscando algo que no tenía mucho que ver, encontre que efectivamente puede no haber soporte instalado para el chip.

Pero podría agregarse desde launchpad:

[https://launchpad.net/ath9k-htc-installer](https://launchpad.net/ath9k-htc-installer)

O bien con este debian:

[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)

---

### Post by asterix77 on 2010-11-19
Raro el tema, tengo ese mismo modelo y uso la versión 10.04 de ubuntu, y fue reconocido sin hacer nada. 

Al parecer ubuntu te lo reconoce por tu lsusb.

Deberías postear la salida de lsmod para saber si el módulo está cargado.

¿tal vez falta el firmware?.

Deberías revisar esta página, tal vez te sirva de algo.

[http://wireless.kernel.org/en/users/Drivers/ath9k_htc](http://wireless.kernel.org/en/users/Drivers/ath9k_htc)


Saludos

PD: En realidad para conectarme vía wifi prefiero wicd, ya que si mal no recuerdo para hacerlo por network-manager tuve problemas.

Nota: Encontré este otro tutorial: [http://leonardom.wordpress.com/2010/05/24/install-wireless-usb-adapter-tl-wn721n-driver-on-ubuntu-10-4/](http://leonardom.wordpress.com/2010/05/24/install-wireless-usb-adapter-tl-wn721n-driver-on-ubuntu-10-4/)

Saludos

---

### Post by maximo68 on 2010-11-25
Con el paquete ath9k-htc reconocio el hardware ahora esta reconocido y funcionando.
Ahora voy por la impresora (lexmark z515) tengo un problema parecido 
 
:D Gracias a todos
 
> **biale said:**
> Buscando algo que no tenía mucho que ver, encontre que efectivamente puede no haber soporte instalado para el chip.
 
Pero podría agregarse desde launchpad:
 
[https://launchpad.net/ath9k-htc-installer](https://launchpad.net/ath9k-htc-installer)
 
O bien con este debian:
 
[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)

---

