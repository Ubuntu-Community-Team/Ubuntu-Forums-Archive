---
title: "TVTime sin señal ENLTV"
date: 2008-09-02
forum: Hardware
---

### Post by guillermoezquer on 2008-09-02
hola gente les pido disculpas por volver a sacar el siguiente tema... pero he hecho lo q dicen los otros foros y lo q dicen un monton de tutoriales en la red y sigo sin hacer funcionar tvtime con mi tarjeta ENLTV... tv time me sigue diciendo q no tiene señal...  ya escribi en otro thread pero no me han constestado por eso es q decidi abrir uno nuevo... por cierto estoy usando ubuntu 8.04

---

### Post by fmsismo on 2008-09-03
Si haces un lscpi que te devuelve?

Configuraste el módulo con la sintonizadora?

Yo probe una flyview 2000 con gusty y no tuve problemas. Si el canal lo tenes sintonizado y la norma es correcta (pal-nc).

Fijate que en otro post adjunte un script para buscar los chips de la sintonizadora.  Te adjunto el link del archivo y del thread.

[http://ubuntuforums.org/showthread.php?t=304444&page=1](http://ubuntuforums.org/showthread.php?t=304444&page=1)
[http://ubuntuforums.org/attachment.php?attachmentid=67137&d=1209132896](http://ubuntuforums.org/attachment.php?attachmentid=67137&d=1209132896)

Saludos

---

### Post by guillermoezquer on 2008-09-03
esto es lo q me da cdo hago un lspci...

00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
04:04.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
04:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

si ves... toma como q tengo la philips SAA7130 lo cual es correcto... pero tvtime me dice q no tiene señal...

---

### Post by Mauro22 on 2008-09-03
Tenes alguna webcam o algo que transmita video aparte de la sintonizadora?


Ejecuta tvtime desde consola a ver si da algun error


Proba desde la consola

tvtime --device=/dev/video0

Luego con video1, etc, a ver cual anda.

OJO: Hace eso luego de haber cargado los modulos (sudo modprobe saa7134 card=3)

---

### Post by guillermoezquer on 2008-09-03
primero q nada gracias por las respuestas... te comento mi avance... ahora tvtime me toma el video... lo q no me anda es el sonido... he tratado de probar varias card y el resultado es el mismo... tengo conectada la placa al line-in y no esta mutado en el panel de sonido... tambien prove de conectar directamente a la salida de la placa pero tampoco hubo resultado... no se q mas puedo hacer...

---

### Post by fmsismo on 2008-09-04
Cual era el problema con el cual no tenías video.

Enchufá un par de parlantes o auriculares a la salida de audio de tu placa sintonizadora.  Así vamos aislando el problema.  Una vez que tengas sonido ahí, la forma más fácil de salir andando es que pongas el cable loop (que va desde la salida de la sintonizadora al line-in te tu placa de sonido).

Saludos

---

### Post by guillermoezquer on 2008-09-04
ya lo he hecho de las 2 formas... conectando los parlantes directamente a la salida de la placa y haciendo loop por la entrada de la placa de sonido donde tambien me fije q no estuviera mutada al line-in... y de ninguna de las 2 formas escucho nada... Tambien probe el siguiente script q encontre en un foro para ir probando los distintos tuner pero me tira errores a medida q se va ejecutando... 
#/bin/sh
MAXTUNER=73
i=0
while [ $i -lt $MAXTUNER ];
do
rmmod tuner saa7134
modprobe saa7134 card=3 tuner=$i
echo "Tuner actual:" $i
sleep 3 #
#tvtime
scantv
i=$(($i+1))
done

este es lo q me dise cdo lo ejecuto como root

El programa «scantv» no está instalado actualmente.  Puede instalarlo escribiendo:
apt-get install scantv
bash: scantv: orden no encontrada
/sbin/modprobe: invalid option -- d
Usage: /sbin/modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
/sbin/modprobe -r [-n] [-i] [-v] <modulename> ...
/sbin/modprobe -l -t <dirname> [ -a <modulename> ...]
Tuner actual: 1

si alguien pudiera ver cual es el problema lo agradeceria... yo la verdad q soy bastante nuevo en esto como para entender bien el script o cual es su problema... GRACIAS!

---

### Post by guillermoezquer on 2008-09-04
yo de nuevo... ahi logre solucionar uno de los problemitas q me deci cdo ejecutaba el scrip instlando el scantv.... lo q me sale ahora cdo ejecuto el script es:

[defaults]
input = Television
norm = NTSC

vbi: open failed [/dev/vbi]
open /dev/vbi: No such file or directory
/sbin/modprobe: invalid option -- d
Usage: /sbin/modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
/sbin/modprobe -r [-n] [-i] [-v] <modulename> ...
/sbin/modprobe -l -t <dirname> [ -a <modulename> ...]
Tuner actual: 7

tambien veo q me toma como norm NTSC y yo tengo configurado TVtime Palm-nc q es la norma q funciona.... gracias de nuevo

---

### Post by vk-cdg on 2008-09-04
> **guillermoezquer said:**
> primero q nada gracias por las respuestas... te comento mi avance... ahora tvtime me toma el video... lo q no me anda es el sonido... he tratado de probar varias card y el resultado es el mismo... tengo conectada la placa al line-in y no esta mutado en el panel de sonido... tambien prove de conectar directamente a la salida de la placa pero tampoco hubo resultado... no se q mas puedo hacer...


Yo tengo el mismo problema que vos, aún hoy sin solución. En mi caso sonido sale, pero a MUY bajo volumen. Me di cuenta cuando conecté unos auriculares a la salida de la placa sintonizadora una madrugada con todo en silencio. 
Hice la prueba de conectar unos parlantes amplificados directamente a la sintonizadora y con el volumen (de los parlantes) al mango obtengo un sonido moderado, digamos que si alguien mas habla en casa me tapa lo que sale por los parlantes.

Según mi deducción, es un problema de ubuntu, ya que con Mandriva anda bien y con Windowze también.

---

### Post by fmsismo on 2008-09-04
Ojo que el script tiene hardcodeado a la capturadora, tenes que modificarlo por el tuyo.

El scantv antes venía con el tvtime.  Fijate si queres instalarlo a mano.

sudo apt-get install scantv

El error con el modprobe no lo entiendo.

Podes tirar lsmod o correr los comandos del script a mano.  Y tirar el output uno por uno.

Saludos

---

### Post by guillermoezquer on 2008-09-04
ya intale scantv a mano y el error no me sale mas.. el error del modprobe si sigue... la verdad q no se por que aca les pego lo q me sale cdo hago un lsmod para ver si alguien entiende por q salta ese error... GRACIAS!
Module                  Size  Used by
tuner                  32204  0 
saa7134               171356  0 
binfmt_misc            14860  1 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
acpi_cpufreq           10832  1 
cpufreq_conservative    10632  0 
cpufreq_stats           8416  0 
cpufreq_ondemand       11152  2 
cpufreq_userspace       6180  0 
cpufreq_powersave       3200  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
video                  23444  0 
output                  5632  1 video
sbs                    17808  0 
sbshc                   8960  1 sbs
dock                   12960  0 
container               6656  0 
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
lp                     14916  0 
ipv6                  311848  25 
snd_hda_intel         440408  3 
tuner_simple           17428  1 
tuner_types            19072  1 tuner_simple
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
nvidia               8115088  34 
tea5767                 8964  0 
evdev                  14976  5 
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
ir_common              46340  1 saa7134
snd_seq_oss            38912  0 
compat_ioctl32         11264  1 saa7134
videodev               39424  3 tuner,saa7134,compat_ioctl32
v4l1_compat            17156  1 videodev
v4l2_common            15872  2 tuner,saa7134
serio_raw               9092  0 
snd_seq_midi           10688  0 
videobuf_dma_sg        16900  1 saa7134
videobuf_core          23172  2 saa7134,videobuf_dma_sg
tveeprom               16900  1 saa7134
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
button                 10912  0 
i2c_viapro             11672  0 
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             41128  1 
parport                44300  3 ppdev,lp,parport_pc
psmouse                46236  0 
pcspkr                  4992  0 
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
i2c_core               28544  8 tuner,saa7134,tuner_simple,nvidia,tea5767,v4l2_common,tveeprom,i2c_viapro
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10400  1 snd
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sd_mod                 33280  7 
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
pata_jmicron            8448  0 
sata_via               14596  6 
ata_generic             9988  0 
floppy                 69096  0 
pata_via               15620  0 
ahci                   33028  0 
pata_acpi               9856  0 
ehci_hcd               41996  0 
uhci_hcd               29856  0 
r8169                  36612  0 
libata                176432  6 pata_jmicron,sata_via,ata_generic,pata_via,ahci,pata_acpi
usbcore               169904  3 ehci_hcd,uhci_hcd
scsi_mod              178488  4 sd_mod,sg,sr_mod,libata
thermal                19744  0 
processor              41448  2 acpi_cpufreq,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  11

---

### Post by fmsismo on 2008-09-04
Hace esta prueba, baja el módulo de memoria y subilo con estos parámetros.

[INDENT]
#bajas el módulo de memoria
sudo rmmod saa7134_alsa saa7134 
#lo subis con estos parámetros
sudo modprobe saa7134 card=3 tuner=69
#backup de la lista de estaciones
mv ~/.tvtime/stationlist.xml ~/.tvtime/stationlist.old
#corres el scan de canales
tvtime-scanner [/INDENT]


Si esto te funcionó, fijate si tenes una línea del módulo saa7134 o sino agregala.
sudo gedit /etc/modprobe.d/options
# opciones para tarjeta de captura de video con chip phillips
options saa7134 card=3 tuner=69 i2c_scan=1 ir_debug=1

PD, el script que te pasaba yo estaba mejor

---

### Post by guillermoezquer on 2008-09-04
Hola fmsismo... la verdad q no recuerdo cual era el script q me diste vos... si todavia lo tienes no tengo problema en probarlo a ver si me funciona.. fuera de esto hice lo q me dijiste y en la linea

sudo modprobe saa7134 card=3 tuner=69

me vuelve a tirar el error del parametro de opcion... 

Usage: /sbin/modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
/sbin/modprobe -r [-n] [-i] [-v] <modulename> ...
/sbin/modprobe -l -t <dirname> [ -a <modulename> ...]

lo q me parecio muy raro fue q  puse la misma linea sin poner el tuner=69 y no me tiro error... no se si esto te indique algo especial...
tambien lo agregue de forma manual en modprobe.d/options y nada... realmente esto ya me esta empesando a molestar... jeje realmente quiero librarme de win... pero es algo q necesito.
Cualquier otra sugerencia sere bienvenida...

---

### Post by guillermoezquer on 2008-09-04
WWWWWWWWWWWWWOOOOOOOOOOOOOWWWWWWWWWW jaja me paso lo mismo q a vk-cdg... si tengo sonido... lo q pasa es q demaciaaaaaaado bajo.... tuve q poner mi oido en el parlante de mi equipo de musica para escucharlo... y por lo q lei q me puso es un problema de ubuntu... si alguien sabe cual podria ser o si tiene solucion lo agradeceria mucho, al igual q agradesco a fmsismo por tanta ayuda con todos los pasos anteriores...

---

### Post by Goico on 2008-09-06
Yo tengo una sintonizadora igual a esa y la instalo asi:

1) Bajo los modulos que se cargan por defecto
# rmmod saa7134_alsa
# rmmod saa7134

2) Levanto los modulos con los parametros correctos
# modprobe saa7134 card=3 tuner=69

3) Instalo tvtime
# apt-get install tvtime
Durante la instalacion seleccionamos que el input de la señal es cable y la norma PAL-Nc

ahora .. como normalmente me genera problemas con el sonido la plaquita fea esta .. uso un script que encontre en la web para ejecutarlo:

#!/bin/bash
amixer -q set "Line" 100% unmute
#amixer -q set "Analog Mix" 100% unmute
tvtime
amixer -q set "Line" 100% mute

Lo que hace esto es .. lleva el volumen de "Line" al tope, la linea que deje comentada es porque algunas placas se conectan al "Analog Mix" o "Auxiliar" .. despues ejecuta el tvtime .. y cuando lo cerramos mutea otra vez.
Se que hay una opcion en el tvtime.xml para configurar el "mute on exit", pero el problema es que al volver a abrirlo .. sigue muted, por lo tanto con este script se soluciona todo.

Espero le sirva a alguien, cada vez que instalo una nueva version de Ubuntu, con estos pasos tengo tv en no mas de 5 minutos!


Saludos

---

### Post by guillermoezquer on 2008-09-06
tampoco che... no hay forma... no tengo idea de como hacer para subir el volumen... he probado todo lo q he encontrado... pero no hay forma... gracias igual por todas sus respuestas

---

### Post by Menghus on 2009-03-19
buenas vengo a revivir un post muerto perdon!. la cuestion es que a gracias al post descubri que es con device 1, te hago una pregunta?

como hago para agregar en las opciones que debe ser device1 en ves de 0? si soy un asco de principiante en esto, saludos y gracias por la onda.

---

### Post by Mauro22 on 2009-03-19
Hola!


Tenes que iniciar tvtime desde la consola, asi:

tvtime --device=/dev/video1

---

### Post by ichMartin on 2010-02-20
> **fmsismo said:**
> Hace esta prueba, baja el módulo de memoria y subilo con estos parámetros.

[INDENT]
#bajas el módulo de memoria
sudo rmmod saa7134_alsa saa7134 
#lo subis con estos parámetros
sudo modprobe saa7134 card=3 tuner=69
#backup de la lista de estaciones
mv ~/.tvtime/stationlist.xml ~/.tvtime/stationlist.old
#corres el scan de canales
tvtime-scanner [/INDENT]


Si esto te funcionó, fijate si tenes una línea del módulo saa7134 o sino agregala.
sudo gedit /etc/modprobe.d/options
# opciones para tarjeta de captura de video con chip phillips
options saa7134 card=3 tuner=69 i2c_scan=1 ir_debug=1

PD, el script que te pasaba yo estaba mejor


Hola, disuculpen que reviva el post después de tnato tiempo, pero es que soy nuevo con ubuntu y tb estoy intentando instalar la placa. 
Seguí un par de tutoriales y al final pude conseguir imagen pero con audio muuuy bajo. Después reinicié la maquina y ya no pude conseguir que tvtime encuentre señal. Al parecer está trabado de alguna manera en la norma NTSC y no se como cambiarlo a Pal-Nc. No me hace caso cuando lo cambio por el menú y no se hacerlo por consola. Alguien sabría decirme como???
Disculpen y gracias!

---

