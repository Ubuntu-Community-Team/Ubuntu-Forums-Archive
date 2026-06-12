---
title: "[SOLUCIONADO] No Reconoce Tarjeta Audio Externa"
date: 2009-07-11
forum: Hardware
---

### Post by RafaelG on 2009-07-11
Hola bueno tengo una dificulta, Actualize Alsa 1.0.20 utilizando el Siguiente link ([http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)) desde entonces alsa no reconoce mi Tarjeta de sonido externa y utilizando la tarjeta Intel HDA reproduciendo cualquier tema pocos minutos despues empieza a Chicharrea y deja de sonar.

**cat /proc/asound/version**
Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on Jul 11 2009 for kernel 2.6.28-13-generic (SMP).
[B]
aplay -l[/B]
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

 **lsusb** 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 005: ID 1241:0022 Belkin 
Bus 006 Device 002: ID 062a:6722 Creative Labs 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 006: ID 047f:0ca1 Plantronics, Inc. USB DSP v4 Audio Interface
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[FONT=monospace]
[/FONT]
Saludos

---

### Post by pagondel on 2009-07-11
```
lsusb
```

---

### Post by RafaelG on 2009-07-11
Edite el Thread por mas antecedentes

---

### Post by Carlos C on 2009-07-12
En "Preferencias de Sonido", si ves la pestaña "dispositivos", ¿estás usando PulseAudio o Alsa? Verifica que esté configurado para usar PulseAudio.
Si escribes en el terminal:
```
asoundconf list
```
¿qué dispositivos te muestra? Puedes seleccionar uno de ellos para que sea usado por el sistema mediante el comando:
```
asoundconf set-default-card <nombre_de_la_tarjeta>
```

---

### Post by RafaelG on 2009-07-15
Hola Carlos bueno disculpa la demora recien hoy pude ingresar al foro, mucho trabajo, Pude Solucionar el problema  con los Siguientes Codigos

_**Re-Configurando ALSA**_
sudo soundoff
sudo dpkg-reconfigure linux-sound-base
sudo apt-get -y install libesd-alsa0 alsa-oss alsa-base libsdl1.2debian-als
sudo apt-get install libflashsupport[FONT=monospace]
[/FONT]

---

