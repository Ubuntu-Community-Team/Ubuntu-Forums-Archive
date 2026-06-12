---
title: "Mi presentacion"
date: 2011-02-25
forum: Hardware
---

### Post by CartaAleta on 2011-02-25
Hola, como estan?, espero que bien, soy un estudiante de sistemas, recien iniciado en este sistema asi que estoy aprendiendo en a los tumbos..  y por supuesto ya tengo mi primer problema:
 
 
no logro encontrar los drivers para un toshiba l645, ni los de wifi y video
las placas son realtk rtl8188ce wirless Lan 802.11n pci-e nic, y una intel(r) HD graphics respectivamente.. si alguien me puede ayudar lo agradeceria!!
 
 
y disculpen las molestias

---

### Post by guillermolisi on 2011-02-25
Bienvenido !

Contanos que version de Ubuntu estas usando.

Salvo que estes con una version obsoleta o que las placas que mencionas sean muuuy nuevas, deberia funcionar ya que en Linux la gran mayoria de drivers vienen incluidos en el kernel (nucleo) del SO.

Si podes, abri una terminal e ingresa los siguientes comandos, copiando las salidas de cada uno para luego mostrarlas aqui, asi sbremos exactamente como se esta reconociendo el hardware:
```
sudo lspci
```
```
sudo lsusb
```
```
sudo lshw
```
```
sudo lsmod
```

---

### Post by CartaAleta on 2011-02-25
> **guillermolisi said:**
> Bienvenido !
 
Contanos que version de Ubuntu estas usando.
 
Salvo que estes con una version obsoleta o que las placas que mencionas sean muuuy nuevas, deberia funcionar ya que en Linux la gran mayoria de drivers vienen incluidos en el kernel (nucleo) del SO.
 
Si podes, abri una terminal e ingresa los siguientes comandos, copiando las salidas de cada uno para luego mostrarlas aqui, asi sbremos exactamente como se esta reconociendo el hardware:
```
sudo lspci
```
```
sudo lsusb
```
```
sudo lshw
```
```
sudo lsmod
```
es la version 10.10 del ubuntu, en cuanto pueda me conecto con el cable, ya que estoy en windows ahora y para hacerlo me tengo que trasladar. muchas gracias!!
 
en un rato subo los outputs

---

### Post by CartaAleta on 2011-02-25
sudo lspci:
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
03:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by CartaAleta on 2011-02-25
lsusb:

Bus 002 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 003: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 14cd:6116 Super Top 
Bus 001 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by CartaAleta on 2011-02-25
lshw
PCI (sysfs)  



lsmod:

Module                  Size  Used by
parport_pc             26058  0 
dm_crypt               11385  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_intel          31738  1 
snd_hda_codec          87552  1 snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
joydev                  8735  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
psmouse                59033  0 
videodev               43098  1 uvcvideo
snd                    49006  8 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13359  2 uvcvideo,videodev
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
serio_raw               4022  0 
lp                      7342  0 
intel_ips              14479  1 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40172  2 
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
btrfs                 489451  0 
zlib_deflate           19266  1 btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
usbhid                 36882  0 
hid                    67742  1 usbhid
i915                  290938  3 
drm_kms_helper         30200  1 i915
drm                   168054  4 i915,drm_kms_helper
ahci                   19013  0 
libahci                21667  1 ahci
intel_agp              26360  2 i915
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
atl1c                  29949  0 
output                  1883  1 video
agpgart                32011  2 drm,intel_agp

ACA ESTAN LOS OUTPUTS! MUCHAS GRACIAS

---

### Post by hectorivand on 2011-02-25
Pregunta, tu notebook tiene algún interruptor físico para habilitar el Wifi?

Al parecer no la reconoce o no la "ve"

Acá están los drivers para tu placa, baja la versión para Linux que indica ahí abajo, lee el readme y no vas a tener problemas.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Comenta como te fue.

Saludos
Nacho

---

### Post by guillermolisi on 2011-02-25
Parece que falta la salida del "lshw", porque no la veo, solo la referencia.

En la salida de "lspci" aparecen dos placas de red, una Realtek y una Atheros. Alguna es la inalambrica y otra la cableada. Siendo cualquiera de las dos y salvo que sean modelos muy nuevos, deberia funcionar sin agregarle nada a la 10.10 (a lo sumo una actualizacion para estar al dia con los ultimos arreglos, particularmente del kernel).

---

### Post by hectorivand on 2011-02-25
> **guillermolisi said:**
> Parece que falta la salida del "lshw", porque no la veo, solo la referencia.

En la salida de "lspci" aparecen dos placas de red, una Realtek y una Atheros. Alguna es la inalambrica y otra la cableada. Siendo cualquiera de las dos y salvo que sean modelos muy nuevos, deberia funcionar sin agregarle nada a la 10.10 (a lo sumo una actualizacion para estar al dia con los ultimos arreglos, particularmente del kernel).

Los drivers Realtek que vienen por defecto en las nuevas versiones andan muy mal! he visto que la conexión que hacía con el router / Ap era de 1MB. 

Tenes razón, no vi la realtek, raro que no se ve con lsusb, siendo que es una inalámbrica y una notebook.

En fin.

Saludos
Nacho

---

### Post by biale on 2011-02-26
La info esta aqui:

> 
Bus 002 Device 003: ID 0bda:5801 Realtek Semiconductor Corp. 

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
03:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)


Googleando, encuentro que si fuera la Rev 02, el driver sería:

[http://art.ubuntuforums.org/showthread.php?t=1658112&page=3](http://art.ubuntuforums.org/showthread.php?t=1658112&page=3)

> Realtek has a new RTL8192CU driver on their website, released on 1/28/2011. I used this driver to get the device working on an HP Pavilion AMD64X2 Turion

Pero es la rev 01, y el driver sería este:

[http://en.community.dell.com/support-forums/software-os/f/3525/t/19352306.aspx](http://en.community.dell.com/support-forums/software-os/f/3525/t/19352306.aspx)

[http://www.meabi.com/ubuntu-netbook-wireless-problem-solved-for-dell-mini/](http://www.meabi.com/ubuntu-netbook-wireless-problem-solved-for-dell-mini/)

> 
Thanks SIVA9789, my solution wasalready:
driver for RTL8188CE Dell Inspiron Mini 1018:

sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms


Ahora que siga alguien que tenga mas idea que yo...

---

### Post by CartaAleta on 2011-02-26
en unos minutos intento hacerlo, como es la forma de instalarlos? como en el reply de arriba?, perdonen pero estoy aprendiendo :)

---

### Post by CartaAleta on 2011-02-26
> **hectorivand said:**
> Pregunta, tu notebook tiene algún interruptor físico para habilitar el Wifi?

Al parecer no la reconoce o no la "ve"

Acá están los drivers para tu placa, baja la versión para Linux que indica ahí abajo, lee el readme y no vas a tener problemas.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Comenta como te fue.

Saludos
Nacho

para prenderla tengo que apretar FN + F8.... pero al hacerlo no enciende

---

### Post by CartaAleta on 2011-02-26
> **hectorivand said:**
> pregunta, tu notebook tiene algún interruptor físico para habilitar el wifi?

Al parecer no la reconoce o no la "ve"

acá están los drivers para tu placa, baja la versión para linux que indica ahí abajo, lee el readme y no vas a tener problemas.

[http://www.realtek.com.tw/downloads/downloadsview.aspx?langid=1&pnid=21&pfid=48&level=5&conn=4&downtypeid=3&getdown=false&downloads=true](http://www.realtek.com.tw/downloads/downloadsview.aspx?langid=1&pnid=21&pfid=48&level=5&conn=4&downtypeid=3&getdown=false&downloads=true)

comenta como te fue.

Saludos
nacho
  
con eso basto!!! Anda barbaro ahora! Muchisimas gracias a todos!!!! Ojala pronto pueda ayudar yo tambien! 

Gracias por su tiempo

---

### Post by martinpifa on 2011-05-06
Hola tambien soy nuevo en esto al igual que carta aleta, con la diferencia de que estudio antropologia, no sistemas, jajaj
quisiera si alguien puede que me diga a donde tengo que ir a poner los comandos cuando me dice:

You can enter top-level directory of driver and execute follwing command to 
Compile, Installation, or uninstall the driver: 
 
    1. Change to Super User 
       sudo su 
 
    2. Compile driver from the source code  
       make 
 
    3. Install the driver to the kernel 
       make install 
       reboot 
 
    4. uninstall driver 
       make uninstall 

tengo que abrir una shell e ingresarlos ahi? lo hice y no reconoce nada.
por donde entro a este top level directory?

desde ya gracias por su ayuda

Aguante LINUX!!!

---

### Post by martinpifa on 2011-05-06
ya estoy con sueño me olvide de decirles que tengo la misma placa, que ya baje los drivers que le recomendaron a carta aleta y que ademas abri el readme de los drivers: al cargar los comandos en una shell comun, entro como superusuario y despues cuando procedo a instalar los drivers poniendo - make install- me pone: 

 make: *** No hay ninguna regla para construir el objetivo «install».  Alto.

---

