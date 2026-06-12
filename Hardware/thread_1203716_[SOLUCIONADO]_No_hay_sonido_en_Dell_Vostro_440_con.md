---
title: "[SOLUCIONADO] No hay sonido en Dell Vostro 440 con Ubuntu 9.04"
date: 2009-07-03
forum: Hardware
---

### Post by lagneila on 2009-07-03
Hola:

Tengo un equipo de sobremesa Dell Vostro 440 (reciente). Venía instalado con Vista y funcionaba bien el sonido. Al instalar Ubuntu 9.04 va todo estupendo salvo el tema del sonido. 

Soy nuevo en esto del Ubuntu. He consultado algunos foros y he conseguido recopilar la siguiente información de mi sistema, por si alguien puede ayudarme:

Información del Sistema relacionada a Audio
Versión de Ubuntu: jaunty
# Listar los dispositivos pci relacionados con audio:
```

$ lspci | grep -i audio

```
> 
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller

# Listar las Tarjetas disponibles con Alsa.
```

$ asoundconf list

```
> 
Names of available sound cards:
Intel

```

$ cat /proc/asound/cards

```
> 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ff8000 irq 22

# Listar los módulos o drivers de sonido cargados por el sistema.
```

$ lsmod | grep -i snd

```
> 
snd_hda_intel         434100  1 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

# Revisar que proceso está usando nuestro dispositivo de audio /dev/dsp:
```

$ lsof /dev/snd/controlC0 /dev/snd/pcmC0D0c /dev/snd/pcmC0D0p /dev/snd/pcmC0D1p /dev/snd/seq /dev/snd/timer

```
> 
COMMAND    PID     USER   FD   TYPE DEVICE SIZE NODE NAME
mixer_app 3623 lagneila   21u   CHR  116,7      5455 /dev/snd/controlC0




Un saludo...

---

### Post by RafaelG on 2009-07-03
> **lagneila said:**
> Hola:

Tengo un equipo de sobremesa Dell Vostro 440 (reciente). Venía instalado con Vista y funcionaba bien el sonido. Al instalar Ubuntu 9.04 va todo estupendo **salvo el tema del sonido**.


Hola Lagneila, disculpa cual seria el problema en especifico: No tienes sonido?, tienes error, etc...

Saludos

---

### Post by lagneila on 2009-07-06
> **RafaelG said:**
> Hola Lagneila, disculpa cual seria el problema en especifico: No tienes sonido?, tienes error, etc...

Saludos

Hola, gracias por la ayuda.

Efectivamente No hay sonido (hay silencio total) pero tampoco ocurre ningún error. 

Los problemas de cables, de altavoces,... están descartados pues el sonido Sí que funciona con el Windows Vista que venía por defecto.

Quiero pensar que es un problema de Drivers adecuados de la tarjeta de sonido (que va integrada en la placa) para el Ubuntu 9.04. No se si esos drivers aun no existen o no soy capaz de encontrarlos e instalarlos.

Éstas son las especificaciones del ordenador: [http://www1.euro.dell.com/es/es/empresas/Sobremesas/desktop-vostro-420/pd.aspx?refid=desktop-vostro-420&cs=esbsdt1&s=bsd](http://www1.euro.dell.com/es/es/empresas/Sobremesas/desktop-vostro-420/pd.aspx?refid=desktop-vostro-420&cs=esbsdt1&s=bsd)

Saludos.

---

### Post by moreback on 2009-07-06
Todo parece estar en orden, ¿revisaste los niveles de volumen con **Aplicaciones -> Sonido -> Control de volumen**?

El comando **alsamixer** también sirve para hacer lo mismo, pero desde la consola.

---

### Post by flakojaime on 2009-07-08
Hola,
 
Yo tuve problemas de sonido igual en un  notebook dell 1730, el problema era que estaba bajo el sonido en el Alsamixer...
 
saludos

---

### Post by lagneila on 2009-07-08
> **flakojaime said:**
> Hola,
 
Yo tuve problemas de sonido igual en un  notebook dell 1730, el problema era que estaba bajo el sonido en el Alsamixer...
 
saludos

Hola,

Por lo que veo en los controles de sonido se encuentran activados y con el volumen alto (ver imagen adjunta). Sigo pensando que puede ser la falta de los drivers adecuados.

Saludos y gracias.

---

### Post by RafaelG on 2009-07-08
> **lagneila said:**
> Hola, Sigo pensando que puede ser la falta de los drivers adecuados.

Saludos y gracias.


Hola Lagneila, **ALSA** (Advanced Linux Sound Architecture) es un componente del nucleo Linux destinado a sustituir a **OSS**  (Open Sound Sistema). Las Metas de **ALSA** es la configuración automática de tarjetas de sonido y el manejo de múltiples dispositivos de sonido en un sólo sistema.

Puede que necesites hacer un Upgrade  **ALSA 1.0.20 **drivers para solucionar tu problema, para saber que version de Alsa estas utilizando revisa en un terminal lo siguiente:

```
cat /proc/asound/version
```
Saludos

---

### Post by lagneila on 2009-07-09
> **RafaelG said:**
> Hola Lagneila, **ALSA** (Advanced Linux Sound Architecture) es un componente del nucleo Linux destinado a sustituir a **OSS**  (Open Sound Sistema). Las Metas de **ALSA** es la configuración automática de tarjetas de sonido y el manejo de múltiples dispositivos de sonido en un sólo sistema.

Puede que necesites hacer un Upgrade  **ALSA 1.0.20 **drivers para solucionar tu problema, para saber que version de Alsa estas utilizando revisa en un terminal lo siguiente:

```
cat /proc/asound/version
```Saludos

Hola:

Esta es la versión de la que dispongo ahora mismo

```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.18rc3.

```

Intentaré subir a la versión que mencionas. Gracias.

---

### Post by RafaelG on 2009-07-09
> **lagneila said:**
>  Hola:
Esta es la versión de la que dispongo ahora mismo

```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.18rc3
```

Lagneila te dejo dos Link uno en espanol y otro en ingles para actualizar **Alsa 1.0.20**

Actualizar Alsa 1.0.20
[http://fausto23.wordpress.com/2009/05/10/actualizar-alsa-1-0-20-en-ubuntu-jaunty/](http://fausto23.wordpress.com/2009/05/10/actualizar-alsa-1-0-20-en-ubuntu-jaunty/)

Upgrade Alsa 1.0.20
[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)


Saludos

---

### Post by lagneila on 2009-07-10
> **RafaelG said:**
> Lagneila te dejo dos Link uno en espanol y otro en ingles para actualizar **Alsa 1.0.20**

Actualizar Alsa 1.0.20
[http://fausto23.wordpress.com/2009/05/10/actualizar-alsa-1-0-20-en-ubuntu-jaunty/](http://fausto23.wordpress.com/2009/05/10/actualizar-alsa-1-0-20-en-ubuntu-jaunty/)

Upgrade Alsa 1.0.20
[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)


Saludos

Conseguido y Solucionado. 

La situación actual de mi sistema es la esperada:

```

$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on Jul 11 2009 for kernel 2.6.28-13-generic (SMP).

```

He seguido los pasos indicados en las páginas para Actualizar **Alsa 1.0.20** y el sonido se ha hecho. 

Muchas Gracias.

---

### Post by Carlos C on 2009-07-11
Ok, edito el título y lo dejo como solucionado. Gracias lagnelia por el feedback. Lo mismo a RafaelG y quienes propusieron soluciones.

---

