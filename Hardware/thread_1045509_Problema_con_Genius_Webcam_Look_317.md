---
title: "Problema con Genius Webcam Look 317"
date: 2009-01-20
forum: Hardware
---

### Post by geoflavio on 2009-01-20
Hola a todos:
Ya me termine volviendo loco de buscar como hacer andar mi Genius Webcam Look 317 y no hay caso.
Tengo Ubuntu 8.10 sobre un AMD64.
Logre instalar el módulo gscpa, ya que aparentemente se podría hacer andar con ese módulo ya que utiliza un chipset Pixart:
lsusb
Bus 003 Device 005: ID 03f0:3d17 Hewlett-Packard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 005: ID 093a:2623 Pixart Imaging, Inc.**
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Sin embargo no logre tener mayor exito, el cheese me sigue diciendo que no hay nada y no existe /dev/video0, además la salida de lsmod es la siguiente
gspca                 702032  0
compat_ioctl32         18176  1 gspca
videodev               46720  2 gspca,compat_ioctl32
usbcore               175376  8 gspca,snd_usb_audio,snd_usb_lib,usblp,usbhid,ehci_hcd,ohci_hcd
Y el dmesg me tira lo siguiente:
[  145.098096] ppdev0: registered pardevice                                                                                                    
[  145.144593] ppdev0: unregistered pardevice                                                                                                  
[  147.663135] ppdev0: registered pardevice                                                                                                    
[  147.712168] ppdev0: unregistered pardevice                                                                                                  
[  149.985385] ppdev0: registered pardevice                                                                                                    
[  150.042973] ppdev0: unregistered pardevice
[ 2103.453115] Linux video capture interface: v2.00
[ 2103.480334] usbcore: registered new interface driver gspca
[ 2103.480833] gspca: gspca driver 01.00.20 registered
[ 2135.648158] usb 2-1: USB disconnect, address 2
[ 2137.692358] usb 3-2: USB disconnect, address 2
[ 2137.694129] usblp0: removed
[ 2139.676012] usb 3-3: new high speed USB device using ehci_hcd and address 5
[ 2139.812610] usb 3-3: configuration #1 chosen from 1 choice
[ 2139.814257] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x03F0 pid 0x3D17
[ 2141.480011] usb 1-2: new full speed USB device using ohci_hcd and address 4
[ 2141.686942] usb 1-2: configuration #1 chosen from 1 choice
[ 3203.940636] usb 1-2: USB disconnect, address 4
[ 3208.240672] usb 1-2: new full speed USB device using ohci_hcd and address 5
[ 3208.464403] usb 1-2: configuration #1 chosen from 1 choice
[ 4087.819244] usb 1-2: USB disconnect, address 5
[ 4089.606061] usb 1-2: new full speed USB device using ohci_hcd and address 6
[ 4089.826005] usb 1-2: configuration #1 chosen from 1 choice

Desde ya muchas gracias por su ayuda.

---

### Post by GeoMX on 2009-05-21
También tengo esta cámara, buscando cómo conseguir instalarla he llegado a la conclusión de que simplemente no está soportada en Linux:

La cámara no está en la lista de identificadores USB:
[http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)

Tampoco en la lista de dispostivos soportados por el driver gspca (el que  soporta otras cámaras Genius):
[http://www.kernel.org/doc/Documentation/video4linux/gspca.txt](http://www.kernel.org/doc/Documentation/video4linux/gspca.txt)

Quien pretenda conseguir una cámara para Ubuntu, mejor evitar esta :(.

---

### Post by geoflavio on 2009-05-22
Sipis, yo también había llegado a la misma conclusión, sin embargo tenía la ilusión de que sea diferente ^_^.-

---

### Post by atari130xe on 2009-05-22
Una de las Genius que recomiendo por Calidad de imagen y compatibilidad con Ubuntu (la compré cuando tenia instalada Ubuntu 7.10) es la [COLOR="Red"][SIZE="4"]Genius Look 316[/SIZE][/COLOR], comprenla con total confianza, que funciona perfecto, probaron actualizar a Ubuntu 9.04? le instalé esa ultima version a un amigo hace 1 semana y "magicamente" le reconoció una camara Logitech que no andaba an ninguna otra versión de Ubuntu, sería cuestion de probar con el Live CD al menos. suerte!

---

