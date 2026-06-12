---
title: "Como saber si tengo instalados los ultimos controladores del hardware"
date: 2010-01-21
forum: Hardware
---

### Post by Seba_83 on 2010-01-21
Amigos, nuevamente recurro a su ayuda, sospecho que no tengo instalados los ultimos controladores para mi notebook, el cual es un hp 530
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 14
model name    : Genuine Intel(R) CPU           T2050  @ 1.60GHz
stepping    : 8
cpu MHz        : 800.000
cache size    : 2048 KB

*-pci
     description: Host bridge
     product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Cont

*-display:0
     description: VGA compatible controller
     product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller.

La verdad es que no tengo mucha nocion de ubuntu, menos de linux, sin embargo me esfuerzo por aprender.

es suficiente los datos posteados, existe algun comando para saber si los controladores del hardware estan actualizados.
gracias por todo.
Seba.

---

### Post by Seba_83 on 2010-01-21
Amigos, acabo de instalar el fuch y respecto al video esta es la informacion que arroja:

Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic

#lspci|grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

#cat /var/log/Xorg.0.log|grep EE
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load module "i810" (module does not exist, 0)

#cat /var/log/messages |grep error
Jan 17 19:39:49 sebastian-laptop kernel: [ 9302.231981] gnome-panel[1540]: segfault at 18 ip 011e9435 sp bf89d840 error 4 in libgtk-x11-2.0.so.0.1800.3[f85000+3b8000]

#cat /var/log/syslog |grep error
Jan 19 16:13:18 sebastian-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jan 19 16:37:56 sebastian-laptop pulseaudio[1367]: alsa-sink.c: Probablemente sea un error en el controlador ALSA «snd_hda_intel». Por favor, informe esto a los desarrolladores de ALSA.
Jan 19 20:00:15 sebastian-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jan 19 20:15:05 sebastian-laptop pulseaudio[1377]: alsa-sink.c: Probablemente sea un error en el controlador ALSA «snd_hda_intel». Por favor, informe esto a los desarrolladores de ALSA.
Jan 20 14:17:45 sebastian-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jan 20 20:21:00 sebastian-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jan 20 20:26:52 sebastian-laptop pulseaudio[1312]: alsa-sink.c: Probablemente sea un error en el controlador ALSA «snd_hda_intel». Por favor, informe esto a los desarrolladores de ALSA.
Jan 20 21:38:15 sebastian-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Jan 20 21:43:32 sebastian-laptop pulseaudio[1312]: alsa-util.c: Lo más probable es que sea un error del controlador ALSA «snd_hda_intel». Por favor, informe esto a los desarrolladores de ALSA.
Jan 20 21:43:32 sebastian-laptop pulseaudio[1312]: alsa-util.c: Lo más probable es que sea un error del controlador ALSA «snd_hda_intel». Por favor, informe esto a los desarrolladores de ALSA.
Jan 20 22:17:35 sebastian-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Jan 21 14:03:44 sebastian-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Jan 21 14:15:28 sebastian-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Jan 21 16:14:34 sebastian-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Jan 21 19:51:55 sebastian-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jan 21 19:52:05 sebastian-laptop pulseaudio[1364]: alsa-sink.c: Probablemente sea un error en el controlador ALSA «snd_hda_intel». Por favor, informe esto a los desarrolladores de ALSA.
Jan 21 20:12:31 sebastian-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jan 21 20:12:42 sebastian-laptop pulseaudio[1423]: alsa-sink.c: Probablemente sea un error en el controlador ALSA «snd_hda_intel». Por favor, informe esto a los desarrolladores de ALSA.
Jan 21 20:15:51 sebastian-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012

#lsmod |grep drm
drm                   159584  3 i915
agpgart                34988  2 drm,intel_agp

#lsmod |grep agp
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp

#glxinfo |grep direct
direct rendering: Yes

---

### Post by moreback on 2010-01-21
Para saber si tienes lo último debieras ejecutar **Sistema -> Administración -> Gestor de actualizaciones** y pulsa sobre Comprobar. Si aparecen paquetes para actualizar, entonces no tienes al día tu Ubuntu.

Saludos.

---

### Post by RafaelG on 2010-01-24
> **moreback said:**
> Para saber si tienes lo último debieras ejecutar **Sistema -> Administración -> Gestor de actualizaciones** y pulsa sobre Comprobar. Si aparecen paquetes para actualizar, entonces no tienes al día tu Ubuntu.

Saludos.


Exacto!

---

