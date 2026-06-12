---
title: "El extraño caso de la batería en el NB200 de Toshiba"
date: 2010-01-18
forum: Hardware
---

### Post by donmatas on 2010-01-18
HOlanda compas:

instalé 9.04 en un Netbook Toshiba NB200. Funciona relativamente bien, pero tiene un sorprendente problema. La batería se descarga sola. O sea, la cargo al 100%, apago el computador y lo desenchufo y un par de días después lo trato de prender de nuevo (desenchufado) y nada. Lo enchufo y se prende y adivinen qué... batería 0%. He probado cargando la batería y sacándola luego y no se descarga. O sea, queda algo prendido al apagar la computadora uqe es lo que descarga la batería. Estuve investigando y parece que es la cámara integrada la que no se apaga bien y jode todo.
En este mismo foro pero en inglés proponen un asolución que dice > "tengo el mismo problema. Creo que se produce porque la cámara integrada sigue prendida cuando apago el sistema gracias al 'Sleep and Charge feature'. Agrega 'echo auto > /sys/bus/usb/devices/1-2/power/level' y 'echo 1 >/sys/bus/usb/devices/1-2/power/autosuspend' a tu  'init scripts' o /etc/profile para asegurarte que la cámara se apague cuando suspendas o apagues. Mientras tanto pueden poner en la lista negra de 'uvcvideo module' para evitar que la cámara siga funcionando, pero no evitará que sigua chupando energía".
 Como veran, mi inglés me da para traducir el texto, pero no para entender qué es lo que tengo que hacer. ¿Alguien podría darme una mano?

salud
DM

pd: el posteo original está en [http://ubuntuforums.org/showthread.php?p=7807698#post7807698](http://ubuntuforums.org/showthread.php?p=7807698#post7807698)

---

### Post by Carlos C on 2010-01-19
Esta complicado, puede ser un problema del kernel o algo que tendrás que configurar desde el bios. Cuando apagas el computador ¿queda algún led encendido? Mira este reporte de bug, al final hablan de tu modelo:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784)

¿Qué kernel tienes instalado?
```
uname -r
```

Lo muevo al subforo "Hardware", no te olvides de NO publicar en el foro principal.
Saludos.

---

### Post by donmatas on 2010-01-27
Gracias compa.
cuando apago el computador todo se apaga.
No le puedo mandar por ahroa el kernel, porque no tengo el cable para conectarme a la red elecéctrica y obviamente no tengo batería (el compu es de una amiga que olvidó la fuente de poder). Apenas tenga el dato lo comparto
Chequié el foro y al parecer es el mismo problema
salud
DM

---

### Post by nopersona on 2010-01-27
Interesante el caso. Prueba hacer lo que te dicen, agrega las opciones con 

```
sudo gedit /etc/profile
```

Voy a buscar algo más a ver qué encuentro. Se me ocurre también ver los logs, o agregar algo en las opciones del kernel para que le de la señal a la bios.

---

### Post by nopersona on 2010-01-27
Encima de un post tuyo, un usuario indica una opción para apagar su cámara y su bluetooth con un simple script. 

> **ShaunG said:**
> Hey guys,

Not sure if these will be of any use to anyone, but they are really simple bash scripts to turn camera on/off and turn bluetooth on/off, they are based on ReneVYL's trick.

They work for me so far, and don't seem to be harming anything.

If you want to use them, stick them in /usr/local/bin.They will need to be run as root. You can verify they work by running lsusb before and after running them. You will need to replace BUS_AND_DEVICE_NUM_GOES_HERE with the bus and device number of the camera/bluetooth device. In my case I'd replace it with 1-2 for the camera, and 5-2 for my bluetooth.

Camera/Bluetooth ON
```
#!/bin/bash

# Make sure only root can run our script
if [[ $EUID -ne 0 ]]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi

echo on > /sys/bus/usb/devices/BUS_AND_DEVICE_NUM_GOES_HERE/power/level

```

Camera/Bluetooth OFF

```
same as above, replace on with suspend

```

Bastante sencillo, por ejemplo haces un 

```
sudo gedit /usr/local/bin/camara
```

Y pegas:

```

#Camera/Bluetooth ON
#!/bin/bash

# Make sure only root can run our script
if [[ $EUID -ne 0 ]]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi

echo on > /sys/bus/usb/devices/BUS_AND_DEVICE_NUM_GOES_HERE/power/level
```

Tan solo basta cambiar los valores 1 y 2 por la respectiva salida de tu cámara.

---

### Post by donmatas on 2010-04-04
> **Carlos C said:**
> Esta complicado, puede ser un problema del kernel o algo que tendrás que configurar desde el bios. Cuando apagas el computador ¿queda algún led encendido? Mira este reporte de bug, al final hablan de tu modelo:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784)

¿Qué kernel tienes instalado?
```
uname -r
```

Lo muevo al subforo "Hardware", no te olvides de NO publicar en el foro principal.
Saludos.

gracias compa. disculpen la demora, pero recién logro enchufar el compu. El kernell es 
```
2.6.31-20-generic
```

espero me puedan ayudar

salud
DM

---

### Post by donmatas on 2010-04-04
> **nopersona said:**
> Encima de un post tuyo, un usuario indica una opción para apagar su cámara y su bluetooth con un simple script. 



Bastante sencillo, por ejemplo haces un 

```
sudo gedit /usr/local/bin/camara
```

Y pegas:

```

#Camera/Bluetooth ON
#!/bin/bash

# Make sure only root can run our script
if [[ $EUID -ne 0 ]]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi

echo on > /sys/bus/usb/devices/BUS_AND_DEVICE_NUM_GOES_HERE/power/level
```

Tan solo basta cambiar los valores 1 y 2 por la respectiva salida de tu cámara.

gracias nopersona, pero soy un novato y no entiendo mucho de esto. Por ejemplo no se cuàl es la salida de mi càmara y aunque supiera todavía me faltaría saber a qué te refieres con "valores 1 y 2". Te agradezco mucho la ayuda.

La info que tengo es la siguiente
```


paulina@paulina-laptop:/sys/bus/usb/devices$ ls
1-0:1.0  1-2:1.0  2-0:1.0  4-0:1.0  usb1  usb3  usb5
1-2      1-2:1.1  3-0:1.0  5-0:1.0  usb2  usb4
paulina@paulina-laptop:/sys/bus/usb/devices$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

salud y gracias
DM

---

### Post by donmatas on 2010-04-16
> **nopersona said:**
> Encima de un post tuyo, un usuario indica una opción para apagar su cámara y su bluetooth con un simple script. 



Bastante sencillo, por ejemplo haces un 

```
sudo gedit /usr/local/bin/camara
```

Y pegas:

```

#Camera/Bluetooth ON
#!/bin/bash

# Make sure only root can run our script
if [[ $EUID -ne 0 ]]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi

echo on > /sys/bus/usb/devices/BUS_AND_DEVICE_NUM_GOES_HERE/power/level
```

Tan solo basta cambiar los valores 1 y 2 por la respectiva salida de tu cámara.

y cómo hago para que se ejecute el script? 

saludos
DM

---

### Post by asterix77 on 2010-04-16
Para ejecutar un script primero debes darle permiso de ejecución

En este caso 

#chmod +x /usr/local/bin/camara

y luego simplemente digitas en consola

#camara

Si quieres que se ejecute al inicio te vas (en Karmic) a Sistema--Preferencias--Aplicaciones al inicio y agregas el script

Saludos

---

### Post by donmatas on 2010-04-16
> **asterix77 said:**
> Para ejecutar un script primero debes darle permiso de ejecución

En este caso 

#chmod +x /usr/local/bin/camara

y luego simplemente digitas en consola

#camara

Si quieres que se ejecute al inicio te vas (en Karmic) a Sistema--Preferencias--Aplicaciones al inicio y agregas el script

Saludos

estoy a punto de cantar victoria!
ya logré detener la cámara, ahora sólo me falta probar que esa era la fuga de energía. Les cuento cuando tenga respueta

salud
DM

---

