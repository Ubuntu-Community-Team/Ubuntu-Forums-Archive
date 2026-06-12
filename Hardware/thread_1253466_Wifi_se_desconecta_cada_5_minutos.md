---
title: "Wifi se desconecta cada 5 minutos"
date: 2009-08-30
forum: Hardware
---

### Post by akiestudio on 2009-08-30
Hola buenas a todos ,soy nuevo en linux y ubuntu y tengo problemas.

 Mi conexion wifi, estando conectada y navegando , pasados 5 minutos , las paginas nos carga aunque estoy conectado y tengo que volver a reconectarme a la red. como puedo solucionar este problema , muchas gracias.

Alguna ayuda gracias

---

### Post by akiestudio on 2009-08-30
Mirando por ahi  he visto que si voy a configuracion de sistema->administracion-> usuarios y grupos: , mi usuario, y en propiedades, en privilegios de usuario veo que no tengo marcada la opcion de conectar a internet con un moden o , la de conectarse a rede inalambricas,¿Puede ser ese el problema? ¿ Como puedo darme privilegios de usuario como la del root ? 
Hola buenas a todos ,soy nuevo en linux y ubuntu y tengo problemas.
 Mi conexion wifi, estando conectada y navegando , pasados 5 minutos , las paginas nos carga aunque estoy conectado y tengo que volver a reconectarme a la red. como puedo solucionar este problema.
Alguna ayuda gracias

---

### Post by Hei Ku on 2009-08-30
Podes poner en una terminal lspci y postear el resultado aca?

Que usas para conectarte a la wifi? el NetworkManager?

---

### Post by akiestudio on 2009-08-30
fran@fran:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
04:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

El networkmanager lo tengo instalado ,pero no lo localizo y no se si lo estoy usando , creo que si ?

---

### Post by uylug on 2009-08-30
fijate este comando

```
sudo iwconfig wlan0 retry 9999999
```

---

### Post by akiestudio on 2009-08-30
Lo puse en la consola:
sudo iwconfig wlan0 retry 9999999pero no pasa nada , que hace este comando, o que deberia hacer.

---

### Post by uylug on 2009-08-30
Sigue desconectandose? Ese comando de alguna manera aumenta el reintento de envio de la informacion. En general es default 7 que se supera facilmente.

Yo lo tengo que usar todos los dias en casa para hacer andar la wifi.

Fijate que pasa si haces ping al gateway.

```
ping 192.168.1.1
```

---

### Post by akiestudio on 2009-08-31
Me sale esto;


PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.07 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.983 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=2.57 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=1.99 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=2.02 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=1.49 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=1.54 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=1.25 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=3.03 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=0.965 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=0.953 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=1.51 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=0.872 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=0.949 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=1.85 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=1.64 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=64 time=1.19 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=64 time=0.945 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=64 time=1.80 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=64 time=1.68 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=64 time=1.13 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=64 time=1.45 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=64 time=1.98 ms
64 bytes from 192.168.1.1: icmp_seq=24 ttl=64 time=1.15 ms
64 bytes from 192.168.1.1: icmp_seq=25 ttl=64 time=1.09 ms
64 bytes from 192.168.1.1: icmp_seq=26 ttl=64 time=1.38 ms
64 bytes from 192.168.1.1: icmp_seq=27 ttl=64 time=1.54 ms
64 bytes from 192.168.1.1: icmp_seq=28 ttl=64 time=1.58 ms
64 bytes from 192.168.1.1: icmp_seq=29 ttl=64 time=2.25 ms

y no termina nuca....

Ni con ese comando funciona,sigue pasandome, pierdo conexion, alguna idea mas

---

### Post by pabloatilio on 2009-08-31
> **akiestudio said:**
> Hola buenas a todos ,soy nuevo en linux y ubuntu y tengo problemas.

 Mi conexion wifi, estando conectada y navegando , pasados 5 minutos , las paginas nos carga aunque estoy conectado y tengo que volver a reconectarme a la red. como puedo solucionar este problema , muchas gracias.

Alguna ayuda gracias

Yo tuve el mismo problema y era una cuestión de configuración en el router, leyendo vi que había que poner manualmente los DNS por un bug que traía el firmware de ese router y no había en su momento actualización. Cuestión de probar. Saludos.

---

### Post by akiestudio on 2009-09-01
Hola muchas gracias , 

Pero no entiendo esto;

poner manualmente los DNS por un bug que traía el firmware de ese router 

Podrias explicarme como se hace eso:

Gracias, tu ya solucionastes el problema?

---

### Post by Mister X on 2009-09-01
es una laptop?
puede ser problema de temperatura, conozco un caso que le pasaba eso, lo solucionó actualizando la BIOS

---

### Post by pabloatilio on 2009-09-01
> **akiestudio said:**
> Hola muchas gracias , 

Pero no entiendo esto;

poner manualmente los DNS por un bug que traía el firmware de ese router 

Podrias explicarme como se hace eso:

Gracias, tu ya solucionastes el problema?

Así de extraño como suena, pero en mi caso fue la solución. Se trataba de un router de la firma linksys y no quiere decir que va a ser la solución para tu caso, pero es cuestión de probar.

Desconozco tu nivel de conocimiento del tema, así que perdoname si soy muy básico, deberías tener presente cual es la marca y modelo del router que utilizas para conectarte a internet via wi-fi (suponiendo que es tuyo y tenes acceso a él). Luego podrías buscar en internet si esa marca y modelo específico tienen ese problema, no vaya a ser cosa que el problema lo origine el router y no el Sistema Operativo. ¿probaste con otros equipos / sistemas operativos de conectarte? , de ser así ¿ tenés el mismo problema ?.

Para poner manualmente los DNS en el router tenes que saber primero cuales son los números de DNS de tu proveedor de internet (ISP) y luego entrar al router a configurarlo, por lo general a través de un navegador web , introduciendo una dirección del tipo por ej: 192.168.1.1 ; probablemente luego te pedirá un nombre de usuario y contraseña, etc. 

Sería conveniente en caso de que no sepas como hacer estos pasos, consultar el manual del router o la guía de configuración que pudiera traer.

Saludos

---

### Post by akiestudio on 2009-09-01
Muchas gracias, ya entre en el router y ya tenia los dns,puesto....con otro sistema operativo, no hagamo publicidad , que ya bastante * son , no tengo problemas.

Mister X: SI es un laptop , fujitsu siemens amilo pi2550, como se si es problema de temperatura , hay alguna aplicacion que pueda medirtela, como puedo y como se actualiza la bios, el laptop tiene solo 6 meses, alguna idea de que puedo hacer
gracias a todos

---

### Post by sergiom99 on 2009-09-01
La temperatura la podes medir con lm-sensors
1) ```
$ sudo apt-get install lm-sensors
```

2) ```
$ sudo sensors-detect
```

3) ```
$ sensors

[I]acpitz-virtual-0
Adapter: Virtual device
temp1:       +30.0°C  (crit = +95.0°C)

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +27.0°C
Core0 Temp:  +24.0°C
Core1 Temp:  +33.0°C
Core1 Temp:  +31.0°C
[/I]
```

---

### Post by akiestudio on 2009-09-02
[FONT=monospace]Estos son los datos que me dan.

acpitz-virtual-0
Adapter: Virtual device
temp1:       +53.0°C  (crit = +104.0°C) 

Son Altos? y alguna manera de bajar la temperatura, supongo que no ?

Gracias
[/FONT]

---

### Post by sergiom99 on 2009-09-02
> **akiestudio said:**
> [FONT=monospace]Estos son los datos que me dan.

acpitz-virtual-0
Adapter: Virtual device
temp1:       +53.0°C  (crit = +104.0°C) 

Son Altos? y alguna manera de bajar la temperatura, supongo que no ?

Gracias
[/FONT]
Es casi la mitad de la temperatura crítica, así que no parece tan grave. Tambien depende de lo que estes haciendo en ese momento.

Qué tenés dual boot en la laptop? Que configuración de hard tiene? Video?
Para actualizar el BIOS, tenés que buscar updates en la página del fabricante, es específico para tu modelo.

Para que los fans y las zonas de temperatura anden mejor, podes compilarte un DSDT, que es muy sencillo [1]

Yo no buscaría por el lado de la Temp. pero sí trataría de reemplazar NetworkManager por Wicd que maneja mucho mejor las redes wifi y su autenticación.
```
sudo aptitude install wicd
```

Suerte!
[1] [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

---

### Post by akiestudio on 2009-09-02
Muchas gracias 

A que te refieres con ;

Qué tenés dual boot en la laptop? Que configuración de hard tiene? Video?

Y como lo puedo ver..Te refieres a las especificaciones del laptop...

---

### Post by akiestudio on 2009-09-02
Ahora no tengo ni internet , me instale el wicd , y aparzco como conectado pero no puedo navegar , alguna ayuda a configurarlo , uso jazztel y tengo encriptacion wep , una ayuda gracias

---

### Post by sergiom99 on 2009-09-02
> **akiestudio said:**
> Muchas gracias 

A que te refieres con ;

Qué tenés dual boot en la laptop? Que configuración de hard tiene? Video?

Y como lo puedo ver..Te refieres a las especificaciones del laptop...
Exactamente, cual es el procesador, memoria, placa de video, etc.
Eso tal vez pueda orientarnos en la solucion.

Y dual-boot significa eso mismo, un booteo dual entre Ubuntu y otro Sistema Operativo (otro GNU/Linux, un Window$, lo que sea)

---

### Post by Mister X on 2009-09-02
53 grados no es una temperatura demasiado alta, sin embargo como te dijeron arriba hay que tener en cuenta si es la temperatura de la máquina en reposo o con cierta carga. Si tenés 53 grados y el procesador está con poco carga, probablemente te suba unos cuantos grados al hacerlo trabajar mas.

Y por mas que 53 grados estén lejos del limite del procesador, acá el problema no es el micro, sino los otros componentes que puedan estar cerca del micro y se vean afectados por la temperatura que disipa el procesador.

---

### Post by akiestudio on 2009-09-02
Pues perdonar, pero haciendo pruebas , me he cargado el servidor. He metido un script erroneo, porque leei por ahi algo que me confundio y ahora , me sale una pantalla azul donde dice:

Error al iniciar el servidor X(su interfaz grafica): Probablemente no este configurado correctamente.¿Desea ver la salida del servidor x para diagosticarla el problema?

Le dijo que si , me pide usuario y contraseña,y una vez alli me aparece linea de comandos , pero no se como hacerlo , quizas con un Livecd se pueda recuperar, ¿ eso que he j****o es el grub? , soy totalmente ignorante en linux  ayuda....mas ahora que nunca

---

### Post by jjgomera on 2009-09-02
como te manejas con la consola?

lo primero de todo, que demonios estabas haciendo para tocar las X?

prueba primero si tienes una copia del archivo de configuración de las X, en una consola ejecuta:

```
ls /etc/X11/
```

pega también aquí el contenido del archivo /etc/X11/xorg.conf

---

### Post by akiestudio on 2009-09-03
Me aparece los siguiente:

app-defaults
cursors
default-display-manager
fonts
ja_JP.eucJp
ja_JP.UTF-8
x
xinit
xkb
xorg.conf
xorg.conf.20090719135152
 xorg.conf.20090719135300
xorg.conf_backup_2009762130
Xsession
Xsession.d
Xsession.options
XvMCConfig
Xwrapper.config
 

Si hago un ls /etc/X11/xorg.conf

sale 

Not starting K  Display Manager(kdm); it is not the default display manager.

*starting atieventsd    OK
*starting Avahi mDNS/DNS-SD Daemon avahi-daemon  OK
*Starting common Unix Printing system: cupsd                OK
*Starting  system PulseAudio Daemon saned disabled:edit /etc/default/saned
*starting system tools backends system-tools-backends OK
* Enabling additional executable binary formats binfmt-support OK
*starting web server apache2      OK
*checking battery state....
/dev/sda:
setting Advanced Power management level to 0x80(128)
/dev/sda:
setting Advance Power Management level to 0x80(128)    OK
Edit  /etc/default/jackd to start jackd
*Starting TiMidity++ ALSA midi emulation ....
Alsa lib pulse.c:272:(pulse_connect)PulseAudio:Unable to connect : Access denied           FAIL
--------------------------------------------
Lo que hize fue:

Administracion-Preferencias de la ventana de entrada-Seguridad-Configuracion servidor X...
Y donde pone ajuste del servidor 
Nombre del servidor : Lo cambie por otro , 
Comando: Le puse una ruta con script que lei por ahi que podia solucionarme lo de internet , (estaba en ingles) debe ser que no lo entendi bien  y que debia de colocar ahi la ruta donde guarde mi script y entonces llegaron los problemas

Ahi alguna manera de poder restaurarlo .

---

### Post by akiestudio on 2009-09-03
Nadie sabe cual el archivo que puedo editar para que volverlo a poner todo correctamente...
¿Tendre que reinstalar de nuevo ubuntu?

---

### Post by jjgomera on 2009-09-03
no estás siendo muy específico con lo que hiciste, vamos, que no te pido que lo expliques porque es normal que no lo recuerdes todo, pero si hiciste lo que leiste por ahí, pon el enlace de donde lo leiste a ver

> **akiestudio said:**
> 
Si hago un ls /etc/X11/xorg.conf

ese no es el contenido, para verlo en consola sería:
```
cat /etc/X11/xorg.conf
```
pega el contenido aquí antes de pasar a usar las copias de seguridad, que tienes tres, dos de julio

---

### Post by akiestudio on 2009-09-03
Bueno la verdad que no me acuerdo donde lo lei y ademas era para ubuntu 8 ,vamos que la arruiné del todo , lo que si que puedo es decirte que script habia y que le puse, quizas se me ocurre ahora editarlo como el antiguo y a ver que pasa...
este es el script 

#!/bin/sh
sleep 20 
/opt/wicd/tray.py

era para el wicd y la tarjeta de red...

Puedo editar algo desde la consola, porque , aunque tengo windows instalado , cuando voy a home ,no veo mi nombre de usuario y no puedo ir al escritorio que tengo la ruta del fichero correcto, el xorg-fog no creo que este mal...

Este esta es la ruta del archivo original
/usr/x11r6/bin/x-br-audit 0

Asi que se me acaba de ocurrir el , hacer una copia renombrarle con el nombre del que yo hice y guardarlo en la ruta que cambie  voy a probar a ver que pasa y os cuento

---

### Post by akiestudio on 2009-09-03
Bueno parece ser que ese archivo no existe ahora, alguien , me puede decir que pone en ese archivo para que pueda copiarlo y llamarlo con otro nombre el archivo es el :

/usr/X11R6/bin/X -br -audit 0

grascias

---

### Post by Hei Ku on 2009-09-03
ese es un archivo binario, o sea un ejecutable, no un archivo de texto.
Que haces tocando archivos del servidor de video cuando el problema es con la wifi?

---

### Post by akiestudio on 2009-09-04
Pues eso me pregunto yo , que hago tocando algo que desconozco.....
Parece ser que tengo copias de seguridad, creeis que la instalacion de esas copias podria solucionar el problema..? 
Como se hace eso si es que tengo que hacerlo , o directamente formateo el laptop?

---

### Post by Hei Ku on 2009-09-04
Proba con esto, a ver si recupera el archivo:

sudo apt-get install --reinstall xserver-xorg

---

### Post by akiestudio on 2009-09-04
Ya probe y nada , asi que he formateado , ahora ando liado con la tarjeta grafica ati radeon 4550 , a ver si consigo los drivers pero ese es otro tema , gracias a todos

---

