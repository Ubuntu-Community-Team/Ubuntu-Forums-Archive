---
title: "Placa sintonizadora de TV"
date: 2010-07-13
forum: Hardware
---

### Post by Leandro17 on 2010-07-13
Hola, recien me compre una placa sintonizadora de tv externa marca Kaiomy modelo TVNPC U2 PRO, en Windows funciona bien ya que trae el software y los drivers, pero no pude nisiquiera comprobar si me detecta el hardware, me fije algunos tutoriales pero son viejos y no me devuelve nada los comandos, espero ayuda, no tendria sentido utilizar win solo para ver tele... saludos

---

### Post by mama21mama on 2010-07-14
Hola,

en la terminal pone....

```
lspci
```
y pega el resultado aquí, con esto veremos que chip usa y demas para proseguir con la instalación.

Saludos

---

### Post by Leandro17 on 2010-07-15
este es el resultado

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

---

### Post by Leandro17 on 2010-07-15
en otro foro me han dicho que tengo que activar el modulo em28xx si no me equivoco... pero como lo hago?

---

### Post by alfplayer on 2010-07-17
Para ver qué módulos están cargados se puede usar el comando *lsmod*. Para cargar un módulo *sudo modprobe nombre_de_módulo*

---

### Post by euzkoarima on 2010-07-17
En la lista de lspci no veo ninguna placa. O estoy más distraído que de costumbre o no está.
Como conectas esa placa ?
No la tendrás conectada por usb ?

Si está conectada por usb deberías usar el comando lsusb para saber "como la ve" el linux.

Saludos,
Eduardo

---

### Post by Leandro17 on 2010-07-17
> **alfplayer said:**
> Para ver qué módulos están cargados se puede usar el comando *lsmod*. Para cargar un módulo *sudo modprobe nombre_de_módulo*

probé con *sudo modprobe em28xx* pero me dice que el modulo no se ha encontrado..

> **euzkoarima said:**
> En la lista de lspci no veo ninguna placa. O estoy más distraído que de costumbre o no está.
Como conectas esa placa ?
No la tendrás conectada por usb ?

Si está conectada por usb deberías usar el comando lsusb para saber "como la ve" el linux.

Saludos,
Eduardo

Si efectivamente es mediante USB, probé con lsusb y me dio el siguiente resultado:

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID eb1a:2863 eMPIA Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

me da la sensacion que "Bus 002 Device 002: ID eb1a:2863 eMPIA Technology, Inc." es el sintonizador

---

### Post by alfplayer on 2010-07-17
Sí, eso parece, eb1a:2863. Para qué versión de Ubuntu? Es una versión vieja? Ahora es cuestión de encontrar el driver.

---

### Post by Leandro17 on 2010-07-17
> **alfplayer said:**
> Sí, eso parece, eb1a:2863. Para qué versión de Ubuntu? Es una versión vieja? Ahora es cuestión de encontrar el driver.

yo estoy usando Ubuntu lucid

---

### Post by alfplayer on 2010-07-17
Qué raro, con 10.04 puedo cargar bien el módulo em28xx con *sudo modprobe em28xx*

---

### Post by Leandro17 on 2010-07-17
> **alfplayer said:**
> Qué raro, con 10.04 puedo cargar bien el módulo em28xx con *sudo modprobe em28xx*

a mi me dice esto:

Module em28xx not found.


lo raro es que en synaptic busco em28xx y me marca como instalado... me dice que la version es la 32-24

---

### Post by alfplayer on 2010-07-17
Los archivos de em28xx los tengo en el directorio */lib/modules/2.6.32-21-generic-pae/kernel/drivers/media/video/em28xx*

---

### Post by Leandro17 on 2010-07-17
a mi me aparecen 3 archivos... te dejo un impresion de pantalla

[[IMG]http://img188.imageshack.us/img188/8949/pantallazoyb.th.png[/IMG]]("http://img188.imageshack.us/img188/8949/pantallazoyb.png")

que deberia hacer con esto

---

### Post by alfplayer on 2010-07-17
Si se está usando ese kernel (2.6.32-21-generic) debería encontrarse con modprobe.

---

### Post by Leandro17 on 2010-07-18
en realidad estoy usando el 2.6.32-23, y ahi no aparece la carpeta em28xx en drivers/media/video... voy a reiniciar para ver si puedo iniciar con la otra version para ver si pasa algo

con el kernel 2.6.32-21 hago sudo modprobe em28xx me pide la contraseña y despues no pasa nada
y en los programas todavia no me encuentra el dispoositivo

---

### Post by alfplayer on 2010-07-18
Eso sería porque el módulo se cargo correctamente (se puede verificar que aparezca en la salida de *lsmod*).

Después se podría verificar que las aplicaciones para ver tv usen el dispositivo de entrada correcto.

Qué aplicación estás usando?

---

### Post by Leandro17 on 2010-07-18
> **alfplayer said:**
> Eso sería porque el módulo se cargo correctamente (se puede verificar que aparezca en la salida de *lsmod*).

Después se podría verificar que las aplicaciones para ver tv usen el dispositivo de entrada correcto.

Qué aplicación estás usando?

en lsmod me aparece

```
Module                  Size  Used by
nls_iso8859_1           3249  0 
nls_cp437               4919  0 
vfat                    8901  0 
fat                    47767  1 vfat
em28xx                 82206  0 
v4l2_common            15431  1 em28xx
ir_common              38875  1 em28xx
videobuf_vmalloc        5586  1 em28xx
videobuf_core          16356  2 em28xx,videobuf_vmalloc
tveeprom               11102  1 em28xx
ueagle_atm             26377  0 
usbatm                 12872  1 ueagle_atm
atm                    35745  1 usbatm
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_conexant    22577  1 
fbcon                  35102  72 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_hda_intel          21877  2 
bitblit                 4707  1 fbcon
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
softcursor              1189  1 bitblit
snd_hwdep               5412  1 snd_hda_codec
vga16fb                11385  0 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
joydev                  8708  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                    1153  2 
i915                  282354  3 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  17 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
drm_kms_helper         29297  1 i915
ath5k                 121792  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
mac80211              204922  1 ath5k
intel_agp              24177  2 i915
drm                   162471  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
psmouse                63245  0 
video                  17375  1 i915
ath                     7611  1 ath5k
output                  1871  1 video
cfg80211              126485  3 ath5k,mac80211,ath
agpgart                31724  2 intel_agp,drm
led_class               2864  1 ath5k
lp                      7028  0 
parport                32635  2 ppdev,lp
uvcvideo               56990  0 
videodev               34361  3 em28xx,v4l2_common,uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
serio_raw               3978  0 
usb_storage            39425  0 
ahci                   32008  2 
r8169                  33884  0 
mii                     4381  1 r8169

```

estoy probando con varias pero ninguna me detecta el dispositivo...
las ap&#314;icaciones con q pruebo son: mythtv, me tv, zapping, xawtv, kaffeine y tvtime...

---

### Post by mama21mama on 2010-07-18
Cual de todas es [Chicony Electronics]("http://www.google.com.ar/search?hl=es&newwindow=1&rlz=1G1GGLQ_ESAR299&q=Chicony+Electronics+%2Bubuntu&aq=f&aqi=&aql=&oq=&gs_rfai=") o [eMPIA Technology]("http://www.google.com.ar/search?q=eMPIA+Technology+%2Bubuntu&hl=es&newwindow=1&rlz=1G1GGLQ_ESAR299&prmd=df&ei=l0VDTL6oKcP88Aa69OjPDw&start=10&sa=N") ?


:s

---

### Post by Leandro17 on 2010-07-18
empia

---

### Post by alfplayer on 2010-07-18
Buscando en la web, 04f2:b091 Chicony parece que es webcam.

---

### Post by alfplayer on 2010-07-18
Yo chequearía las configuraciones de las aplicaciones, para que estén conectadas al dispositivo de captura correcto, por ejemplo, puede ser /dev/video0 (cero u otro número).

---

### Post by Leandro17 on 2010-07-18
probé así pero sólo me detecta la cámara web

---

### Post by euzkoarima on 2010-07-18
NO ESTOY SEGURO pero según estuve leyendo en varias pág (por ejemplo en [0]) el driver em28xx necesitaría el paquete linux-firmware-nonfree.
Fijate si lo tenés instalado, sino es así, supongo que instalarlo no debería ser peligroso, supongo que a lo sumo seguirá todo igual

[0] [http://www.cadiidxa.lunasexta.org/?p=787]("http://www.cadiidxa.lunasexta.org/?p=787")

Saludos,
Eduardo

---

### Post by Leandro17 on 2010-07-19
> **euzkoarima said:**
> NO ESTOY SEGURO pero según estuve leyendo en varias pág (por ejemplo en [0]) el driver em28xx necesitaría el paquete linux-firmware-nonfree.
Fijate si lo tenés instalado, sino es así, supongo que instalarlo no debería ser peligroso, supongo que a lo sumo seguirá todo igual

[0] [http://www.cadiidxa.lunasexta.org/?p=787](http://www.cadiidxa.lunasexta.org/?p=787)

Saludos,
Eduardo

ya tengo instalado el paquete, probe ejecutando dmesg y en las ultimas lineas me aparece lo siguiente:

```
[  687.516449] usbcore: registered new interface driver em28xx
[  687.517338] em28xx driver loaded
[  728.885285] __ratelimit: 24 callbacks suppressed
[  728.885289] mythfrontend.re[2493]: segfault at c ip b3c6822d sp a89a3e50 error 4 in libQtGui.so.4.6.3[b3a28000+a59000]

```

no me aparece nada de  v4l y nada de eso...
creo que como van las cosas deberia instalar xp para ver tv, xq con vista me va lento :(

---

### Post by guillermolisi on 2010-07-19
> **Leandro17 said:**
> ya tengo instalado el paquete, probe ejecutando dmesg y en las ultimas lineas me aparece lo siguiente:

```
[  687.516449] usbcore: registered new interface driver em28xx
[  687.517338] em28xx driver loaded
[  728.885285] __ratelimit: 24 callbacks suppressed
[  728.885289] mythfrontend.re[2493]: segfault at c ip b3c6822d sp a89a3e50 error 4 in libQtGui.so.4.6.3[b3a28000+a59000]

```no me aparece nada de  v4l y nada de eso...
creo que como van las cosas deberia instalar xp para ver tv, xq con vista me va lento :(
Por el ultimo error pareceria que mythfrontend usa Qt en lugar de GTK. Luego posiblemente por cuestiones de version (habria que revisar requisitos minimos para mythfrontend) cancela cuando requiere alguna funcionalidad de LibQtGui que es version 4.6.3.

El driver/modulo esta cargado, asi que ahora el problema viro para otro lado.

---

### Post by euzkoarima on 2010-07-19
Como dice Guillermo, el driver está cargado, ahora el problema es otro.
Propongo que probar con cheese (que no usa qt), a ver si te detecta el aparato.

Saludos,
Eduardo

---

### Post by Leandro17 on 2010-07-21
> **euzkoarima said:**
> Como dice Guillermo, el driver está cargado, ahora el problema es otro.
Propongo que probar con cheese (que no usa qt), a ver si te detecta el aparato.

Saludos,
Eduardo

cheese detecta solo la webcam

---

### Post by euzkoarima on 2010-07-21
Cosa e'mandinga, che!!!

Bueno, mucho no se me ocurre, por las dudas, a ver si nos inspiramos, proba de:

1. enchufas el aparato
2. abris cheese
3. tiras un dmesg a ver si nos da algo útil.

Saludos,
Eduardo

---

### Post by Leandro17 on 2010-07-22
esto es lo ultimo que me aparece:

```
[   46.831697] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   46.831754] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   46.839916] vga16fb: initializing
[   46.839921] vga16fb: mapped to 0xc00a0000
[   46.839925] vga16fb: not registering due to another framebuffer present
[   46.950018] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   46.950262] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   46.950450] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   47.028539] Console: switching to colour frame buffer device 160x50
[   47.524345] ppdev: user-space parallel port driver
[   49.583014] NET: Registered protocol family 8
[   49.583018] NET: Registered protocol family 20
[   49.603716] [ueagle-atm] driver ueagle 1.4 loaded
[   49.603758] usbcore: registered new interface driver ueagle-atm
[   80.905311] wlan0: Selected IBSS BSSID 0e:b7:7d:7b:09:ed based on configured SSID
[   91.268033] wlan0: no IPv6 routers present
[  100.652059] usb 2-1: new high speed USB device using ehci_hcd and address 2
[  100.788655] usb 2-1: configuration #1 chosen from 1 choice

```

---

### Post by euzkoarima on 2010-07-22
En este último dmesg no dice nada de la sintonizadora, solo habla del modem ueagle_atm DSL.

O ubuntu ni se enteró que la enchufaste o copiaste la parte del dmesg que no era. Por lo que contás del cheese (que no la ve) supongo que es la primera.

De haberla reconocido en alguna parte debería decir algo como :
usbcore: registered new interface driver em28xx
Tal como habías posteado antes.

No se me ocurre que más probar a no ser enchufar, tirar dmesg si no pasa nada sacarla y volver a encufarla, supongo que si la reconoce, el cheese debería andar.

Algún otro que tire una idea ?

Saludos,
Eduardo

---

### Post by guillermolisi on 2010-07-23
```
sudo lshw
```

y 

```
lsusb
```

en consola/terminal con el dispositivo enchufado, a ver que devuelve.

---

### Post by Leandro17 on 2010-07-25
esto es lo que me dovlivio con sudo lshw

```
leandro-laptop            
    description: Notebook
    product: Compaq Presario CQ50 Notebook PC
    vendor: Hewlett-Packard
    version: F.31
    serial: 2CE846201T
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook uuid=E5637A60-B6AA-11DD-AC09-D3DE21864ADA
  *-core
       description: Motherboard
       product: 360B
       vendor: Wistron
       physical id: 0
       version: 09.47
       serial: 2CE846201T
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.31 (10/17/2008)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: V916765G24QCFW-F5
             vendor: 4000000000000000
             physical id: 0
             serial: 199A300D
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM [empty]
             physical id: 1
             slot: DIMM2
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU             575  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1a
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: CPU
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 667MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx x86-64 constant_tsc up arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
        *-cache:0
             description: L2 cache
             physical id: 1b
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 1d
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back data
     *-cache
          description: L1 cache
          physical id: 1c
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back instruction
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:50000000-503fffff memory:40000000-4fffffff(prefetchable) ioport:5110(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:52500000-525fffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:50e0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:50c0(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:50a0(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:54705c00-54705fff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:54700000-54703fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=8192) memory:53700000-546fffff ioport:50400000(size=17825792)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 02
                serial: 00:1f:16:52:d6:59
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:26 ioport:3000(size=256) memory:50410000-50410fff(prefetchable) memory:50400000-5040ffff(prefetchable) memory:50420000-5043ffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) memory:52600000-536fffff ioport:51500000(size=16777216)
           *-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 00:23:4d:d5:d0:ed
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k ip=192.168.0.50 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:52600000-5260ffff
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:5080(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:5060(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:5040(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:54705800-54705bff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:27 ioport:5108(size=8) ioport:511c(size=4) ioport:5100(size=8) ioport:5118(size=4) ioport:5020(size=32) memory:54705000-547057ff
           *-disk
                description: ATA Disk
                product: WDC WD1200BEVS-6
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXC708L10054
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=bd1abd1a
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: ca37d4e8-a97f-784a-b09f-6ba43827673b
                   size: 79GiB
                   capacity: 79GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2001-02-26 13:38:39 filesystem=ntfs state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 66fdf12d-5b13-d84b-80cd-9d34c346c042
                   size: 8941MiB
                   capacity: 8970MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-11-19 08:55:47 filesystem=ntfs label=PRESARIO_RP state=clean
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 23GiB
                   capacity: 23GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 22GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1019MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7591S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.83
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:54706000-547060ff ioport:5000(size=32)
        *-generic UNCLAIMED
             description: Signal processing controller
             product: 82801I (ICH9 Family) Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:54704000-54704fff
     *-scsi
          physical id: 1
          bus info: usb@1:3
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define4
       vendor: OEM_Define2
       physical id: 1
       version: OEM_Define5
       serial: OEM_Define2
       capacity: 75mWh

```y esto el lsusb

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID eb1a:2863 eMPIA Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```perdon por la tardanza

---

### Post by guillermolisi on 2010-07-25
Esta es la placa de captura de video > Bus 002 Device 002: ID eb1a:2863 eMPIA Technology, Inc. y poniendo en Google eb1a:2863, que es la identificacion del fabricante y el dispositivo USB, sale abudante informacion, entre la que podes darle una leida a [http://www.mombu.com/gnu_linux/mandriva/t-how-to-make-modprobe-permanent-3171883.html](http://www.mombu.com/gnu_linux/mandriva/t-how-to-make-modprobe-permanent-3171883.html) que si bien esta referenciado con Mandriva es equivalente para el caso de Ubuntu.

---

### Post by euzkoarima on 2010-07-30
Hace unos días que no entraba al foro. Agrego un par de links 

Primero, parace que el problema es común [0] (no sos el único "en desgracia")

Según [1] el problema puede estar en que la sintonizadora se identifique como disco, y menciona [2]



[0] [http://foros.softonic.com/configuracion/sintonizador-tv-108523-2]("http://foros.softonic.com/configuracion/sintonizador-tv-108523-2")
[1] [http://www.pclinuxos.com/forum/index.php?PHPSESSID=0ht9p6c68n6mpccrmpv9jkrqj4&topic=62416.15]("http://www.pclinuxos.com/forum/index.php?PHPSESSID=0ht9p6c68n6mpccrmpv9jkrqj4&topic=62416.15")
[2] [http://reactivated.net/writing_udev_rules.html#example-camera]("http://reactivated.net/writing_udev_rules.html#example-camera")


Saludos,
Eduardo

---

