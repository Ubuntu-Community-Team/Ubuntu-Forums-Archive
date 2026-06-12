---
title: "Problemas con mi placa de video ATI"
date: 2012-12-14
forum: Hardware
---

### Post by DaHater on 2012-12-14
Hola! Soy nuevo aca y tambien nuevo en ubuntu (a pesar de haber estado usando otras versiones), en fin.
Ya se que seguramente este es un tema viejo, pero no puedo lograr conseguir la solucion a mi problema, no es por vago, pero me gustaria que me ayuden en forma directa para poder detallar los posibles impedimentos con los que me encuentre.
Instale Ubuntu 12.10 (64 bits) y no me reconoce la placa de video. Las caracteristicas de mi maquina son:
-Mother: MSI 880GGM-E41
-Procesador:AMD Athlon II X4 640 Processor 3.0Ghz
-Ram: DDR3 4GB 
-HDD: 1Tb
-Placa de video onboard: ATI Radeon HD 4250

¿Como debo instalar paso a paso el controlador de la placa de video?

Desde ya muchisimas gracias a aqullos que puedan aportar cualquier ayuda :D

---

### Post by rojojuan on 2012-12-15
> **DaHater said:**
> Hola! Soy nuevo aca y tambien nuevo en ubuntu (a pesar de haber estado usando otras versiones), en fin.
Ya se que seguramente este es un tema viejo, pero no puedo lograr conseguir la solucion a mi problema, no es por vago, pero me gustaria que me ayuden en forma directa para poder detallar los posibles impedimentos con los que me encuentre.
Instale Ubuntu 12.10 (64 bits) y no me reconoce la placa de video. Las caracteristicas de mi maquina son:
-Mother: MSI 880GGM-E41
-Procesador:AMD Athlon II X4 640 Processor 3.0Ghz
-Ram: DDR3 4GB 
-HDD: 1Tb
-Placa de video onboard: ATI Radeon HD 4250

¿Como debo instalar paso a paso el controlador de la placa de video?

Desde ya muchisimas gracias a aqullos que puedan aportar cualquier ayuda :D

Fijate aquí:

[http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/](http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/)

---

### Post by DaHater on 2012-12-15
> **rojojuan said:**
> Fijate aquí:

[http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/](http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/)

Gracias por tu respuesta!
He intentado primero usando el repositor de Tomasz Makarewicz y la pc me reconocio la placa como VESA-RS880. Asi que lo desinstale.

Ahora estoy probando bajandolo desde la pag de AMD (todo desde el terminal), pero cuando ejecuto 
-sudo sh ./amd-driver-installer-*.run --buildpkg Ubuntu/quantal
me aparece esto:

Created directory fglrx-install.EMR56M
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-8.97.100.3....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/quantal
apt 0.9.7.5ubuntu5.1 for amd64 compiled on Dec 12 2012 13:50:19
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
Unable to install dpkg-dev.  Please manually install and try again.
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
Removing temporary directory: fglrx-install.EMR56M

Y entonces al colocar los otros comandos me tira errores :(
¿Que debo hacer?

---

### Post by DaHater on 2012-12-15
Hice 
sudo apt-get install dpkg-dev

Y ahora me aparece:

Created directory fglrx-install.drIJmP
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-8.97.100.3....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/quantal
Resolving build dependencies...
apt 0.9.7.5ubuntu5.1 for amd64 compiled on Dec 12 2012 13:50:19
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
Unable to resolve  debhelper  dh-modaliases execstack.  Please manually install and try again.
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.970-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.HrFDJX
dpkg-buildpackage: host architecture amd64
 debian/rules build
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 fglrx.install \
			 fglrx-dev.install \
			 fglrx-dev.links \
			 fglrx-amdcccle.install \
			 fglrx.grub-gfxpayload \
			 fglrx.dirs \
			 fglrx.links \
			 fglrx.postinst \
			 fglrx.postrm \
			 fglrx.preinst \
			 fglrx.prerm \
			 overrides/fglrx; do \
		sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
			-e "s|#LIBDIR#|usr/lib|g" \
			-e "s|#LIBDIR32#|usr/lib32|g" \
			-e "s|#BINDIR#|usr/bin|g" \
			-e "s|#SYSCONFDIR#|etc|g" \
			-e "s|#MANDIR#|usr/share/man/man1|g" \
			-e "s|#LDSOCONF#|usr/lib/fglrx/ld.so.conf|g" \
			-e "s|#ALTLDSOCONF#|usr/lib/fglrx/alt_ld.so.conf|g" \
			-e "s|#ALTPRIORITY#|1000|g" \
			-e "s|#PXALTPRIORITY#|900|g" \
			-e "s|#AUTOSTARTDIR#|etc/xdg/autostart|g" \
			-e "s|#DATADIR#|usr/share|g" \
			-e "s|#PKGDESKDIR#|usr/share/fglrx|g" \
			-e "s|#PKGDATADIR#|usr/share/fglrx|g" \
			-e "s|#PKGCONFIGDIR#|usr/lib/fglrx|g" \
			-e "s|#PKGBINDIR#|usr/lib/fglrx/bin|g" \
			-e "s|#PKGLIBDIR#|usr/lib/fglrx|g" \
			-e "s|#PKGLIBDIR32#|usr/lib32/fglrx|g" \
			-e "s|#PKGDRIVERSDIR#|usr/lib/fglrx/xorg|g" \
			-e "s|#XORGEXTRA#|usr/lib/x86_64-linux-gnu/xorg/extra-modules|g" \
			-e "s|#PKGEXTENSIONDIR#|usr/lib/fglrx/xorg|g" \
			-e "s|#XORGEXTENSIONSDIR#|usr/lib/xorg/modules/extensions|g" \
			-e "s|#DRIVERNAME#|fglrx|g" \
			-e "s|#DRIVERDEVNAME#|fglrx-dev|g" \
			-e "s|#DRIVERSRCNAME#||g" \
			-e "s|#INCLUDEDIR#|usr/include|g" \
			-e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \
			-e "s|#GRUBBLKLISTDIR#|usr/share/grub-gfxpayload-lists/blacklist|g" \
			-e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
			-e "s|#PXDIR#|usr/lib/pxpress|g" \
			-e "s|#PXDIR32#|usr/lib32/pxpress|g" \
			-e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \
			-e "s|#PXDIRNAME#|pxpress|g" \
			-e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \
			-e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \
			-e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \
			-e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \
			-e "s|#CVERSION#|8.970|g" \
			-e "s|#SRCXARCH#|xpic_64a|g" \
			-e "s|#SRCARCH#|x86_64|g" \
			-e "s|#SRCLIBDIR#|lib64|g" \
			-e "s|#DEB_HOST_MULTIARCH#|x86_64-linux-gnu|g" \
			-e "s|#OTHER_ARCH#|i386-linux-gnu|g" \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		xpic_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
		arch/x86_64/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
make: dh: Command not found
make: *** [build] Error 127
dpkg-buildpackage: error: debian/rules build gave error exit status 2
Removing temporary directory: fglrx-install.drIJmP


Y ahora que? :'(

---

### Post by guillermolisi on 2012-12-15
Por las dudas y para quitar del medio cuestiones de permisos y privilegios, por que no llevas a cabo la instalacion como root ? (sudo su)

---

### Post by dirty fingers on 2012-12-15
y así no se puede ?

```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install fglrx-installer

```

---

### Post by DaHater on 2012-12-16
> **guillermolisi said:**
> Por las dudas y para quitar del medio cuestiones de permisos y privilegios, por que no llevas a cabo la instalacion como root ? (sudo su)
OK! Voy a probarlo en todas las intalaciones que haga.
Gracias :D

---

### Post by DaHater on 2012-12-16
> **dirty fingers said:**
> y así no se puede ?

```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install fglrx-installer

```
Me tira este error :(

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete fglrx-installer

---

### Post by DaHater on 2012-12-16
Paso a detallar los inconvenientes instalando el controlador de AMD:

    1) wget http://www2.ati.com/drivers/legacy/amd-driver-installer-12.6-legacy-x86.x86_64.zip

    2) unzip amd-driver-installer-*

    3) sudo sh ./amd-driver-installer-*.run --buildpkg Ubuntu/quantal
Primer Error:
Unable to install dpkg-dev.  Please manually install and try again.
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
Removing temporary directory: fglrx-install.HE49nc

Solución: 
       sudo apt-get install dpkg-dev
       (En el proceso me aparecio: "El paquete indicado a continuación se instaló de forma automática y ya no es necesarios.
  linux-headers-3.5.0-17
Use «apt-get autoremove» para eliminarlo." Y lo ignore, no influye en nada ¿Verdad?)

Y nuevamente:
       sudo sh ./amd-driver-installer-*.run --buildpkg Ubuntu/quantal
Segundo Error:
Unable to resolve  debhelper  dh-modaliases execstack.  Please manually install and try again.
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.970-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.X78o3Q
dpkg-buildpackage: host architecture amd64
 debian/rules build
#Create important strings
for i in 10fglrx \
             dkms.conf \
             fglrx.install \
             fglrx-dev.install \
             fglrx-dev.links \
             fglrx-amdcccle.install \
             fglrx.grub-gfxpayload \
             fglrx.dirs \
             fglrx.links \
             fglrx.postinst \
             fglrx.postrm \
             fglrx.preinst \
             fglrx.prerm \
             overrides/fglrx; do \
        sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#LIBDIR#|usr/lib|g" \
            -e "s|#LIBDIR32#|usr/lib32|g" \
            -e "s|#BINDIR#|usr/bin|g" \
            -e "s|#SYSCONFDIR#|etc|g" \
            -e "s|#MANDIR#|usr/share/man/man1|g" \
            -e "s|#LDSOCONF#|usr/lib/fglrx/ld.so.conf|g" \
            -e "s|#ALTLDSOCONF#|usr/lib/fglrx/alt_ld.so.conf|g" \
            -e "s|#ALTPRIORITY#|1000|g" \
            -e "s|#PXALTPRIORITY#|900|g" \
            -e "s|#AUTOSTARTDIR#|etc/xdg/autostart|g" \
            -e "s|#DATADIR#|usr/share|g" \
            -e "s|#PKGDESKDIR#|usr/share/fglrx|g" \
            -e "s|#PKGDATADIR#|usr/share/fglrx|g" \
            -e "s|#PKGCONFIGDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGBINDIR#|usr/lib/fglrx/bin|g" \
            -e "s|#PKGLIBDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGLIBDIR32#|usr/lib32/fglrx|g" \
            -e "s|#PKGDRIVERSDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTRA#|usr/lib/x86_64-linux-gnu/xorg/extra-modules|g" \
            -e "s|#PKGEXTENSIONDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTENSIONSDIR#|usr/lib/xorg/modules/extensions|g" \
            -e "s|#DRIVERNAME#|fglrx|g" \
            -e "s|#DRIVERDEVNAME#|fglrx-dev|g" \
            -e "s|#DRIVERSRCNAME#||g" \
            -e "s|#INCLUDEDIR#|usr/include|g" \
            -e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \
            -e "s|#GRUBBLKLISTDIR#|usr/share/grub-gfxpayload-lists/blacklist|g" \
            -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#PXDIR#|usr/lib/pxpress|g" \
            -e "s|#PXDIR32#|usr/lib32/pxpress|g" \
            -e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \
            -e "s|#PXDIRNAME#|pxpress|g" \
            -e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \
            -e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \
            -e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \
            -e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \
            -e "s|#CVERSION#|8.970|g" \
            -e "s|#SRCXARCH#|xpic_64a|g" \
            -e "s|#SRCARCH#|x86_64|g" \
            -e "s|#SRCLIBDIR#|lib64|g" \
            -e "s|#DEB_HOST_MULTIARCH#|x86_64-linux-gnu|g" \
            -e "s|#OTHER_ARCH#|i386-linux-gnu|g" \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        xpic_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
make: dh: Command not found
make: *** [build] Error 127
dpkg-buildpackage: error: debian/rules build gave error exit status 2
Removing temporary directory: fglrx-install.s4mZOm

Solución:
       sudo apt-get install debhelper  dh-modaliases execstack

Por tercera y ultima vez hago (Aparentemente funcionó):
       sudo sh ./amd-driver-installer-*.run --buildpkg Ubuntu/quantal


    4) sudo dpkg -i fglrx*.deb
Error:
dpkg: dependency problems prevent configuration of fglrx:
 fglrx depende de lib32gcc1; sin embargo:
  El paquete `lib32gcc1' no está instalado.
 fglrx depende de libc6-i386; sin embargo:
  El paquete `libc6-i386' no está instalado.
 fglrx depende de dkms; sin embargo:
  El paquete `dkms' no está instalado.

dpkg: error al procesar fglrx (--install):
 problemas de dependencias - se deja sin configurar
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depende de fglrx; sin embargo:
 El paquete `fglrx' no está configurado todavía.

dpkg: error al procesar fglrx-amdcccle (--install):
 problemas de dependencias - se deja sin configurar
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depende de fglrx; sin embargo:
 El paquete `fglrx' no está configurado todavía.

dpkg: error al procesar fglrx-dev (--install):
 problemas de dependencias - se deja sin configurar
Procesando disparadores para ureadahead ...
ureadahead will be reprofiled on next reboot
Se encontraron errores al procesar:
 fglrx
 fglrx-amdcccle
 fglrx-dev

Que denso que se esta volviendo esto!! :'(

---

### Post by guillermolisi on 2012-12-16
ES denso, solo que al gestor de paquetes hace que parezca simple.

Antes de encarar cualquier instalacion manual de un paquete, siempre pero siempre hay que tomar nota de las dependencias, resolverlas ANTES de comenzar la instalacion, es decir, instalar esos paquetes (y sus otras posibles dependencias) y por ultimo el paquete que queres instalar a mano.

Es decir, hay que leer, tener paciencia, ser metodico, volver a leer, verificar y luego, despues, hacer.

---

### Post by DaHater on 2012-12-16
.

---

### Post by DaHater on 2012-12-16
> **guillermolisi said:**
> ES denso, solo que al gestor de paquetes hace que parezca simple.

Antes de encarar cualquier instalacion manual de un paquete, siempre pero siempre hay que tomar nota de las dependencias, resolverlas ANTES de comenzar la instalacion, es decir, instalar esos paquetes (y sus otras posibles dependencias) y por ultimo el paquete que queres instalar a mano.

Es decir, hay que leer, tener paciencia, ser metodico, volver a leer, verificar y luego, despues, hacer.

Ok entiendo. Si me pudeieras ayudar con esta lista de errores te lo agradeceria demasiado

dpkg: dependency problems prevent configuration of fglrx:
 fglrx depende de lib32gcc1; sin embargo:
 El paquete `lib32gcc1' no está instalado.
 fglrx depende de libc6-i386; sin embargo:
 El paquete `libc6-i386' no está instalado.
 fglrx depende de dkms; sin embargo:
 El paquete `dkms' no está instalado.

 dpkg: error al procesar fglrx (--install):
 problemas de dependencias - se deja sin configurar
 dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depende de fglrx; sin embargo:
 El paquete `fglrx' no está configurado todavía.

 dpkg: error al procesar fglrx-amdcccle (--install):
 problemas de dependencias - se deja sin configurar
 dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depende de fglrx; sin embargo:
 El paquete `fglrx' no está configurado todavía.

 dpkg: error al procesar fglrx-dev (--install):
 problemas de dependencias - se deja sin configurar
 Procesando disparadores para ureadahead ...
 ureadahead will be reprofiled on next reboot
 Se encontraron errores al procesar:
 fglrx
 fglrx-amdcccle
 fglrx-dev


No entiendo del todo que paquetes o dependencias tengo que instalar :S

---

### Post by dirty fingers on 2012-12-17
> **DaHater said:**
> Me tira este error :(

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete fglrx-installer

Mala mia !

El paquete para tu versión de ubuntu esta en

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

y no en 

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Mira la lista para confirmar.

pd: nada que tenga mas de 3 lineas y no salga de una vale la pena insistir en la consola. Las computadoras están para darnos soluciones, no problemas.

---

### Post by DaHater on 2012-12-17
> **dirty fingers said:**
> Mala mia !

El paquete para tu versión de ubuntu esta en

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

y no en 

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Mira la lista para confirmar.

pd: nada que tenga mas de 3 lineas y no salga de una vale la pena insistir en la consola. Las computadoras están para darnos soluciones, no problemas.
OK! Ahora... No entendi un c****o de la pagina que me pasaste O__O
jajaja
¿Como tendria que hacer entonces ahora?

---

### Post by dirty fingers on 2012-12-17
serían los mismos comandos pero usando

```
**ppa:ubuntu-x-swat/x-updates**
```

---

### Post by DaHater on 2012-12-17
> **dirty fingers said:**
> serían los mismos comandos pero usando

```
**ppa:ubuntu-x-swat/x-updates**
```
Hice:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install fglrx  (le quite -installer porque me aparecia el error que te comente antes)

Comenzo a descargar unos 85Mb de la aplicacion, reinicie y puff otra vez me la reconoce como VESA:RS880 y desaparecieron el lanzador y la barra superior de unity. y para volver a recuperarlo tengo que desintalar el programa
Otra cosas, en la carpeta de aplicaciones me aparecen dos iconos de catalyst control center, uno es para ejecutar como administrador. no importa a cual le de clic siempre me dice que no funciona porque aparentemente no hay ningun controlador instalado D:

Mañana si tengo tiempo voy a probar nuevamente tadas las configuraciones que me recomendaron y buscare mas en la web... Que agotador u.u

---

