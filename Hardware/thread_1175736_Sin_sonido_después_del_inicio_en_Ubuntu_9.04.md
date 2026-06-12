---
title: "Sin sonido después del inicio en Ubuntu 9.04"
date: 2009-06-01
forum: Hardware
---

### Post by atari130xe on 2009-06-01
Acabo de instalar desde cero Ubuntu 9.04 en la pc de mi hna, ella tenía la versión 8.10 pero como la nueva funciona más rápido en algunos aspectos decidí instalarle Jaunty en limpio.

Todo muy bién, inclusive funcionando desde el modo LiveCD con sonido sin problemas, luego al reiniciar, fué donde empezaron:

Primero se entrecortaba y queda un ruido molesto en lugar del sonido normal
y luego sencillamente la PC quedó sin sonido alguno, (arranca con sonido normal en el GDM (loguin) y el sonido de inicio del sistema, pero una vez en el escritorio, no hay manera de que lo haya en ninguna aplicación y en Wine simplemente al hacer la prueba de sonido literalmente se congela y hay que matar el proceso.

```
juana@juana-desktop:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: VT82xx [HDA VIA VT82xx], dispositivo 0: ALC662 Analog [ALC662 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: VT82xx [HDA VIA VT82xx], dispositivo 1: ALC662 Digital [ALC662 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

```
juana@juana-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
04:04.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
juana@juana-desktop:~$ 

```

y en los mjes de sucesos del sistema con referencia al sonido (pulseaudio) encontré esto que se repite:

> Jun  1 14:15:20 juana-desktop pulseaudio[3132]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 14:15:20 juana-desktop pulseaudio[3132]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
un  1 14:24:25 juana-desktop pulseaudio[4103]: pid.c: Stale PID file, overwriting.
Jun  1 14:24:25 juana-desktop pulseaudio[4103]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 14:24:25 juana-desktop pulseaudio[4103]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.

Googleando encontré a varios con problemas similares pero con chips Intel mayormente y en Notebooks, pero no en PC de escritorio.
gracias

---

### Post by pablo.s on 2009-06-01
Podés probar con deshabilitar
PulseAudio y activar ALSA.

---

### Post by atari130xe on 2009-06-01
Aparentemente es un problema con el demonio PulseAudio, por alguna razón hay algún problema de "autorizacion" en el sistema o duplicación del demonio al inicio, inicia bién pero al ejecutar cualquier aplicación se inicia nuevamente, si alguien sabe como se maneja el tema de policykit o algo al respecto, yo simplemente probé a hacer lo siguiente y funcionó:

En una sesión normal, maté el demonio PulseAudio y luego lo volví a lanzar, como resultado: el sonido funciona PERFECTO, sin ruidos, claro y transparente. O sea es raro, simplemente no se como hacer para que funcione sin tener que hacer todos esos pasos, ni mi hna ni mi sobrinito son "eruditos" en el tema. :P
 
Esto es lo que hice básicamente para que en una sesión normal, funcione el sonido.

```
juana@juana-desktop:~$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() falló.

```

```
juana@juana-desktop:~$ killall pulseaudio

```

```
juana@juana-desktop:~$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
W: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
W: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
```

El resultado: el sonido funcionando perfecto.

Alguien con alguna sugerencia para "normalizar" el tema? :D

---

### Post by Mauro22 on 2009-06-01
Si mal no recuerdo, a vos los problemas con el audio te persiguen, no? Tenias problemas en GG?? xD



Mucho del tema no se, pero si vos decis que matando el proceso y volverlo a cargar, se va, yo haria un script y lo pongo al inicio y listo el pollo.


```
#!/bin/bash

killall pulseaudio
pulseaudio
```

Guardarlo en /usr/bin
Darle permisos chmod +x archivo
Y cargarlo al inicio.



Se que me van a pegar por no dar una solucion "mejor", pero es lo que se me ocurre.



Saludos!

PD: lo del principio si no eras vos, perdon xD

---

### Post by atari130xe on 2009-06-01
Si Mauro!!! se nota que me seguís los pasos (o los tumbos :P) que me hace dar Ubuntu jejeje, si pero desde la 8.04 no tuve mas problemas con el sonido en MI pc jejeje, pero bueno ahora que lo estoy instalando en otros equipos aparecen algunos problemas, (sonido y video mas que nada), por lo gral, la gente tiene las pc pre-armadas que compraron en Carrefour, Fravega, o negocios de ese estilo, por consiguiente, traen chips de video y audio integrados, que gralmente no funcionan bien con Ubuntu (Chip de video Chrome9 por ej.), asi que cada vez que voy a instalar me encuentro con algunos inconvenientes de esa clase. Voy a probar con tu script
saludos amigo!

---

