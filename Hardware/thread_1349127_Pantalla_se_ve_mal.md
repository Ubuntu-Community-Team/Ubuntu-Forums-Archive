---
title: "Pantalla se ve mal"
date: 2009-12-07
forum: Hardware
---

### Post by serbesa on 2009-12-07
Hola,acabo de instalra ubuntu 9.10 y mi problema es que la pantalla se ve mal, me explico, se ven rayas verticales que aparecen y se van, que son bastante molestas. Intente configurala en la siostema pantalla, pero no hay casos, cambiando la frecuencia a 75, se ve peor, y las otras resoluciones ni hablar.

tengo un monitor Samsung SyncMaster 933NW,
y segun fuch, tengo esta informacion de video
```

Escritorio:    GNOME

```
```

$lspci|grep -i vga
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)

```
```

$cat /var/log/Xorg.0.log|grep EE
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) open /dev/fb0: No such file or directory

```
```

$cat /var/log/messages |grep error

```
```

$cat /var/log/syslog |grep error
Dec  8 00:09:22 pcrob NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec  8 00:11:23 pcrob pulseaudio[1611]: alsa-sink.c: Probablemente sea un error en el controlador ALSA «snd_intel8x0». Por favor, informe esto a los desarrolladores de ALSA.
Dec  8 00:19:05 pcrob NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Dec  8 00:19:11 pcrob NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Dec  8 00:20:14 pcrob NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Dec  8 00:39:09 pcrob NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec  8 00:39:52 pcrob pulseaudio[1526]: alsa-sink.c: Probablemente sea un error en el controlador ALSA «snd_intel8x0». Por favor, informe esto a los desarrolladores de ALSA.
Dec  8 00:45:24 pcrob NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Dec  8 00:54:12 pcrob NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Dec  8 01:13:44 pcrob NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec  8 01:14:12 pcrob pulseaudio[1424]: alsa-sink.c: Probablemente sea un error en el controlador ALSA «snd_intel8x0». Por favor, informe esto a los desarrolladores de ALSA.

```
```

$lsmod |grep drm

```
```

$lsmod |grep agp

```
```

$glxinfo |grep direct
direct rendering: Yes

```

saludos y cualquier ayuda será bien recibida.

---

### Post by kamus on 2009-12-08
No se si revisaste este link [http://ubuntuforums.org/showthread.php?t=1224660](http://ubuntuforums.org/showthread.php?t=1224660), de lo contrario espero te sirva de ayuda para solucionar tu problema.

Saludos

---

### Post by Carlos C on 2009-12-08
Esa tarjeta la verdad no da buenos resultados en linux ¿No existe la opción de que pruebes con otra tarjeta? porque no hay hasta ahora un soporte adecuado en linux para tarjetas SiS.

Existe un thread en Ubuntuforums dedicado a estas tarjetas:

[http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967)

Podrás ver que existen mucho problemas incluso para obtener la resolución adecuada. Sin embargo al final del thread hay un aporte que te puede interesar:

[http://ubuntuforums.org/showpost.php?p=8451508&postcount=283](http://ubuntuforums.org/showpost.php?p=8451508&postcount=283)

[http://ajoliveira.com/ajoliveira/uk/software/xorg.php](http://ajoliveira.com/ajoliveira/uk/software/xorg.php)

Nunca lo he probado pero no pierdes nada con intentarlo.

Edito: no había leído lo que propone Kamusin. Parece mejor idea probar lo que él sugiere primero.


Saludos.

---

### Post by serbesa on 2009-12-08
probe primero lo que dijo kamus, y no me resultó

despues seguí los pasos de [http://ajoliveira.com/ajoliveira/uk/software/xorg.php](http://ajoliveira.com/ajoliveira/uk/software/xorg.php), y creo que me resultó, aunque tengo unas dudas, despues de revisar sistema/preferencia/pantalla, sale con una tasa de refresco de 0 hz, y no sé si eso está bien para mi monitor,,,
saludos.

---

### Post by CdK1 on 2009-12-08
Cómo está configurado tu Xorg?, aka xorg.conf, la sección "Driver"...

---

### Post by serbesa on 2009-12-08
Buenas...
en resumen esto ha ocurrido, primero no tenía un archivo xorg.conf, y cree uno segun el tema postedo por kamus, y el problema persistió, despues probe con un tema postedo por  carlos c ([http://ajoliveira.com/ajoliveira/uk/software/xorg.php](http://ajoliveira.com/ajoliveira/uk/software/xorg.php)), y paso algo raro, porque al entran me daban a elegir algunas opciones entre ellas "run ubuntu in low graphics mode", y tenia que elejir esa para entrar, y todo se veía bien, sin rayas, pero tenia una tasa de refresco de 0 hz, entre otras cosas raras, como que no me funcionaba tvtime (tambien tengo unas dudas de tvtime, pero la dejare para despues)
Luego como habia guardado el xorg.conf anterior, lo reestablecí, pero sigué el problema de las rayas.

El xorg.conf que tengo ahora
es el siguiente:

Section "Device"
Identifier "Video Device"
Driver "sis"
EndSection
Section "Monitor"
Identifier "Configured Monitor"
EndSection
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Video Device"
EndSection

saludos

---

### Post by CdK1 on 2009-12-16
Pués tú "xorg.conf" deja bastante que decir, te recomiendo que reconfigures de la siguiente manera:

sudo dpkg-reconfigure xserver-xorg -phigh

Eso reconfigura todo automáticamente

sudo dpkg-reconfigure xserver-xorg

Esto lo hace manualmente

Luego editas tú /etc/X11/xorg.conf para dejarlo a gusto, sería bueno que el resultado de tú archivo lo postearas, otra cosa, que te tira esto:

lsmod | grep sis

Espero te funcione...

---

