---
title: "Sin internet ni bluetooth JJ en msi vr 340"
date: 2009-06-13
forum: Hardware
---

### Post by sartrejp on 2009-06-13
Hola, compré una notebook msi vr340x, instalé ubuntu y no puedo conectarme a internet, ni siquiera enchufando el cable que uso en la pc de escritorio y confieso que no se para donde salir.
Alguna idea?

---

### Post by pablo.s on 2009-06-13
> **sartrejp said:**
>  confieso que no se para donde salir.
Alguna idea?

Nosotros tampoco sabemos
para donde salir.

Podría ser un lspci-lsusb?

---

### Post by sartrejp on 2009-06-13
Gracias por la celeridad en responder, voy lento porque no tengo ni un misero pendrive, paso los archivos con el telefono y de ahi a la otra pc

lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 04)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
01:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
01:04.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)


lsusb
Bus 002 Device 004: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 002 Device 002: ID 0db0:6877 Micro Star International RT2573
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 22b8:4810 Motorola PCS Triplet GSM Phone (storage)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by pablo.s on 2009-06-13
Hay un [reporte de bug]("https://bugs.launchpad.net/ubuntu/+bug/312157") que 
se parece al problema tuyo:
hay varias soluciones.
Espero que puedas leerlo.

---

### Post by sartrejp on 2009-06-13
gracias, voy a ver que pasa

---

### Post by sartrejp on 2009-06-13
No hay caso, no puedo conectarme.
Siempre me da que eth0 is not configured
o ignoring unknow interface eth0

---

### Post by pablo.s on 2009-06-13
Veo que estas perdidisimo,
por los mensajes que aparecen
en la lista.
Ya cuando mencionan "instalar
Windows" me empiezo a preocupar.

Ahi en el reporte de bug que te
mencionaba antes, un muchacho
dijo que [aca habia encontrado]("http://ubuntuforums.org/showpost.php?p=7276275&postcount=8")
una solucion. La probaste?

---

### Post by sartrejp on 2009-06-13
Si, si hago eso el icono del network-manager se convierte en un circulo rojo (como el de contramano) y no reacciona directamente.
Me peleé con el que me la vendió para que me saque el windows (asi no me obligaban a tenerlo para la garantía) y ahora no puedo conectarme ni en mi casa.....
es un bajón

---

### Post by pablo.s on 2009-06-13
Se me ocurre que podrias
probar con un LiveCD de
Intrepid o una version 
anterior y ver si pasa 
lo mismo. Por lo que veo
de lspci no muestra una
tarjeta WiFi, pero si la
de red.

---

### Post by sartrejp on 2009-06-13
Decís que no la detecta o que la pc no la tiene? 
Lo más frustrante es darme cuenta de los asistemático y pobre que es mi conocimiento sobre linux

---

### Post by pablo.s on 2009-06-13
Supuestamente la tiene,
la placa WiFi, pero no 
la esta mostrando.
No te preocupes por si
sabes sobre Linux, todos
aprendemos todos los dias
cosas nuevas. Imposible
saber todo.

Proba si podes con un
LiveCD de Ubuntu mas
antiguo o de alguna otra
distribucion, para ver si
no esta haciendo una
black list de las tarjetas.

---

### Post by Hei Ku on 2009-06-13
También serviria ver qué te tira el ifconfig.
El cable de red esta conectado a un router con DHCP? O sea, no es ningun engendro de ADSL que requiera configuracion extra, no?

---

### Post by sartrejp on 2009-06-13
No hay caso, no se conecta ni con Intrepid, ni con Hardy. Tampoco con OpenSuse y mandriva no termina de cargar nunca.

Ifconfig da esto
eth0      Link encap:Ethernet  direcciónHW 00:21:85:54:62:49
         dirección inet6: fe80::221:85ff:fe54:6249/64 Alcance:Vínculo
         ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
         RX packets:21527 errors:0 dropped:0 overruns:0 frame:0
         TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
         colisiones:0 txqueuelen:100
         RX bytes:1306284 (1.3 MB)  TX bytes:3204 (3.2 KB)
         Memoria:feac0000-feae0000

lo        Link encap:Bucle local
         inet dirección:127.0.0.1  Máscara:255.0.0.0
         dirección inet6: ::1/128 Alcance:Anfitrión
         ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
         RX packets:12 errors:0 dropped:0 overruns:0 frame:0
         TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
         colisiones:0 txqueuelen:0
         RX bytes:832 (832.0 B)  TX bytes:832 (832.0 B)

wlan0     Link encap:Ethernet  direcciónHW 00:21:85:79:9a:fe
         ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         colisiones:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  direcciónHW
00-21-85-79-9A-FE-00-00-00-00-00-00-00-00-00-00
         ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         colisiones:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

El cable está conectado al modem, si lo enchufo en la pc de escritorio (incluso cuando recién instalo el so) se conecta directamente, sin tener que tocar nada de nada

---

### Post by sartrejp on 2009-06-13
Me conecté! me dijeron en la lista de mail que econocimiento de MAC
Address (o como quiera que se escriba) por parte del ISP. La idea
general es que Fibertel le entrega conectividad a una dada placa de red,
la cual tiene una dada dirección de hardware. Al enchufar el cable en
otra placa de red (la de tu notebook) el servicio "desconoce" esa nueva
placa de red, y no se conecta (textual del mail), así que listo, el problema era ese.
Muchas gracias por su invaluable ayuda.
Ahora voy a ver si puedo hacer andar el bluetooth, ya que mi idea es compartir internet de la pc de escritorio a la notebook mediante el bluetooth, si llego a chocar contra alguna otra pared, vuelvo.
De nuevo gracias!

---

### Post by pablo.s on 2009-06-13
> **sartrejp said:**
> Muchas gracias por su invaluable ayuda.
Ahora voy a ver si puedo hacer andar el bluetooth, ya que mi idea es compartir internet de la pc de escritorio a la notebook mediante el bluetooth, si llego a chocar contra alguna otra pared, vuelvo.
De nuevo gracias!

¿Es posible eso?
Segun tengo entendido no...
Aunque como te dije antes,
aprendemos todos los dias
algo.

---

### Post by sartrejp on 2009-06-13
He visto por ahí que lo hacen con palms o celulares, entonces con otra pc con ubuntu se tendría que poder.
También explicaban como hacerlo en algún lado con dos windows xp sp2, ubuntu no puede ser menos jejeje, ya veremos... (primero tengo que hacer andar el bluetooth de la pc )

---

### Post by pablo.s on 2009-06-13
Ah, momento, vos te
referis a lo que se
llama "tethering"?
No es asi, pero bueno,
proba, si funciona
conta como es...

---

