---
title: "Problenas ATI movility radeon hd4570"
date: 2010-10-04
forum: Hardware
---

### Post by zaret on 2010-10-04
Hola mi problema es algo complejo: Tenia instalada mi tarjeta de video ATI mobility con el driver privativo, cada ves que actualizaqba kernel tenia que reinstalar el controlador privativo desde la consola. pero ahora  me da el siguiente arror al hacer el glxinfo

zaret@zaret-laptop:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15

no se que hacer
saludos

---

### Post by Carlos C on 2010-10-04
Hola. A partir de Jaunty, según recuerdo, las tarjetas ATI no necesitan de un driver privativo para funcionar y es posible tener aceleración gráfica con el driver que viene instalado en Ubuntu por defecto ¿Qué versión de Ubuntu estás utilizando?

Saludos!

---

### Post by zaret on 2010-10-04
Bueno la verdad es que en jaunty nunca pude tener aceleracion 3D con el driver libre, yo uso Lucid y espero actualizar pronto a maverik, bueno purgue el fglrx y trate de reinstalarlo, pero al revisar el log de instalacion, me dio esto

zaret@zaret-laptop:/usr/share/ati$ cat fglrx-install.log 
Package build failed!
Package build utility output:
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.771-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
#Create important strings
for i in 10fglrx \
             dkms.conf \
             fglrx.install \
             fglrx-dev.install \
             fglrx-amdcccle.install \
             overrides/fglrx; do \
        sed -e "s|#XMODDIR#|usr/lib/fglrx/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32/fglrx|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib/fglrx|"       \
            -e "s|#CVERSION#|8.771|"   \
            -e "s|#XARCH#|x750_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x750_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
        debian/modaliases/fglrx-modules.alias.override
dh build
make: dh: Command not found
make: *** [build] Error 127
dpkg-buildpackage: error: debian/rules build gave error exit status 2
[Error] Generate Package - error generating package : Ubuntu/lucid

saludos ojala sirva de ayuda

---

### Post by Carlos C on 2010-10-05
Honestamente no estoy seguro de que sea posible hacer funcionar ese driver en Jaunty. Me parece que lo mejor es utilizar el driver open source.

---

### Post by zaret on 2010-10-05
la verdad el driver estaba corriendo sin problemas en las ultimas 3 actualizaciones del kernel, en lucid, y con la ultima no se que paso con la compatibilidad, pero ahora falla la instalacion.

Bueno despues de leer mucho por la red y no encontrar  nada se me ocurrio cambiar el orden de la busqueda y  encontre esto

Para los que usen el kernel 2.6.32-25 cambiaro algunos parametros por los que el driver de ati no puede compilar, a lo cual se puede resolver de esta manera

                                                   primero: **$ uname -r **
 para asegurarse que estamos corriendo el kernel 2.6.32-25. si no es asi no sigas con lo siguientes pasos.
 **$ cd /usr/src/linux-headers-2.6.32-25-generic/arch/x86/include/asm/ **
 **$ sudo mv compat.h compat.h.bak **
 **$ sudo wget -c [http://cloud.dolphinaura.com/scripts/kernel/fglrx_10.9_fix/compat.h]("http://www.tipete.com/ext?url=http://cloud.dolphinaura.com/scripts/kernel/fglrx_10.9_fix/compat.h") **
 listo ahora pueden emplazar el catalyst 10.9 (o reemplazarlo)
 fuente:

[http://dolphinaura.posterous.com/fglrx-fix-for-catalyst-109-1]("http://www.tipete.com/ext?url=http://dolphinaura.posterous.com/fglrx-fix-for-catalyst-109-1")

[http://ubuntuforums.org/showpost.php?p=9877727&postcount=10]("http://www.tipete.com/ext?url=http://ubuntuforums.org/showpost.php?p=9877727&postcount=10")                                





Ahora solo es nesesario reinstalar nuestro controlador privativo y vuelta a la felicidad
saludos

---

