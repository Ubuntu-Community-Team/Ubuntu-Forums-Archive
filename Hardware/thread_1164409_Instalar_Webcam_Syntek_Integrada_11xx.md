---
title: "Instalar Webcam Syntek Integrada 11xx"
date: 2009-05-19
forum: Hardware
---

### Post by kubuntero on 2009-05-19
LES PIDO POR FAVOR QUE RESPONDAN SI LES RESULTA EL MÉTODO O NO.

Este tutorial está probado en un Packard Bell Easynote MX550 con Kubuntu y Ubuntu 10.04.

Empecemos:

**Escribo en negrita los comandos que tienes que escribir. Si hay un signo $ _adelante_ del comando debes omitirlo.**

Al hacer un simple lsusb en la consola les mostrara algo asi


```
$ **lsusb**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 174f:a821 Syntek Web Cam - Packard Bell BU45, PB Easynote MX66-208W
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


el código 174f:a821 nos dice que la camara es una Syntek modelo 11XX

NOTA El driver también soporta los modelos (por el momento)
05e1:0501, 174F:a311, 174F:a312, 174f:5a35, 174f:5a31, 174f:6a31, 174f:6a33, 174f:6a51, 174F:6a54.


[SIZE="6"]1º Paquetes Escenciales[/SIZE]

Instalemos algunos paquetes escenciales, para esto tipeamos:

```

$ **sudo apt-get install linux-headers-`uname -r`**
$ **sudo apt-get install cheese**

```

En vez de Cheese pueden instalar cualquier otro programa que prefiran para usar su cámara.




[SIZE="6"]2º Descargamos el modulo (driver)[/SIZE]

Entramos desde el navegador a [http://sourceforge.net/projects/syntekdriver/files/syntekdriver/Release%202.1.0/stk11xx-2.1.0.tar.gz/download](http://sourceforge.net/projects/syntekdriver/files/syntekdriver/Release%202.1.0/stk11xx-2.1.0.tar.gz/download)
Luego extraemos y movemos la carpeta en nuestro /home/usuario


[SIZE="6"]3º Instalamos[/SIZE]

Abrimos un terminal y tipeamos


```
$ **cd stk11xx-2.1.0**
$ **wget http://bookeldor-net.info/merdier/Makefile-syntekdriver**
$ **make -f Makefile-syntekdriver**
$ **sudo make -f Makefile-syntekdriver install**
```


Cargamos el Módulo (sin signos $) y verificamos que funciona (les debería mostrar algo parecido)
Código:
```
$ **sudo modprobe stk11xx**

$ **dmesg |tail**
[ 5082.589538] stk11xx: Syntek USB2.0 webcam driver startup
[ 5082.589578] stk11xx: Syntek USB2.0 - STK-1135 based webcam found.
[ 5082.589583] stk11xx: Syntek AVStream USB2.0 VGA WebCam - Product ID 0xA821.
[ 5082.589590] stk11xx: Release: 0005
[ 5082.589595] stk11xx: Number of interfaces : 1
[ 5082.592257] stk11xx: Initialize USB2.0 Syntek Camera
[ 5082.932505] stk11xx: Syntek USB2.0 Camera is ready
[ 5082.932634] stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0
[ 5082.932705] usbcore: registered new interface driver usb_stk11xx_driver
[ 5082.932713] stk11xx: v1.3.1 : Syntek USB Video Camera

$ **sudo lsusb -v|grep -A 8 Syntek**
Bus 001 Device 002: ID 174f:a821 Syntek Web Cam - Packard Bell BU45, PB Easynote MX66-208W
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x174f Syntek
  idProduct          0xa821 Web Cam - Packard Bell BU45, PB Easynote MX66-208W
  bcdDevice            0.05
  iManufacturer           1 Syntek
  iProduct                2 USB2.0
  iSerial                10
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          147
    bNumInterfaces          1
~/stk11xx-1.4.0$
```




TIP:
Si la imágen se ve invertida verticalmente hacemos lo siguiente:

```

$ **cat /sys/class/video4linux/video0/vflip**

$ **echo 1 >/sys/class/video4linux/video0/vflip**

```

Recuerden que pueden también pueden modificar la imagen agregando filtros en Cheese.



LES PIDO POR FAVOR QUE RESPONDAN SI LES RESULTA EL MÉTODO O NO PARA INTENTAR CORREGIRLO EN CASO DE QUE CONTENGA ERRORES


fuente: [http://doc.ubuntu-fr.org/syntek](http://doc.ubuntu-fr.org/syntek)

---

### Post by prezeus on 2009-05-25
No funcionó... me pone coud not connect to video device /dev/video0. Me dí cuenta que no tenía el archivo video0 asi que renombré el video1 que sí tenía, pero tampoco sirvió. Gracias de todas formas, y si tienes alguna idea para ayudarme estaré agradecido.

---

### Post by kubuntero on 2009-05-26
> **prezeus said:**
> No funcionó... me pone coud not connect to video device /dev/video0. Me dí cuenta que no tenía el archivo video0 asi que renombré el video1 que sí tenía, pero tampoco sirvió. Gracias de todas formas, y si tienes alguna idea para ayudarme estaré agradecido.




hiciste bien es paso 4????
escribiste el comando tal cual aparece ahí???

Que te sale al ingresar "lsusb"??

---

### Post by spina4x on 2009-07-25
No me funcionó, al escribir sudo modprobe stk11xx no de devuelve nada.
Al ingresar lsusb, me sale esto:
Bus 002 Device 005: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 003: ID 174f:6a33 Syntek Web Cam - Asus F3SA, F9J, F9S
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by kubuntero on 2009-07-25
> **spina4x said:**
> No me funcionó, al escribir sudo modprobe stk11xx no de devuelve nada.
Al ingresar lsusb, me sale esto:
Bus 002 Device 005: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 003: ID 174f:6a33 Syntek Web Cam - Asus F3SA, F9J, F9S
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Tu camara es reconocida como 174f:6a33 así que el driver debería servirte.

Cuando se ingresa el comando "modprobe" es correcto que no se devuelva ningun mensaje.

que sale cuando ingresas el comando "dmesg |tail" ????

---

### Post by fragua on 2009-09-05
Hola Kubuntero,

Probado y funcionando.
Segui todos los pasos en mi packardbell easynote
con una camara.
Bus 001 Device 002: ID 174f:a821 Syntek Web Cam - Packard Bell BU45, PB Easynote MX66-208W

Saludos y muchas gracias

fragua

---

### Post by Esparte on 2010-04-06
Hola, sabes he instalado perfectamente mi camara con tu tutorial, pero queria saber si tenias una solucion para instalar el microfono que viene con la camara o no se si esta integrado a la camara pero que viene con el pc packard bell mx 550,

---

### Post by kubuntero on 2010-05-22
> **Esparte said:**
> Hola, sabes he instalado perfectamente mi camara con tu tutorial, pero queria saber si tenias una solucion para instalar el microfono que viene con la camara o no se si esta integrado a la camara pero que viene con el pc packard bell mx 550,

el mic aún no he podido hecharlo a andar...
si averiguas cómo por favor me avisas :)

---

### Post by ilomo on 2010-05-24
Vaya por delante mi agradecimiento a Kubuntero por este post facil.

Me ha funcionado en un Asus F3f.
He tenido que instalar "Cheese" necesariamente porque "Camera monitor" no lo detectaba.

En cuanto al SONIDO, hay que verificar que en Sistema/Preferencias/Sonido en la pestaña Entrada el Volumen de Entrada no esté a 0 y que esté seleccionado el micro correspondiente (en mi caso, microphone 1).

Nuevamente, gracias y un cordial saludo a tod@s.

---

### Post by higadillos on 2010-06-09
I get this when i enter [B][COLOR=DarkRed]dmesg |tail

[/COLOR][/B][COLOR=DarkRed][COLOR=Black][ 6489.131444] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[ 6754.945390] ath5k phy0: noise floor calibration timeout (2417MHz)
[ 7118.347322] device eth0 entered promiscuous mode
[ 7291.225079] device eth0 left promiscuous mode
[ 7477.479183] ath5k phy0: unsupported jumbo
[ 7500.512087] device eth0 entered promiscuous mode
[ 7784.747544] device eth0 left promiscuous mode
[ 9542.407887] stk11xx: Syntek USB2.0 webcam driver startup
[ 9542.407993] usbcore: registered new interface driver usb_stk11xx_driver
[ 9542.408567] stk11xx: v2.0.0 : Syntek USB Video Camera
[/COLOR]
[COLOR=Black]and this when i enter[B] lsusb -v|grep -A 8 Syntek

[/B]Bus 001 Device 002: ID 174f:8a12 Syntek Syntek 0.3MPixel USB 2.0 UVC PC Camera
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x174f Syntek
  idProduct          0x8a12 Syntek 0.3MPixel USB 2.0 UVC PC Camera
  bcdDevice            7.25
  iManufacturer           2 Syntek
  iProduct                3 USB2.0 UVC PC Camera
  iSerial                 4 0001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          353
    bNumInterfaces          2


but it did not work. any helpplease?
[/COLOR][/COLOR]

---

### Post by dpanario on 2010-06-19
> **kubuntero said:**
> LES PIDO POR FAVOR QUE RESPONDAN SI LES RESULTA EL MÉTODO O NO.

No lo he probado, pero como tengo un Packard bell mx45-009 me vengo peleando hace tiempo con la maldita webcam desde que dejo de funcionar a partir del 8.04, te dejo un script de instalación, probado en jaunty, karmic y lucid.

Es solo copiar, guardar en un archivo y ejecutar.
----------------------------------------------------------

#!/bin/sh

# Dependencias
sudo apt-get install build-essential

# Controlador
wget [http://downloads.sourceforge.net/project/syntekdriver/syntekdriver/Release%202.1.0/stk11xx-2.1.0.tar.gz?use_mirror=freefr](http://downloads.sourceforge.net/project/syntekdriver/syntekdriver/Release%202.1.0/stk11xx-2.1.0.tar.gz?use_mirror=freefr)
tar xvzf stk11xx-2.1.0.tar.gz && cd stk11xx-2.1.0 && wget [http://bookeldor-net.info/merdier/Makefile-syntekdriver](http://bookeldor-net.info/merdier/Makefile-syntekdriver) && make -f Makefile-syntekdriver && sudo make -f Makefile-syntekdriver install
sudo modprobe stk11xx && sudo lsusb -v | grep -A 8 Syntek && sudo addgroup $USER video && cat /sys/class/video4linux/video0/vflip && echo 1 >/sys/class/video4linux/video0/vflip
sudo echo "Syntek Webcam" | sudo tee -a /etc/modprobe.d/options && sudo echo "options stk11xx vflip=1 brightness=0xBBBB" | sudo tee -a /etc/modprobe.d/options

# Camorama
sudo apt-get install camorama

# Mensaje
zenity --info --title="Proceso finalizado" --text="Ya está, prueba abriendo Camorama a ver si funciona." \

-----------------------------------------------------------

Saludos

---

### Post by javierlu on 2010-07-10
A mi me fue perfecto. Mi ordenador es un easynote  BU
Saludos y gracias por la ayuda. JVRL

---

