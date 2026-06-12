---
title: "[SOLVED] cq 40 305 la sin sonido"
date: 2009-08-25
forum: Hardware
---

### Post by charlezz on 2009-08-25
hola comunidad  de linux soy un nuevo usuario q recientemente esta aprendiendo a  utilizar esta herramienta tan grande como es linux y como cualquier usuario nuevo me  encontre con varios  problemitas pero ahora  me  he encontrado  con uno que me supera  por   demas ...
instale  ubuntu 9.04 en mi notebook HP cq40 305 LA hice la instalación y al iniciar no tengo sonido alguno. 
entonces   empece a   investigar con gente conocida y en foros pero no he encontrado la solucion...
paso a  describir lo que he hecho para ver  si alguien me ayuda un poco.
primero en entorno grafico revise que  los  canales no estén en  mute que al parecer es  algo que las  distros suelen hacer  segun varios  foros. 
luego revise  el alsamixer y comprobé nuevamente que los  canales están habilitados .
luego agregué algunas  lineas de  código al archivo alsa-base.conf que  fui encontrando en varios foros exclusivos de  ubunntu. pero esto no prdujo ningun cambio.
me  recomendaron usar  el alsaconf pero al parecer  jaunty no lo trae.
me recomendaron buscar un kernel mas actualizado para  ver  si tiene un mejor  reconocimeiento de  de hardware pero la verdad es   que no me animo a  meterme an algo tan complicado... soy bastante newbie
 bueno  espero que alguien me  ayude  a  resolverlo por  que se me acaban las alternativas  y es un bajon encontrarse  con problemas asi y no poder  arreglarlos 
desde ya muchas gracias   al  que conteste este post ydisculpen  si algo esta  mal es  mi primer post en un foro

gracias 

**[CH@rLEZz]**

---

### Post by Cajuma on 2009-08-26
Hola
Fijate en:

Sistema>Preferencias>sonido>dispositivos proba con el que se
adapte a tu tarjeta de sonido.

---

### Post by josecuervo86 on 2009-08-26
Si podes, tambien corre el siguiente comando en una terminal, para ver que hardware tenes:

```
lspci
```

Luego pega el resultado

---

### Post by charlezz on 2009-08-26
hice el lspci y de los  dispositivos que me arrojo este el el de  sonido:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

en las opciones  de estan en Sistema>Preferencias>sonido>dispositivos no hay ninguna que le parezca

---

### Post by guillermolisi on 2009-08-26
> **charlezz said:**
> hice el lspci y de los  dispositivos que me arrojo este el el de  sonido:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

en las opciones  de estan en Sistema>Preferencias>sonido>dispositivos no hay ninguna que le parezca
Ingresa en una consola/terminal el comando "lsmod" (sin las comillas) y mostranos que sale.

---

### Post by charlezz on 2009-08-26
esto es  lo que me  arrojó el lsmod

charlezz@uma-notebook:~$ lsmod
Module                  Size  Used by
i915                   65668  2 
drm                    96424  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434228  3 
uvcvideo               63368  0 
joydev                 18368  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
psmouse                61972  0 
compat_ioctl32          9344  1 uvcvideo
serio_raw              13444  0 
usbhid                 42336  0 
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
pcspkr                 10496  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
iTCO_wdt               19108  0 
snd_rawmidi            29696  1 snd_seq_midi
iTCO_vendor_support    11652  1 iTCO_wdt
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
ieee80211_crypt_tkip    16896  0 
wl                   1281364  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
btusb                  19608  2 
video                  25360  0 
output                 11008  1 video
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by guillermolisi on 2009-08-26
> **charlezz said:**
> esto es  lo que me  arrojó el lsmod

charlezz@uma-notebook:~$ lsmod
Module                  Size  Used by
i915                   65668  2 
drm                    96424  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434228  3 
uvcvideo               63368  0 
joydev                 18368  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
psmouse                61972  0 
compat_ioctl32          9344  1 uvcvideo
serio_raw              13444  0 
usbhid                 42336  0 
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
pcspkr                 10496  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
iTCO_wdt               19108  0 
snd_rawmidi            29696  1 snd_seq_midi
iTCO_vendor_support    11652  1 iTCO_wdt
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
ieee80211_crypt_tkip    16896  0 
wl                   1281364  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
btusb                  19608  2 
video                  25360  0 
output                 11008  1 video
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
Salvo que este dejando pasar por alto algo que no logro detectar, para mi los modulos de sonido estan correctamente cargados. No veo nada raro.

Pregunta, esa maquina tiene algun control de volumen externo, tipo ruedita/potenciometro, combinacion de teclas Fn+<tecla de funcion>, alguna tecla de silencio total en el sistema de parlantes ?

Se supone que el audio de esa maquina funciona bien o nunca pudiste comprobarlo ?

---

### Post by charlezz on 2009-08-26
encontre la solucion la saque de un foro externo q encontre buscando el problema direstamente por el nombre del dispositivo les copio lo que decia el otro foro para todos los que tengan el mismo problema ya que es un problema habitual!
----------------------------------------------------------------------------------------------------------------------------------------------
root [ /home/leprosys ]-> lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

Hacer funcionar el sonido me ha costado mucho, el problema fue que me deje ir por el tutorial que esta en la Wiki de Arch. Este dispositivo de sonido es problemático, en Debian como en Ubuntu que fue donde tuve problemas con la calidad pero que se solucionaba fácilmente. [ver post]

Pero en Arch después de instalar Alsa:
# pacman -S alsa-lib alsa-utils alsa-oss

Lo único que hay que hacer es agregar las siguientes lineas al archivo "/etc/modprobe.d/sound" y si no existe pues habrá que crearlo:
options snd slots=snd-hda-intel
options snd-hda-intel enable_msi=1 model=hp-dv5
# Intel Corporation 82801I (ICH9 Family) HD Audio Controller
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
Lo encontré en el foro de ArchLinux

No hay que tocar ningún otro archivo de configuración y si se toco algo en "/etc/rc.conf" "/etc/modprobe.d/alsa-base" "/etc/modprobe.conf " habrá que dejarlos como estaban.

Nota: probé usar "alsaconf" que crea y añade los módulos a "/etc/modprobe.d/sound" pero no funciona.

---------------------------------------------------------------------------------------------------------------------------------------
 lo unico malo de esta solucion es que no puedo controlar el volumen desde el teclado con la tecla fn pero bueno por lo menos ahora tengo sonido ! 
estoy feliz!

gracias a todos los involucrados!

---

### Post by charlezz on 2009-08-26
gracias ya encontre la solucion la puse en el foro lo unico que hice fue crear el archibo sound y le pusse las lineas de codigo q dice ahi y listo!
lo de las teclas ya lo habia revisado... lo mismo ahora no controlan el volumen lo debo hacer desde la barra del entorno grafico.

mucha gracias!

---

