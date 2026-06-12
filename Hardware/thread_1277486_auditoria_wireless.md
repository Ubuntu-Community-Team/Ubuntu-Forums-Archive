---
title: "auditoria wireless"
date: 2009-09-28
forum: Hardware
---

### Post by capcabgue on 2009-09-28
Hola.

Como dice el título, estoy tratando de hacer una auditoría sobre las redes wifi, lo estoy haciendo con  aircrack-ng, pero cuando trato de activar el modo monitor, me dice:
Interface               Chipset                      Driver

eth1                       Unknown                              wl


Sin embargo, navego por internet inalambricamente, alguien me puede decir como hacer que me reconozca el chipset y el driver, o para hacer mi auditoría no importa tener el chipset reconocido.

Saludos y en espera de su respuesta

---

### Post by asterix77 on 2009-09-29
¿Que versión de ubuntu usas?

¿Que tarjeta inalámbrica usas?

escribe en consola lspci y pega el contenido, también escribe lo que te aparece con el comando iwconfig

Al menos en mi caso mi tarjeta inalámbrica me aparece como Wlan0, ya que ethx se refiere a redes cableadas  (al menos en mi caso).

Saludos

---

### Post by capcabgue on 2009-09-29
Hola lo que me da con lpci es lo siguiente (creo que la última línea es la de wifi):

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

En cuanto a mi iwconfig sale lo siguiente:

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:223  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

Utilizo Ubuntu 9.04 en un DELL Inspiron 1525, me reconoce todo (el sonido unn poco bajo), pero todo ok.

Gracias

---

### Post by asterix77 on 2009-09-29
Yo tengo un notebook dell inspiron 1501 con una tarjeta Broadcon BCM4311, que al principio tampoco podía colocar en modo monitor.

Necesito saber si tienes instalado el driver b43 activado. Para ello tienes que ir a sistema-administración-controladores de hardware. Debieran aparecer dos controladores para tu tarjeta inalámbrica.

a) Broadcom b43 wireless drver
b) Controlador inalámbrico Broadcom STA

La que tienes que habilitar es la primera (es la que al menos uso yo). Después de esto preba si ingresa a modo monitor.

PD: mi versión de ubuntu es la 8.10, no sé si cambia un poco la ruta en 9.04

Otra cosa ¿como tratas de colocar en modo monitor tu tarjeta de red?

---

### Post by angelsv on 2009-09-29
A mi me paso igual q a ti, pero hice lo q te aconseja asterix77; lo q tienes q hacer es activar el driver para tu tarjeta wireless.

Prueba eso y nos cuentas

salu2

---

### Post by capcabgue on 2009-10-02
> **asterix77 said:**
>  Broadcom b43 wireless drver

La verdad sólo tengo una tarjeta: Broadcom STA wireless driver.
En cuanto a como la pongo en modo de monitor es haciendo:
iwconfig (sale esto entre otras cosas)
eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated  
          Link Quality:5  Signal level:224  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

airmon-ng stop eth1
airmon-ng start eth1 (sale lo siguiente)
Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
3228    NetworkManagermodo monitor, quedo ahí no más
3248    avahi-daemon
3249    avahi-daemon
3258    wpa_supplicant
4215    dhclient
Process with PID 4215 (dhclient) is running on interface eth1


Interface    Chipset        Driver

eth1        Unknown         wl (monitor mode enabled)

Pero como no me dice donde esta activado el modo monitor, quedo ahí.
El "tutorial que estoy siguiendo para hacer esto es el siguiente:
[http://www.ubuntu-ve.org/node/2735](http://www.ubuntu-ve.org/node/2735)

dentro de todos los que vi.

Finalmente uso la versión de Ubuntu 9.04 de 64 bits.

Saludos

PD: como se reinicia la tarjeta, ya que cada vez que hago esto tengo que reiniciar mi pc para poderme conectar a Internet, a pesar que veo la red.

---

### Post by themasterdark on 2009-10-03
Holaa...

Buenas, yo tengo el mismo notebook, con la misma tarjeta wifi...
y bueno probe por todos lados con los drivers que me sirvieran para activarla en modo monitor, pero es imposible xD

lei mucho... y lo mas probable es que no se pueda... te lo comento para que no te partas la cabeza buscando como.

Saludos =D

^^

---

### Post by capcabgue on 2009-10-04
> **themasterdark said:**
> Holaa...

Buenas, yo tengo el mismo notebook, con la misma tarjeta wifi...
y bueno probe por todos lados con los drivers que me sirvieran para activarla en modo monitor, pero es imposible xD

lei mucho... y lo mas probable es que no se pueda... te lo comento para que no te partas la cabeza buscando como.

Saludos =D

^^


Me tinco, ya que en alguna parte, mientras me partía la cabeza, leí que NO con todas las tarjetas se podía hacer esto de jar de modo monitor, pero me dije, siempre hay alguien que sabe más y me puede decir que estoy haciendo mal o confirmar mis sospechas.

Gracias por el dato

---

### Post by asterix77 on 2009-10-05
Yo creo que si se puede, yo otuve bastante información de esta página.

[http://linuxwireless.org/en/users/Drivers/b43#fw-bcm43xx](http://linuxwireless.org/en/users/Drivers/b43#fw-bcm43xx)

Espero te sirva, Saludos

---

### Post by asterix77 on 2009-10-05
[B][SIZE=2]Cito textualmente un párrafo que aparece en dicha página[/SIZE]
[/B]

**working**

 
[LIST]
[*]Station mode 
[*]Mesh networking mode (b43 only) 
[*]Access Point mode 
[*]Ad-Hoc (IBSS) mode (b43 only) 
[*]**Monitor and Promisc mode.** 
[*]"Monitor while operating" and multiple monitor interfaces. 
[*]In-Hardware traffic de/encryption (relieves your CPU). 
[*]LEDs to signal card state and traffic. 
[*]In-Hardware MAC address filter (b43 only; impossible on b43legacy hardware) 
[*]Packet injection (with radiotap; no FCS injection currently though hardware supports it - a radiotap flag is being discussed for this) 
[*]Bluetooth coexistence protection, if the bluetooth card is physically connected to the wireless chip. (Does not protect against external BT dongles) 
[*]Probably something we forgot to add here.
[/LIST]

Recuerdo que de aquí seguí instrucciones, para instalar el firmware, y después seguí las instrucciones según mi versión del kernel.

---

### Post by themasterdark on 2009-10-05
De hecho yo tambien probe con dichas instrucciones, pero de todos modos no, funcionaba el driver claro pero no para modo monitor.

Saludos =)

---

### Post by CondorDelta on 2010-01-28
Compa..
yo tengo la misma tarjeta..
le recomiendo comprese algun adaptador wiffi para sus auditorias..
en mi caso yo me compre el sgte...

Adaptador USB Tp-Link 
TL-WN422G Wireless
 Antena Desmontable de 4dbi
CONECTOR SMA

[http://www.sunnyline.com.pl/oscommerce/catalog/images/twn422g.jpg](http://www.sunnyline.com.pl/oscommerce/catalog/images/twn422g.jpg)

Es buenisimo..
lo he usado en backtrack 4
Ubuntu 9.10

wifislax y wifiway me dieron drama...

pero en general buen adaptador...

incluso en algunas redes injecta..
eso si no en todas...

---

