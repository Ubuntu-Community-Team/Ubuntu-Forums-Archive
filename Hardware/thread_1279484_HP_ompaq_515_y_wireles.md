---
title: "HP ompaq 515 y wireles?"
date: 2009-09-30
forum: Hardware
---

### Post by Mr-Judo on 2009-09-30
Hola, soy nuevo en esto y ya recivi ayuda para los drivers de video, y ahora estoy complicado con la coneccion wireles.
El tema es asi, con win xp, tenia un programa que buscaba las redes disponibles, ponia la clave y listo. Resulta que no se como hacer eso con ubuntu ya que no puedo ni ver el dispositivo wlan, y asi saber si esta instalado o no. la compu tiene una luz que indica que esta apagado. necesito solucionar esto ya que en unos dias me tengo que internar y en el sanatorio solo voy a tener acceso por wifi...

---

### Post by guillermolisi on 2009-09-30
> **Mr-Judo said:**
> Hola, soy nuevo en esto y ya recivi ayuda para los drivers de video, y ahora estoy complicado con la coneccion wireles.
El tema es asi, con win xp, tenia un programa que buscaba las redes disponibles, ponia la clave y listo. Resulta que no se como hacer eso con ubuntu ya que no puedo ni ver el dispositivo wlan, y asi saber si esta instalado o no. la compu tiene una luz que indica que esta apagado. necesito solucionar esto ya que en unos dias me tengo que internar y en el sanatorio solo voy a tener acceso por wifi...
De que maquina estamos hablando ? Marca y modelo ?

---

### Post by Mr-Judo on 2009-09-30
Hola, la maquina es una HP Compaq 515, pude hacer andar el disposivo con los driver de windows y "windows wireles driver". El tema es que con el controlador privativo no me funciona es decir cuando reinicio la maquina el dispositivo queda desactivado.

---

### Post by guillermolisi on 2009-10-01
> **Mr-Judo said:**
> Hola, la maquina es una HP Compaq 515, pude hacer andar el disposivo con los driver de windows y "windows wireles driver". El tema es que con el controlador privativo no me funciona es decir cuando reinicio la maquina el dispositivo queda desactivado.
Usaste ndiswrapper para utilizar el driver que esta hecho para Windows ?

Si es asi, me parece que te falta algo mas de trabajo para que no te suceda lo que comentas al reiniciar la maquina.

---

### Post by Mr-Judo on 2009-10-01
Seguro que falta laburo... Como dije antes soy nuevo en esto de linux.
Bueno gente, el tema es asi desinstale la aplicacion "windows wireles driver" e instale el driver privativo con el administrador de hardware. Si no reinicio la maquina todo OK funciona al pelo. Pero cuando reinicio me pone el dispositivo como "No esta en uso". 

Notebock HP Compaq 515.(AMD AthlonX2 DualCore QL-64)
Ubuntu 8.04 (Hardy)

---

### Post by guillermolisi on 2009-10-01
> **Mr-Judo said:**
> Seguro que falta laburo... Como dije antes soy nuevo en esto de linux.
Bueno gente, el tema es asi desinstale la aplicacion "windows wireles driver" e instale el driver privativo con el administrador de hardware. Si no reinicio la maquina todo OK funciona al pelo. Pero cuando reinicio me pone el dispositivo como "No esta en uso". 

Notebock HP Compaq 515.(AMD AthlonX2 DualCore QL-64)
Ubuntu 8.04 (Hardy)
Serias tan amable de postear las salidas en una terminal/consola de los comandos "lspci" y "lsusb" (sin las comillas) ?

Luego, con la interface inalambrica activa, la salida del comando "lsmod" ?

---

### Post by Mr-Judo on 2009-10-02
**Aca va lo que tira la consola:**
**"lspci"**
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4357 (rev 10)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
______________________________________________________________________________________

**"lsusb"**
Bus 007 Device 002: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 07b2:5101 Motorola BCS, Inc. SurfBoard SB5101 Cable Modem
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

______________________________________________________________________________________

[B]"lsmod"
[/B]Module                  Size  Used by
af_packet              27272  2 
cdc_ether               8448  0 
usbnet                 23304  1 cdc_ether
mii                     7552  1 usbnet
ipv6                  312104  14 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
cpufreq_stats           8416  0 
cpufreq_powersave       3200  0 
cpufreq_ondemand       11152  0 
freq_table              6464  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    10632  0 
cpufreq_userspace       6180  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
dock                   12960  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0 
uvcvideo               62212  0 
compat_ioctl32         11136  1 uvcvideo
videodev               30720  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
snd_hda_intel         442328  3 
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
fglrx                1804800  27 
snd_pcm                92296  2 snd_hda_intel,snd_pcm_oss
ndiswrapper           244000  0 
sky2                   54020  0 
container               6656  0 
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
video                  23444  0 
output                  5632  1 video
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
psmouse                46236  0 
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
serio_raw               9092  0 
wmi_acer               11076  0 
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
battery                16776  0 
ac                      8328  0 
button                 10912  0 
snd                    70984  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
i2c_piix4              11148  0 
i2c_core               28544  1 i2c_piix4
evdev                  14976  7 
pcspkr                  4992  0 
soundcore              10400  1 snd
ext3                  149264  1 
jbd                    57128  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sd_mod                 33280  4 
ehci_hcd               42124  0 
ohci_hcd               28956  0 
usbcore               170288  7 cdc_ether,usbnet,uvcvideo,ndiswrapper,ehci_hcd,ohci_hcd
ahci                   33284  3 
libata                176816  1 ahci
scsi_mod              178744  4 sg,sr_mod,sd_mod,libata
thermal                19744  0 
processor              40424  1 thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4224  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3

---

### Post by guillermolisi on 2009-10-02
Fijate que la placa wifi que estas usando es Broadcom Corporation BCM4312 802.11b/g (rev 01), listada en la salida del lspci (asi vas viendo como se usa y de donde se obtiene esta informacion)

Luego, en la salida de lsmod tenes cargando ndiswrapper con lo cual no se si la placa funciona porque aun esta operando este modulo o por el driver nativo que decis haber instalado.

Para ser prolijos con esto, habria que desinstalar ndiswrapper o por lo menos evitar que se cargue cuando se inicia la maquina. Fijate si en el archivo /etc/modules hay una linea que menciona ndiswrapper.

Si esta, agregale un # en la primera posicion de la linea con un editor de texto tipo gvim, nano o equivalente, previa mencion con sudo (sudo nano /etc/modules).

Habria que revisar que el driver nativo de esa placa no esta en la blacklist (/etc/modprobe.d/blacklist.conf) porque si esta no va a funcionar con ese driver.

---

### Post by Mr-Judo on 2009-10-02
Muchas gracias por la ayuda, y pido disculpas por que me canse y reinstale ubuntu, pero esta vez me asegure que el dispositivo wireles este activo. Resulta que reconocio todo re bien.
Claro ahora que se mas o menos como es voy a tener mas cuidado a la hora de instalar cosas. Lo que pasa que uno estaba acostumbrado a otra cosa, que va a ser...

---

