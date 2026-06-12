---
title: "instalar webcam genius i-look 1321 v1"
date: 2009-09-07
forum: Hardware
---

### Post by capv on 2009-09-07
alguien me puede ayudar a instalar una webcam genius i-look 1321 v1 en kubuntu 8.04

---

### Post by natali eduardo on 2009-09-07
Hola, que version de ubuntu tenes?



Muchas cámaras funcionan por defecto en Ubuntu,


Existe una excelente aplicación llamada [Camorama]("http://camorama.fixedgear.org/") para ver, modificar y guardar imagenes desde una **webcam**, podes instalarlo con synaptic o por consola así: 

 sudo apt-get install camorama
xawtv es otra aplicación que puedes usar para probar tu cámara.  
 sudo apt-get install xawtv

Sino EasyCamLos programas que tienen soporte para webcams son:  [aMSN]("http://doc.ubuntu-es.org/AMSN"), [kopete]("http://doc.ubuntu-es.org/Kopete"), [ekiga]("http://doc.ubuntu-es.org/Ekiga") y  [Skype 2.0]("http://www.skype.com/download/skype/linux/choose/").

Mira acá sino:
[http://doc.ubuntu-es.org/Webcam#Usar_la_webcam](http://doc.ubuntu-es.org/Webcam#Usar_la_webcam)

Saludos Edu..

---

### Post by guillermolisi on 2009-09-07
> **capv said:**
> alguien me puede ayudar a instalar una webcam genius i-look 1321 v1 en kubuntu 8.04
Conecta la camara, reinicia el equipo y en una consola/terminal corre "lsusb" (sin las comillas) y pega aqui la salida que te devuelva, asi sabremos que chip usa esa camara.

---

### Post by capv on 2009-09-08
> **natali eduardo said:**
> Hola, que version de ubuntu tenes?
 
 
 
Muchas cámaras funcionan por defecto en Ubuntu,
 
 
Existe una excelente aplicación llamada [Camorama]("http://camorama.fixedgear.org/") para ver, modificar y guardar imagenes desde una **webcam**, podes instalarlo con synaptic o por consola así: 
 
sudo apt-get install camorama
xawtv es otra aplicación que puedes usar para probar tu cámara. 
sudo apt-get install xawtv
 
Sino EasyCamLos programas que tienen soporte para webcams son: [aMSN]("http://doc.ubuntu-es.org/AMSN"), [kopete]("http://doc.ubuntu-es.org/Kopete"), [ekiga]("http://doc.ubuntu-es.org/Ekiga") y [Skype 2.0]("http://www.skype.com/download/skype/linux/choose/").
 
Mira acá sino:
[http://doc.ubuntu-es.org/Webcam#Usar_la_webcam](http://doc.ubuntu-es.org/Webcam#Usar_la_webcam)
 
Saludos Edu..
 
tengo la verion kubuntu 8.04,  instale primero la 6.06 con un cd y despues por internet actualice a kubuntu 8.04, por que en ese momento era lo mas estable, ahora compre un webcam y dudo si actualice correctamente ya que no me reconoce la webcam.

---

### Post by natali eduardo on 2009-09-08
Hola, en mi caso en ubuntu 8.04 y 9.04 andubo bien, no te recomiendo hacer upgrades por internet como describis, es mejor formatear e instalar con el cd desde cero. Como te fue probaste lo que te puse? la camaras genius por lo general funcionan, yo tengo una china de $35 que no tiene marca, y funciona muy bien.. Saludos Edu..

---

### Post by Hei Ku on 2009-09-08
> **natali eduardo said:**
> Hola, en mi caso en ubuntu 8.04 y 9.04 andubo bien, no te recomiendo hacer upgrades por internet como describis, es mejor formatear e instalar con el cd desde cero. Como te fue probaste lo que te puse? la camaras genius por lo general funcionan, yo tengo una china de $35 que no tiene marca, y funciona muy bien.. Saludos Edu..

La recomendacion de no hacer upgrade es totalmente desacertada. De hecho, es experiencia de cada uno, pero que quede claro que es solo una preferencia.

Como ejemplo, yo vengo actualizando mi version desde la 6.10 sin problemas.
El problema puede tener que ver con que los drivers estan en el kernel y puede ser que no esten incluidos en el kernel de la 8.04, pero sí en los de la 9.04.

---

### Post by capv on 2009-09-08
> **guillermolisi said:**
> Conecta la camara, reinicia el equipo y en una consola/terminal corre "lsusb" (sin las comillas) y pega aqui la salida que te devuelva, asi sabremos que chip usa esa camara.

la primera linea es la webcam, lo comprobe desconectandola
root@cesar-desktop:/usr/src# lsusb
Bus 005 Device 008: ID 0458:704c KYE Systems Corp. (Mouse Systems)
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0458:003a KYE Systems Corp. (Mouse Systems)
Bus 001 Device 001: ID 0000:0000

despues segui los pasos del siguiente link "http://doutdex.wordpress.com/2007/05/13/como-agregar-camara-web-webcam-a-ubuntu/"

paso 3) instalando unp y gspca-source dice que hay dependencias incumplidas.

paso 4) desempaquetando  		@page { size: 21.59cm 27.94cm; margin: 2cm } 		P { margin-bottom: 0.21cm } 	--> 	  unp gspca-source.tar.bz2
 encuentro que ese archivo no existe y termino desempaquetando gspca.tar.bz2 que es el que tengo en el dierctorio

paso 5) tengo que instalar el parche que se indica en uno de los comentarios del link de donde estoy siguiendo los pasos.

arriba esta el resumen de lo que pude hacer, abajo esta todo lo que salia de la konsole cuando lo estaba haciendo. al fin de la historia todavia no funciona la webcam podrian ayudarme.



root@cesar-desktop:~# sudo rmmod gspca
root@cesar-desktop:~# sudo rmmod sn9c102
ERROR: Module sn9c102 does not exist in /proc/modules
root@cesar-desktop:~#
root@cesar-desktop:~# ls
cache-cesar-desktop      path.tar.gz         socket-cesar-desktop
gspcav1-20071224         quickcamE2500.diff  tmp-cesar-desktop
gspcav1-20071224.tar.gz  share               video0
root@cesar-desktop:~# cd usr/src/modules
-su: cd: usr/src/modules: No existe el fichero ó directorio
root@cesar-desktop:~# cd /usr/src/modules
root@cesar-desktop:/usr/src/modules# sudo apt-get install build-essential
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct
the problem.
root@cesar-desktop:/usr/src/modules#
root@cesar-desktop:/usr/src/modules# sudo dpkg --configure -a
Configurando libalsa-ocaml (0.1.2-2ubuntu1) ...
Configurando libavahi-client-dev (0.6.22-2ubuntu4.1) ...
Configurando ledit (1.15-1) ...
Configurando ocaml-base (3.10.0-8) ...
Configurando changetrack (4.3-3) ...

Configurando interchange (5.5.1-1) ...
Adding system group: interchange.
Agregando grupo `interchange' (GID 124) ...
Terminado.
Adding system user: interchange.
Aviso: El directorio /usr/lib/interchange que especificó ya existe.
Añadiendo usuario del sistema `interchange' (UID 115) ...
Agregando nuevo usuario `interchange' (UID 115) con grupo `interchange' ...
El directorio personal '/usr/lib/interchange' ya existe.  No se lo copia desde '
/etc/skel'.
adduser: Precaución: El directorio personal `/usr/lib/interchange'  no pertenece
 al usuario que se esta creando actualmente.
chown: no se puede acceder a «/var/run/interchange»: No existe el fichero ó dire
ctorio
Starting Interchange Server: [: 15: Illegal number:
Low traffic settings.
Action 'sha1' did not compile correctly (Can't locate Digest/SHA1.pm in @INC (@I
NC contains: /usr/lib/interchange /usr/lib/interchange/lib /etc/perl /usr/local/
lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/
lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 256) line
1, <SYSTAG> line 19.
BEGIN failed--compilation aborted at (eval 256) line 1, <SYSTAG> line 19.
).
Interchange V5.5.1
Running with old signals.
***************************************************************
***************************************************************
****                                                       ****
****  You are running a Perl with threads enabled -- this  ****
****  is not recommended for a production environment.     ****
****                                                       ****
****  If the Interchange daemon does not start, add this   ****
****  line to interchange.cfg:                             ****
****                                                       ****
****    Variable MV_GETPPID_BROKEN  1                      ****
****                                                       ****
****  Then restart the server.                             ****
****                                                       ****
***************************************************************
***************************************************************

Configurando rrdtool (1.2.19-1ubuntu1) ...
Configurando libagrep-ocaml (1.0-9) ...
Configurando ocaml-interp (3.10.0-8) ...

Configurando libao-ocaml (0.1.7.1-4build1) ...
Configurando librrds-perl (1.2.19-1ubuntu1) ...
Configurando libgtkspell-dev (2.0.10-4) ...
Configurando ocaml-nox (3.10.0-8) ...

Configurando emacs22 (22.1-0ubuntu10.1) ...
Byte-compiling add-on packages, please wait... done.

Configurando libgnorbagtk0 (1.4.2-37ubuntu1) ...

Configurando bbdb (2.35.cvs20060204-1.1ubuntu1) ...
install/bbdb: Ignoring Flavor emacs ...
install/bbdb: Byte-compiling for emacs22 ...
Generating bbdb-autoloads...
Byte-compiling bbdb. This takes looooooong...
 done.

Configurando libbenchmark-ocaml-dev (0.6-7) ...

Configurando camlidl (1.05-10) ...
dpkg: problemas de dependencias impiden la configuración de cvs-mailcommit:
 cvs-mailcommit depende de postfix | mail-transport-agent; sin embargo:
  El paquete `postfix' no está instalado.
  El paquete `mail-transport-agent' no está instalado.
dpkg: error al procesar cvs-mailcommit (--configure):
 problemas de dependencias - se deja sin configurar
Configurando liblablgtk2-ocaml (2.10.0-2) ...
Configurando flow-tools (1:0.68-11) ...
Starting flow-capture: flow-capture.

Configurando libhtml-table-perl (2.04a-1) ...
Configurando libappconfig-perl (1.56-2) ...
Configurando libesd0-dev (0.2.38-0ubuntu9) ...
Configurando dvbackup (0.0.4rj1-6) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Configurando imlib-base (1.9.15-6) ...
Configurando libconfigreader-perl (0.5-4) ...
Configurando libxmu-dev (2:1.0.4-1) ...
Configurando libao-ocaml-dev (0.1.7.1-4build1) ...
Configurando camaelon.app (0+20060914+dfsg-2) ...
Configurando libcarp-clan-perl (5.9-2) ...
Configurando libbonobo2-dev (2.22.0-0ubuntu1) ...
Configurando libart-2.0-dev (2.3.20-1) ...
Configurando binstats (1.08-8) ...
Configurando libagrep-ocaml-dev (1.0-9) ...

Configurando libglade2-dev (1:2.6.2-1) ...

Configurando interchange-ui (5.5.1-1) ...
Starting Interchange Server: [: 15: Illegal number:
Low traffic settings.
Calling UI...
Action 'sha1' did not compile correctly (Can't locate Digest/SHA1.pm in @INC (@I
NC contains: /usr/lib/interchange /usr/lib/interchange/lib /etc/perl /usr/local/
lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/
lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 280) line
1, <SYSTAG> line 19.
BEGIN failed--compilation aborted at (eval 280) line 1, <SYSTAG> line 19.
).
...UI is loaded...
Interchange V5.5.1
Running with old signals.
***************************************************************
***************************************************************
****                                                       ****
****  You are running a Perl with threads enabled -- this  ****
****  is not recommended for a production environment.     ****
****                                                       ****
****  If the Interchange daemon does not start, add this   ****
****  line to interchange.cfg:                             ****
****                                                       ****
****    Variable MV_GETPPID_BROKEN  1                      ****
****                                                       ****
****  Then restart the server.                             ****
****                                                       ****
***************************************************************
***************************************************************

Configurando libxml-light-ocaml-dev (2.2-8) ...

Configurando flowscan (1.006-12) ...
Configurando ocaml (3.10.0-8) ...

Configurando libalsa-ocaml-dev (0.1.2-2ubuntu1) ...

Configurando liblablgtk2-ocaml-dev (2.10.0-2) ...

Configurando camlp4 (3.10.0-8) ...
Configurando libxaw-headers (2:1.0.4-1) ...
Configurando gdk-imlib11 (1.9.15-6) ...

Configurando libbit-vector-perl (6.4-6) ...
Configurando flowscan-cuflow (1.7-2) ...
Configurando camlp4-extra (3.10.0-8) ...
Configurando libcameleon-ocaml-dev (1.9.18.svn20070918-1build1) ...

Configurando cameleon (1.9.18.svn20070918-1build1) ...

Configurando libgnome32 (1.4.2-37ubuntu1) ...

Configurando gnome-libs-data (1.4.2-37ubuntu1) ...

Configurando libgnomeui32 (1.4.2-37ubuntu1) ...

Configurando libgnomesupport0 (1.4.2-37ubuntu1) ...

Configurando libgnorba27 (1.4.2-37ubuntu1) ...

Configurando gnome-bin (1.4.2-37ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Se encontraron errores al procesar:
 cvs-mailcommit
root@cesar-desktop:/usr/src/modules# sudo apt-get install build-essential
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
build-essential ya está en su versión más reciente.
Tal vez quiera ejecutar `apt-get -f install' para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
  cvs-mailcommit: Depende: postfix pero no va a instalarse o
                           mail-transport-agent
E: Dependencias incumplidas. Intente 'apt-get -f install' sin paquetes (o especi
fique una solución).
root@cesar-desktop:/usr/src/modules# lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0458:003a KYE Systems Corp. (Mouse Systems)
Bus 001 Device 001: ID 0000:0000
root@cesar-desktop:/usr/src/modules# cd ..
root@cesar-desktop:/usr/src# lsusb
Bus 005 Device 008: ID 0458:704c KYE Systems Corp. (Mouse Systems)
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0458:003a KYE Systems Corp. (Mouse Systems)
Bus 001 Device 001: ID 0000:0000
root@cesar-desktop:/usr/src# lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0458:003a KYE Systems Corp. (Mouse Systems)
Bus 001 Device 001: ID 0000:0000
root@cesar-desktop:/usr/src# cd ..
root@cesar-desktop:/usr# cd ..
root@cesar-desktop:/# apt-get install gspca-source unp
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
gspca-source ya está en su versión más reciente.
unp ya está en su versión más reciente.
Tal vez quiera ejecutar `apt-get -f install' para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
  cvs-mailcommit: Depende: postfix pero no va a instalarse o
                           mail-transport-agent
E: Dependencias incumplidas. Intente 'apt-get -f install' sin paquetes (o especi
fique una solución).
root@cesar-desktop:/# cd /usr/scr
-su: cd: /usr/scr: No existe el fichero ó directorio
root@cesar-desktop:/# cd /usr/src
root@cesar-desktop:/usr/src#
root@cesar-desktop:/usr/src# unp gspca-source.tar.bz2
gspca-source.tar.bz2: not found
bunzip2: Can't open input file gspca-source.tar.bz2: No such file or directory.
tar: Esto no parece un archivo tar
tar: Salida con error demorada desde errores anteriores
gspca-source.tar.bz2 - unknown extension, checking with file
bunzip2: Can't open input file gspca-source.tar.bz2: No such file or directory.
tar: Esto no parece un archivo tar
tar: Salida con error demorada desde errores anteriores
root@cesar-desktop:/usr/src# cd /modules
-su: cd: /modules: No existe el fichero ó directorio
root@cesar-desktop:/usr/src# cd ..
root@cesar-desktop:/usr# cd ..
root@cesar-desktop:/# cd /usr/src/modules
root@cesar-desktop:/usr/src/modules# unp gspca-source.tar.bz2
gspca-source.tar.bz2: not found
bunzip2: Can't open input file gspca-source.tar.bz2: No such file or directory.
tar: Esto no parece un archivo tar
tar: Salida con error demorada desde errores anteriores
gspca-source.tar.bz2 - unknown extension, checking with file
bunzip2: Can't open input file gspca-source.tar.bz2: No such file or directory.
tar: Esto no parece un archivo tar
tar: Salida con error demorada desde errores anteriores
root@cesar-desktop:/usr/src/modules# cd /usr/src
root@cesar-desktop:/usr/src# unp gspca-source.tar.bz2
gspca-source.tar.bz2: not found
bunzip2: Can't open input file gspca-source.tar.bz2: No such file or directory.
tar: Esto no parece un archivo tar
tar: Salida con error demorada desde errores anteriores
gspca-source.tar.bz2 - unknown extension, checking with file
bunzip2: Can't open input file gspca-source.tar.bz2: No such file or directory.
tar: Esto no parece un archivo tar
tar: Salida con error demorada desde errores anteriores
root@cesar-desktop:/usr/src# cd ..
root@cesar-desktop:/usr# cd ..
root@cesar-desktop:/# unp gspca-source.tar.bz2
gspca-source.tar.bz2: not found
bunzip2: Can't open input file gspca-source.tar.bz2: No such file or directory.
tar: Esto no parece un archivo tar
tar: Salida con error demorada desde errores anteriores
gspca-source.tar.bz2 - unknown extension, checking with file
bunzip2: Can't open input file gspca-source.tar.bz2: No such file or directory.
tar: Esto no parece un archivo tar
tar: Salida con error demorada desde errores anteriores
root@cesar-desktop:/# cd /usr
root@cesar-desktop:/usr# unp gspca-source.tar.bz2
gspca-source.tar.bz2: not found
bunzip2: Can't open input file gspca-source.tar.bz2: No such file or directory.
tar: Esto no parece un archivo tar
tar: Salida con error demorada desde errores anteriores
gspca-source.tar.bz2 - unknown extension, checking with file
bunzip2: Can't open input file gspca-source.tar.bz2: No such file or directory.
tar: Esto no parece un archivo tar
tar: Salida con error demorada desde errores anteriores
root@cesar-desktop:/usr# cd /src
-su: cd: /src: No existe el fichero ó directorio
root@cesar-desktop:/usr# cd/usr/src
-su: cd/usr/src: No existe el fichero ó directorio
root@cesar-desktop:/usr# cd /usr/src
root@cesar-desktop:/usr/src# unp gspca-source.tar.bz2
gspca-source.tar.bz2: not found
bunzip2: Can't open input file gspca-source.tar.bz2: No such file or directory.
tar: Esto no parece un archivo tar
tar: Salida con error demorada desde errores anteriores
gspca-source.tar.bz2 - unknown extension, checking with file
bunzip2: Can't open input file gspca-source.tar.bz2: No such file or directory.
tar: Esto no parece un archivo tar
tar: Salida con error demorada desde errores anteriores
root@cesar-desktop:/usr/src# gspca.tar.bz2
-su: gspca.tar.bz2: orden no encontrada
root@cesar-desktop:/usr/src# unp gspca.tar.bz2
modules/
modules/gspca/
modules/gspca/debian/
modules/gspca/debian/rules
modules/gspca/debian/control.modules.in
modules/gspca/debian/postinst.modules.in
modules/gspca/debian/control
modules/gspca/debian/compat
modules/gspca/debian/copyright
modules/gspca/debian/changelog
modules/gspca/Mars-Semi/
modules/gspca/Mars-Semi/mr97311.h
modules/gspca/decoder/
modules/gspca/decoder/gspcadecoder-OSX.c
modules/gspca/decoder/gspcadecoder.c
modules/gspca/decoder/gspcadecoder-OSX.h
modules/gspca/decoder/gspcadecoder.h
modules/gspca/Transvision/
modules/gspca/Transvision/tv8532.h
modules/gspca/Sonix/
modules/gspca/Sonix/sonix.h
modules/gspca/Sonix/sn9cxxx.h
modules/gspca/Sunplus/
modules/gspca/Sunplus/spca561.h
modules/gspca/Sunplus/spca501_init.h
modules/gspca/Sunplus/spca501.dat
modules/gspca/Sunplus/spca506.h
modules/gspca/Sunplus/spca508.dat
modules/gspca/Sunplus/spca508_init-OSX.h
modules/gspca/Sunplus/spca501_init-OSX.h
modules/gspca/Sunplus/spca505_init.h
modules/gspca/Sunplus/spca508_init.h
modules/gspca/Sunplus/spca561-OSX.h
modules/gspca/Sunplus/spca505.dat
modules/gspca/utils/
modules/gspca/utils/spcaCompat.h
modules/gspca/utils/spcagamma.h
modules/gspca/utils/spcausb.h
modules/gspca/Etoms/
modules/gspca/Etoms/et61xx51.h
modules/gspca/Sunplus-jpeg/
modules/gspca/Sunplus-jpeg/sp5xxfw2.h
modules/gspca/Sunplus-jpeg/spca500_init.h
modules/gspca/Sunplus-jpeg/sp5xxfw2.dat
modules/gspca/Sunplus-jpeg/jpeg_qtables.h
modules/gspca/Sunplus-jpeg/spca500.dat
modules/gspca/Vimicro/
modules/gspca/Vimicro/pas106b.h
modules/gspca/Vimicro/vc032x_sensor.h
modules/gspca/Vimicro/pb0330.h
modules/gspca/Vimicro/tas5130c_vf0250.h
modules/gspca/Vimicro/tas5130c.h
modules/gspca/Vimicro/cs2102.h
modules/gspca/Vimicro/hv7131c.h
modules/gspca/Vimicro/vc032x.h
modules/gspca/Vimicro/zc3xx.h
modules/gspca/Vimicro/hdcs2020.h
modules/gspca/Vimicro/ov7630c.h
modules/gspca/Vimicro/icm105a.h
modules/gspca/Vimicro/hv7131b.h
modules/gspca/Pixart/
modules/gspca/Pixart/pac7311.h
modules/gspca/Pixart/pac207-OSX.h
modules/gspca/Pixart/pac207.h
modules/gspca/Conexant/
modules/gspca/Conexant/cx11646.h
modules/gspca/Conexant/cxlib.h
modules/gspca/Makefile.kld
modules/gspca/gspca_core.c
modules/gspca/gspca_build
modules/gspca/Makefile
modules/gspca/changelog
modules/gspca/gspca.h
root@cesar-desktop:/usr/src# cd /usr/src/modules
root@cesar-desktop:/usr/src/modules# make
make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Al
to.
root@cesar-desktop:/usr/src/modules# make clean
make: *** No hay ninguna regla para construir el objetivo `clean'.  Alto.
root@cesar-desktop:/usr/src/modules# make
make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Al
to.
root@cesar-desktop:/usr/src/modules# sudo make install
make: *** No hay ninguna regla para construir el objetivo `install'.  Alto.
root@cesar-desktop:/usr/src/modules# make clean
make: *** No hay ninguna regla para construir el objetivo `clean'.  Alto.
root@cesar-desktop:/usr/src/modules# make install
make: *** No hay ninguna regla para construir el objetivo `install'.  Alto.
root@cesar-desktop:/usr/src/modules# sudo apt-get install build-essential
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
build-essential ya está en su versión más reciente.
Tal vez quiera ejecutar `apt-get -f install' para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
  cvs-mailcommit: Depende: postfix pero no va a instalarse o
                           mail-transport-agent
E: Dependencias incumplidas. Intente 'apt-get -f install' sin paquetes (o especi               fique una solución).
root@cesar-desktop:/usr/src/modules# make clean
make: *** No hay ninguna regla para construir el objetivo `clean'.  Alto.
root@cesar-desktop:/usr/src/modules# cd /usr/src/modules/gspca
root@cesar-desktop:/usr/src/modules/gspca# make clean
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
        .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
        *.symvers *.err
root@cesar-desktop:/usr/src/modules/gspca# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/gspca CC=cc modul               es
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-24-386'
scripts/Makefile.build:46: *** CFLAGS was changed in "/usr/src/modules/gspca/Mak               efile". Fix it to use EXTRA_CFLAGS.  Alto.
make[1]: *** [_module_/usr/src/modules/gspca] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-24-386'
make: *** [default] Error 2
root@cesar-desktop:/usr/src/modules/gspca# cd /usr/src/modules/gspca/gspcav1-20071224
root@cesar-desktop:/usr/src/modules/gspca/gspcav1-20071224# #patch -p1 < cs2102k_and_tas5130ck_gspcav1-20071224.patch
root@cesar-desktop:/usr/src/modules/gspca/gspcav1-20071224# make clean
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
        .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
        *.symvers *.err
root@cesar-desktop:/usr/src/modules/gspca/gspcav1-20071224# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/gspca/gspcav1-20071224 CC=cc modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-24-386'
  CC [M]  /usr/src/modules/gspca/gspcav1-20071224/gspca_core.o
sudo make   CC [M]  /usr/src/modules/gspca/gspcav1-20071224/decoder/gspcadecoder.o
  LD [M]  /usr/src/modules/gspca/gspcav1-20071224/gspca.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/src/modules/gspca/gspcav1-20071224/gspca.mod.o
  LD [M]  /usr/src/modules/gspca/gspcav1-20071224/gspca.ko
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-24-386'
root@cesar-desktop:/usr/src/modules/gspca/gspcav1-20071224# sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae
root@cesar-desktop:/usr/src/modules/gspca/gspcav1-20071224# sudo modprobe gspca
root@cesar-desktop:/usr/src/modules/gspca/gspcav1-20071224# cd ..
root@cesar-desktop:/usr/src/modules/gspca# cd ..
root@cesar-desktop:/usr/src/modules# cd ..
root@cesar-desktop:/usr/src# cd ..
root@cesar-desktop:/usr# cd ..
root@cesar-desktop:/#

---

### Post by capv on 2009-09-08
> **natali eduardo said:**
> Hola, en mi caso en ubuntu 8.04 y 9.04 andubo bien, no te recomiendo hacer upgrades por internet como describis, es mejor formatear e instalar con el cd desde cero. Como te fue probaste lo que te puse? la camaras genius por lo general funcionan, yo tengo una china de $35 que no tiene marca, y funciona muy bien.. Saludos Edu..

me aparece una ventana con el siguinet mensaje: 
could no connect to video device (/dev/video). please cheak connection.

no lo puedo utilizar.

tampoco puedo usar cheese.

pd: estas segura que pudiste hacer funcionar esta webcam genius i-look 1321 v1 ; pregunto por que existe un modelo genius i-look 1321 v2.

---

### Post by capv on 2009-09-08
> **Hei Ku said:**
> La recomendacion de no hacer upgrade es totalmente desacertada. De hecho, es experiencia de cada uno, pero que quede claro que es solo una preferencia.

Como ejemplo, yo vengo actualizando mi version desde la 6.10 sin problemas.
El problema puede tener que ver con que los drivers estan en el kernel y puede ser que no esten incluidos en el kernel de la 8.04, pero sí en los de la 9.04.


osea que me recomiendas actualizar la version de kubuntu 8.04 a 8.10 o 9.04

---

### Post by guillermolisi on 2009-09-08
> **capv said:**
> osea que me recomiendas actualizar la version de **kubuntu** 8.04 a 8.10 o 9.04
Si, esta recomendando eso y aprovecho para hacer un comentario antes de que pongas manos a la obra.

Si actualizas a 8.10 podras seguir usando KDE3.5 pero si vas a la 9.04 usaras KDE4 que deberias llevarlo a la version 4.3 que anda muy bien, mucho mejor que las anteriores 4 a 4.2

---

