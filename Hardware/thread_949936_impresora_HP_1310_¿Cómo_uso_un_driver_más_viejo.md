---
title: "impresora HP 1310 ¿Cómo uso un driver más viejo?"
date: 2008-10-16
forum: Hardware
---

### Post by valucha on 2008-10-16
[COLOR="DarkOrchid"]hola!

Hace masomenos un mes,en una de las tantas actualizaciones, se actualizó el driver de la impresora Hewlett Packard psc 1310. Y resulta que ese driver tiene un bug que hace que no pueda imprimir más que en rojo.
¿Es posible "volver al controlador anterior"? ¿Cómo?
Gracias!!...


Saludos, Vale[/COLOR]

---

### Post by santiagoward2000 on 2008-10-17
Hola Valucha!
¿Sabés cuál es el paquete de esos drivers? Si sabés, podés abrir Synaptic, seleccionás el paquete ese, y vas a Paquete > Forzar versión. (Ahora creo que estás en KDE, no? Me imagino que Adept debe tener una opción parecida, pero ahí supongo que algún kdeero te podrá guiar).
Suerte!

---

### Post by valucha on 2008-10-17
[COLOR="DarkOrchid"]Bueno, consegui una version mas actualizada en la pagina. Esta en un .run Como hago ahora para forzar el paquete? Porque esta deshabilitada la opcion en el menu.
Gracias por adelantado, y perdon por la falta de tildes, se me desconfiguro el teclado 
[/COLOR]

---

### Post by Mauro22 on 2008-10-17
Para ejecutar un .run decis?

:P

Creo que era

./ aa.run

o

sh aa.run

---

### Post by valucha on 2008-10-17
[COLOR="DarkOrchid"]Es que no se si es exactamente lo que hay que hacer... Porque segun Santi, deberia ponerlo en el synaptic, ahi lo correria y no se si no voy a meter la pata.[/COLOR]

---

### Post by santiagoward2000 on 2008-10-17
> **valucha said:**
> [COLOR="DarkOrchid"]Es que no se si es exactamente lo que hay que hacer... Porque segun Santi, deberia ponerlo en el synaptic, ahi lo correria y no se si no voy a meter la pata.[/COLOR]

No. Lo que yo decía es si la versión vieja está todavía por algún repositorio, con Synaptic podés forzarlo a que vuelva a instalar la vieja y no busque más actualizaciones.
Para instalar un .run, la verdad que no sé cómo se hace.

---

### Post by valucha on 2008-10-17
[COLOR="DarkOrchid"]Ejecute el .run y sigue imprimiendo en rojo. Podre sacar el driver del cd de ubuntu?[/COLOR]

---

### Post by valucha on 2008-10-17
[COLOR="DarkOrchid"]Encontré el driver viejo... lo instalé, pero sigue imprimiendo en rojo...

Sé que es un bug porque [acá]("https://bugs.launchpad.net/hplip/+bug/262841") está aunque con diferente impresora supongo que es el mismo problema.

¿Alguna sugerencia?, me la paso imprimiendo y es molesto tener que ir a Windows...

Esto paso de un momento para el otro, ahora recuerdo que fue porque cambié el cartucho negro que no tenía más por otro negro pero recargado. ¿Podrá ser eso?.  En Windos imprime en negro, y todos los colores que quiera.[/COLOR]

---

### Post by EnriqueK on 2008-10-17
Ejecutá en terminal
 ```
hp-check
```
Seguramente aparecerám algunos errores causados por dependencias faltantes, seguí las instrucciones a ver que tal.

---

### Post by valucha on 2008-10-18
[Color="DarkOrchid"] error: SIP not installed or version not found.


Ese es el único error que me aparece. ¿Cómo puedo arreglarlo? [/Color]

---

### Post by faktorqm on 2008-10-20
Podes postear las salidas completas de los siguientes comandos por favor? (con la impresora enchufada)

```
hp-check -t
```

```
hp-levels
```

```
lsusb
```

Gracias! Salu2!

---

### Post by valucha on 2008-10-20
Como no!..

> hp-check -t

HP Linux Imaging and Printing System (ver. 2.8.5)
Dependency/Version Check Utility ver. 14.0

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux valen-desktop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

Distribution:
ubuntu 8.04

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.2 installed

Checking PyQt version...
OK, version 3.17 installed.

Checking SIP version...
error: SIP not installed or version not found.

Checking for CUPS...
Status: el programa de planificación de tareas se está ejecutando
Version: 1.3.7
error_log is set to level: warn
note: For troubleshooting printing issues, it is best to have the CUPS 'LogLevel'
note: set to 'debug'. To set the LogLevel to debug, edit the file /etc/cups/cupsd.conf (as root),
note: and change the line near the top of the file that begins with 'LogLevel' to read:
note: LogLevel debug
note: Save the file and then restart CUPS (see your OS/distro docs on how to restart CUPS).
note: Now, when you print, helpful debug information will be saved to the file:
note: /var/log/cups/error_log
note: You can monitor this file by running this command in a console/shell:
note: tail -f /var/log/cups/error_log

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.82.4


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: cups - Common Unix Printing System...
OK, found.

Checking for dependency: cups-ddk - CUPS driver development kit...
OK, found.

Checking for dependency: cups-devel- Common Unix Printing System development files...
OK, found.

Checking for dependency: dbus - Message bus system...
OK, found.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency: libjpeg - JPEG library...
OK, found.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
OK, found.

Checking for dependency: libusb - USB library...
OK, found.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt - Qt interface for Python...
OK, found.

Checking for dependency: python-ctypes - A foreign function library for Python...
OK, found.

Checking for dependency: python-dbus - Python bindings for dbus...
OK, found.

Checking for dependency: python-devel - Python development files...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 2.8.5 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hpssd]
# Note: hpssd does not support dynamic ports
# Port 2207 is the IANA assigned port for hpssd
port=2207

[hplip]
version=2.8.5

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
doc=/usr/share/doc/hplip-2.8.5
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp/

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=yes
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=yes
internal-tag=2.8.5.23


-------------------------------
| DISCOVERED PARALLEL DEVICES |
-------------------------------

No devices found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model              
  --------------------------------  -------------------
  hp:/usb/psc_1310_series?serial=B  HP psc 1310 series 
  R4A13H04ZO2                                          

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
warning: No queues found.

----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/psc_1310_series?serial=BR4A13H04ZO2' is a Hewlett-Packard psc_1310_series all-in-one
device `v4l:/dev/video0' is a Noname Genius VideoCAM Express V2 virtual device


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


-----------------
| USB I/O SETUP |
-----------------


Checking for permissions of USB attached printers...
 
HP Device 0x3f11 at 001:003: 
    Device URI: hp:/usb/psc_1310_series?serial=BR4A13H04ZO2
    Device node: /dev/bus/usb/001/003
    Mode: 0666
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/003
# owner: root
# group: lp
user::rw-
group::rw-
other::rw-



-----------
| SUMMARY |
-----------

error: 1 error or warning.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.




>  hp-levels

HP Linux Imaging and Printing System (ver. 2.8.5)
Supply Levels Utility ver. 1.3

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device: hp:/usb/psc_1310_series?serial=BR4A13H04ZO2

HP Linux Imaging and Printing System (ver. 2.8.5)
System Tray Status Service ver. 0.1

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


Black cartridge
Part No.: 27 (C8727AN)/56 (C6656AN)
Health: Good/OK

----------------------------------------------------------------
|////////////////////////////////                              | (approx. 51%)
----------------------------------------------------------------

Tri-color cartridge
Part No.: 28 (C8728AN)/57 (C6657AN)
Health: Good/OK

----------------------------------------------------------------
|//////////////////////////////////////////////////////////    | (approx. 92%)
----------------------------------------------------------------


Done.



> Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:3f11 Hewlett-Packard PSC-1315/PSC-1317
Bus 001 Device 002: ID 0458:7004 KYE Systems Corp. (Mouse Systems) VideoCAM Express
Bus 001 Device 001: ID 0000:0000

---

### Post by faktorqm on 2008-10-20
Me da que no tenes el SIP ese... o que lo tenes pero dejó de encontrarlo... y encima no se que es... ¡a leer!

bueno, la cosa es que podrias empezar por instalar la ultima version de hplip, que la bajas de este link:

[http://sourceforge.net/project/downloading.php?groupname=hplip&filename=hplip-2.8.9.run&use_mirror=ufpr](http://sourceforge.net/project/downloading.php?groupname=hplip&filename=hplip-2.8.9.run&use_mirror=ufpr)

Éste es el tutorial (gráfico) de instalacion que te guia en los distintos pasos:
[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

Ésta es la salida de comandos mia (ya que estaba, me lo instale yo...)

```
faktorqm@the-edge:~/Escritorio$ sh hplip-2.8.9.run 
Creating directory hplip-2.8.9
Verifying archive integrity... All good.
Uncompressing HPLIP 2.8.9 Self Extracting Archive..........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

HP Linux Imaging and Printing System (ver. 2.8.9)
HPLIP Installer ver. 5.0

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Mon-20-Oct-2008_19:50:20.log

|
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to chose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) :  

Initializing. Please wait...
 

INTRODUCTION
------------
This installer will install HPLIP version 2.8.9 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).


DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 8.04.

Is "Ubuntu 8.04" your correct distro/OS and version (y=yes*, n=no, q=quit) ? 


SELECT HPLIP OPTIONS
--------------------
Would you like to enable support for parallel (LPT:) connected printers? (y=yes, n=no*, q=quit) ? 


ENTER ROOT/SUPERUSER PASSWORD
-----------------------------
Please enter the root/superuser password: 
Password accepted


INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: https://help.ubuntu.com/community/Repositories/Ubuntu for more information.  Disable the CD-ROM/DVD source if you do not have the Ubunbtu installation media inserted in the drive.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 


RUNNING PRE-INSTALL COMMANDS
----------------------------


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 3 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: python-devel (python-devel - Python development files)
warning: Missing REQUIRED dependency: cups-devel (cups-devel- Common Unix Printing System development files)
warning: Missing REQUIRED dependency: libusb (libusb - USB library)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 6 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'network': libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
warning: Missing REQUIRED dependency for option 'gui': pyqt (PyQt 3- Qt interface for Python (for Qt version 3.x))
warning: Missing OPTIONAL dependency for option 'gui': pyqt4 (PyQt 4- Qt interface for Python (for Qt version 4.x))
warning: Missing OPTIONAL dependency for option 'fax': reportlab (Reportlab - PDF library for Python)
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scanning library development files)
warning: Missing OPTIONAL dependency for option 'scan': scanimage (scanimage - Shell scanning program)


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
sudo aptitude update (Pre-depend step 3)


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo aptitude install --assume-yes python2.5-dev'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes libcupsys2-dev'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes cupsys-bsd'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes libusb-dev'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes libsnmp-dev'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes python-qt3'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes python-qt4'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes python-reportlab'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes libsane-dev'
Please wait, this may take several minutes...
Running 'sudo aptitude install --assume-yes sane-utils'
Please wait, this may take several minutes...
 

RUNNING POST-PACKAGE COMMANDS
-----------------------------


RE-CHECKING DEPENDENCIES
------------------------
|

[1]+  Stopped                 sh hplip-2.8.9.run
faktorqm@the-edge:~/Escritorio$ 

```

Se colgó! Le tuve que dar un castañaso... Voy a ver si reinicio y reinstalo a ver que hace....... un papelon!!

Ésta es la página donde dice que tu impresora esta correctamente soportada por Ubuntu 8.04:
[http://hplipopensource.com/hplip-web/models/psc/psc_1310_series.html](http://hplipopensource.com/hplip-web/models/psc/psc_1310_series.html)

---

### Post by valucha on 2008-10-21
[COLOR="DarkOrchid"]NO hay caso, sigue rojo.[/COLOR]

---

### Post by faktorqm on 2008-10-22
Y la unica que se me ocurre es que desinstales un par de paquetes y vuelvas a los anteriores y si te vuelve a andar los marques como "para no actualizar" (no se la opcion de memoria)

Tendrias que hacer:

```
sudo apt-get remove hpijs hplip
```

Bajarte estos dos archivos: 

hpijs: [http://mir1.ovh.net/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5_i386.deb](http://mir1.ovh.net/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5_i386.deb)

hplip: [http://ftp.oleane.net/pub/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5_i386.deb](http://ftp.oleane.net/pub/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5_i386.deb)

Instalarlos y probar a ver si anda. Si no anda, probamos otra cosa. Salu2!

---

### Post by valucha on 2008-10-22
[COLOR="DarkOrchid"]Ya lo hice eso, primero conseguí volver al viejo y nada, y ahora con el nuevo tampoco... Pienso que tendrá que ver más con el tema de que cambié el cartucho es trucho (es recargado)[/COLOR]

---

### Post by faktorqm on 2008-10-22
No es eso! ¿acaso en windows imprime en rojo tambien? no, entonces el cartucho no es.

Proba de volver atras la version de CUPS, significa Common Unix Printing System. Los paquetes si mal no recuerdo son cupsys y cupsys-common. Salu2!

---

### Post by EnriqueK on 2008-10-22
Aquí tenés versiones anteriores del hplip, aunque personalmente no creo que sea problemas del driver, yo tengo la HP 13600 y no tengo ningún problema, tal vez est&#347; imprimiendo en negro compuesto y que por tratarse de un cartucho trucho, a lo mejor no funcionan las tintas azul y amarillo , dando como resultado un magenta y si las otras tintas "algo" aportan, daría como resultado un rojo.
[http://sourceforge.net/project/showfiles.php?group_id=149981&package_id=165777](http://sourceforge.net/project/showfiles.php?group_id=149981&package_id=165777)

---

### Post by valucha on 2008-10-22
> **faktorqm said:**
> No es eso! ¿acaso en windows imprime en rojo tambien? no, entonces el cartucho no es.

Proba de volver atras la version de CUPS, significa Common Unix Printing System. Los paquetes si mal no recuerdo son cupsys y cupsys-common. Salu2!

[COLOR="DarkOrchid"]NO me deja forzar la versión y si me bajo desde la pág de los repositorios cualquier versión anterior tampoco me deja instalarla porque hay una versión posterior instalada.[/COLOR]

---

### Post by santiagoward2000 on 2008-10-22
> **valucha said:**
> [COLOR="DarkOrchid"]NO me deja forzar la versión y si me bajo desde la pág de los repositorios cualquier versión anterior tampoco me deja instalarla porque hay una versión posterior instalada.[/COLOR]

¿Y si desinstalás la que está instalada y después instalás la que bajaste de la página? (Después vas a tener que marcar en Synaptic para que no lo actualice)

---

### Post by valucha on 2008-10-22
[COLOR="DarkOrchid"]La versión anterior del cups tampoco soluciona la cosa :S Solo qu8eda el gutenprint[/COLOR]

---

### Post by faktorqm on 2008-10-23
Proba y si no aca pude encontrar finalmente como solucionar el error del SIP.

```
sudo apt-get install libexosip2-4 python2.5-sip4 libusb-0.1-4
```

Despues volve a fijarte si te sigue diciendo que falta SIP. 

Si todo sigue igual, proba de sacar el cartucho negro, e intentar imprimir algo exclusivamente verde, (puede ser un cuadradito chiquito relleno) a ver que hace. 
Despues saca el color y pone solo el negro e intenta lo mismo en escala de grises. Despues volvelo a poner a ver si vuelve a rojo o segun donde haya saltado en alguna de toooodas las pruebas.

Dificil de buscar en internet, encontre pocas cosas... espero se solucione de algun modo. Salu2!

---

### Post by valucha on 2008-10-23
> **faktorqm said:**
> Proba y si no aca pude encontrar finalmente como solucionar el error del SIP.

```
sudo apt-get install libexosip2-4 python2.5-sip4 libusb-0.1-4
```

Despues volve a fijarte si te sigue diciendo que falta SIP. 

Si todo sigue igual, proba de sacar el cartucho negro, e intentar imprimir algo exclusivamente verde, (puede ser un cuadradito chiquito relleno) a ver que hace. 
Despues saca el color y pone solo el negro e intenta lo mismo en escala de grises. Despues volvelo a poner a ver si vuelve a rojo o segun donde haya saltado en alguna de toooodas las pruebas.

Dificil de buscar en internet, encontre pocas cosas... espero se solucione de algun modo. Salu2!
[COLOR="DarkOrchid"]

Lo instalé y seguía apareciendo el error e imprimiendo en rojo.
Probé,lo de sacar el cartucho, pero no podés imprimir si falta alguno de los 2 cartuchos.

Tengo una noticia muchisimo peor...
Reinstalé Ubuntu desde 0, sin conservar más que mis archivos, y sigue imprimiendo rojo, aún antes de actualizar... Es decir, en este momento tengo Hardy limpio limpio, y cuando antes en este momento me imprimia perfecto, ahora imprime rojo.


:( :( :( :(
[/COLOR]

---

### Post by faktorqm on 2008-10-24
> **valucha said:**
> [COLOR="DarkOrchid"]

Lo instalé y seguía apareciendo el error e imprimiendo en rojo.
Probé,lo de sacar el cartucho, pero no podés imprimir si falta alguno de los 2 cartuchos.

Tengo una noticia muchisimo peor...
Reinstalé Ubuntu desde 0, sin conservar más que mis archivos, y sigue imprimiendo rojo, aún antes de actualizar... Es decir, en este momento tengo Hardy limpio limpio, y cuando antes en este momento me imprimia perfecto, ahora imprime rojo.


:( :( :( :(
[/COLOR]

:O ok... tu impresora se enojo con ubuntu....:lolflag:

estas segura que no actualizaste ningun paquete no? y si probas el live cd del 7.10 tambien imprime en rojo? (para descartar no mas, en caso de que ande bien, podes instalar 7.10, marcar los paquetes para que no te los actualice, poner el cd de 8.04 como repositorio, actualizar a 8.04 y ya)
No tenes otro metodo de conexion? (usb. puerto paralelo, ethernet?) eso de que no podes imprimir sin uno de los cartuchos es cualquiera!! deberia dejarte... pero bueno. en windows te sigue funcionando? estas segura que te la toma con tu modelo? ya te estoy preguntando cualquier cosa pero capaz encontramos la solucion... salu2!

---

### Post by valucha on 2008-10-24
> **faktorqm said:**
> :O ok... tu impresora se enojo con ubuntu....:lolflag:

estas segura que no actualizaste ningun paquete no? y si probas el live cd del 7.10 tambien imprime en rojo? (para descartar no mas, en caso de que ande bien, podes instalar 7.10, marcar los paquetes para que no te los actualice, poner el cd de 8.04 como repositorio, actualizar a 8.04 y ya)
No tenes otro metodo de conexion? (usb. puerto paralelo, ethernet?) eso de que no podes imprimir sin uno de los cartuchos es cualquiera!! deberia dejarte... pero bueno. en windows te sigue funcionando? estas segura que te la toma con tu modelo? ya te estoy preguntando cualquier cosa pero capaz encontramos la solucion... salu2!
[COLOR="DarkOrchid"]
NO actualicé NINGUN paquete.
En el live cd ahora lo pruebo.

Tengo otro metodo de conexión, esa fichita parecida a la del usb pero más gordita, pero perdí el cable, o lo tiré.
Me toma perfecto el modelo.
En Windows sigue funcionando.


Me parece que tenemos que encarar la cosa pensando en que cuando cambié el cartucho por uno recargado se **** todo. Pero no es que es trucho! sino que está recargado!. Y la tinta que hay ahi es negra, porque en Windows impirime negro al menos.


Esto me está poniendo loca :(
[/COLOR]

---

