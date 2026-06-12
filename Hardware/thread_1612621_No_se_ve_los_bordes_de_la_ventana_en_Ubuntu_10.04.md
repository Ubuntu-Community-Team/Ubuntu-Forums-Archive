---
title: "No se ve los bordes de la ventana en Ubuntu 10.04"
date: 2010-11-03
forum: Hardware
---

### Post by PeTTi on 2010-11-03
Actualice al nuevo Ubuntu, y los bordes de las ventanas no se ven, al menos que en efectos visuales le ponga ninguno.
Se ve que no reconoce la placa de video.
La placa de video que tengo es una Geoforce 9600.
 
**EDIT**:
hice unos cambios, que fue ir a Configuración de Hadware, poner el que decía recomendado
 [IMG]http://imgur.com/XwZkN.png[/IMG]
 y fue peor, porque reinicié, y ahora solo veo en 800xalgo... 
Y cuando voy a las configuraciones de Nvidia pasa esto:
 [IMG]http://imgur.com/mSqyP.png[/IMG]
Gracias :)

---

### Post by guillermolisi on 2010-11-03
Estas corriendo nvidia-settings con privilegios de superusuario (sudo), tal como aconseja el mensaje del ultimo screenshot ?

---

### Post by PeTTi on 2010-11-03
> **guillermolisi said:**
> Estas corriendo nvidia-settings con privilegios de superusuario (sudo), tal como aconseja el mensaje del ultimo screenshot ?
No, ¿cómo se hace?
sudo nvidia-settings ?
Si es así, lo puse y no pasó nada.

---

### Post by guillermolisi on 2010-11-03
En una terminal/consola ingresa ```
sudo nvidia-settings
```Te va a pedir la password de la cuenta de usuario con la que instalaste Ubuntu (que no se vera en pantalla mientras la escribas) y que posiblemente sea la que usas habitualmente. Luego deberias ver la misma ventana que copiaste pero con mas opciones y sin ese mensaje. 

Comenta que tal te resulto.

---

### Post by PeTTi on 2010-11-03
> **guillermolisi said:**
> En una terminal/consola ingresa ```
sudo nvidia-settings
```Te va a pedir la password de la cuenta de usuario con la que instalaste Ubuntu (que no se vera en pantalla mientras la escribas) y que posiblemente sea la que usas habitualmente. Luego deberias ver la misma ventana que copiaste pero con mas opciones y sin ese mensaje. 

Comenta que tal te resulto.
nah@nah-soloUbuntu:~$ sudo nvidia-settings
[sudo] password for nah: 

Y se abre lo mismo que cuando voy a Nvidia Setting, y me aparece el mismo cartel que en la imagen que puse antes.

---

### Post by guillermolisi on 2010-11-04
En una terminal/consola pone "lsmod" (sin las comillas) y mostra su salida. Eso nos mostrara que modulos/drivers se estan usando, especialmente para la placa de video.

---

### Post by marcelo_bur on 2010-11-04
Bue, yo no se mucho, pero quizás esto ayude.
Personalmente cuando tengo que hacer algo como root uso el comando 'sudo -i' y luego sigo trabajando.
Dejo un screenshot de la terminal.
[http://img607.imageshack.us/img607/5922/pantallazop.png]("http://img607.imageshack.us/img607/5922/pantallazop.png")
Saludos

---

### Post by PeTTi on 2010-11-04
> **guillermolisi said:**
> En una terminal/consola pone "lsmod" (sin las comillas) y mostra su salida. Eso nos mostrara que modulos/drivers se estan usando, especialmente para la placa de video.

nah@nah-soloUbuntu:~$ lsmod
Module                  Size  Used by
snd_hda_codec_realtek   203375  1 
snd_hda_intel          22037  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
binfmt_misc             6587  1 
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
arc4                    1153  2 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nvidia               7087672  24 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
bitblit                 4707  1 fbcon
zd1211rw               42217  0 
softcursor              1189  1 bitblit
snd                    54180  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              205402  1 zd1211rw
soundcore               6620  1 snd
ppdev                   5259  0 
psmouse                63245  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
vga16fb                11385  1 
cfg80211              126528  2 zd1211rw,mac80211
vgastate                8961  1 vga16fb
parport_pc             25962  1 
serio_raw               3978  0 
usbhid                 36110  0 
intel_agp              24119  0 
hid                    67032  1 usbhid
agpgart                31724  2 nvidia,intel_agp
lp                      7060  0 
parport                32635  3 ppdev,parport_pc,lp
floppy                 53016  0 
r8169                  34076  0 
mii                     4381  1 r8169

> Bue, yo no se mucho, pero quizás esto ayude.
Personalmente cuando tengo que hacer algo como root uso el comando 'sudo -i' y luego sigo trabajando.
Dejo un screenshot de la terminal.
[http://img607.imageshack.us/img607/5922/pantallazop.png](http://img607.imageshack.us/img607/5922/pantallazop.png)
Saludos
Puse:
sudo -i
Y luego:
sudo nvidia-settings
Y se me abrió esto:
[IMG]http://imgur.com/x7YLE.png[/IMG]

---

### Post by marcelo_bur on 2010-11-04
Ahora si la máquina te ve como root. Esa es la ventana desde la cual podes configurar las preferencias de tu tarjeta de video, incluyendo resolución de pantalla y otras cosas. Pero seguramente Guillermo sabrá explicarte todo eso mejor que yo. Te comento que también tengo una Nvidia y me funciona mejor con los drivers genéricos de Ubuntu que con el propietario, hice la prueba en una ocasión.
Saludos

---

### Post by PeTTi on 2010-11-04
Ahora tengo la resolución de siempre, los efectos de siempre, pero no se ven los bordes de la ventana, excepto de Google Chrome, pero debe ser porque tiene otro tipo de borde de ventana.
Probé poniendo todo tipo de bordes de ventana y siempre pasa lo mismo..

---

### Post by guillermolisi on 2010-11-04
Que pasa si suspendes los efectos de escritorio ? Vuelven los bordes ?

---

### Post by PeTTi on 2010-11-05
> **guillermolisi said:**
> que pasa si suspendes los efectos de escritorio ? Vuelven los bordes ?

sí                            .

---

### Post by guillermolisi on 2010-11-05
Proba con lo que se recomienda en [este post]("http://ubuntuforums.org/showpost.php?p=9998601&postcount=10") y comenta que resultado obtenes

---

### Post by PeTTi on 2010-11-05
> **guillermolisi said:**
> Proba con lo que se recomienda en [este post]("http://ubuntuforums.org/showpost.php?p=9998601&postcount=10") y comenta que resultado obtenes

Ahora me fijo, lo que hice y funcionó, fue instalar el Emerald y cuando reinicié me apareció la barra de Emerald :D

EDIT:
Poniendo:

metacity --replace


Funcionó. :D
Gracias chaval :)

---

