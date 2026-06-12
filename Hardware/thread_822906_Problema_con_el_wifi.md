---
title: "Problema con el wifi"
date: 2008-06-08
forum: Hardware
---

### Post by switcherlinux on 2008-06-08
Hola, soy nuevo en Ubuntu y en el foro, pues vengo con un problemilla, ubuntu no reconoce mi INTEL/PRO WIRELESS 3945 ABG por lo que no tengo wifi, por cierto tengo el Ubuntu 8.04, ya he buscado en todas partes y no encuentro la manera de instalar el driver, espero que puedan ayudarme.

muchas gracias

---

### Post by osensei on 2008-06-08
Según vi en un par de páginas, hay una mejora para el driver de tu placa wifi en el paquete linux-backports-modules-hardy.

Para instalarlo tenés que ejecutar el siguiente comando en la terminal:

```
sudo apt-get install linux-backports-modules-hardy
```

Espero que te sirva.

Saludos!

---

### Post by switcherlinux on 2008-06-09
gracias por responder pero el wifi sigue sin funcionar, el led sigue estando rojo u.u

por cierto mi ordenador es un portatil HP Pavilion dv6500 por si sirve de algo saberlo

---

### Post by sergiom99 on 2008-06-09
fijate si estos otros threads te sirven:
[http://ubuntuforums.org/showthread.php?t=814117&highlight=WIRELESS+3945](http://ubuntuforums.org/showthread.php?t=814117&highlight=WIRELESS+3945)
[http://ubuntuforums.org/showthread.php?t=814596&highlight=WIRELESS+3945](http://ubuntuforums.org/showthread.php?t=814596&highlight=WIRELESS+3945)
[http://ubuntuforums.org/showthread.php?t=768766&highlight=WIRELESS+3945](http://ubuntuforums.org/showthread.php?t=768766&highlight=WIRELESS+3945)

Suerte!

---

### Post by faktorqm on 2008-06-09
Hola, hay bastante info aunque la mayoria esta para ubuntu 6.06. aca encontre algo para 8.04, decime si te sirvio:

[http://www.ubuntu-es.org/index.php?q=node/88882](http://www.ubuntu-es.org/index.php?q=node/88882)

si no te funciono el de arriba: [http://www.cofradia.org/modules.php?name=News&file=article&sid=21002](http://www.cofradia.org/modules.php?name=News&file=article&sid=21002)

si no te funciono el de arriba: [http://obux.wordpress.com/2008/03/27/solucionar-problemas-con-intel-pro-wireless-3945-en-dell-inspiron-1520-con-ubuntu/](http://obux.wordpress.com/2008/03/27/solucionar-problemas-con-intel-pro-wireless-3945-en-dell-inspiron-1520-con-ubuntu/)

si no te funciono el de arriba: [http://www.kubuntu-es.org/foro/200805/intel-pro-wireless-3945abg-hardy-heron-804-ipw3945](http://www.kubuntu-es.org/foro/200805/intel-pro-wireless-3945abg-hardy-heron-804-ipw3945)

pagina del proyecto: [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

espero que te haya servido. Salu2!!

---

### Post by switcherlinux on 2008-06-09
joo hecho de menos el "Siguiente, Siguiente, Siguiente" de los instaladores de Windows... :(

bueno pues las paginas que están en inglés las descarto ya que no me defiendo muy bien en esa lengua... y el resto en español solo una no la he visto antes, el resto  ninguna me a funcionado o soy demasiado torpe... asique estoy  siguiendo esta guia: [http://obux.wordpress.com/2008/03/27/solucionar-problemas-con-intel-pro-wireless-3945-en-dell-inspiron-1520-con-ubuntu/](http://obux.wordpress.com/2008/03/27/solucionar-problemas-con-intel-pro-wireless-3945-en-dell-inspiron-1520-con-ubuntu/)

ahora, ahí dice que tengo que sustituir cierto driver por otro, ¿como lo hago? 

espero que llegue pronto el Ubuntu 8.10 :)

---

### Post by sergiom99 on 2008-06-09
Te dicen que tenes que sacar este ([http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)) y cambiarlo por este ([http://intellinuxwireless.org/?n=downloads](http://intellinuxwireless.org/?n=downloads)) de acuerdo al kernel que tengas. Las instrucciones estan aca: [http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi)

Despues seguis con los pasos 2 en adelante de la pagina que posteaste.

Sino chifla que seguimos mirando.

---

### Post by switcherlinux on 2008-06-09
gracias por ayudarme pero esque no sé inglés!! :(


y lo unico que quiero saber es donde está la carpeta del controlador antiguo para sustituirlo por el nuevo

---

### Post by Mister X on 2008-06-09
Por favor posteá la salida del comando lsmod

---

### Post by switcherlinux on 2008-06-10
sale esto:

Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
container               5632  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
snd_hda_intel         344728  4 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  2 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
uvcvideo               58116  0 
snd_seq_oss            35584  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
snd_seq_midi            9376  0 
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
nvidia               7825536  36 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_core               24832  1 nvidia
snd_timer              24836  2 snd_pcm,snd_seq
psmouse                40336  0 
sdhci                  19076  0 
serio_raw               7940  0 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  19856  5 
output                  4736  1 video
ricoh_mmc               4352  0 
mmc_core               51460  1 sdhci
wmi_acer                9644  0 
ac                      6916  0 
button                  9232  0 
battery                14212  0 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
evdev                  13056  8 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
soundcore               8800  2 snd
intel_agp              25492  0 
agpgart                34760  2 nvidia,intel_agp
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
ata_generic             8324  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
ata_piix               19588  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
pata_acpi               8320  0 
ahci                   28420  2 
ohci1394               33584  0 
libata                159344  4 ata_generic,ata_piix,pata_acpi,ahci
scsi_mod              151436  5 sbp2,sr_mod,sg,sd_mod,libata
ieee1394               93752  2 sbp2,ohci1394
r8169                  32900  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  5 uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3

---

### Post by Mister X on 2008-06-10
Hasta gusty venia el modulo ipw3945 para esa placa, en hardy creo que viene el iwl3945, tratá de cargar el modulo:

```
sudo modprobe iwl3945
```

si te tira algun error, postealo

---

### Post by switcherlinux on 2008-06-12
me da error:

jesus@jesus-laptop:~$ sudo modprobe iwl3945
[sudo] password for jesus: 
WARNING: /etc/modprobe.d/ipw3945.save line 3: ignoring bad line starting with '^0'
jesus@jesus-laptop:~$

---

### Post by dgcampos on 2008-06-12
> **switcherlinux said:**
> me da error:

jesus@jesus-laptop:~$ sudo modprobe iwl3945
[sudo] password for jesus: 
WARNING: /etc/modprobe.d/ipw3945.save line 3: ignoring bad line starting with '^0'
jesus@jesus-laptop:~$

fijate que es un warning no un error, se debe de haber cargado el modulo, y? funciona el wifi ahora?

---

### Post by switcherlinux on 2008-06-12
pues no :( el led del wifi sigue estando rojo, no sé por que siempren me pasan estas cosas a mi...

---

### Post by switcherlinux on 2008-06-13
alguien sabe algo? :(

no puede ser tan complicado hacer esto...

---

### Post by lega on 2008-06-13
Ojo que mi notebook, Compaq F755 el led siempre queda en rojo aunque este encendido pero igual anda y muy bien, fijate si tipeando ifconfig en la consola no te sale algo como wlan0 o algo así...

Saludos

---

### Post by switcherlinux on 2008-06-15
pues no...

jesus@jesus-laptop:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:1b:24:dc:c4:76  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:183 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:165619 (161.7 KB)  TX bytes:23523 (22.9 KB)
          Interrupción:219 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:1532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1532 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:76600 (74.8 KB)  TX bytes:76600 (74.8 KB)

jesus@jesus-laptop:~$ 

la red se llama Garvi y no veo nada de eso

---

### Post by switcherlinux on 2008-06-16
bah ya me arté esperaré a la proxima version de Ubuntu a ver si da mejores resultados.... me lo voy a desinstalar

---

### Post by luks911 on 2008-06-16
> **switcherlinux said:**
> bah ya me arté esperaré a la proxima version de Ubuntu a ver si da mejores resultados.... me lo voy a desinstalar

Si llegué a tiempo y todavía te quedan ganas de probar, [acá hay un tutorial]("http://www.ubuntu-es.org/index.php?q=node/88882"). 

Saludos

---

