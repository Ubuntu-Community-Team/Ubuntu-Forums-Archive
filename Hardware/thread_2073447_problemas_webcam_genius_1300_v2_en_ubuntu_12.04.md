---
title: "problemas webcam genius 1300 v2 en ubuntu 12.04"
date: 2012-10-19
forum: Hardware
---

### Post by Alejo1982 on 2012-10-19
No puedo hacer funcionar la webcam genius  islim 1300 v2 en ubuntu 12.04. Al parecer hay varios con este problema  pero todas las soluciones que vi no me funcionan. La webcam la compré  porque "supuestamente" no necesita drivers y funciona con linux (eso  decía la caja) pero no logro ver nada ni con cheese ni con skype ni  camorama, nada. tengo instalado video4linux control panel y parecieras  que reconoce la webcam, mismo si pongo lsusb desde terminal, incluso en  configuracion de video de skype me marca islim 1300 v2, pero no  funciona. Ayer probe con todos los puertos usb de mi compu y no sé cómo  en configuración de skype pude ver imagen de la webcam pero al rato ya  volvió a desaparacer.  
¿alguna idea de cómo solucionarlo?? no quiero volver a windows !!!  pero no sé esta vez como hacer andar la camara y necesito usarla

**agrego que la última solución (*fallida*) que intenté fue esta:**

Bueno parece que linux reconoce tu webcam, el problema es que on tiene el driver. Descargatelo de esta pagina:

[http://mxhaard.***/download.html](http://mxhaard.***/download.html)

Ahí te pone dos drivers, uno por si tu kernel es menor del 2.6.11:

[http://mxhaard.***/spca50x/Download/spca5xx-20060501.tar.gz](http://mxhaard.***/spca50x/Download/spca5xx-20060501.tar.gz)

Y otro por si tu kernel es mayor del 2.6.11:

[http://mxhaard.***/spca50x/Download/gspcav1-20070110.tar.gz](http://mxhaard.***/spca50x/Download/gspcav1-20070110.tar.gz)

Descargate el adecuado, si no sabes que kernel tienes ejecuta en un terminal:

Código:

uname -r


A mi me sale esto:

Código:

2.6.17-11-generic


Por lo que me tengo que descargar el que es para kernel mayores que el 2.6.11.

Ahora a partir de aqui voy a hacer los pasos que me corresponden a mi, con el archivo gspcav1-20070110.tar.gz.

1º Descomprimimos el archivo:

Código:

tar -xzvf gspcav1-20070110.tar.gz


2º Vamos al directorio que se ha creado al descomprimirlo:

Código:

cd gspcav1-20070110


3º Compilamos el modulo y lo instalamos:

Código:

make
sudo make install


4º Cargamos el modulo:

sudo gedit /etc/modprobe.d/options

En ese archivo añadimos:

Código:

options gspca force_rgb=0


Guardas, cierras y ahora si, cargamos el modulo:

Código:

sudo modprobe gspca


Y teoricamente ya deberia estar instalado el driver, tras haber hecho eso te debería funcionar bien.

BUENO A MI NO ME FUNCIONÓ 
EN TERMINAL ME SALÍA ESTO:

usuario@usuario-desktop:~$ tar -xzvf gspcav1-20070110.tar.gz
tar (child): gspcav1-20070110.tar.gz: No se puede open: No existe el archivo o el directorio
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
usuario@usuario-desktop:~$ cd gspcav1-20071224
usuario@usuario-desktop:~/gspcav1-20071224$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/usuario/gspcav1-20071224 CC=cc modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.2.0-32-generic»
  CC [IMG]http://a15.t26.net/avatares/1/7/7/2/16_17721310.jpg?425753[/IMG]  /home/usuario/gspcav1-20071224/gspca_core.o
/home/usuario/gspcav1-20071224/gspca_core.c:37:26: error fatal: linux/config.h: No existe el archivo o el directorio
compilación terminada.
make[2]: *** [/home/usuario/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/usuario/gspcav1-20071224] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.2.0-32-generic»
make: *** [IMG]http://o1.t26.net/img/avatares/m/16/0.jpg[/IMG] Error 2
usuario@usuario-desktop:~/gspcav1-20071224$ sudo make install
[sudo] password for usuario: 
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: no se puede efectuar `stat' sobre «gspca.ko»: No existe el archivo o el directorio
make: *** [IMG]http://o1.t26.net/img/avatares/m/16/2.jpg[/IMG] Error 1
usuario@usuario-desktop:~/gspcav1-20071224$ sudo gedit /etc/modprobe.d/options
usuario@usuario-desktop:~/gspcav1-20071224$ sudo modprobe gspca
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
FATAL: Module gspca not found.

---

### Post by guillermolisi on 2012-10-19
Si estas usando 12.04 y estas usando el kernel 2.6.17-11-generic lo primero que tenes que hacer es aplicar todas las actualizaciones que falten para tener el sistema al dia.

Luego de eso volve a probar y vemos que resultado obtuviste.

---

### Post by Alejo1982 on 2012-10-20
> **guillermolisi said:**
> Si estas usando 12.04 y estas usando el kernel 2.6.17-11-generic lo primero que tenes que hacer es aplicar todas las actualizaciones que falten para tener el sistema al dia.

Luego de eso volve a probar y vemos que resultado obtuviste.

todo actualizado y sigue sin funcionar la webcam, la reconoce pero no funciona
usuario@usuario-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 003: ID 0458:7071 KYE Systems Corp. (Mouse Systems) **
Bus 002 Device 002: ID 03eb:0902 Atmel Corp. 4-Port Hub

---

### Post by guillermolisi on 2012-10-20
Lamentablemente [hay registrado un bug]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=668211") al respecto que, segun indican en su cierre, se solucionaria con el kernel 3.2.29-1
> From: Ben Hutchings <ben@decadent.org.uk>
To: [email]668211-close@bugs.debian.org[/email]
Subject: Bug#668211: fixed in linux 3.2.29-1
Date: Tue, 18 Sep 2012 18:26:35 +0000
Source: linux
Source-Version: 3.2.29-1

We believe that the bug you reported is fixed in the latest version of
linux, which is due to be installed in the Debian FTP archive.

A summary of the changes between this version and the previous one is
attached.

Thank you for reporting the bug, which will now be closed.  If you
have further comments please address them to [email]668211@bugs.debian.org[/email],
and the maintainer will reopen the bug report if appropriate.

Debian distribution maintenance software
pp.
Ben Hutchings <ben@decadent.org.uk> (supplier of updated linux package)

(This message was generated automatically at their request; if you
believe that there is a problem with it please contact the archive
administrators by mailing [email]ftpmaster@debian.org[/email])
El que abrio el ticket termino usando otra WebCam.

No encontre un solo caso de exito informado buscando con Google.
Probaria con un kernel mas nuevo, tal vez el 3.5 por ejemplo, sin eliminar el que estas usando. Si tampoco resulta, reinicias con el de siempre y podes remover el que hayas agregado para probar.

---

### Post by Alejo1982 on 2012-10-20
> **guillermolisi said:**
> Lamentablemente [hay registrado un bug]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=668211") al respecto que, segun indican en su cierre, se solucionaria con el kernel 3.2.29-1

El que abrio el ticket termino usando otra WebCam.

No encontre un solo caso de exito informado buscando con Google.
Probaria con un kernel mas nuevo, tal vez el 3.5 por ejemplo, sin eliminar el que estas usando. Si tampoco resulta, reinicias con el de siempre y podes remover el que hayas agregado para probar.


PERDÓN POR LA IGNORANCIA PERO SOY BASTANTE NUEVO CON LINUX, QUE SIGNIFICA CUANDO DICEN ESTO RESPECTO A ESE BUG: 
tags 668211 + upstream forwarded 668211 [http://thread.gmane.org/gmane.linux.drivers.video-input-infrastructure/49501](http://thread.gmane.org/gmane.linux.drivers.video-input-infrastructure/49501) quit [email]shubhadeepc@gmail.com[/email] wrote: > Upon doing "git bisect", it appears that this commit > [http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=commitdiff;h=e1620d591a75a10b15cf61dbf8243a0b7e6731a2](http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=commitdiff;h=e1620d591a75a10b15cf61dbf8243a0b7e6731a2) > introduces the regression. > >** The camera works on disabling CONFIG_USB_SUSPEND in the kernel.** > > I've reported the issue on the uvc mailing list. Thanks for your detective work.  Marking so.
SE PUEDE DESHABILITAR LA CONFIGURACIÓN USB EN EL KERNEL??:confused:

---

### Post by guillermolisi on 2012-10-20
Ese parrafo que te llamo la atencion se refiere a compilar el kernel Linux haciendo uso de esa opcion, es decir deshabilitandole la posibilidad de que suspenda el suministro de energia y la comunicacion de datos en los puertos USB.

Lo habia leido pero me parecio algo descabellado. Es muchisimo mas rapido y sencillo instalar una nueva version de kernel estable, probarla y (eventualmente) desinstalarla que compilar el kernel con opciones personalizadas (que no tiene nada de malo, solo que te complicas a la hora de las actualizaciones ya que dejas de usar una imagen Linux de stock, usas una propia).

Ademas, no me consta que sea una solucion comprobada ya que no encontre un solo caso que la confirme como exitosa.

---

### Post by norberto on 2012-12-02
please exec this command and all will be fine with iSlim 1300 v2

sudo sh -c "echo -n -1 > /sys/module/usbcore/parameters/autosuspend"

---

