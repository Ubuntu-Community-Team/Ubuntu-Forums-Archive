---
title: "Problemas con red wireless en Karmic Koala"
date: 2009-11-14
forum: Hardware
---

### Post by fepe55 on 2009-11-14
Hola gente,

Acabo de instalar Karmic Koala y todo fue bien, sin ningún problema. Pero no me puedo conectar a la red wireless de casa.

Tengo un mother ASUS P5Q3 Deluxe con wi-fi integrado, y funcionaba perfecto en Hardy y Jaunty, pero acá parece que no quiere. O sea, me fijo y aparece la red, pero cuando elijo para conectarme, me pide la key (WEP 64-bits), la ingreso, piensa un rato y nada.

Probé sacando el *encrypt* de la red y tampoco se conecta.

Encontré varios lugares donde hablan de esta clase de problemas, pero son todos distintos y como no estoy seguro no quiero ponerme a hacer macanas :p

Uno de los que encontré y probé sin éxito (podría haberlo hecho mal, aunque no veo cómo :p) es este: [http://ubuntuforums.org/showpost.php?p=8295253](http://ubuntuforums.org/showpost.php?p=8295253)

Agradezco cualquier tipo de ayuda. Díganme qué necesitan saber, lspci lsmod lsusb o lo que sea y se los paso.

Muchas gracias =)

---

### Post by fepe55 on 2009-11-16
Sigo sin poder solucionarlo. ¿Alguna idea? ¿Alguien?

Gracias.

---

### Post by guillermolisi on 2009-11-16
Para saber como Ubuntu reconoce tu hardware, mostra la salida del comando "lspci" (sin las comillas) en una consola/terminal. Adicionalmente y por las dudas, idem pero con "lsusb".

---

### Post by sergiom99 on 2009-11-17
Ubuntu o Kubuntu?
podes probar instalando wicd en lugar del networkmanager estandar>
```
sudo aptitude install wicd
```

suerte!

---

### Post by fepe55 on 2009-11-19
> **guillermolisi said:**
> Para saber como Ubuntu reconoce tu hardware, mostra la salida del comando "lspci" (sin las comillas) en una consola/terminal. Adicionalmente y por las dudas, idem pero con "lsusb".

Guillermo, acá te paso los dos. La placa wireless, como verás, está en *lsusb*, pero te paso igual los dos:

*lspci*
```

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GTX] (rev a2)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b1)
05:00.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev 10)
05:02.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
05:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)

```

*lsusb*
```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0b05:1742 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 003: ID 0925:8888 Lakeview Research 
Bus 006 Device 002: ID 0925:8888 Lakeview Research 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Y ya que estamos, no sé si sirve, pero te paso el *lsmod*

*lsmod*
```

Module                  Size  Used by
binfmt_misc            10220  1 
rt2870sta             552712  0 
arc4                    2144  2 
ecb                     3296  2 
rt2800usb              40800  0 
rt2x00usb              13600  1 rt2800usb
rt2x00lib              34624  2 rt2800usb,rt2x00usb
led_class               5256  1 rt2x00lib
snd_hda_codec_analog    79680  1 
input_polldev           4720  1 rt2x00lib
mac80211              210104  2 rt2x00usb,rt2x00lib
ppdev                   8232  0 
lp                     11908  0 
parport                40528  2 ppdev,lp
cfg80211              109144  2 rt2x00lib,mac80211
joydev                 13088  0 
saa7134_alsa           14560  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  4 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
saa7134               178356  1 saa7134_alsa
ir_common              52740  1 saa7134
v4l2_common            21024  1 saa7134
videodev               43360  2 saa7134,v4l2_common
v4l1_compat            16804  1 videodev
v4l2_compat_ioctl32    13344  1 videodev
videobuf_dma_sg        14436  2 saa7134_alsa,saa7134
videobuf_core          21188  2 saa7134,videobuf_dma_sg
tveeprom               14884  1 saa7134
snd_seq_midi            8192  0 
asus_atk0110            9472  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
iptable_filter          3872  0 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              21200  1 iptable_filter
crc_ccitt               2336  1 rt2800usb
x_tables               25832  1 ip_tables
snd                    77096  19 snd_hda_codec_analog,saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
usbhid                 43968  0 
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
skge                   45264  0 
usb_storage            65952  0 
sky2                   55556  0 
intel_agp              32816  0 

```


> **sergiom99 said:**
> Ubuntu o Kubuntu?
podes probar instalando wicd en lugar del networkmanager estandar>
```
sudo aptitude install wicd
```

suerte!

Sergio: Estoy en Ubuntu.



Ahí creo que está todo. Cualquier cosa, paso lo que haga falta.

Muchas gracias.

---

### Post by guillermolisi on 2009-11-20
Estoy investigando en el foro de Networking and Wireless y hay otros casos similares pero hasta donde lei, no hay algo contundente como solucion. Si podes leer y entender en Ingles, paso los threads para que veas por tu propia cuenta. 

La salida del lsmod me parece normal, no tenes mas que un driver/modulo para la placa ([FONT=monospace]rt2800usb)[/FONT], lo cual es bueno.

Antes de probar con wicd seguiria investigando porque el tema pasa por cambios en el kernel que usa KK y no por otro lado.

Sigo buscando.

---

### Post by fepe55 on 2009-11-22
> **guillermolisi said:**
> Estoy investigando en el foro de Networking and Wireless y hay otros casos similares pero hasta donde lei, no hay algo contundente como solucion. Si podes leer y entender en Ingles, paso los threads para que veas por tu propia cuenta. 

La salida del lsmod me parece normal, no tenes mas que un driver/modulo para la placa ([FONT=monospace]rt2800usb)[/FONT], lo cual es bueno.

Antes de probar con wicd seguiria investigando porque el tema pasa por cambios en el kernel que usa KK y no por otro lado.

Sigo buscando.


¡Muchas gracias Guillermo! Si podés pasame los *threads*, con el inglés me llevo bien.

Ya estoy a punto de volver a Jaunty, no aguanto más Windows, hacía seis meses que ni lo tocaba y me siento "perdido" :p

---

### Post by guillermolisi on 2009-11-23
Fijate en estos threads. Pareceria que, en general, hay que utilizar unos drivers nuevos de Ralink en lugar de los que tenes en uso actualmente.

[http://ubuntuforums.org/showthread.php?t=1310569&highlight=rt2800usb](http://ubuntuforums.org/showthread.php?t=1310569&highlight=rt2800usb)

[http://ubuntuforums.org/showthread.php?t=1333255&highlight=rt2800usb](http://ubuntuforums.org/showthread.php?t=1333255&highlight=rt2800usb)

[http://ubuntuforums.org/showthread.php?t=1155941&highlight=rt2800usb](http://ubuntuforums.org/showthread.php?t=1155941&highlight=rt2800usb)

Cualquier duda que tengas, consulta antes de hacer.

---

### Post by fepe55 on 2009-11-23
Guillermo:

Finalmente lo pude arreglar, y por suerte era muy fácil, simplemente puse "rt2800usb" en *blacklist* (via [un post]("http://ubuntuforums.org/showpost.php?p=8366327&postcount=3") de unos de los *threads* que pasaste).

Ya estoy disfrutando Karmic y configurándolo a mi medida.

Mil gracias, si no fuera por vos tendría que haber vuelto a Jaunty :p

Así que, nuevamente, **¡¡¡GRACIAS!!!**

---

