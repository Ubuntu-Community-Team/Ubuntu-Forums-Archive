---
title: "HP Scanjet 2400 in Ubuntu 10.10"
date: 2011-01-26
forum: Hardware
---

### Post by ranjank on 2011-01-26
Yesterday my brother gave a 2 year old Hp Scanjet 2400 . I connected it to my Ubuntu PC . I have Simple Scan , Scan Lite , Xsane installed in my pc . When I tried to scan a photo it scans only in 300dpi that too in B&W . How can I fix it .

---

### Post by ranjank on 2011-01-26
Any Solutions ? Urgent guys .

---

### Post by Tres_Iqus on 2011-04-13
In Spanish respose

descargar driver

1.- Conectar el Scanner y no prenderlo

2.- Desde una consola realizar los siguientes pasos

     sudo apt-get install xsane
     cd 2400drv
     sudo cp usr/lib/libsane.* /usr/lib
     sudo cp hp2400/usr/lib/sane/libsane-hp2400.* /usr/lib/sane/

Editar el archivo dll.conf

     sudo nano /etc/sane.d/dll.conf 

y agregar debajo de donde dice hp5400 el modelo de nuestro scanner en este caso hp2400


3.- Encender el Scanner y abrir el programa Xsane, seleccionar el primer dispositivo para que funciones correctamente

---

### Post by Jayster K on 2012-07-01
There are now drivers for the HP ScanJet 2400.  All you have to do is to install some packages via apt-get or Synaptic, and you will be able to use the XSane software to scan images.  Refer to:
[https://launchpad.net/~lion-simba/+archive/hp2400](https://launchpad.net/~lion-simba/+archive/hp2400)

First, add this software source to your repositories.
ppa:lion-simba/hp2400

For 32-bit users, install this package:
libsane-hp2400

For 64-bit users, install these packages:
libsane-hp2400x64
scanimage-ia32
xsane-ia32

Go into System > Administration > Users and groups
Look for the "saned" group and make sure your user account is included in that group.

Reboot your computer.

Make sure you have installed XSane Image Scanner.  Launch XSane and you should be able to scan images now.

Note that you can only scan colour images.  Greyscale scanning will not work.

Hope this helps!

---

