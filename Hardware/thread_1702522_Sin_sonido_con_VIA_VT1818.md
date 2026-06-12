---
title: "Sin sonido con VIA VT1818"
date: 2011-03-07
forum: Hardware
---

### Post by losoollenos on 2011-03-07
Hola cómo andan tod@s ???

Bueno los otros días cambié el Mother para solucionar un problema de compatibilidad y ahora tengo otro !!! jajaj.

Es que este Mother (Asus m4a87td) trae el sonido on-board con la VIA VT1818, y creo que no la está detectando correctamente.

Creí entender del inglés que se solucionaba instalando el "linux-backports-modules-alsa-maverick-generic" pero no tuve esa suerte, o, a lo mejor, me está faltando hacer algo más, no se.....

Dejo el "lspci":

ubuntu@maverick:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
04:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
05:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5670]
05:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
ubuntu@maverick:~$ 

Espero me puedan dar una mano.

Muchas gracias!!!

---

### Post by guillermolisi on 2011-03-08
La salida de "sudo lsmod" ayudaria para saber que drivers/modulos se estan cargando y asociados con que placa (esa maquina tiene audio analogico y digital/HDMI)

---

### Post by losoollenos on 2011-03-08
ubuntu@maverick:~$ sudo lsmod
[sudo] password for uuntu: 
Module                  Size  Used by
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_atihdmi     3079  1 
binfmt_misc             7984  1 
snd_hda_codec_via      62447  1 
snd_seq_midi            5932  0 
snd_hda_intel          26147  2 
snd_hda_codec         100951  3 snd_hda_codec_atihdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_rawmidi            22207  1 snd_seq_midi
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
radeon                910067  2 
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    68212  1 radeon
drm_kms_helper         32836  1 radeon
gspca_zc3xx            47258  0 
snd                    64181  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
gspca_main             27688  1 gspca_zc3xx
videodev               49359  1 gspca_main
psmouse                62080  0 
serio_raw               4910  0 
v4l1_compat            15519  1 videodev
v4l2_compat_ioctl32    12614  1 videodev
drm                   206198  4 radeon,ttm,drm_kms_helper
edac_core              46822  0 
edac_mce_amd            9387  0 
i2c_algo_bit            6208  1 radeon
k10temp                 3535  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
xhci_hcd               60496  0 
asus_atk0110           12987  0 
i2c_piix4              10047  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
ahci                   22210  2 
pata_jmicron            2771  0 
r8169                  42254  0 
mii                     5261  1 r8169
pata_atiixp             4405  0 
libahci                26148  1 ahci
ubuntu@maverick:~$ 

Gracias

---

### Post by guillermolisi on 2011-03-08
Hasta donde veo los modulos de audio estan correctamente cargados y asociados a ambas salidas. Tal vez la mirada de otro ayude a descubrir si sobra o falta algo.

Revisaste la configuracion de Pulse Audio para ver cual de las dos salidas toma por defecto y como hace el fallback ?

---

### Post by losoollenos on 2011-03-08
En Sistema/Preferencias/Sonido la opción de Hardware es "Audio interno", y en Salida "Audio interno Analog Stereo".

Explicame por favor qué es el fallback.

Muchas gracias

---

### Post by guillermolisi on 2011-03-08
Fallback es el metodo que utiliza un proceso cuando tiene mas de una alternativa para utilizar recursos de la maquina. En este caso como tenes dos salidas de audio, si elegis una y esa no se puede habilitar o da un error, entonces el servidor de audio (Pulse en este caso) busca el siguiente recurso en la lista para intentar lograr proveer audio.

Los cables estaran correctamente colocados ? A veces las salidas son confusas, sobre todo cuando contas con varias.

Como estan los niveles de volumen para cada canal de cada una ?

---

### Post by losoollenos on 2011-03-08
Tengo sonido en windows, así que la placa no es y los cables están bien conectados.

Me parece que en las opciones de sonido está faltando una salida, porque me muestra dos, no son tres?: la normal, la óptica y la de la placa de video (Ati radeon 5670), me explico?

---

### Post by guillermolisi on 2011-03-08
Puede ser que este faltando una, pero a mi entender la HDMI y la optica son ambas digitales, solo cambia el conector fisico.

Que funcione en Windows no necesarimente significa que los cables estan correctamente conectados porque como se usan otros drivers puede ocurrir que las señales se canalicen en forma diferente y lo que esta presente en un conector lo esta en otro en Linux.

De todas formas lo que digo no es concluyente, es mi apreciacion al respecto.

---

### Post by losoollenos on 2011-03-08
JJAAAJJJ !!! que alegría !!!, le faltaba una "trabita" más a la ficha para entrar del todo, anda de diez.

Gracias Guillermo, un abrazo !!!

---

