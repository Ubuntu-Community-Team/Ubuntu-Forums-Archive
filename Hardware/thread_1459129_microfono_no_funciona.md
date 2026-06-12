---
title: "microfono no funciona"
date: 2010-04-21
forum: Hardware
---

### Post by 3nG3ndR0 on 2010-04-21
hola a todos, nunca había usado el mic en ubuntu e instale el Teamspeack 3 y no me funciona el mic, en preferencias de sonido>entrada> no esta en mute y en nivel de entrada no se mueve al hablar, no se como solucionar e buscado en google pero nada.

el mic esta bueno lo uso en windows.

distribución: ubuntu 9.10

ariel@ariel-desktop:~$ uname -a

```
Linux ariel-desktop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

```ariel@ariel-desktop:~$ aplay -l

```
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC883 Analog [ALC883 Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: SB [HDA ATI SB], dispositivo 1: ALC883 Digital [ALC883 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
```ariel@ariel-desktop:~$ cat /proc/asound/version

```
Advanced Linux Sound Architecture Driver Version 1.0.20.
```ariel@ariel-desktop:~$ head -n 1 /proc/asound/card*/codec#*

```
Codec: Realtek ALC883
```

---

### Post by jagrock on 2010-07-03
Tengo el mismo problema... Pudiste solucionarlo?

---

### Post by 3nG3ndR0 on 2010-07-05
> **jagrock said:**
> Tengo el mismo problema... Pudiste solucionarlo?

no e podido utilizar el TS en ubuntu.

---

### Post by Lutho on 2010-07-17
yo tuve un problema, similar pero me pasaba en con la aplicación skype.
Bueno alguien me recomendó instalar "control de volumen PulseAudio"
bueno la cual cuando entro en la aplicación en las pestallas de arriba "Dispositivo de entrada" es ahi donde pude configurar mi micrófono.

---

### Post by nopersona on 2010-07-31
Ya probaste un alsamixer por terminal?

---

