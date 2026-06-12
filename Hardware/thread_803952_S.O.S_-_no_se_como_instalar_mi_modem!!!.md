---
title: "S.O.S - no se como instalar mi modem!!!"
date: 2008-05-22
forum: Hardware
---

### Post by maxkcr on 2008-05-22
tengo en casa ubuntu 7.10 FF y hasta ahora me conectaba desde windows via dial-up. trate de hacer lo mismo en ubuntu pero no marca ni nada. supongo que el problema debe ser que no me esta tomando el modem... 
pero voy a readme de los driver para linux que me vinieron con el modem y no entiendo que es lo que tengo que hacer!!!
transcribo el archivo:

[B]Installation
============

1. Unpack tar.gz package file:

	$ gzip -dc slmodem-2.9.X.tar.gz | tar xf -

2. 'cd' to package directory:

	$ cd slmodem-2.9.X

3. Review and edit 'Makefile' (if need):

   In many cases you will need to correct path to your local kernel
   source tree:

        KERNEL_DIR=/path/to/linux

   Default KERNEL_DIR is '/lib/modules/<kerne-version>/build'. Many Linux
   Distributions use directory '/usr/src/linux-<version>' also.

   Note: If you are using Linux kernel 2.4, only header files should be
         available for build in $(KERNEL_DIR)/include

   Another way to pass right value KERNEL_DIR is to use command line
   parameter while running 'make':

        $ make KERNEL_DIR=/path/to/linux ...

4. Run 'make' command to compile package:

	$ make

5. Install. As 'root' user run:

	# make install

   It will install:

   - application 'slmodemd' under '/usr/sbin' directory

   - hardware specific drivers (kernel modules) 'slamr' and 'slusb'
     under conventional kernel modules directory

   - character device nodes '/dev/slamr0-3' with major number 212
     (for pci modems) and '/dev/slusb0-3' with major number 213
     (for usb modems).

   - config modules for autoloading (by editing file '/etc/modules.conf')
     (only with 2.4 kernels)

6. Config modem country.

   Use AT+GCI=<T.35 country code> command to setup country.

   Also you can setup default modem country by passing command line
   parameter '--country=MY_COUNTRY' to program 'slmodemd'.

   See output of 'slmodemd --countrylist' for a list of supported
   country names and T.35 country codes (see also 'slmodemd --help').

   Note: Command ATI7 shows currently installed country setting.

8. Uninstallation.

   In package directory just type:

	# make uninstall


Getting Started
===============

After successful installation and configuration:

1. Load modem driver.

   Load your modem hardware specific kernel module:

	# modprobe slamr

   if you are using AMR/CNR/PCI modem, or

	# modprobe slusb

   if you are using SmartUSB56 Modem.

   Note: this will be done automatically when modules were
         configured for 'loading on demand'

   Note: this is safe to load both 'alamr' and 'slusb' modules.

2. Run soft modem application.

       # /usr/sbin/slmodemd [options] <device_name>

   Where device name is appropriate device node for your modem
   (look at output of 'dmesg' command).
   Run '/usr/sbin/slmodemd --help' for details.

   Examples:

       # /usr/sbin/slmodemd --country=USA /dev/slamr0

   , or for SmartUSB56 Modems:

       # /usr/sbin/slmodemd --country=ITALY /dev/slusb0

3. Using the modem.

   When 'slmodemd' is running this creates PTY (pseudo-terminal) to
   emulate modem port device, also this creates symbolic link
   like '/dev/ttySL0' (shown at startup).

   Config your application to use this link '/dev/ttySL0' (or PTY node
   itself) as modem port.

   Note: Some application want 'to know' that they are working with
         pseudo-terminal and may require additional configurations.

   Known application notes:

   - 'wvdial' requires option 'Carrier Check = no' in config file

   - some versions of 'kppp' may not work properly with devices named
     like '/dev/ttySL0'. To workaround this you may create symbolic link
     '/dev/modem' ( # ln -s /dev/ttySL0 /dev/modem ) and use this link
     as modem device with 'kppp'

4. Startup automation.

    There are examples of startup scripts in 'scripts' directory.


ALSA mode
=========

ALSA has the built-in modem drivers included in 'alsa-driver' >= 1.0.2
and in Linux kernel >= 2.6.5. Currently there is 'intel8x0m' (snd-intel8x0m)
modem driver, which supports ICH based AC97 modems (MC97).

1. Configure your kernel and enable ALSA and ICH based modem support
   ( 'Device Drivers' -> 'Sound' -> 'Advanced Linux Sound Architecture' ->
     'PCI devices' -> 'Intel i8x0/MX440; AMD768/8111 modems' ) .

2. Build and install kernel and modules as usual (make , make modules_install,
   etc.). ICH modem driver modem module name is 'snd-intel8x0m'
  (if was configured as module).

3. Build application 'slmodemd' with ALSA support. For this in
   slmodem-2.9.x dir:

      $ cd modem
      $ make SUPPORT_ALSA=1

   This will build 'slmodemd' with ALSA support. If compilation is failed
   review Makefile (near ALSA_SUPPORT condition) and define right library
   and/or CFLAGS

4. Use option '--alsa' when running 'slmodemd' and ALSA conventional
   device name ('hw:0' or 'hw:1' for instance). If modem support in
   the kernel was enabled as module module 'snd-intel8x0m' should be loaded.
   When using ALSA modem driver you don't need to load other modules ('slamr').
[/B]

me lo podrian traducir un poco??? pq no me queda claro que tendria que editar del archivo Makefile pq no tengo la ruta /lib/modules/<kerne-version>/build' sino: '/usr/src/linux-headers-2.9.15-20' pero lo cambie por esto y cuando quiero ejecutar el comando $ make KERNEL_DIR=/usr/src/linux-headers-2.9.15-20 me tira un choclo de mensajes entre ellos algunos errores y el modem sigue sin funcionar... ¿¿¿???
El modem es un Smart Link (ni idea el modelo)

---

### Post by damispyderbyte on 2008-05-22
Translation:

Instalación 
============ ============ 

1. 1. Tar.gz desempaquetar los paquetes: paquete tar.gz Desempaquete el archivo: 

$ Gzip-dc slmodem-2.9.X.tar.gz | tar xf - $ gzip-dc slmodem-2.9.X.tar.gz | tar xf -- 

2. 2. 'cd' al paquete de directorio: 'cd' al paquete de directorio: 

$ Cd slmodem-2.9.X $ Slmodem CD-2.9.X 

3. 3. Examen y editar 'Makefile' (si es necesario): Revisar y editar 'Makefile' (si es necesario): 

En muchos casos se necesita para corregir su camino hacia el núcleo local En muchos casos se necesita para corregir su camino hacia el núcleo local 
árbol de código fuente: árbol de código fuente: 

KERNEL_DIR = / ruta / al / linux KERNEL_DIR = / ruta / al / linux 

KERNEL_DIR por defecto es "/ lib / modules / <kerne-version> / construir». El valor predeterminado es KERNEL_DIR '/ lib / modules / <kerne-version> / construir ». Muchas muchas Linux Linux 
Distribuciones uso directorio '/ usr/src/linux- <version>' también. Distribuciones uso directorio '/ usr/src/linux- <version>' también. 

Nota: Si está utilizando el kernel de Linux 2,4, sólo los archivos de cabecera debe Nota: Si está utilizando el kernel de Linux 2,4, sólo los archivos de cabecera debe ser 
disponible para construir en $ (KERNEL_DIR) / include disponible para construir en dólares (KERNEL_DIR) / include 

Otra forma de pasar el valor KERNEL_DIR derecho es a utilizar la línea de comandos Otra forma de pasar derecho KERNEL_DIR valor es utilizar la línea de comandos 
parámetro durante la ejecución de 'hacer': parámetro durante la ejecución de 'hacer': 

$ Make KERNEL_DIR = / ruta / al / linux ... $ Make KERNEL_DIR = / ruta / al / linux ... 

4. 4. Run 'make' para compilar el paquete: Ejecutar 'make' para compilar el paquete: 

Make make $ $ 

5. 5. Instalar. Instalar. Como 'root' usuario ejecute: Como 'root' el usuario debe ejecutar: 

# Make install # make install 

Se instalarán: se instalarán: 

-- La aplicación 'slmodemd' en '/ usr / sbin' - Solicitud 'slmodemd' en '/ usr / sbin' 

-- Controladores de hardware específicos (módulos del kernel) 'slamr' y 'slusb' - controladores de hardware específicos (módulos del kernel) 'slamr' y 'slusb' 
convencionales en virtud de los módulos del kernel directorio Bajo convencionales módulos del kernel Directorio 

-- Dispositivo de caracteres nodos' / dev/slamr0-3 'con mayor número 212 - nodos de dispositivos de caracteres' / dev/slamr0-3' con mayor número 212 
(para el bus PCI modems) y '/ dev/slusb0-3' con mayor número 213 (pci para módems) y '/ dev/slusb0-3' con mayor número 213 
(por usb modems). (para los módems USB). 

-- Configuración de módulos para autoloading (editando el archivo '/ etc / modules.conf') - Config módulos para autoloading (editando el archivo '/ etc / modules.conf') 
(sólo con los núcleos 2,4) (2,4 sólo con los núcleos) 

6. 6. Config modem país. País Configuración módem. 

Use AT + GCI = <T.35 país code> comando para configurar país. Use AT + GCI = <T.35 país code> comando para configurar país. 

También puede configurar modem por defecto país que pasa por línea de comandos también se puede configuración por defecto del módem país que pasa por línea de comandos 
parámetro '- country = MY_COUNTRY' para programar 'slmodemd'. parámetro '- country = MY_COUNTRY' para programar 'slmodemd'. 

Ver la salida de 'slmodemd - countrylist' para una lista de ver la salida de 'slmodemd - countrylist' para una lista de los 
los nombres de países y T.35 códigos de países (ver también 'slmodemd - help'). T.35 los nombres de países y códigos de países (ver también 'slmodemd - help'). 

Nota: Command ATI7 muestra actualmente instalados país. Nota: Command ATI7 muestra actualmente instalados país. 

8. 8. Desinstalación. Desinstalación. 

En el paquete de directorio, sólo tienes que escribir: En tan solo tipo de paquete directorio: 

# # Make uninstall make uninstall 


¿Por dónde empezar ¿Por dónde empezar? 
=============== =============== 

Después de la instalación y configuración: Después del éxito de la instalación y configuración: 

1. 1. Cargar controlador de módem. Cargar controlador de módem. 

Cargue su módem de hardware específicas de módulos del núcleo: La carga de su módem de hardware específicas de módulos del núcleo: 

# Modprobe slamr # modprobe slamr 

si está usando AMR / CNR / PCI modem, o si está usando AMR / CNR / PCI modem, o 

# Modprobe slusb # modprobe slusb 

si está usando SmartUSB56 Modem. si está usando SmartUSB56 Modem. 

Nota: esto se hará automáticamente cuando se módulos Nota: esto se hará automáticamente cuando se módulos 
configurado para "cargar a la demanda" configurado para 'carga en la demanda' 

Nota: este es seguro para cargar tanto »alamr 'y' slusb 'módulos. Nota: este es seguro para cargar tanto »alamr 'y' slusb 'módulos. 

2. 2. Ejecutar aplicación suave módem. Ejecutar aplicación Soft modem. 

# / Usr / sbin / slmodemd [opciones] <device_name> # / usr / sbin / slmodemd [opciones] <device_name> 

En caso de que el nombre del dispositivo es apropiado nodo de dispositivo para su módem Cuando el nombre del dispositivo es apropiado para su módem nodo de dispositivo 
(ver a la salida de 'dmesg'). (ver a la salida de 'dmesg'). 
Run '/ usr / sbin / slmodemd - help' para más detalles. Run '/ usr / sbin / slmodemd - help' para más detalles. 

Ejemplos: Ejemplos: 

# / Usr / sbin / slmodemd - country = EE.UU. / dev/slamr0 # / usr / sbin / slmodemd - country = EE.UU. / dev/slamr0 

, O para SmartUSB56 Modems: o para SmartUSB56 Modems: 

# / Usr / sbin / slmodemd - country = ITALIA / dev/slusb0 # / usr / sbin / slmodemd - country = ITALIA / dev/slusb0 

3. 3. Usando el módem. Usando el módem. 

Cuando 'slmodemd' está funcionando esto crea PTY (pseudo-terminal) Cuando 'slmodemd' está funcionando esto crea PTY (pseudo-terminal) 
puerto de módem emular dispositivo, también crea este enlace simbólico emular dispositivo de puerto del módem, esto también crea enlace simbólico 
como '/ dev/ttySL0' (que se muestra en el arranque). como '/ dev/ttySL0' (que se muestra en el arranque). 

Config su solicitud para utilizar este enlace '/ dev/ttySL0' (PTY o nodo Configure su aplicación a la utilización de este espacio '/ dev/ttySL0' (o nodo HTP 
propiamente dicho) como puerto de módem. propiamente dicho) como puerto de módem. 

Nota: Algunos aplicación quiere 'saber' que están trabajando con Nota: Algunos aplicación quiere 'saber' que están trabajando con 
pseudo-terminal y pueden requerir configuraciones adicionales. pseudo-terminal y pueden requerir configuraciones adicionales. 

Conocido notas de aplicación: Aplicación Conocido Notas: 

-- 'Wvdial' requiere opción 'Carrier Check = no "en fichero de configuración -« Wvdial opción requiere' Carrier Check = no "en fichero de configuración 

-- Algunas versiones de 'kppp' puede que no funcionen correctamente con el nombre de dispositivos - Algunas versiones de 'kppp' puede que no funcione correctamente con los dispositivos de llamada 
como '/ dev/ttySL0'. como '/ dev/ttySL0'. Para esta solución puede crear enlace simbólico a esta solución puede crear enlace simbólico 
'/ dev / modem' (# ln-s / dev/ttySL0 / dev / modem) y el uso de este espacio "/ dev / modem '(# ln-s / dev/ttySL0 / dev / modem) y utilizar este enlace 
como módem con dispositivo 'kppp' como módem con dispositivo 'kppp' 

4. 4. Arranque de automatización. Automatización de arranque. 

Hay ejemplos de scripts de inicio en 'scripts'. Hay ejemplos de scripts de inicio en 'scripts'. 


ALSA ALSA modo modo 
========= ========= 

ALSA ha incorporado en el módem incluido en 'alsa-driver'> = 1.0.2 ALSA ha incorporado en el módem incluido en los conductores' alsa-driver '> = 1.0.2 
y en el kernel de Linux> = 2.6.5. y en el kernel de Linux> = 2.6.5. Actualmente hay 'intel8x0m' (SND-intel8x0m) En la actualidad hay 'intel8x0m' (SND-intel8x0m) 
controlador de módem, que apoya ICH basado AC97 modems (MC97). controlador de módem, que apoya AC97 ICH basado modems (MC97). 

1. 1. Configure su kernel y permitir que ALSA y ICH basado módem Conjunto apoyo de su núcleo y permitirá a ALSA y ICH basado módem apoyo 
( 'Device Drivers' ->' Sound '->' Linux Advanced Sound Architecture "-> ( 'Device Drivers' ->' Sound '->' Linux Advanced Sound Architecture" -> 
Los dispositivos PCI '->' Intel i8x0/MX440; AMD768/8111 modems'). Los dispositivos PCI '->' Intel i8x0/MX440; AMD768/8111 modems'). 

2. 2. Construir e instalar el núcleo y los módulos como de costumbre (make, make modules_install, Construir e instalar el núcleo y los módulos como de costumbre (make, make modules_install, 
etc.) etc) .. ICH controlador de módem módulo módem nombre es "snd-intel8x0m 'ICH controlador de módem módulo módem nombre es" snd-intel8x0m " 
(si se configura como módulo). (si se configura como módulo). 

3. 3. Construir aplicación 'slmodemd' con el apoyo de ALSA. Construir aplicación 'slmodemd' con el apoyo de ALSA. Por esto en Para esto en 
slmodem-2.9.x dir: slmodem-2.9.x Dir: 

$ Cd $ módem módem CD 
$ Make SUPPORT_ALSA = 1 Make $ 1 = SUPPORT_ALSA 

Este se basará 'slmodemd' con el apoyo de ALSA. Este se basará 'slmodemd' con el apoyo de ALSA. Si la compilación no es la compilación Si es Error 
revisión Makefile (cerca de ALSA_SUPPORT condición) y definir derecho de examen biblioteca Makefile (cerca de ALSA_SUPPORT condición) y definir derecho de biblioteca 
y / o CFLAGS y / o CFLAGS 

4. 4. Utilice la opción '- alsa' cuando se ejecuta 'slmodemd' ALSA y Uso convencional opción '- alsa' cuando se ejecuta 'slmodemd' convencionales y ALSA 
nombre de dispositivo ( 'hw: 0 "o" hw: 1' por ejemplo). nombre de dispositivo ( 'hw: 0 "o" hw: 1' por ejemplo). Si el modem de apoyo en caso de módem de apoyo a 
el núcleo se habilitó como módulo módulo 'snd-intel8x0m "debe ser cargada. fue habilitado como módulo del kernel el módulo 'snd-intel8x0m "debe ser cargada. 
Cuando se utiliza ALSA controlador de módem no es necesario cargar otros módulos ( 'slamr'). Cuando se utiliza ALSA driver modem no es necesario cargar otros módulos ( 'slamr').

---

### Post by maxkcr on 2008-05-23
gracias x la intecion pr no se cuanto em dpodria ayudar esa traduccion (la hubiera hecho yo con power traslator)
a ver q puedo hacer

---

