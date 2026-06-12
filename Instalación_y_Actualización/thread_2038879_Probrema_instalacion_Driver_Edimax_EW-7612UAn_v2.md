---
title: "Probrema instalacion Driver Edimax EW-7612UAn v2"
date: 2012-08-07
forum: Instalación y Actualización
---

### Post by chelosawa on 2012-08-07
Hola a todos,

Tengo Ubuntu 11.04 en un Lenovo ThinkPad y acabo de adquirir una antena para WiFi usb, pero tengo problemas instalando el driver.
La antena es una Edimax EW-7612UAn V2 y el driver se puede bajar desde [http://www.edimax.com/en/downloadBox.php?pd_id=425&download_link=/images/Image/Driver_Utility/Wireless/NIC/EW-7612UAn_V2/RTL8192CU_linux_v3.0.2164.20110715_EDIMAX%20EW-7612UAn%20V2.zip]("http://www.edimax.com/en/downloadBox.php?pd_id=425&download_link=/images/Image/Driver_Utility/Wireless/NIC/EW-7612UAn_V2/RTL8192CU_linux_v3.0.2164.20110715_EDIMAX%20EW-7612UAn%20V2.zip")
Al hacer make me entrega el siguiente error: 
```
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-15-generic'
make[1]: *** No rule to make target `EW-7612UAn'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-15-generic'
make: *** [modules] Error 2

```

He buscado info en mil foros en todos los idiomas, y no he podido solucionar mi problemilla. 
Alguien sabe que se puede hacer?? No soy principiante en Linux, pero tampoco ningún experto!

Agradezco su ayuda de antemano!

Saludos,

Mauricio.

---

### Post by asterix77 on 2012-08-07
Bueno, a ver si te sirve de algo. En verdad el foro está un poco abandonado al parecer.

Me da la impresión que tu problema se genera al compilar desde el código fuente, bueno para que puedas hacer eso necesitas tener instalado algunos paquetes y librerías extras (al más puro y viejo estilo de linux)

Pregunta: ¿has instalado build-essential?, necesario para la instlación por esta forma.

Se arregla de la siguiente forma:
$sudo apt-get update
$sudo apt-get install build-essential

También a veces se puede necesitar instalar las librerías de desarrollo del kernel, necesarias para determinados paquetes:

$sudo apt-get install linux-headers-`uname -r`

Con esto debiera ser suficiente para compilar, si tienes errores durante la compilación, pégalos acá. Lo normal es que si los tengas, y se deba a una dependencia no instalada, si ves que falta un paquete solo debes abrir synaptic, buscarlo, e instalarlos.

Otra cosa, pega la salida acá del siguiente comando
$sudo lsusb

Más importante que el modelo de dispositivo usb, es ver el tipo de chip que posee, ya que por lo general tienes más opciones de buscar driver y de instalarlos más fácil


Saludos

---

### Post by chelosawa on 2012-08-08
Gracias por la respuesta, pero lamentablemente no me sirvió mucho. 
Los paquetes y las librerías que dices las tengo todas en su última versión. 
Aquí la salida de lsusb
```
chelo@kafka:~$ lsusb
Bus 002 Device 003: ID 17ef:4815 Lenovo Integrated Webcam [R5U877]
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 7392:7822 Edimax Technology Co., Ltd 
Bus 001 Device 004: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Alguna otra idea??

Gracias nuevamente y saludos!

---

### Post by asterix77 on 2012-08-08
Puedo ver por la salida y según el siguiente enlace [http://www.wikidevi.com/wiki/Edimax_EW-7822GTN](http://www.wikidevi.com/wiki/Edimax_EW-7822GTN)

Bus 001 Device 006: ID 7392:7822 Edimax Technology Co., Ltd
Que el chips es un Realtek RTL8192CU

Encontré la siguiente página que te puede ayudar [http://wiki.debian.org/rtl819x](http://wiki.debian.org/rtl819x) que es de Debian, como Ubuntu es similar las instrucciones igual sirven. Basicamente debes instalar [firmware-realtek]("http://packages.debian.org/firmware-realtek") and [wireless-tools]("http://packages.debian.org/wireless-tools") packages:

La sección 
wget [ftp://ftp.dlink.com/Wireless/dwa130_revC/Drivers/dwa130_revC_drivers_linux_006.zip](ftp://ftp.dlink.com/Wireless/dwa130_revC/Drivers/dwa130_revC_drivers_linux_006.zip) no me resultó desde la terminal

Por lo que usé un navegador [ftp://ftp.dlink.com/Wireless/dwa130_revC/Drivers/](ftp://ftp.dlink.com/Wireless/dwa130_revC/Drivers/)

Espero que te sirva y saludos

---

### Post by chelosawa on 2012-08-10
Graciaaas!

Funcionó la cosa... no como dijiste, pero funcionó.
No pude instalar el paquete firmware-realtek. Tuve problemas con los repositorios que eran de Debian.
Al final pillé el driver para el chip RTL8192CU acá [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true")
y ahora todo anda perfecto.

Nuevamente muchas gracias y saludos!

---

### Post by asterix77 on 2012-08-11
Me alegro que te haya servido, para eso estamos....

Saludos

---

