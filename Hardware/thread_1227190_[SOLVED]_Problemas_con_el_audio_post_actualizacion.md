---
title: "[SOLVED] Problemas con el audio post actualizacion"
date: 2009-07-30
forum: Hardware
---

### Post by KaKuS on 2009-07-30
Estimados, voy directo al problema. Después de la ultima actualizacion de kernel el audio dejo de funcionar, al reproducir cualquier sonido solo se escuchan unos chasquidos (frituras para los amigos).

En Sistema>Preferencias>Sonido testie todos los adaptadores y con el unico que escuche un tono es con el OSS - Open Sound System. Lo seleccione en todos los items pero ni el firefox ni los sonidos del sistema respetaron esa configuración ya que se siguen escuchando los chasquidos.

Info que les puede servir (pidan mas q hay :) )

```
cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
```
```
uname -r
2.6.28-14-generic
```

Me detecta la placa como una Intel Corporation 82801H (ICH8 Family) HD Audio Controller

Es una notebook TOSHIBA Tecra y hasta ahora no me habia dado problemas.

A ver si me ayudan :P:P:P:P

Saludos!

---

### Post by Mauro22 on 2009-07-30
Te recomendaria volver al kernel anterior... y ver si en la proxima version, anda mejor.


Si el hardware te anda, no actualices el kernel... a menos que sea medio kamikaze jeje...


En el proximo booteo, en el grub elegi el kernel anterior, a ver si ahi anda bien.

---

### Post by KaKuS on 2009-07-30
> **Mauro22 said:**
> Te recomendaria volver al kernel anterior... y ver si en la proxima version, anda mejor.


Si el hardware te anda, no actualices el kernel... a menos que sea medio kamikaze jeje...


En el proximo booteo, en el grub elegi el kernel anterior, a ver si ahi anda bien.

Es que me quería hacer hombre (?)

Ahora pruebo, pero pensé que si aparecía en la lista de actualizaciones no había drama.

---

### Post by guillermolisi on 2009-07-30
Si podes iniciar con el kernel anterior y funciona, mostranos la salida del comando lsmod.

Luego, reinicia con el nuevo kernel y repeti la misma operacion para que podamos comparar si en ambos casos esta cargando correctamente los modulos de audio.

---

### Post by KaKuS on 2009-07-31
Que mal, inicie con el kernel anterior y sigue haciendo lo mismo. Lo que quiere decir que me tengo que poner a mirar que otras cosas se actualizaron ese día.


Alguna idea de que puede ser? Alguna info que les pueda pegar?

Acá les pongo alguna info mas:

```
 cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x92100000 irq 22

```

```
lsmod | grep -i snd
snd_hda_intel         434228  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

```

Tengo exactamente el mismo problema que se reporta en este bug pero la solución que dan ahi no me soluciono nada...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/398551](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/398551)

---

### Post by guillermolisi on 2009-07-31
Como estan los controles/niveles de los canales si ingresas "alsamixer" en una consola/terminal ?
No habran quedado al minimo o silenciados ?

---

### Post by KaKuS on 2009-07-31
Reinstale todo, ahora funciona. Me molesta haber tenido que recurrir a esto pero bue.

Guillermo gracias por la ayuda, no llegue a verificar eso.... espero no haber laburado tanto por un simple nivel de audio.


Saludos y gracias...... sale un {SOLVED} xD

---

### Post by guillermolisi on 2009-07-31
> **KaKuS said:**
> Reinstale todo, ahora funciona. Me molesta haber tenido que recurrir a esto pero bue.

Guillermo gracias por la ayuda, no llegue a verificar eso.... espero no haber laburado tanto por un simple nivel de audio.


Saludos y gracias...... sale un {SOLVED} xD
Tendras que vivir con eso hasta la proxima oportunidad :D

---

### Post by yess on 2009-08-01
Hola... soy nueva en el foro y me pasa que tengo exactamente el mismo problema que kakus, solo escucho chasquidos para todo los sonidos de mi laptop dell inspiron 1420, no tengo ni idea a que se deba si ayer funcionaba perfectamente, soy nueva en linux y estoy tratando con todas mis fuerzas librarme de una vez de windows, si me pudieran ayudar estaria muy agradecida.
les dejo info que pueda servir:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

2.6.27-14-server

yess@yess-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9fc000 irq 21
 lsmod | grep -i snd
snd_hda_intel         384816  4 
snd_pcm_oss            46720  0 
snd_mixer_oss          22784  2 snd_pcm_oss
snd_pcm                83460  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38400  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29832  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  2 snd
snd_page_alloc         16264  2 snd_hda_intel,snd_pcm

---

### Post by KaKuS on 2009-08-02
> **yess said:**
> Hola... soy nueva en el foro y me pasa que tengo exactamente el mismo problema que kakus, solo escucho chasquidos para todo los sonidos de mi laptop dell inspiron 1420, no tengo ni idea a que se deba si ayer funcionaba perfectamente, soy nueva en linux y estoy tratando con todas mis fuerzas librarme de una vez de windows, si me pudieran ayudar estaria muy agradecida.
les dejo info que pueda servir:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

2.6.27-14-server

yess@yess-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9fc000 irq 21
 lsmod | grep -i snd
snd_hda_intel         384816  4 
snd_pcm_oss            46720  0 
snd_mixer_oss          22784  2 snd_pcm_oss
snd_pcm                83460  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38400  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29832  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  2 snd
snd_page_alloc         16264  2 snd_hda_intel,snd_pcm

Antes que nada ejecuta alsamixer en la consola y con las flechitas subi todos los niveles (es lo q me falto probar a mi xD).

Sino te voy guiando...

---

### Post by yess on 2009-08-02
Hola kakus muchisimas gracias por tu ayuda! diste en el clavo y solucione mi problema muchas gracias de verdad!!! y gracias por responder tan rapido estaba que me volvia loca jaja

saludos!!!

---

### Post by guillermolisi on 2009-08-02
Bienvenida Yess !! Otro(a) Ubuntero mexicano !! (que paso, les siguieron los pasos a Fetova ? :)  )

---

### Post by yess on 2009-08-04
Gracias por la bienvenida Guillermo Lisi!

saludos!!!

---

### Post by ivank18 on 2009-08-19
hola acabo d actualizar el kernel y perdi el sonido y el video, con el antiguo me funciona pero quiero saber si es necesario modificar la configuracion  en el nuevo kernel para q funcione porq cada vez q necesite actualizar el kernel pasara lo mismo y no se si tenga q volver a actuallizar el alsa y los drivers d sonido en cada kernel.
gracias.

---

### Post by ivank18 on 2009-08-20
hola no tengo sonido tras actualizar el kernel tampoco el driver de la tarjeta de video, me gustaria saber si es necesario reinstalar los drivers cada vez q actualice el kernel y como solucinarlo.
gracias

---

### Post by Hei Ku on 2009-08-20
Si los instalaste manualmente, vas a tener que volver a instalarlos cada vez. 

Mandale besos y abrazos a tu fabricante de hardware la proxima vez que lo veas, por hacerte la vida mas facil.

---

