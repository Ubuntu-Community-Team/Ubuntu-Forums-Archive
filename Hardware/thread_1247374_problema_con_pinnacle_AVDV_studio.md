---
title: "problema con pinnacle AV/DV studio"
date: 2009-08-22
forum: Hardware
---

### Post by mdquevedo on 2009-08-22
buenas como andan
quisiera saber si alguno de ustedes sabe configurar una capturadora de video
pinnacle AV/DV studio (version 9) en ubuntu jaunty
no se si hay algun modulo que tenga que activar o como hacer para poder usarla
ubuntu la reconoce con el comando lspci
pero no puedo hacerla funcionar con los programas 
no se que puede ser
alguna idea?

---

### Post by guillermolisi on 2009-08-23
> **mdquevedo said:**
> buenas como andan
quisiera saber si alguno de ustedes sabe configurar una capturadora de video
pinnacle AV/DV studio (version 9) en ubuntu jaunty
no se si hay algun modulo que tenga que activar o como hacer para poder usarla
ubuntu la reconoce con el comando lspci
pero no puedo hacerla funcionar con los programas 
no se que puede ser
alguna idea?
Podrias mostrar la salida del lspci ? Asi todos vemos como es reconocida la placa por tu sistema.

---

### Post by mdquevedo on 2009-08-25
gracias por contestar
perdon por la tardansa 
esta es la salida del lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:09.0 Communication controller: Agere Systems 56k WinModem (rev 01)
00:0b.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
00:0c.0 Multimedia controller: 00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:09.0 Communication controller: Agere Systems 56k WinModem (rev 01)
00:0b.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
00:0c.0 Multimedia controller: Pinnacle Systems Inc. AV/DV Studio Capture Card
00:0c.1 FireWire (IEEE 1394): Pinnacle Systems Inc. Device 0015
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 300/305 PCI/AGP VGA Display Adapter (rev 90)

00:0c.1 FireWire (IEEE 1394): Pinnacle Systems Inc. Device 0015
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 300/305 PCI/AGP VGA Display Adapter (rev 90)

estube investigando un poco y la podria hacer andar con el modulo zoran
pero no puedo instalar lo en el kernel
este es el error que me sale al tratar de ponerlo en el kernel

cosina@cosina:~/Escritorio/driver-zoran-0.9.5$ make
Making Unified Zoran (zr360x7) driver for 2.6.28-15-generic kernel...
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/cosina/Escritorio/driver-zoran-0.9.5/zoran_procfs.o
/home/cosina/Escritorio/driver-zoran-0.9.5/zoran_procfs.c:30:26: error: linux/config.h: No existe el fichero ó directorio
In file included from /home/cosina/Escritorio/driver-zoran-0.9.5/zoran_procfs.c:49:
/home/cosina/Escritorio/driver-zoran-0.9.5/zoran.h:268: error: redefinición de ‘struct v4l2_jpegcompression’
/home/cosina/Escritorio/driver-zoran-0.9.5/zoran_procfs.c: En la función ‘zoran_write_proc’:
/home/cosina/Escritorio/driver-zoran-0.9.5/zoran_procfs.c:222: error: declaración implícita de la función ‘copy_from_user’
/home/cosina/Escritorio/driver-zoran-0.9.5/zoran_procfs.c: En el nivel principal:
/home/cosina/Escritorio/driver-zoran-0.9.5/zoran_procfs.c:287: error fatal: abriendo el fichero de dependencias /home/cosina/Escritorio/driver-zoran-0.9.5/.zoran_procfs.o.d: Permiso denegado
compilación terminada.
make[2]: *** [/home/cosina/Escritorio/driver-zoran-0.9.5/zoran_procfs.o] Error 1
make[1]: *** [_module_/home/cosina/Escritorio/driver-zoran-0.9.5] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [here] Error 2
 
alguna idea?

---

