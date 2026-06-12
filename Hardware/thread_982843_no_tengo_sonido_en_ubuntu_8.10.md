---
title: "no tengo sonido en ubuntu 8.10"
date: 2008-11-15
forum: Hardware
---

### Post by marcesneibrun on 2008-11-15
hola como estan?
el problema es el siguiente, no puedo ver ningun video con sonido,cuando voy al icono de sonido lo pongo al maximo y comienza a titilar, no se oye nada y me cuelga la compu teniendola que reiniciar.
Si pueden ayudarme lo agradezco
Marcelo

---

### Post by guillermolisi on 2008-11-17
Sabes que placa/chip de sonido estas usando ?

Si no lo sabes, podrias mostrarnos la salida del siguiente comando en consola/terminal:

```
lspci
```

De ahi podremos ver que modelo de placa de audio tenes en la maquina.
La otra es que leas el manual de la motherboard si vino con sonido integrado.

Luego, podrias pasar que tipo de maquina estas usando (procesador, cantidad de memoria, tamaño de disco rigido) ?

---

### Post by Yunow on 2008-11-19
En mi caso tengo esto...

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

Busqué en muchas parte y lo que está haciendo la gente es volver al sonido de 8.04, pero tampoco me funcionó.

Alguien sabe si se puede usar pulseaudio???

Saludos.

---

### Post by guillermolisi on 2008-11-19
> **Yunow said:**
> En mi caso tengo esto...

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

Busqué en muchas parte y lo que está haciendo la gente es volver al sonido de 8.04, pero tampoco me funcionó.

Alguien sabe si se puede usar pulseaudio???

Saludos.
Verificaste si se estan cargando los modulos de sonido para esa placa ? (lsmod en la consola)

---

### Post by Yunow on 2008-11-20
No se que buscar... pero esto es lo que me devuelve...

```

Module                  Size  Used by
michael_mic             2560  6 
arc4                    2048  6 
ecb                     3584  6 
ieee80211_crypt_tkip    10496  3 
binfmt_misc            11400  1 
i915                   30976  2 
drm                    81812  3 i915
af_packet              22272  4 
ipv6                  261636  23 
ppdev                   9476  0 
acpi_cpufreq            7564  0 
cpufreq_userspace       3736  0 
cpufreq_stats           5252  0 
cpufreq_powersave       1792  0 
cpufreq_ondemand        8212  1 
freq_table              4612  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     7200  0 
sbs                    13832  0 
sbshc                   6784  1 sbs
container               4608  0 
iptable_filter          3456  0 
ip_tables              13584  1 iptable_filter
x_tables               16388  1 ip_tables
deflate                 3712  0 
zlib_deflate           20248  1 deflate
twofish                 6784  0 
twofish_common         13824  1 twofish
camellia               18688  0 
serpent                17280  0 
blowfish                8320  0 
des_generic            16640  0 
cbc                     4352  0 
aes_i586                8192  0 
aes_generic            27688  1 aes_i586
xcbc                    5768  0 
sha256_generic         11648  0 
sha1_generic            2432  0 
crypto_null             3328  0 
crypto_blkcipher       19716  3 ecb,cbc,crypto_null
af_key                 36880  0 
sbp2                   23436  0 
parport_pc             34980  0 
lp                     11812  0 
parport                36040  3 ppdev,parport_pc,lp
joydev                 12096  0 
pcmcia                 40364  0 
psmouse                40464  0 
serio_raw               7044  0 
sdhci                  17672  0 
ipw2200               147912  0 
ieee80211              34376  1 ipw2200
ieee80211_crypt         6272  2 ieee80211_crypt_tkip,ieee80211
mmc_core               48404  1 sdhci
yenta_socket           26636  1 
rsrc_nonstatic         13056  1 yenta_socket
pcmcia_core            39952  3 pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                  2944  0 
iTCO_wdt               11936  0 
iTCO_vendor_support     3844  1 iTCO_wdt
video                  19344  0 
output                  3712  1 video
battery                12932  0 
ac                      5892  0 
asus_laptop            18296  0 
led_class               5380  1 asus_laptop
button                  8080  0 
intel_agp              26940  1 
agpgart                34352  3 drm,intel_agp
evdev                  12032  12 
ext3                  135304  1 
jbd                    43924  1 ext3
mbcache                 8448  1 ext3
sg                     37552  0 
usbhid                 31616  0 
hid                    42624  1 usbhid
sr_mod                 17316  0 
cdrom                  36768  1 sr_mod
sd_mod                 30224  4 
ata_piix               22276  3 
pata_acpi               7296  0 
8139too                25856  0 
ata_generic             8068  0 
libata                165008  3 ata_piix,pata_acpi,ata_generic
scsi_mod              152972  5 sbp2,sg,sr_mod,sd_mod,libata
dock                   10124  1 libata
ohci1394               32816  0 
ieee1394               92472  2 sbp2,ohci1394
8139cp                 23296  0 
mii                     5760  2 8139too,8139cp
ehci_hcd               37900  0 
uhci_hcd               25232  0 
usbcore               148336  4 usbhid,ehci_hcd,uhci_hcd
raid10                 25344  0 
raid456               129040  0 
async_xor               4224  1 raid456
async_memcpy            2816  1 raid456
async_tx                7496  3 raid456,async_xor,async_memcpy
xor                    16264  2 raid456,async_xor
raid1                  24960  0 
raid0                   8448  0 
multipath               8448  0 
linear                  6400  0 
md_mod                 83988  6 raid10,raid456,raid1,raid0,multipath,linear
dm_mirror              28032  0 
dm_snapshot            20000  0 
dm_mod                 61412  2 dm_mirror,dm_snapshot
thermal                18716  0 
processor              32948  3 acpi_cpufreq,thermal
fan                     5508  0 
fuse                   48796  5 

```

---

### Post by guillermolisi on 2008-11-20
Bueno, salvo que haya leido mal y considerando el modelo de placa de sonido que tiene tu PC, no se estan cargando los modulos necesarios para que funcione el audio.

A titulo de ejemplo y para que veas la diferencia, te paso la misma informacion pero de una de las PC que uso con Ubuntu:

Salida de lspci para audio
```
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
```
Salida de lsmod (solo modulos de audio)
```
snd_hda_intel         344728  2
snd_hwdep              10500  1 snd_hda_intel
snd_pcm_oss            42016  0
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11528  2 snd_hda_intel,snd_pcm
snd_mixer_oss          17792  1 snd_pcm_oss
snd_seq_dummy           4868  0
snd_seq_oss            35456  0
snd_seq_midi            9248  0
snd_rawmidi            25632  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54096  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

```

Para lograr que se cargue el modulo proba lo siguiente en una consola:
```
modinfo soundcore
```

Si la salida te devuelve algo asi:
```
filename:       /lib/modules/2.6.24-21-server/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:
vermagic:       2.6.24-21-server SMP mod_unload 686
```
Significa que no tenes que compilar nada. Caso contrario habra que hacer un laburo adicional compilando (esta parte sugiero dejarla para despues, cuando tengamos la verificacion de esta comprobacion).

Suponiendo que te devuelve la existencia del Core sound module, ingresa en consola lo siguiente:
```
modprobe snd-hda-intel ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
```

Si te da error, repeti pero anteponiendo sudo antes de modprobe (separado por un espacio - sudo modprobe ....)(te pedira que ingreses tu pass).

Luego, siempre en consola, ingresas alsamixer (necesita que tengas instalado el paquete alsa-utils) y levantas todos los controles y habilitas todo. Luego proba si se escucha sonido.

Comenta si esto fue exitoso porque de serlo, para no tener que cargar a mano el modulo de sonido cada vez que inicias la PC, hay que editar el archivo /etc/modules y agregarle al final una linea con la identificacion del modulo de sonido que deberia salir cuando ejecutes un nuevo lsmod (podria ser snd_hda_intel).

Mas info en [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

---

### Post by Yunow on 2008-11-20
No funciono :(

Lo que sale del modinfo...

```

filename:       /lib/modules/2.6.25-2-386/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:        
vermagic:       2.6.25-2-386 mod_unload 486 

```

Y cuando corro para levantar los módulos no funciona...

Como usuario

```

WARNING: Failed to open config file /etc/modprobe.d/alsa-base.save: Permission denied
FATAL: Module snd_hda_intel not found.
WARNING: Failed to open config file /etc/modprobe.d/alsa-base.save: Permission denied
FATAL: Module snd_pcm_oss not found.
WARNING: Failed to open config file /etc/modprobe.d/alsa-base.save: Permission denied
FATAL: Module snd_mixer_oss not found.
WARNING: Failed to open config file /etc/modprobe.d/alsa-base.save: Permission denied
FATAL: Module snd_seq_oss not found.

```

Y como sudo 

```

FATAL: Module snd_hda_intel not found.
FATAL: Module snd_pcm_oss not found.
FATAL: Module snd_mixer_oss not found.
FATAL: Module snd_seq_oss not found.

```

Que puede ser??? esos modulos se descargan con synaptic???

Saludos y gracias por ayudar.

---

### Post by guillermolisi on 2008-11-22
Mmm .... tenes instalados los paquetes de alsa necesarios para configurar los modulos de sonido ?

Te paso la lista que tengo en una de mis maquinas para que compares.

alsa-base (fundamental)
alsa-oss
alsaplayer-esd
alsaplayer-oss
alsa-tools (fundamental)
ALSA utils (fundamental)
libao2
libasound2
libesd-alsa0
libsdl1.2debian-alsa
linux-sound-base (fundamental)
mpg123-alsa

Estos paquetes estan en una instalacion 8.04, pero supongo que para Alsa no deberia haber mucha diferencia con la 8.10.

Podes revisar que tenes y que te falta a traves del Synaptic.

---

### Post by atari130xe on 2008-11-22
Seguimos con el tema del sonido en Ubuntu :(, los que me conocen en el foro saben lo que vengo padeciendo desde algunas versiones atrás. Cuando apareció la 8.04 fué el acabose jejeje sonido? si, pero no para varias fuentes simultaneas, en la 8.10 supongo pasa lo mismo, la falta de "tunning" en el sistema de sonido (cosas no habilitadas por defecto, cosas ausentes, etc.) la unica solucion que yo estoy aplicando para las instalaciones que vengo haciendo es quitar pulseaudio y dejar alsa, sip un retroceso pero al menos funciona, a veces me dicen ¿pero que placa de audio tenés? y yo digo: de todo un poco, en 5 computadoras las 5 instalaciones con el mismo problema (las 5 con diferentes chips de audio), y bueno en algun momento será solucionado. El misterio que me gustaria resolver es el que hardware o configuracion tienen los que me dijeron que el sonido simultaneo les funciona de "una" en sus sistemas, yo hasta ahora no lo logre y voy por unas cuantas instalaciones limpias. paciencia! :)

---

### Post by mixed on 2008-11-24
Hola yo no soy especialista en linux ,hace ya unos meses que lo estoy usando ,tengo dos pc en red . la mia y la de mi novia =P te voy a comentar los problemas que tuvimos (ella) acerca del sonido. en mi pc reconocio todo no tuve que instalar nada . los dos pusimos 8.04 lts . tal vez porque mi pc es un viejita tengo mas soporte en drivers. es un p4 2.4 mother asus y video gforce 6200. pero ella si tuvo problemas tiene un amd2 mother gigabyte y video saphire x500. en la instalacion todo barbaro. pero cuando intentaba arrancar linux. le salia un error del noapic. tenia que editar el kernel cada vez para cargar linux. una vez adentro no reconocia la placa de video ni la de sonido. en fin investigando y leyendo foros le pudo hacer funcionar el video y la placa de sonido tenia los drivers correctos (alsa) pero no se escuchaba nada. asi que intente instalarle intrepid. y bastante mejor . soluciono el noapic del comienzo el driver lo reconocio del video. y del sonido tambien. solo que no se escuchaba.. el problema fue cambiar de plug de salida por donde sale el sonido . tal vez parezca tonto pero mas de uno ni se fijo cambiando la salida de sonido..de atras de la pc.

---

### Post by Yunow on 2008-11-24
guillermolisi:
  Ya probé todo, instalé todo lo que tenías y sigue el problema. No se que mas hacer... voy  a ver si me pongo a compilar el ultimo driver de alsa que era un error que está en la wiki de ubuntu pero en la versión 6.04 (un poco viejo)

  Este es el error que sale en Sonido cuando quiero probar si funciona.

<code>
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
</code>

Probé de todo lo que encontré en foros, cambiando archivos de configuración...

Lo que no pude probar es iniciar una version live para ver si funciona el sonido porque no tengo lectora de dvd y esta mother no levanta desde pendrive.

Saludos y seguiré buscando.

---

### Post by guillermolisi on 2008-11-24
> **Yunow said:**
> guillermolisi:
  Ya probé todo, instalé todo lo que tenías y sigue el problema. No se que mas hacer... voy  a ver si me pongo a compilar el ultimo driver de alsa que era un error que está en la wiki de ubuntu pero en la versión 6.04 (un poco viejo)

  Este es el error que sale en Sonido cuando quiero probar si funciona.

<code>
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
</code>

Probé de todo lo que encontré en foros, cambiando archivos de configuración...

Lo que no pude probar es iniciar una version live para ver si funciona el sonido porque no tengo lectora de dvd y esta mother no levanta desde pendrive.

Saludos y seguiré buscando.

Ese problema de la version 6.04 deberia estar recontra solucionado a esta altura.

Probaste abriendo alsamixer en una consola, habilitando y levantando todos los volumenes ? Y esto mismo pero probando los parlantes en los demas conectores de la placa de audio ?

Despues de haber agregado los paquetes que te faltaban (que no se si te faltaban algunos y cuales eran), volviste a hacer el proceso que te comente al principio ?

Si lo hiciste, que te devolvio la salida del comando lsmod ?

---

### Post by Yunow on 2008-11-24
Sigue todo igual

Al correr alsamixer
```

No mixer elems found

```

lsmod sigue todo igual...

Encontré algo mas...

```

/etc/init.d/alsa-utils stop
rmmod snd_hda_intel
modprobe snd-hda-intel
/etc/init.d/alsa-utils start

```

Probando algo tan simple encuentro que al cargar el modulo da "FATAL: Module snd_hda_intel not found"

Así que estoy buscando algo con respecto a eso...

Saludos.

---

### Post by guillermolisi on 2008-11-24
> **Yunow said:**
> Sigue todo igual

Al correr alsamixer
<code>
No mixer elems found
</code>

lsmod sigue todo igual...

Encontré algo mas...

<code>
/etc/init.d/alsa-utils stop
rmmod snd_hda_intel
modprobe snd-hda-intel
/etc/init.d/alsa-utils start
</code>

Probando algo tan simple encuentro que al cargar el modulo da "FATAL: Module snd_hda_intel not found"

Así que estoy buscando algo con respecto a eso...

Saludos.

Buscando en Google encontre un caso similar, digo similar porque esta persona tenia problemas con el modem, no con el audio. Pero sirvio para ver que los nombres de los modulos pueden ser otros.
Te cito a continuacion los comandos que esta persona uso y que resultado tuvo, como para que los repitas a ver que pasa:
```

[merce en trobairitz]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-es"):~$ lsmod | grep snd
snd_intel8x0           33692  1
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8
snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm


[merce en trobairitz]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-es"):~$ lsof /dev/snd/*
COMMAND    PID  USER   FD   TYPE DEVICE SIZE NODE NAME
mixer_app 5031 merce   36u   CHR  116,0      8675 /dev/snd/controlC0


[merce en trobairitz]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-es"):~$ cat /proc/asound/cards
0 [ICH6           ]: ICH4 - Intel ICH6
                     Intel ICH6 with unknown codec at 0xb0040800,
irq 169

[merce en trobairitz]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-es"):~$ cat /proc/asound/modules0 snd_intel8x0
```Fijate que en este caso el modulo principal se llama snd_intel8x0 con lo cual probaria el procedimiento que se aconseja en el site de Alsa para placas Intel (que es el que te sugeri hicieras en primer termino) pero en lugar de usar snd_hda_intel habria que usar snd_intel8x0.

Si queres leer el mensaje directamente anda a 
[https://lists.ubuntu.com/archives/ubuntu-es/2006-September/018957.html](https://lists.ubuntu.com/archives/ubuntu-es/2006-September/018957.html)

---

### Post by Yunow on 2008-11-25
Todo salve vacío...

```
yunow@yunowPC:~$ lsmod | grep snd
yunow@yunowPC:~$ lsof /dev/snd/*
lsof: status error on /dev/snd/*: No such file or directory
lsof 4.78
 latest revision: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/)
 latest FAQ: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ)
 latest man page: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man)
 usage: [-?abhlnNoOPRstUvVX] [+|-c c] [+|-d s] [+D D] [+|-f]
 [-F [f]] [-g [s]] [-i [i]] [+|-L [l]] [+m [m]] [+|-M] [-o [o]]
 [-p s] [+|-r [t]] [-S [t]] [-T [t]] [-u s] [+|-w] [-x [fl]] [--] [names]
Use the ``-h'' option to get more help information.
yunow@yunowPC:~$  cat /proc/asound/cards
cat: /proc/asound/cards: No existe el fichero ó directorio
yunow@yunowPC:~$ cat /proc/asound/modules0 snd_intel8x0
cat: /proc/asound/modules0: No existe el fichero ó directorio
cat: snd_intel8x0: No existe el fichero ó directorio
```


Ya probé varias cosas más y sin resultado... Traté de usar el module-assistant para usar los fuentes de alsa y tampoco los puedo compilar, da un error.

Tampoco puedo correr alsamixer

```

yunow@yunowPC:~$ alsamixer 
No mixer elems found

```

Si logro solucionarlo les aviso.

Saludos.

---

### Post by guillermolisi on 2008-11-26
Encontre algo relacionado con esa placa de sonido pero es necesario ser mas especifico para saber si funcionara o no segun este sitio:

[http://hardware4linux.info/module/HDA_Intel/](http://hardware4linux.info/module/HDA_Intel/)

Dale una mirada, esta en Ingles, y pregunta lo que haga falta.

De paso, no pasarias una salida completa del lspci asi veo de primera mano que clase de hardware estas usando ?

---

### Post by Yunow on 2008-11-26
Te paso lo que me pediste, mientras leo lo que me dejaste...

```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
01:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
01:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
01:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

```

Es una notebook asus A3AC (creo).

---

### Post by losoollenos on 2008-11-28
Hola que tal, me sumo al problema porque estuve probando varias cosas y no puedo solucionarlo.
De repente dejó de tener audio en toda cuestión y desapareció el ícono del panel. Acá está el lspci:

ubuntu@ubuntu-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 655 Host (rev 50)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000]

Gracias y saludos !!!!!

---

### Post by guillermolisi on 2008-11-29
> **losoollenos said:**
> Hola que tal, me sumo al problema porque estuve probando varias cosas y no puedo solucionarlo.
De repente dejó de tener audio en toda cuestión y desapareció el ícono del panel. Acá está el lspci:

ubuntu@ubuntu-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 655 Host (rev 50)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000]

Gracias y saludos !!!!!
Por casualidad, hiciste alguna actualizacion que te cambio el kernel ?

Cuando inicias la PC el Grub te dice que presiones Esc para ver el menu con las alternativas de arranque.

La primera entrada es el kernel mas nuevo que tenes en la PC. SI tenes uno anterior, proba de iniciar con ese y fijate si tenes audio.

Si no tenes mas que un solo kernel (no tomes en cuenta las entradas indicadas como arranque seguro), copia la salida del comando lsmod y vemos si aun tenes los modulos cargados.

Despues conta como salio la prueba o envia la salida que te mencione.

---

### Post by guillermolisi on 2008-11-29
> **Yunow said:**
> Es una notebook asus A3AC (creo).
Por que la duda ?

No se si leiste los links que te pase, pero con algunas maquinas las placas de audio ICH6 e ICH7 tienen problemas para hacerlas andar con Ubuntu.

---

### Post by losoollenos on 2008-11-29
Gracias por tu respuesta guillermolisi.
Te comento que sí tengo las dos versiones del Kernel en el Grub, la que termina en 7 y la otra en 9....pero en ninguna hay audio. No te sabría decir si fue a partir de la actualización el problema. Te paso el lsmod:

ubuntu@ubuntu-desktop:~$ lsmod
Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  4 
binfmt_misc            16904  1 
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
video                  25104  0 
output                 11008  1 video
pci_slot               12552  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
evdev                  17696  6 
serio_raw              13444  0 
psmouse                45200  0 
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
pcspkr                 10624  0 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
arc4                    9984  2 
snd_usb_audio          89728  1 
snd_usb_lib            24192  1 snd_usb_audio
snd_pcm                83204  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_usb_audio
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
sn9c102               149124  0 
snd_hwdep              15236  1 snd_usb_audio
videodev               41344  1 sn9c102
v4l1_compat            22404  1 videodev
snd_seq_dummy          10884  0 
rtl8180                36352  0 
mac80211              216820  1 rtl8180
eeprom_93cx6           10240  1 rtl8180
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_seq_oss            38528  0 
cfg80211               32392  2 rtl8180,mac80211
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_usb_lib,snd_seq_midi
nvidia               4717332  32 
i2c_core               31892  1 nvidia
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 14224  0 
snd                    63268  20 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
sis_agp                15232  1 
agpgart                42184  2 nvidia,sis_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ata_generic            12932  0 
sata_sis               13444  3 
pata_acpi              12160  0 
pata_sis               18436  1 sata_sis
ohci_hcd               31888  0 
ehci_hcd               43276  0 
libata                177312  4 ata_generic,sata_sis,pata_acpi,pata_sis
sis900                 27904  0 
mii                    13440  1 sis900
usbcore               148848  6 snd_usb_audio,snd_usb_lib,sn9c102,ohci_hcd,ehci_hcd
scsi_mod              155212  4 sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
ubuntu@ubuntu-desktop:~$ 

Bueno espero que te sirva, muchas gracias y saludos

---

### Post by guillermolisi on 2008-11-29
> **losoollenos said:**
> Gracias por tu respuesta guillermolisi.
Te comento que sí tengo las dos versiones del Kernel en el Grub, la que termina en 7 y la otra en 9....pero en ninguna hay audio. No te sabría decir si fue a partir de la actualización el problema. Te paso el lsmod:

ubuntu@ubuntu-desktop:~$ lsmod
Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  4 
binfmt_misc            16904  1 
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
video                  25104  0 
output                 11008  1 video
pci_slot               12552  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
evdev                  17696  6 
serio_raw              13444  0 
psmouse                45200  0 
**snd_intel8x0**           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
pcspkr                 10624  0 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
arc4                    9984  2 
snd_usb_audio          89728  1 
snd_usb_lib            24192  1 snd_usb_audio
snd_pcm                83204  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_usb_audio
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
sn9c102               149124  0 
snd_hwdep              15236  1 snd_usb_audio
videodev               41344  1 sn9c102
v4l1_compat            22404  1 videodev
snd_seq_dummy          10884  0 
rtl8180                36352  0 
mac80211              216820  1 rtl8180
eeprom_93cx6           10240  1 rtl8180
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_seq_oss            38528  0 
cfg80211               32392  2 rtl8180,mac80211
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_usb_lib,snd_seq_midi
nvidia               4717332  32 
i2c_core               31892  1 nvidia
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 14224  0 
snd                    63268  20 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
sis_agp                15232  1 
agpgart                42184  2 nvidia,sis_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ata_generic            12932  0 
sata_sis               13444  3 
pata_acpi              12160  0 
pata_sis               18436  1 sata_sis
ohci_hcd               31888  0 
ehci_hcd               43276  0 
libata                177312  4 ata_generic,sata_sis,pata_acpi,pata_sis
sis900                 27904  0 
mii                    13440  1 sis900
usbcore               148848  6 snd_usb_audio,snd_usb_lib,sn9c102,ohci_hcd,ehci_hcd
scsi_mod              155212  4 sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
ubuntu@ubuntu-desktop:~$ 

Bueno espero que te sirva, muchas gracias y saludos
Proba de cargar el modulo de sonido:
```
sudo modprobe snd_intel8x0
```Luego verifica que los controles de la consola de audio esten todos habilitados y subilos al maximo para luego probar si tenes audio (con algo simple, lo que tengas a mano y que no requiera de codecs especificos).

Si con esto funciona, edita el /etc/modules con gedit, nano o tu editor preferido y agregale al final ```
snd_intel8x0
``` si es que no esta ingresado ya en ese archivo. De esta forma evitas tener que cargarlo a mano cada vez que inicias.

Todo esto suponiendo que ya hallas verificado los controles de sonido de la consola, que los parlantes esten bien conectados, que el modulo de sonido no se cargue cuando se inicia Ubuntu, etc.

Conta como te fue.

Te marque en negrita el modulo de sonido que tiene tu maquina para esa placa en la salida del lsmod.

---

### Post by guillermolisi on 2008-11-29
> **Yunow said:**
> Sigue todo igual

Al correr alsamixer
```

No mixer elems found

```lsmod sigue todo igual...

Encontré algo mas...

```

/etc/init.d/alsa-utils stop
rmmod snd_hda_intel
modprobe snd-hda-intel
/etc/init.d/alsa-utils start

```Probando algo tan simple encuentro que al cargar el modulo da "FATAL: Module snd_hda_intel not found"

Así que estoy buscando algo con respecto a eso...

Saludos.
Proba lo mismo pero en lugar de snd_hda_intel usa snd_intel8x0.
Es decir
     ```

     modprobe snd_intel8x0 ; modprobe snd_pcm_oss ; modprobe snd_mixer_oss ; modprobe snd_seq_oss 
```


Conta como te fue.

---

### Post by losoollenos on 2008-11-29
Hice esto:

ubuntu@ubuntu-desktop:~$ sudo modprobe snd_intel8x0
ubuntu@ubuntu-desktop:~$ 

Después supuse que los volúmenes de consola era con alsamixer -Dhw ? los controles están al máximo pero no se cómo saber si están habilitados....
Luego probé en sistema/preferencias/sonido y con unos archivos mp3 y nada, no hay audio.
Antes de postear acá probé esto que encontré en el foro/es, te comento por las dudas te sirva.....

sudo killall pulseaudio
sudo alsa force-reload

Luego había que poner en sistema/preferencias/sonido todo en ALSA, pero no pasó nada, obviamente.

Saludos

---

### Post by guillermolisi on 2008-11-29
> **losoollenos said:**
> Hice esto:

ubuntu@ubuntu-desktop:~$ sudo modprobe snd_intel8x0
ubuntu@ubuntu-desktop:~$ 

Después supuse que los volúmenes de consola era con alsamixer -Dhw ? los controles están al máximo pero no se cómo saber si están habilitados....
Luego probé en sistema/preferencias/sonido y con unos archivos mp3 y nada, no hay audio.
Antes de postear acá probé esto que encontré en el foro/es, te comento por las dudas te sirva.....

sudo killall pulseaudio
sudo alsa force-reload

Luego había que poner en sistema/preferencias/sonido todo en ALSA, pero no pasó nada, obviamente.

Saludos
Los controles habilitados de Alsamixer (modo consola) estan "iluminados", una X con fondo de color verde, y los que estan apagados dice MM sin iluminar.

Para seleccionar un control te moves con las flechas izquierda y derecha (cambia de color el nombre del control, al pie de cada slider). Una vez elegido el control que queres habilitar, presionas > para un canal y < para el otro. Si estaba encendido lo apaga y si estaba apagado lo enciende.. Tenes que encender los dos canales del control.

Revisaste la conexion a los parlantes ? Probaste de cambiar el plug a otra salida de la placa (sin importar si dice parlantes, microfono o lo que sea). He leido que hubo casos en los que despues de una actualizacion la salida de parlantes cambio de jack.

Con esa salida del lsmod deberias tener sonido perfectamente porque indica que los modulos de sonido estan cargados.

Estas corriendo Intrepid, cierto  ?

---

### Post by losoollenos on 2008-11-29
Lo solucionaste Guillermo !!!!!
Para que quede un poco más claro y le sirva a alguien más:
Estoy corriendo Intrepid, la conexión de los parlantes estaba bien y no tuve que cambiar la salida.
Habilité el control Master, Pcm y creo que ninguno más (algunos ya estaban habilitados); en realidad para habilitarlos pasaban de MM a dos ceros con fondo verde, primero reemplazabas una M con < por un cero y después la otra con >, para lo cual tuve que apretar < y el de mayúsculas (las flechas para arriba que no se cómo se llaman), lo digo porque esto fue nuevo para mí y por ahí le sirva a algún novatote como yo. Y listo!!!!
Nuevamente agradezco mucho tu atención, porque como te dije, estuve buscando bastante y no podía solucionarlo; un poco seguramente se debe a que muchas explicaciones dan a veces cuestiones como obvias, que no hace falta aclarar y ahí los novatos eternos quedamos pagando.....

Un abrazo y hasta pronto !!!!

Claudio

---

### Post by guillermolisi on 2008-11-29
> **losoollenos said:**
> Lo solucionaste Guillermo !!!!!
Para que quede un poco más claro y le sirva a alguien más:
Estoy corriendo Intrepid, la conexión de los parlantes estaba bien y no tuve que cambiar la salida.
Habilité el control Master, Pcm y creo que ninguno más (algunos ya estaban habilitados); en realidad para habilitarlos pasaban de MM a dos ceros con fondo verde, primero reemplazabas una M con < por un cero y después la otra con >, para lo cual tuve que apretar < y el de mayúsculas (las flechas para arriba que no se cómo se llaman), lo digo porque esto fue nuevo para mí y por ahí le sirva a algún novatote como yo. Y listo!!!!
Nuevamente agradezco mucho tu atención, porque como te dije, estuve buscando bastante y no podía solucionarlo; un poco seguramente se debe a que muchas explicaciones dan a veces cuestiones como obvias, que no hace falta aclarar y ahí los novatos eternos quedamos pagando.....

Un abrazo y hasta pronto !!!!

Claudio
Me alegro mucho !!

Las diferencias en como se ve tu Alsamixer y el mio posiblemente se deban a que yo sigo usando la 8.04 porque no creo que me pase a la 8.10 (no por ahora).

Cuando puedas, mandame una medallita (como esa que se ve abajo a la derecha en cada mensaje).

Otro para vos y ya sabes, aqui se pelea hasta que sale funcionando :)

---

### Post by losoollenos on 2008-11-29
Uhh cómo es lo de las medallitas? son como créditos? yo no sabía nada de eso, nunca le di ni una a los que me ayudaron, DISCULPAS A TODOS !!!!
Explicame por favor porque no me doy cuenta dónde están.....

---

### Post by losoollenos on 2008-11-29
Ah, ahí cuando me loguié apareció, es así ?

---

### Post by Yunow on 2008-11-30
Lo mismo...

```

FATAL: Module snd_intel8x0 not found.
FATAL: Module snd_pcm_oss not found.
FATAL: Module snd_mixer_oss not found.
FATAL: Module snd_seq_oss not found.

```

Los módulos esos se bajan o vienen incluidos en el kernel, como funcionan???

Saludos.

---

### Post by guillermolisi on 2008-11-30
> **losoollenos said:**
> Ah, ahí cuando me loguié apareció, es así ?
Jajajaa !! Si ! Lo hiciste muy bien !!

Gracias !

---

### Post by guillermolisi on 2008-11-30
> **Yunow said:**
> Te paso lo que me pediste, mientras leo lo que me dejaste...

```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
01:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
01:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
01:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

```Es una notebook asus A3AC (creo).
Estuve buscando informacion sobre esa placa de audio y ese modelo de Asus y el puntaje de funcionalidad que se logro bajo Linux es medio. Es decir, no funciona "out of the box" sino que aparentemente hay que laburar un poco ([http://hardware4linux.info/component/17338/](http://hardware4linux.info/component/17338/)).

Fijate que el puntaje mas alto es 5 y a este modelo le asignan un 3 como promedio porque en algunos Linux directamente no funciona y en otros sale con fritas.

En el sitio de Asus, donde estan las caracteristicas de la maquina, no dice mucho, tampoco en los casos que busque en google poniendo "intel 82801FB/FBM/FR/FW/FRW ubuntu".

En otras distribuciones como Madriva, tiran un par de cosas pero nunca pude ver la confirmacion de que fue exitosa la solucion.

De lo que estoy seguro es que el modulo se llama snd_hda_intel y que si la salida de "modinfo soundcore" no da nula tendrias que poder cargar los modulos correspondientes, considerando que tenes los paquetes de Alsa necesarios y suficientes para esta tarea.

Fijate que en este mismo thread aparecio otro caso que con casi la misma placa de audio tenia los modulos cargados y salio funcionando porque era solo una cuestion de volumen en los controles del mixer.

---

### Post by guillermolisi on 2008-12-01
Yunow

Dale una leida a los mensajes de este thread [http://ubuntuforums.org/showthread.php?t=984681](http://ubuntuforums.org/showthread.php?t=984681) que puede ser que por ahi venga la cosa y termine funcionando.

Avisame si probaste algo y como te fue.

---

### Post by Yunow on 2008-12-11
Volvió el sonido en parte...

Después de ver que eran los módulos y consultarlo con amigos que están en linux mas tiempo.

Como los módulos vienen junto con los kernel probé con iniciar con kernels más viejos y dejó de tirar error pero el sonido no funcionaba.

Así que me fijé que kernel tenía instalados y me di cuenta que tenía instalados los kernels generic y los 386 todos mesclados. Así que creo que en versiones ateriores de ubuntu usaba generic, así que instalé todo lo que encontré como generic.

Ahora volvió el sonido para la música, pero los videos de youtube salen sin sonido, probaré de instalar todo 386 a ver que pasa.

Cual es la diferencia entre 386 y Generic???

Saludos.

---

### Post by guillermolisi on 2008-12-12
> **Yunow said:**
> Volvió el sonido en parte...

Después de ver que eran los módulos y consultarlo con amigos que están en linux mas tiempo.

Como los módulos vienen junto con los kernel probé con iniciar con kernels más viejos y dejó de tirar error pero el sonido no funcionaba.

Así que me fijé que kernel tenía instalados y me di cuenta que tenía instalados los kernels generic y los 386 todos mesclados. Así que creo que en versiones ateriores de ubuntu usaba generic, así que instalé todo lo que encontré como generic.

Ahora volvió el sonido para la música, pero los videos de youtube salen sin sonido, probaré de instalar todo 386 a ver que pasa.

Cual es la diferencia entre 386 y Generic???

Saludos.
Si no entendi y recuerdo mal creo que la principal diferencia radica en que el kernel 386 utiliza solamente un nucleo de los que podria poseer un procesador con mas de uno y el generic utiliza los dos (en caso de que sea doble nucleo).

---

### Post by compiz-fusion on 2008-12-24
Hola a todos, como estan? tengo este mismo problemita , no se si se daño despues de una actualizacion o es quer realmente se daño la tarjeta :p . no tengo windows para probarla :lolflag: . esto me paso hace 2 meses.

esta es la info :

***LSPCI:***

> kicker@kicker-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)



***LSMOD:***

> kicker@kicker-desktop:~$ lsmod
Module                  Size  Used by
snd_hda_intel         381488  0 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ipv6                  263972  8 
binfmt_misc            16904  1 
bridge                 56980  0 
rfcomm                 44432  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
pci_slot               12552  0 
container              11520  0 
video                  25104  0 
output                 11008  1 video
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
battery                18436  0 
af_packet              25728  2 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
evdev                  17696  7 
psmouse                45200  0 
serio_raw              13444  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
nvidia               7103300  34 
button                 14224  0 
pcspkr                 10624  0 
i2c_sis96x             12420  0 
i2c_core               31892  2 nvidia,i2c_sis96x
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
sis_agp                15232  1 
agpgart                42184  2 nvidia,sis_agp
ext3                  133384  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
pata_acpi              12160  0 
8139too                31616  0 
pata_sis               18436  3 
8139cp                 27520  0 
ohci_hcd               31888  0 
libata                177312  3 ata_generic,pata_acpi,pata_sis
mii                    13440  2 8139too,8139cp
usbcore               148848  2 ohci_hcd
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 


***modinfo soundcore:***

> kicker@kicker-desktop:~$ modinfo soundcore
filename:       /lib/modules/2.6.27-9-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     E4F49ED9C4CFD1A5A923330
depends:        
vermagic:       2.6.27-9-generic SMP mod_unload modversions 586 




***Despues puse este comando: aqui no tube ningun problema ***

> kicker@kicker-desktop:~$ sudo modprobe snd-hda-intel ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
kicker@kicker-desktop:~$ 


***tengo todo esto instalado:***

> alsa-base (fundamental)
alsa-oss
alsaplayer-esd
alsaplayer-oss
alsa-tools (fundamental)
ALSA utils (fundamental)
libao2
libasound2
libesd-alsa0
libsdl1.2debian-alsa
linux-sound-base (fundamental)
mpg123-alsa

[B][I]
Alsamixer:[/I][/B]

> kicker@kicker-desktop:~$ alsamixer
No mixer elems found



***lsmod | grep snd:***


> kicker@kicker-desktop:~$ lsmod | grep snd
snd_hda_intel         381488  0 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm


ahora no se que mas tengo que hacer, pregunta. en Sistema-preferencia-sonido-dispositivo mire en varios foro que uno lo ponian en Autodetectar y otro en alsa . probe los dos pero aun asi nada :s . espero que alguien mas sepa que se puede hacer

---

### Post by Yunow on 2008-12-27
Yo lo resolví instalando los Restricted-modules del kernel que tenías instalado. Creo que la actualización te lo desinstala porque en cada versión hay más modulos libres. Fijate de reinstalarlos y al reiniciar debería funcionar.

Saludos.

---

### Post by guillermolisi on 2008-12-27
> **compiz-fusion said:**
> Hola a todos, como estan? tengo este mismo problemita , no se si se daño despues de una actualizacion o es quer realmente se daño la tarjeta :p . no tengo windows para probarla :lolflag: . esto me paso hace 2 meses.

esta es la info :

***LSPCI:***




***LSMOD:***



***modinfo soundcore:***



***Despues puse este comando: aqui no tube ningun problema ***




***tengo todo esto instalado:***



[B][I]
Alsamixer:[/I][/B]





***lsmod | grep snd:***





ahora no se que mas tengo que hacer, pregunta. en Sistema-preferencia-sonido-dispositivo mire en varios foro que uno lo ponian en Autodetectar y otro en alsa . probe los dos pero aun asi nada :s . espero que alguien mas sepa que se puede hacer

Me llama la atencion que en tu salida del lspci no figura ningun hardware relacionado con Audio.

Fijate la salida que posteo Yunow del mismo comando y vas a ver una que explicitamente hace referencia al audio, cosa que en tu caso no ocurre.

Estara deshabilitada desde el BIOS ? Se habra roto ?

---

### Post by compiz-fusion on 2008-12-28
> **Yunow said:**
> Yo lo resolví instalando los Restricted-modules del kernel que tenías instalado. Creo que la actualización te lo desinstala porque en cada versión hay más modulos libres. Fijate de reinstalarlos y al reiniciar debería funcionar.

Saludos.

Gracias por responder los dos , de todo modo voy a revisar en el bios , que quiere desir que se haya roto?

instalar los ***Restricted-modules***? , como lo instalo? si es por medio del synaptic cual instalo salen un monton

---

### Post by guillermolisi on 2008-12-28
> **compiz-fusion said:**
> Gracias por responder los dos , de todo modo voy a revisar en el bios , que quiere desir que se haya roto?

instalar los ***Restricted-modules***? , como lo instalo? si es por medio del synaptic cual instalo salen un monton
Por "que se haya roto" quiero significar que tenga algun inconveniente fisico que impida que funcione correctamente. Por ejemplo, si la placa de sonido es discreta, es decir no es integrada a la motherboard, podria haberse movido de su zocalo haciendo que no se la detecte adecuadamente.

Es que como te decia, me llama la atencion que tengas los modulos de sonido cargados (salida del lsmod) pero en la salida del comando lspci no figura ningun componente de hardware relacionado con Audio.

Para instalar los restricted modules podes usar Synaptic o apt-get install <nombre_de_paquete>.

Por ejemplo, en mi maquna tengo instalado linux-restricted-modules-2.6.24-22-generic porque estoy con esa version de kernel.

Para saber que version estas usando e instalar el paquete correcto ingresa en consola:```

uname -a
```
que te va a decir que version y tipo de kernel estas usando.

En mi caso da:
```
guille@guillermo:~$ uname -a
Linux guillermo **2.6.24-22-generic** #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux
```

---

### Post by compiz-fusion on 2009-02-03
***[COLOR="Red"]cambieeeeeeeeeeee[/COLOR]***

compre otra tarjeta madre :p 

pero ahora tengo otro vendito problemaaaaaaaaa. el volumen esta muyy bajoooooooo , hice de todo e reinstale ubuntu 8.10 y nada sigo con el mismo problema. esta muy bajo el volumen


**Distribucion:** ubuntu 8.10
**Tarjeta madre :** intel D102GGC2
**Proc:**pentium IV 3.2 GH
**Ram: **1 GB
**Driver de video:** FGLRX


***lspci***


> 00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



**lsmod**


> Module                  Size  Used by
ipv6                  263972  14 
af_packet              25728  2 
binfmt_misc            16904  1 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_ondemand       14988  2 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
pci_slot               12680  0 
video                  25232  0 
output                 11008  1 video
wmi                    14504  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
snd_hda_intel         384176  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
evdev                  17696  6 
snd_seq_midi           14336  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
serio_raw              13444  0 
snd_rawmidi            29824  1 snd_seq_midi
psmouse                45200  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fglrx                1813960  29 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_piix4              16144  0 
button                 14224  0 
pcspkr                 10624  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
i2c_core               31892  1 i2c_piix4
ati_agp                14988  0 
agpgart                42184  2 fglrx,ati_agp
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ext3                  133256  2 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  5 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
8139too                31616  0 
sata_sil               15752  0 
pata_acpi              12160  0 
8139cp                 27520  0 
mii                    13440  2 8139too,8139cp
ata_generic            12932  0 
pata_atiixp            12800  4 
ehci_hcd               43788  0 
ohci_hcd               32016  0 
libata                178208  4 sata_sil,pata_acpi,ata_generic,pata_atiixp
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
usbcore               149360  3 ehci_hcd,ohci_hcd
dock                   16656  1 libata
thermal                23708  0 
processor              42156  2 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5 





**modinfo soundcore**


> filename:       /lib/modules/2.6.27-11-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     E4F49ED9C4CFD1A5A923330
depends:        
vermagic:       2.6.27-11-generic SMP mod_unload modversions 586


**lsmod | grep snd**


> snd_hda_intel         384176  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm




**Estas son algunas imagenes del sonido:**


[http://www.imaxenes.com/imagen/pantallazo1sq75hp.png.html](http://www.imaxenes.com/imagen/pantallazo1sq75hp.png.html)


[http://www.imaxenes.com/imagen/pantallazo_21pc96fz.png.html](http://www.imaxenes.com/imagen/pantallazo_21pc96fz.png.html)


[http://www.imaxenes.com/imagen/pantallazo_11rh5406.png.html](http://www.imaxenes.com/imagen/pantallazo_11rh5406.png.html)


[http://www.imaxenes.com/imagen/pantallazo_31xg74hi.png.html](http://www.imaxenes.com/imagen/pantallazo_31xg74hi.png.html)

---

### Post by Hei Ku on 2009-02-03
Probaste subir el resto de los volumenes, a ver que pasa? Tambien de cambiar el Master channel.

---

### Post by compiz-fusion on 2009-02-04
si amigo , ya subi todo y a la misma vez cambiaba los canales pero nada :s

---

