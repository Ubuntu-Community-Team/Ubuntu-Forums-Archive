---
title: "Sin Sonido Frontal en Ubuntu"
date: 2009-06-23
forum: Hardware
---

### Post by Meenn on 2009-06-23
Les cuento mi problema.. tengo Ubuntu 9.04 y Windows Vista en el mismo equipo.

en Windows Vista el sonido no tengo ningun drama. la targeta que tengo es una 5.1

en el EVEREST en Vista me indica que esta targeta tengo

 <_< *Realtek ALC888/S/T @ ATI SB600 - High Definition Audio Controller*

> **Placa base**:
            Tipo de procesador =      DualCore Intel Pentium D 820, 2800 MHz (14 x 200)
            Nombre de la Placa Base =     ECS RC415ST-PM
            Chipset de la Placa Base =    ATI Radeon Xpress 1100
            Memoria del Sistema  =    1792 MB (DDR2-533 DDR2 SDRAM)

        **Multimedia:**
            Tarjeta de sonido  =    Realtek ALC888/S/T @ ATI SB600 - High Definition Audio Controller

**Audio PCI/PnP**
             
        Realtek ALC888/S/T @ ATI SB600 - High Definition Audio Controller      PCI


 **ATI SB600 - High Definition Audio Controller** 
 
        Propiedades del dispositivo:
            Descripción del dispositivo  =    ATI SB600 - High Definition Audio Controller
            Tipo de Bus  =    PCI
            Bus / Dispositivo / Función  =    0 / 20 / 2
            Identificador del dispositivo  =    1002-4383
            N° del Sub-sistema =     1631-E02D
            Clase de dispositivo  =    0403 (High Definition Audio)
            Revisión  =    00
            Fast Back-to-Back Transactions  =    No soportado
 
        Funcionalidades del dispositivo:
            Opera a 66 MHz  =    No soportado
            Bus Mastering  =    Activado
y el sonido me funsiona completamente bien en los 6 conectores de atras y los 2 frontales, como aparesen en la fotos.

[IMG]http://img523.imageshack.us/img523/8278/panelw.jpg[/IMG]


[IMG]http://img526.imageshack.us/img526/7420/packardbellimediad3720.jpg[/IMG]


pero en Ubuntu 9.04 solamente me suena los de atraz... y los frontales no.. nada de nada..

y este el hadware que me aparese en linux

 <_<  *Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)*

_**Comando lspci**_
> 00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
**_Comando lsmod_**

> Module                  Size  Used by
pppoe                  18112  2 
pppox                  11276  1 pppoe
binfmt_misc            16776  1 
radeon                342816  2 
ppdev                  15620  0 
drm                    96296  3 radeon
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
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
psmouse                61972  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
i2c_piix4              18448  0 
serio_raw              13316  0 
pcspkr                 10496  0 
ati_agp                14988  0 
agpgart                42696  2 drm,ati_agp
shpchp                 40212  0 
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


y al escuchar musica en Ubuntu, solamente me funsinan los conectores de atraz.. y los frontales a los cuales yo utilizo mayormente el microfono y parlantes no me suena nada de nada. que puedo hacer ?

revise el Alsa Mixer si tenia en mute o con poco volumen pero nada de nada, todos estan al maximo y abilitados.

que puedo hacer ?
 algun driver que hay que bajar o algunas cosas para modificar o otros programas a instalar ?

Saludos..  espero su ayuda

---

### Post by CdK1 on 2009-06-23
has revisado con alsamixer?

Si no lo has hecho, prueba esto:

nano ~/.asoundrc

Y pon:

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

Ahora, claro está, primero ve el asunto con alsamixer...

---

### Post by kamus on 2009-06-24
No has pensando que quizás están mal conectados los conectores en la placa madre?

Saludos:o

---

### Post by Psycopatologic on 2009-06-24
> **kamus said:**
> No has pensando que quizás están mal conectados los conectores en la placa madre?

Saludos:o

Si en vista le funcionan, es por que estan bien conectados y esos no traen conectores, si la placa es integrada viene soldado a la placa, si es PCI bueno, ya se saben la historia.

Haz lo que sugiere Cdk1, lo evidente es tu configuracion en ubuntu ya que no habilitaste todos los canales.

Cero aporte pero weh xD

mira aqui, es un problema similar al tuyo 

[http://ubuntuforums.org/showthread.php?t=1188968](http://ubuntuforums.org/showthread.php?t=1188968)

saludos

---

### Post by Meenn on 2009-11-03
Aqui otravez con el mismo problema...

Sigo sin Sonido frontal.

Instale desde cero Ubuntu 9.10 y otravez no tengo sonido frontal. ¿ que mas puede ser ?

---

