---
title: "problemas tarjeta bcm 4311 rev 2 (no se reconoce)"
date: 2011-02-20
forum: Hardware
---

### Post by popeye54 on 2011-02-20
Hola a todos ustedes, soy nuevo en ubuntu y con conocimientos bastante básicos en computación en general. 
Aburrido de windows instalé ubuntu 10.10 no teniendo problemas sólo con mi tarjeta de red inalámbrica. Estuve buscando en el foro soluciones para esto, encontrando algunas que por desgracia, no me resultaron como esperaba, les detallo a continuación:

Mi tarjeta de red es una bcm 4311 rev 2 (información obtenida al ejecutar lspci), la que estaría soportada por lo encontrado en la sigte pagina: 

[http://linuxwireless.org/en/users/Drivers/b43#Supported_chip_types](http://linuxwireless.org/en/users/Drivers/b43#Supported_chip_types). 

Tengo un controlador que tengo activado y es el Controlador inalámbrico Broadcom STA.

Ahora, mi tarjeta no prende, funciona con un switch, que al activarlo la tarjeta sigue inactiva. Para esto trate en primera instancia de activarlo por la consola, pero me salio el siguiente error: "wlan0: ERROR mientras se obtenían las banderas de interfaz: No existe el dispositivo"

Intenté obtener el fwcutter pero me apareció este otro error: "E: No se ha podido localizar el paquete bcm43xx-fwcutter". 

Espero a que alguien en primera instancia pueda ayudarme a que se me reconozca la tarjeta y luego poder activarla.

Saludos y gracias.

Adjunto el lspci:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
gabriel@gabriel-HP-Pavilion-dv2000-GA534UA-ABA:~$ us Host Ada

---

### Post by RafaelG on 2011-02-22
Popeye54;

Prueba con lo siguiente, desde una terminal ejecuta
```
sudo apt-get install b43-fwcutter
```Asegurate de aceptar la instalacion del firmware tambien, reinicia  y verifica ya que deberia aparecer este nuevo controlador para tu tarjeta inalambrica, en caso de ser asi entonces desactiva el controlador STA y activa este nuevo bcm43. 

Fuente: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Saludos,

---

### Post by popeye54 on 2011-02-23
Gracias, ocupe el comando y realice la instalación del firmware, pero no me apareció ningún otro controlador, si hago correr el comando nuevamente me sale lo sgte:

creando árbol de dependencias       
Leyendo la información de estado... Hecho
b43-fwcutter ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

y ningún otro controlador aparece. De hecho he tratado de ocupar ndiswrapper para tratar de instalar el controlador del fabricante (archivo .inf), pero tampoco he tenido resultados de hecho al darle la ubicación con el comando me devuelve las opciones del comando:

gabriel@gabriel-HP-Pavilion-dv2000-GA534UA-ABA:~$ ndiswrapper -i/home/gabriel/Escritorio/bcmwl5.inf
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card

Tengo instalados los paquetes ndiswrapper-common y ndiswrapper-utils-1.9. Los instale desde el gestor de paquete synaptic.

---

### Post by RafaelG on 2011-02-24
Popeye54;

Por curiosidad, verificaste en el icono del network manager con el click derecho si esta habilitado el wireless, es solo por curiosidad.

Saludos,

---

### Post by popeye54 on 2011-02-26
> **RafaelG said:**
> Popeye54;

Por curiosidad, verificaste en el icono del network manager con el click derecho si esta habilitado el wireless, es solo por curiosidad.

Saludos,


Lo verifique pero no me aparece la opción de redes inalámbricas. Buscando encontré que se debía instalar el controlador bcmwl5.inf, al ejecutar el comando ndiswrapper -l me a parece el controlador instalado pero no me aparece el hardware. 
Como puedo si es un problema de hardware o software finalmente.
sigo buscando una solución.

---

### Post by RafaelG on 2011-02-27
Popeye54;

Podrias revisar este Link
[http://www.taringa.net/posts/linux/9059727/Solucion-definitiva-Broadcom-BCM-43XX-Ubuntu-10_10--BCM4311.html](http://www.taringa.net/posts/linux/9059727/Solucion-definitiva-Broadcom-BCM-43XX-Ubuntu-10_10--BCM4311.html)

Saludos cordiales,

---

### Post by asterix77 on 2011-02-28
Lo que hice yo para activar este modelo de tarjeta, fue primero conectarme a internet vía cable, luego me fui a sistema ----> Administración ----> Controladores de hardware y elegí Broadcom B43 wireless driver.

Si ya instalastes el firmware, intenta ir a sistema ----> Administración ----> Controladores de hardware y elegir Broadcom B43 wireless driver (activarlo). 

En lo personal lo hice así y desactivé el Controlador inalámbrico Boadcom STA, y no he tenido ningún problema para usar mi wifi.

¿Qué te arroja el siguiente comando por la terminal?

$lsmod

Lo anterior muestra los módulos cargado al kernel

Quizás el módulo (driver) no ha sido cargado, en tal caso debieras insertarlo con lo siguiente:

$sudo modprobe b43

y luego intentar encender tu wifi ya sea en forma fisica o por la terminal

$sudo ifconfig wlan0 up


Saludos

---

### Post by popeye54 on 2011-03-03
Hice lo del tutorial que me posteo rafaelg al pie de la letra, pero sin resultados con la activación de la tarjeta.
Con lo de asterix77 posteo lo que me apareció al ejecutar lsmod. Al parecer el controlador está instalado.

~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4657  0 
nls_cp437               6375  0 
vfat                   10954  0 
fat                    56244  1 vfat
nls_utf8                1453  0 
isofs                  34218  0 
ndiswrapper           245044  0 
b43                   187932  0 
ssb                    46201  1 b43
mac80211              267163  1 b43
cfg80211              170485  2 b43,mac80211
ppp_deflate             4450  0 
zlib_deflate           21866  1 ppp_deflate
bsd_comp                5307  0 
ppp_async               8070  1 
crc_ccitt               1699  1 ppp_async
option                 16405  2 
usb_wwan               12201  1 option
usbserial              39539  7 option,usb_wwan
usb_storage            50372  0 
hidp                   15019  0 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_conexant    37663  1 
rfcomm                 40787  4 
binfmt_misc             7984  1 
sco                     9986  2 
bnep                   11985  2 
l2cap                  42304  17 hidp,rfcomm,bnep
nvidia              10221046  44 
snd_hda_intel          26115  2 
snd_hda_codec         100919  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
joydev                 11395  0 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                  6467  0 
btusb                  12929  2 
uvcvideo               62379  0 
bluetooth              59245  10 hidp,rfcomm,sco,bnep,l2cap,btusb
video                  22176  0 
r852                   11348  0 
sm_common               4441  1 r852
snd                    64181  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                  2527  1 video
nand                   38430  2 r852,sm_common
nand_ids                4443  1 nand
nand_ecc                4406  1 nand
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
edac_core              46822  0 
psmouse                62080  0 
v4l2_compat_ioctl32    12614  1 videodev
edac_mce_amd            9387  0 
mtd                    21479  2 sm_common,nand
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
i2c_nforce2             6155  0 
k8temp                  4128  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42030  0 
hid                    84710  2 hidp,usbhid
firewire_ohci          24839  0 
sdhci_pci               7765  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  2 b43,sdhci
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
sata_nv                23770  2 
forcedeth              55649  0 
pata_amd               12050  0 


Me aparece este error al querer activar la wifi por la terminal

gabriel@gabriel-HP-Pavilion-dv2000-GA534UA-ABA:~$ sudo ifconfig wlan0 up
[sudo] password for gabriel: 
wlan0: ERROR mientras se obtenían las banderas de interfaz: No existe el dispositivo

---

### Post by asterix77 on 2011-03-03
mmmm...

Efectivamente el módulo está cargado, debería ser suficiente como para poder activar la interfaz wifi.

Por si las dudas escribe la salida de los siguientes comandos:

$cat /etc/modprobe.d/blacklist.conf

$ifconfig

$iwconfig

A lo mejor tu tarjeta no está asignada como wlan0, sin por ejemplo wlan1

Podrías además intentar quitar el módulo con lo siguiente:

$sudo modprobe -r b43

y luego volverlo a insertar con lo siguiente:

$sudo modprobe b43

Luego intentar encender tu wifi por la terminal con:

$sudo ifconfig wlan0 up

Si es que tu pc tiene un switch de encendido de la wifi, antes de escribir lo anterior ($sudo ifconfig wlan0 up), asegurate de que esté en la posición de encendido.


Saludos

---

### Post by popeye54 on 2011-03-08
Bueno, ejecuté los comandos en la terminal, pero nuevamente sin resultados y con el mismo error anterior. 
Esto fue lo que me salio con $iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

y esto con $ifconfig

eth0      Link encap:Ethernet  direcciónHW 00:16:d3:ac:ca:3d  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:17 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:114 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:114 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:7474 (7.4 KB)  TX bytes:7474 (7.4 KB)

ppp0      Link encap:Protocolo punto a punto  
          Direc. inet:186.10.186.178  P-t-P:10.64.64.64  Másc:255.255.255.255
          ACTIVO PUNTO A PUNTO FUNCIONANDO NOARP MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:27416 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:25016 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:3 
          Bytes RX:27642035 (27.6 MB)  TX bytes:3438270 (3.4 MB)

---

### Post by asterix77 on 2011-03-09
Intenta lo siguiente:

Primero desde la terminal:


 $sudo aptitude purge bcmwl-kernel-source dkms fakeroot patch


Si tienes conexión a internet por cable, instala los siguientes paquetes y por orden:


dkms----->fakeroot-------->patch-------->bcmwl-kernel-source


Si no tienes acceso, tendrías que instalarlo desde el cd de ubuntu:


 dkms (ubicado en: pool -> main -> d)
fakeroot (ubicado en: pool -> main -> f)
patch (ubicado en: pool -> main -> p) y por último:
bcmwl-kernel-source (ubicado en: pool -> restricted -> b)


Saludos

---

