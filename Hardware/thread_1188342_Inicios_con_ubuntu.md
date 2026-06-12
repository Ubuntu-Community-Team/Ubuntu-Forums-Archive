---
title: "Inicios con ubuntu"
date: 2009-06-15
forum: Hardware
---

### Post by rodrychm on 2009-06-15
quetal amigos, tengo varias dudas. Hace dos años he estado usando linux pero no era mi sistema operativo principal sino windows, asi que estoy algo familiarizado, pero tengo muchas lagunas sobre linux. Recien la anterior semana tome la decisicion de dejar windows y me instale kubuntu 9.04 y lo estoy utilizando relativamente bien, con todo lo necesario. Pero mi primer gran duda es que no se si se instalaron correctamente los drivers de mi laptop, por ejemplo la de video. Si alguien pudiera guiarme en como verificar eso, y aun mas, si me diera la pauta de como instarlar los drivers que me falten les agradeceria un monton.
Cualquier ayuda me serviria mucho
Gracias

---

### Post by pablo.s on 2009-06-15
Buenisimo! Te felicito
por dar el gran paso!

Necesitamos saber que
placa de video tenés.
Escribí 

**[COLOR=DarkGreen]lspci[/COLOR]**

en una terminal y copia
y pegá el resultado en 
un nuevo post.

---

### Post by sdennie on 2009-06-15
Fijate con:

```

glxinfo | grep rendering

```

Si dice, "Yes", estas usando un driver que sabe hablar con el hardware directamente y todo debe funcionar bien.

---

### Post by rodrychm on 2009-06-17
Gracias por la ayuda muchachos.
Este es el resultado de lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

---

### Post by juancarlospaco on 2009-06-17
No es una placa de las mas grosas, pero esta reconocida y andando.
:)

---

### Post by rodrychm on 2009-06-17
Quetal muchachos,

Trate de ejecutar: glxinfo | grep rendering
pero me responde error:
Error: unable to open display

Saludos.

---

### Post by rodrychm on 2009-06-17
... antes no pude ejecutar glxinfo por que estaba como root; ahora con mi usuario da esta respuesta:

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Supongo que eso significa que no esta con el driver correcto. Como puedo instalarlo?

---

### Post by pablo.s on 2009-06-17
Fijate si tenés los siguientes
paquetes instalados:

libdrm-intel1
xserver-xorg-video-intel

---

### Post by rodrychm on 2009-06-17
Si pablo.s, tengo instalados ambos paquetes.

Esta son las respuesta con apt-cache show

####bin$ apt-cache show libdrm-intel1
Package: libdrm-intel1
Priority: optional
Section: libs
Installed-Size: 440
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: i386
Source: libdrm
Version: 2.4.5-0ubuntu4
Replaces: libdrm2 (<= 2.4.1-0ubuntu5)
Depends: libc6 (>= 2.3.4), libdrm2 (>= 2.4.1)
Filename: pool/main/libd/libdrm/libdrm-intel1_2.4.5-0ubuntu4_i386.deb
Size: 375090
MD5sum: 53ceb0646871f5d1f457af1d947db632
SHA1: d17d2b724e3135f1f9c91ae43347a92cf256798e
SHA256: e46cf297fad0d7db4371b39dee252963525339ff429ae2d65444a5a47df9a234
Description-es: Interfaz de espacio de usuario para los servicios de DRM del nÃºcleo intel-specific -- ejecutable
 Esta biblioteca implementa la interfaz de espacio de usuario para los
 servicios DRM de intel especÃ*ficos del nÃºcleo. DRM son las iniciales de
 (Direct Rendering Manager) Gestor de Â«renderizadoÂ» directo, que es la
 porciÃ³n del espacio de nÃºcleo de la (Direct Rendering Infrastructure)
 (DRI) Infraestructura de Â«renderizadoÂ» directo. La DRI se usa
 actualmente en Linux para proporcionar controladores OpenGL acelerados por
 hardware.
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Task: ubuntu-desktop, kubuntu-desktop, edubuntu-desktop, xubuntu-desktop, mobile-mid, mobile-netbook-remix, mythbuntu-backend-master, mythbuntu-backend-slave, mythbuntu-desktop, mythbuntu-frontend

#####bin$ apt-cache show xserver-xorg-video-intel
Package: xserver-xorg-video-intel
Priority: optional
Section: x11
Installed-Size: 1292
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: i386
Version: 2:2.6.3-0ubuntu9
Replaces: xserver-xorg (<< 6.8.2-35), xserver-xorg-driver-i810, xserver-xorg-video-i810 (<< 2:1.9.91-1), xserver-xorg-video-i810-modesetting, xserver-xorg-video-intel-modesetting
Provides: xserver-xorg-video-5
Depends: libc6 (>= 2.4), libdrm-intel1 (>= 2.4.5), libdrm2 (>= 2.3.1), libpciaccess0 (>= 0.8.0+git20071002), libxext6, libxv1, libxvmc1, xserver-xorg-core (>= 2:1.5.99.901)
Conflicts: 915resolution, xserver-xorg-driver-i810, xserver-xorg-video-i810 (<< 2:1.9.91-1), xserver-xorg-video-i810-modesetting, xserver-xorg-video-intel-modesetting
Filename: pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.6.3-0ubuntu9_i386.deb
Size: 524390
MD5sum: bc83358be9dabf3c594c5afdea5a39f1
SHA1: 0bbc9f916e9becff045c82b008fbcc523327a7ca
SHA256: 6b1e1dfbb96f9a1d2dd2ca49eccd161b5a61419b3ac76c94b49f4a0670e341b2
Description-es: X.Org X server -- Controlador de pantalla Intel i8xx, i9xx
 Este paquete proporciona el controlador para la familia de chipset Intel
 i8xx y i9xx, incluyendo las series i810, i815, i830, i845, i855, i865,
 i915, i945 e i965.
 .
 Este paquete tambiÃ©n provee un controlador XvMC (CompensaciÃ³n de
 Movimiento XVideo) para los chipsets i810 e i815.
 .
 Puede encontrar mÃ¡s informaciÃ³n sobre X.Org en: [http://www.X.org](http://www.X.org)
 [http://xorg.freedesktop.org](http://xorg.freedesktop.org)
 [http://lists.freedesktop.org/mailman/listinfo/xorg](http://lists.freedesktop.org/mailman/listinfo/xorg)
 .
 Este paquete estÃ¡ construido desde el mÃ³dulo del controlador X.org xf86
 -video-intel.
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Task: ubuntu-desktop, kubuntu-desktop, edubuntu-desktop, xubuntu-desktop, mobile-mid, mobile-netbook-remix, mythbuntu-backend-master, mythbuntu-backend-slave, mythbuntu-desktop, mythbuntu-frontend

---

### Post by pablo.s on 2009-06-17
Tenés los drivers correctos.
Necesitamos investigar ahora
tu xorg.conf para ver la linea
que falta activar para que tengas
aceleración 3D.

Está en [B][COLOR=DarkGreen]/etc/X11/xorg.conf
[/COLOR][/B][COLOR=Black]Pegalo asi vemos que hay.[/COLOR][B][COLOR=DarkGreen]
[/COLOR][/B]

---

### Post by rodrychm on 2009-06-17
Ok Pablo; aqui va el archivo xorg.conf

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

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "ServerFlags"
        Option  "DontZap"       "True"
EndSection

---

### Post by pablo.s on 2009-06-17
Probá reemplazar lo que
tiene por esto ( o sea solo
la sección, no todo, eh? )

```
Section "Device"
       Identifier      "Configured Video Device"
       Option          "AccelMethod" "EXA"
       Option          "CacheLines" "1980"
EndSection
```

y después reiniciás el servidor X.

---

### Post by rodrychm on 2009-06-17
Gracias Pablo, ya hice la modificacion del archivo xorg.conf y reinicie la interfaz grafica. La verdad es que nose como probar si efectivamente esta yendo bien el driver. Para probar si esta bien queria habilitar un escritorio ampliado conectando un monitor a mi laptop, pero no encuentro donde. Ahorita los monitores me estan desplegando lo mismo.
Creo que necesito instalar algun paquete que pueda manejar a mi driver de video.
Tienes alguna sugerencia para probar el video?

---

### Post by pablo.s on 2009-06-17
Con estos comandos

[COLOR="DarkGreen"]**glxinfo | grep rendering**[/COLOR]

te dirá si está activada
la aceleración 3D. Si el
mensaje que devuelve es
"Yes" entonces lo está.
Luego puedes probar con

[COLOR="#006400"]**glxgears**[/COLOR]

que te muestra un juego
de engranajes en 3D, como
demostración.

---

### Post by rodrychm on 2009-06-17
Perdon por ser tan canson, pero creo que no va bien aun. Hice la prueba con los comandos que me indicas y responde mal:

lxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

---

### Post by pablo.s on 2009-06-17
Bueno, ya le encontraremos
la solución. Basicamente hay
un problemita con los drivers
de Intel en Jaunty porque se
está haciendo la transición de
un método que se llama EXA a
otro que se llama UXA y por eso
han metido la mano.
Igualmente, necesitas la
aceleración 3D ya mismo o puedes
esperar un poco a que demos con
una solución?

Una solución un poco primitiva
es instalar los drivers de Intel
que venian en Intrepid,la versión
de Octubre del 2008.

Otra es activar UXA, pero es a tu
propio riesgo de lo que suceda:

```
Section "Device"
       Identifier      "Configured Video Device"
       Option          "AccelMethod" "uxa"
       Option          "CacheLines" "1980"
EndSection
```

---

### Post by rodrychm on 2009-06-17
No es nada urgente, solo que queria tener mi ubuntu lo mejor posible, pero puedo esperar.
Te agradezco mucho por la ayuda y el tiempo que utilizaste.
Gracias, hasta pronto entonces....

---

### Post by pablo.s on 2009-06-17
Disculpa, he editado el
post para que pruebes
activar UXA. Conste que
es EXPERIMENTAL...

---

### Post by rodrychm on 2009-06-18
Ok, me arriesgue a hacer el cambio... he reinciado la interfaz grafica y no ocurrio nada, sigue como antes. Volvi hacer las pruebas con glxinfo | grep rendering y glxgears, y nada, sigue saliendo el mismo error.

---

