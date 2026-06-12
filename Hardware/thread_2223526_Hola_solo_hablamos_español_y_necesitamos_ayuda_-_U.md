---
title: "Hola solo hablamos español y necesitamos ayuda - Ubuntu Studio"
date: 2014-05-11
forum: Hardware
---

### Post by fleetwood1970 on 2014-05-11
Hola a todos:
Mi nombre es Lorena, soy usuaria de Ubuntu desde hace tiempo pero mi marido instalo en su computadora Ubuntu Studio 14.04
El tiene una Sound Blaster Audigy Platinum (creo que se denomina SB0090). La placa tiene mas de 10 años de antiguedad, pero funciona perfectamente.
El tema es que no logra hacer andar esa placa, la computadora toma el sonido on-board aunque muestra que la sound blaster esta fisicamente.
Para explicarlo mejor, cuando mira los meters de audio estos se mueven como que el audio funciona pero no sale nada x parlantes.
Esta placa tiene conectores para MIDI y conectores de tipo PLUG en un panel frontal. 
Alguien me dijo alguna vez que con ubuntu studio se podia hacer que esta placa funciones completamente. Para Windows ya no existen drivers, es muy vieja.
Realmente necesitamos contactarnos con alguien que entienda de AUDIO, de UBUNTU STUDIO y que hable en español. 
Mi marido (es musico aficionado, por ende entiende de audio bastante) no entiende muchos foros que estan en ingles, es demasiado tecnico y yo no entiendo de audio.
Si alguien nos puede indicar x donde empezar, les agradeceriamos mucho.

Los datos de la computadora en cuestion son:

Motherboard GA-945GCM-S2L/S2C (eso dice el manual en su tapa - Es GigaByte)
Es una dual core de Intel 2100 (?)
2GB de memoria ram
Video on-board
Sonido Audigy Soundblaster Platinum (SB0090 creo, fue la primera en salir de ese estilo)

Desde ya muchas gracias x la ayuda - Lorena

---

### Post by gmunioz on 2014-05-11
Hola Lorena:
En principio es necesario que desactives la placa onboard de la motherboard, esto se hace ingresando a la bios por el setup y el procedimiento varía con cada motherboard, si tienes el manual en él se debe indicar el procedimiento para poner** disable** la placa de sonido.
Si una vez reiniciado el sistema, sigue sin funcionar la tarjeta SoundBlaster, abre una terminal y ejecuta en ella:
> sudo su
apt-get install lshw
lspci | grep -i audio
lshw | grep -i audio | grep product
aplay -l | grep -i tarjeta
lsmod | grep -i snd
Copia las salidas y pégalas en el post, con esto se sabrá mejor que hardware de sonido estas usando.

---

### Post by fleetwood1970 on 2014-05-12
Gracias con contestar tan rapido Gmunioz!!!!
Ok, trataremos con esto..... 
Parece una buena forma de comenzar, ver que pasa y que es lo que esta funcionando dentro de esa computadora...
Te posteare lo que salio lo mas rapido posible, ya que la maquina no es mia.

Nuevamente muchas gracias x la ayuda - Lorena

---

### Post by fleetwood1970 on 2014-05-13
Hola Gmunioz:
Aca te dejo todo lo que hicimos en la terminal y las salidas que obtuvimos.
Nuevamente gracias x la ayuda - Lorena

gus@Gus:~$ sudo su
[sudo] password for gus: 
root@Gus:/home/gus# apt-get install lshw
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lshw is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.11.0-11-lowlatency linux-image-3.11.0-11-lowlatency
  linux-lowlatency-headers-3.11.0-11 thunderbird-locale-en
  thunderbird-locale-en-gb thunderbird-locale-en-us
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
root@Gus:/home/gus# lspci / grep -i audio
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of audio
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
root@Gus:/home/gus# lshw / grep -i audio / grep product
Hardware Lister (lshw) - B.02.16
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.16)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information
    -X              use graphical interface

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)

root@Gus:/home/gus# aplay -l / grep -i tarjeta
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy [SB Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy [SB Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy [SB Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@Gus:/home/gus# lsmod / grep -i snd
Usage: lsmod
root@Gus:/home/gus#

---

### Post by fleetwood1970 on 2014-05-18
Hola otra vez:
Publicamos como nos pidieron las salidas que nos dio la terminal pero aun no hemos recibido nada que nos diga como seguir.
Por favor prodrian ayudarnos? Gracias

---

### Post by gmunioz on 2014-05-19
Hola Lorena:
Prueba con abrir una terminal.
Ejecutar en ella:
sudo su
apt-get update
apt-get install --reinstall pulseaudio pavucontrol
nano /etc/pulse/daemon.conf

En el archivo que se abre buscas la línea:

**; default-sample-channels = 2**

Y la dejas así:

**default-sample-channels = 6**

Control + O, guarda. Control + X, cierra.

Pulsa el botón derecho de mouse sobre el icono del altavoz.

Abre el control de volumen.

Archivo ---- Cambiar dispositivo --- Elegir la tarjeta de sonido.

En la pestaña --- Conmutadores --- Desmarcar la casilla Audigy Analog/Digital Output Jack.

En una terminal ejecutar:

pavucontrol

En la pestaña Playback, pulsa el botón derecho del mouse sobre el nombre de cada aplicación que utilice sonido

En Move Stream selecciona la tarjeta de sonido a utilizar.

En las otras  pestañas, pon Default a la tarjeta de sonido predeterminada.

Reinicia para que funcionen todos los altavoces.

---

### Post by fleetwood1970 on 2014-05-20
Hola Gmunioz:
Bueno, hemos podido realizar toda la primera parte de lo que nos indicaste.
Hasta....

En el archivo que se abre buscas la línea:
**; default-sample-channels = 2**
Y la dejas así:
**default-sample-channels = 6**
Control + O, guarda. Control + X, cierra.

A partir de aqui no hemos podido hacer lo demas...
Si hacemos click derecho sobre el icono de sonido en la barra superior de UBUNTU STUDIO no nos conduce a nada. Abre las propiedades de la barra.
Si hacemos click izquierdo, nos muestra el volumen general para subir o bajar volumen - Audacious (los controles) - VLC (los controles) - Sound Settings.
Si entramos en Sound Settings, nos muestra una ventana con pestañas (Playback - Recording - Output Devices - Input Devices - Configuration)
No existe nada como lo que vos citas en tu texto:  

Abre el control de volumen.
Archivo ---- Cambiar dispositivo --- Elegir la tarjeta de sonido.
En la pestaña --- Conmutadores --- Desmarcar la casilla Audigy Analog/Digital Output Jack.

Ejecutamos en una terminal como nos pediste pavucontrol + enter
Nos abrio en control de volumen, que es lo mismo de sound settings.

Todo esto que nos pedis no lo hemos podido hacer ya que no existen las opciones que nombras:

En la pestaña Playback, pulsa el botón derecho del mouse sobre el nombre de cada aplicación que utilice sonido (no es posible hacer esto)
En Move Stream selecciona la tarjeta de sonido a utilizar. (no existe Move Stream)
En las otras  pestañas, pon Default a la tarjeta de sonido predeterminada. 

Si queres te podemos publicar un screen de como se ven las opciones y los menues. Tene en cuenta que estamos usando UBUNTU STUDIO 14.04 en esta computadora.
Gracias nuevamente y espero tus comentarios - Lorena

---

