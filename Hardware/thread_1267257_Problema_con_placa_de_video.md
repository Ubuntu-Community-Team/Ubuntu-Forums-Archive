---
title: "Problema con placa de video"
date: 2009-09-15
forum: Hardware
---

### Post by Mustaine666 on 2009-09-15
Bueno.. resulta que despues de mucho j***r.. con le coky.. y esas cosas.. cuando quise poner los efectos en las ventanas de ubunutu 9.04 .. le hago click y me dice  q no tengo  placa de video..

Instale ubuntu en una compaq S5010LS .. la placa de video es integrada..

y se llama intel extreme grapichs de 64Mb ... 

alguna opcion.. para solucionar esto? .. desde ya muchas gracias!

---

### Post by Applelnx on 2009-09-15
Supongo que lo que te falta son los drivers para aceleracion 3D. 
Fijate si encontras algun post con ese modelo de placa.

---

### Post by guillermolisi on 2009-09-15
> **Mustaine666 said:**
> Bueno.. resulta que despues de mucho j***r.. con le coky.. y esas cosas.. cuando quise poner los efectos en las ventanas de ubunutu 9.04 .. le hago click y me dice  q no tengo  placa de video..

Instale ubuntu en una compaq S5010LS .. la placa de video es integrada..

y se llama intel extreme grapichs de 64Mb ... 

alguna opcion.. para solucionar esto? .. desde ya muchas gracias!
En una consola/terminal ingresa ```
lspci
``` y mostranos la salida que te da, asi veremos como es reconocida la placa de video por Ubuntu y de ahi vemos para donde rumbeamos.

---

### Post by gmunioz on 2009-09-15
Hola mus....:

1- Si tu tarjeta de video funcionaba de una

y ha dejado de funcionar, reinstala:

xorg   xorg-dev   xserver-xorg-video-intel

2- Si tu tarjeta nunca funcionó a pleno, lo 

que es mas factible, es fruto de la desinteligencia

que se produjo entre intel, que da pleno soporte

para GnuLinux y los cambios efectuados por los 

desarrolladores en el kernel, esto ya esta solucionado

en el kernel 2.6.30 , lo puedes obtener de:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.6/)

Estos son los paquetes:

linux-headers-2.6.30-02063006-generic_2.6.30-02063006_amd64.deb	
linux-headers-2.6.30-02063006-generic_2.6.30-02063006_i386.deb	
linux-headers-2.6.30-02063006_2.6.30-02063006_all.deb
linux-image-2.6.30-02063006-generic_2.6.30-02063006_amd64.deb
linux-image-2.6.30-02063006-generic_2.6.30-02063006_i386.deb	
linux-source-2.6.30_2.6.30-02063006_all.deb

Si usas 32 bits no instales los dos amd64 y si usas 64 bits

no instales los dos i386

Se instalan con la orden:

sudo dpkg -i *.deb

ejecutada en el directorio (carpeta) donde se descargaron

Nota: ya esta el kernel 2.6.31, con nvidia funciona haciendo

pinning e instalando los drivers de karmic, pero con tarjetas

intel no me ha funcionado, asi que mantente en el 2.6.30

---

### Post by Mustaine666 on 2009-09-16
resultado del lspci

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0b.0 Communication controller: Agere Systems LT WinModem (rev 02)
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


que hago?

---

### Post by gmunioz on 2009-09-16
Hola mus...:

si no quieres actualizar tu kernel puedes probar con:

1- Editar tu xorg.conf, con la orden en consola:

sudo gedit /etc/X11/xorg.conf

dejar la sección device así:

```
Section "Device"
Identifier "Configured Video Device"
Driver "intel"
Option "AccelMethod" "UXA"
VideoRam 65536
EndSection
```

Inicia el compiz manager:

ccsm

Elige Opciones generales -> General -> remueve la marca de Anular redireccion de ventanas a pantalla completa

Elige Opciones generales -> Display Settings -> remueve la marca de Sincronizar con borrado vertical

cierra ccsm

Reinicia

---

### Post by Mustaine666 on 2009-09-17
bueno.. les cuento.. actualice el kernel.. 

ahora tengo en el grub 6 opciones de linux y el mem test.. 

no paso nada.. con el nuevo kernerl.. seguia con el mismo problema..

decidi hacer lo que me dijo gmunioz .. 

despues de reconfigurar o editar el xorg.conf .. 

y corregir las cosas en el compiz .. 

reinicio la computadora...

y me sale un cartel

que dice

```
Ubuntu is running in low-grapichs mode
The following error was encountered. you may need to update your configuration to solve this.

(EE) Problem parsing the config file
(EE) Error parsing the config file
```


despues de eso.. bueno .. me da unas opciones.. intento seguir en modo de bajo graficos.. y no anda..

tuve que hacer.. q reconfigure todo.. a como estaba antes.. 

bueno.. desde windows me fije y el everest me dice que la placa es de 64mb y en la caja de la pc (es bastante vieja la pc) dice que la placa es de 32MB. ...

alguna posible solucion.. o me resigno a no tener efectos en la pc¿:confused:

---

### Post by Hei Ku on 2009-09-17
Podes probar editar de vuelta el xorg.conf. 

En lo que te paso gmunioz, reemplaza las comillas de apertura y cierre (&#8220;&#8221;)
por comillas simples (")

---

### Post by Mustaine666 on 2009-09-18
> **Hei Ku said:**
> Podes probar editar de vuelta el xorg.conf. 

En lo que te paso gmunioz, reemplaza las comillas de apertura y cierre (“”)
por comillas simples (")


lo probe como me dijiste y paso lo mismo..

y ensima ahora no me andan los pogramas de correo.. el emesene... el pidgin.. no anda ninguno..

solo mozilla y songbird para la musica

---

### Post by Hei Ku on 2009-09-18
Te tiró el mismo mensaje de error?

Posteá como queda el xorg.conf despues que lo modificas, por favor.

---

### Post by Mustaine666 on 2009-09-18
```
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
Identifier "Configured Video Device"
Driver "Intel"
Option "AccelMethod"  "UXA" 
VideoRam 65536
EndSection 

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```


asi queda mi xorg.conf

---

### Post by Hei Ku on 2009-09-18
Intel va con minuscula.

---

### Post by Mustaine666 on 2009-09-23
probe con intel con miniscula.. y paso lo mismo!

---

### Post by Hei Ku on 2009-09-23
Te tira exactamente el mismo mensaje de error? Como quedó el xorg.conf?

---

### Post by Mustaine666 on 2009-09-25
```

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
Identifier "Configured Video Device"
Driver "intel"
Option "AccelMethod"  "UXA" 
VideoRam 65536
EndSection 


Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```


asi me quedò!

---

