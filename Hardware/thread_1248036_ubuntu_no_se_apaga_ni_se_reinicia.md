---
title: "ubuntu no se apaga ni se reinicia"
date: 2009-08-23
forum: Hardware
---

### Post by tsueseres on 2009-08-23
hola, tengo ubuntu 9.04 mi computadora es hp 6gb ram procesador core 2 duo lo he configurado ami gusto y le he instalado los &#7765;rogramas que usaba antes y tmb he ejecutado el gestor de actualizaciones, ahora cadavez que le pongo apagar o reniciar aparece el logo de ubuntu de que se esta cerrando y luego se pone una panatalla negra con una linea he aprensado ctrl+alt+f7 y me aparecen los procesos que se estan cerrando y se queda en system will now reboot pero nada hay se queda y tmb lo he dejado un buen rato asi pero nada se sigue quedando donde mismo. aprenso  ctrl+alt+supr y solo asi me reinicia

esta es una lista de los programas que he instalado  por si de casualidad el problema se encuentre en uno de ellos:

```
sudo aptitude install build-essential

sudo aptitude install kdelibs4-dev

sudo apt-get install ubuntu-restricted-extras

sudo apt-get install gparted

sudo apt-get install dhcp3-server

sudo apt-get install k3b

sudo apt-get install amsn

sudo apt-get install vlc

sudo apt-get install glipper

sudo apt-get install wine

sudo apt-get install mirage

sudo apt-get install amarok

sudo apt-get install ntfsprogs

sudo apt-get install cairo-dock

sudo apt-get install devilspie

sudo apt-get install gtk-recordmydesktop

sudo apt-get install emesene

sudo apt-get install startupmanager

sudo apt-get install mplayer

sudo apt-get install kommander p7zip

sudo apt-get install gmountiso

sudo apt-get install compizconfig-settings-manager

sudo apt-get install compiz-fusion-* (son plugins y extras)

sudo aptitude install wicd
```

---

### Post by staar on 2009-08-23
esto te pasó siempre? o antes andaba? podrías pasar el modelo exacto de la pc, por lo que entendí es una notebook, no? también la salida de ```
lspci
``` sería útil...

saludos

---

### Post by tsueseres on 2009-08-23
> **staar said:**
> esto te pasó siempre? o antes andaba? podrías pasar el modelo exacto de la pc, por lo que entendí es una notebook, no? también la salida de ```
lspci
``` sería útil...

saludos

me paso despues de haber instalado todo, antes si reiniciaba bien el modelo es hp pavilion dv7 2185dx

la salida es

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
05:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
05:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
05:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
05:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

```

---

### Post by staar on 2009-08-23
si apagas la wifi primero, y después la pc, el problema sigue? pasa cuando la usas con la batería, o con el cable, o con ambos? [acá](http://ubuntuforums.org/showthread.php?t=1134201) hay un thread (en inglés, avisá si no entendés) sobre tu tema, con muchas posibles soluciones...

saludos

---

### Post by Martinius on 2009-08-24
Hola a todos. Tengo el mismo problema desde hace algunos días con Ubuntu 9.04, la solucióm precaria que encontré fue cerrar sesión y apagar desde la pantalla de logueo.
¿ Convendría que abra un nuevo thread o que de los detalles acá ?

---

### Post by guillermolisi on 2009-08-24
> **Martinius said:**
> Hola a todos. Tengo el mismo problema desde hace algunos días con Ubuntu 9.04, la solucióm precaria que encontré fue cerrar sesión y apagar desde la pantalla de logueo.
¿ Convendría que abra un nuevo thread o que de los detalles acá ?
Si tu caso posee puntos en comun con este planteado, en forma mayoritaria, seguilo aqui mismo.

Es decir, si el sintoma que tenes, mas alla del hardware, es lo que se indica en el asunto y en el desarrollo de este thread, es pertinenete y corresponde seguirlo aqui.

---

### Post by tsueseres on 2009-08-24
ok ya cheque el link probe todo y no se soluciona nada sigue igual

pero si veo k los problemas son de la wireless card

---

### Post by staar on 2009-08-24
con el comando ```
lsmod
``` listas todos los módulos cargados, correlo y posteá la salida acá, así te podemos ayudar...

saludos

---

### Post by tsueseres on 2009-08-24
> **staar said:**
> con el comando ```
lsmod
``` listas todos los módulos cargados, correlo y posteá la salida acá, así te podemos ayudar...

saludos

```
Module                  Size  Used by
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63776  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
iptable_nat            14724  0 
nf_nat                 30100  1 iptable_nat
arc4                   10240  2 
nf_conntrack_ipv4      24216  3 iptable_nat,nf_nat
snd_hda_intel         557492  3 
ecb                    11392  2 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
nf_conntrack           84752  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         10496  1 nf_conntrack_ipv4
snd_pcm                99464  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
iwlagn                114820  0 
snd_seq_oss            41984  0 
iptable_mangle         11520  0 
iwlcore               106496  1 iwlagn
snd_seq_midi           15744  0 
iptable_filter         11392  0 
snd_rawmidi            33920  1 snd_seq_midi
leds_hp_disk           11400  0 
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
led_class              13064  2 iwlcore,leds_hp_disk
joydev                 20992  0 
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              28304  3 iptable_nat,iptable_mangle,iptable_filter
uvcvideo               69640  0 
psmouse                64028  0 
mac80211              251528  2 iwlagn,iwlcore
compat_ioctl32         18304  1 uvcvideo
sdhci_pci              16896  0 
video                  29204  0 
snd                    78920  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               21712  0 
videodev               45184  2 uvcvideo,compat_ioctl32
x_tables               31624  2 iptable_nat,ip_tables
sdhci                  27396  1 sdhci_pci
serio_raw              14468  0 
lis3lv02d              19408  0 
output                 11648  1 video
pcspkr                 11136  0 
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
iTCO_vendor_support    12420  1 iTCO_wdt
v4l1_compat            23940  2 uvcvideo,videodev
intel_agp              39408  0 
cfg80211               43680  3 iwlagn,iwlcore,mac80211
fglrx                2376104  33 
ohci1394               42164  0 
ieee1394              108288  1 ohci1394
r8169                  46596  0 
mii                    14464  1 r8169
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

```

---

### Post by staar on 2009-08-24
el módulo driver de tu placa es el iwlagn

saludos

---

### Post by tsueseres on 2009-08-24
> **staar said:**
> el módulo driver de tu placa es el iwlagn

saludos

si eso si lo logre conseguir, inclusive le di chmod 755 killwan como decia en un post de abajo pero nada sigue sin reiniciarme, lo unico que me funciona es aprensarle al boton de wireless antes de apagar pero quiero conseguilo apagandolo normalmente

---

### Post by tsueseres on 2009-08-26
mmmm nimodo he tratado demasiadas cosas y ahora me encuentro que tanpoco tenia sonido y tmb intente arreglarlo, pero nada, voy regresar a ubuntu 8.10 hasi me servian bien las cosas

grax por la ayuda

---

### Post by nopersona on 2009-08-28
Mira,[ lee este hilo]("http://ubuntuforums.org/showthread.php?t=1219262&page=3"), tiene información muy útil que te puede servir. Sería genial ver la salida de crtl+alt+f7, así descartaríamos procesos o carga de módulos y/o drivers.

---

