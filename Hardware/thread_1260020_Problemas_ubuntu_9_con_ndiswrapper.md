---
title: "Problemas ubuntu 9 con ndiswrapper"
date: 2009-09-07
forum: Hardware
---

### Post by korba on 2009-09-07
Hola, soy nuevo en Ubuntu.

La cuestión es que probé Ubuntu 9.04 en el "modo de prueba" en mi pc e instalé los drivers de mi adaptador usb inalámbrico. Funcionón todo OK y me conectó a mi red.

Al instalar Ubuntu 9.04 en el disco duro no me guarda la configuración de la red inalámbrica, hago los mismos pasos para configurar con ndiswrapper, pero aunque reconoce el driver como instalado. El programa que gestiona la red (creo que se llama Network-Admin) no me detecta ninguna red inalámbrica y alrededor de mi casa hay un montón. Parece algo de configuración porque como he comentado con el cd virtual me funciona correctamente. ¿Alguna idea? :)

---

### Post by Carlos C on 2009-09-07
Hola. En el terminal escribe:
```
lsusb
```
y copia acá lo que te salga. También escribe:
```
lspci
```
y haces lo mismo.
Saludos.

---

### Post by kamus on 2009-09-08
> **korba said:**
> Hola, soy nuevo en Ubuntu.

La cuestión es que probé Ubuntu 9.04 en el "modo de prueba" en mi pc e instalé los drivers de mi adaptador usb inalámbrico. Funcionón todo OK y me conectó a mi red.

Al instalar Ubuntu 9.04 en el disco duro no me guarda la configuración de la red inalámbrica, hago los mismos pasos para configurar con ndiswrapper, pero aunque reconoce el driver como instalado. El programa que gestiona la red (creo que se llama Network-Admin) no me detecta ninguna red inalámbrica y alrededor de mi casa hay un montón. Parece algo de configuración porque como he comentado con el cd virtual me funciona correctamente. ¿Alguna idea? :)

Que tarjeta inalámbrica tienes? si fue reconocida en la instalacion no deberias tener problemas. Lo otro es que a menos que no este soportada de forma nativa empezaria a jugar con ndiswrapper (lo otro no has probado con Karmic?).

ps:el gestor de conexiones se llama network-manager :P

---

### Post by korba on 2009-09-09
> **Carlos C said:**
> Hola. En el terminal escribe:
```
lsusb
```y copia acá lo que te salga. También escribe:
```
lspci
```y haces lo mismo.
Saludos.

Hola Carlos C, como no conecto desde el pc escribo desde el trabajo y me traigo los resultados en un pemdrive.
te pongo el resultado de lsusb:
```
root@pc-sobremesa:~# lsusb
[COLOR=Blue]**Bus 001 Device 002: ID 15a9:0002  **[/COLOR]**[COLOR=Red]--> mi adaptador USB inalámbrico[/COLOR]**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 0951:1603 Kingston Technology Data Traveler 1GB/2GB Pen Drive
Bus 002 Device 004: ID 03eb:0902 Atmel Corp. 
Bus 002 Device 003: ID 046d:c219 Logitech, Inc. Cordless RumblePad 2
Bus 002 Device 002: ID 03f0:5511 Hewlett-Packard Deskjet F300 series
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

``````
root@pc-sobremesa:~# lshw -C Network
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:62:ee:94:7d:ac
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Cualquier cosa os parezca que debo hacer me lo comentáis, por favor. He instalado y reinstalado el ndiswrapper. Luego cargado el driver.

No entiendo mucho, pero es como que no se asocia bien o algo así porque he leído que con: 

sudo ndiswrapper -m

Nos devuelve esto:
manel@manel-desktop:~/Desktop/WLAN11G$ sudo ndiswrapper -m
adding "**alias wlan0 ndiswrapper**" to /etc/modprobe.d/ndiswrapper ...Y no consigo que me diga lo del alias wlan0.

---

### Post by korba on 2009-09-09
> **kamus said:**
> Que tarjeta inalámbrica tienes? si fue reconocida en la instalacion no deberias tener problemas. Lo otro es que a menos que no este soportada de forma nativa empezaria a jugar con ndiswrapper (lo otro no has probado con Karmic?).

ps:el gestor de conexiones se llama network-manager :P

Es un tema raro, ayer lo volví a probar desde el CD de instalación en modo prueba y me conecta sin problemas. En el modo pruebas utilizo ndiswrapper porque utilizo el driver de XP (mi adaptador USB inalámbrico usa el driver del prisma02 que ya tiene tiempo). De hecho lo probé primero y viendo que funcionaba le dije que me instalara el Ubuntu en el disco duro.

La cuestión es que llevo varios días jugando con ndiswrapper y no consigo nada, ayer quité network-manager e instalé WiCD, pero igual... :(

Es como que cuando está arranca desde el CD en prueba puede activar la red inalámbrica y en modo normal no la activa por alguna razón.

Nota: soy totalmente nuevo en Ubuntu, pero llevo unos cuantos días mareándome con el tema porque me ha gustado el SO y me gustaría cambiarme. Vamos si me deja tener conexión a internet :P

---

### Post by Carlos C on 2009-09-09
> **korba said:**
> En el modo pruebas utilizo ndiswrapper porque utilizo el driver de XP (mi adaptador USB inalámbrico usa el driver del prisma02 que ya tiene tiempo).

Veamos entonces si es posible hacerlo funcionar con ndiswrapper. Primero, tienes que tener ndiswrapper instalado. Lo puedes hacer usando synaptic o mediante apt-get. Verifica que así sea. Luego tienes que instalar el driver de windows. Si el nombre del driver es "driver.inf" el comando sería:
```
sudo ndiswrapper -i driver.inf
```
con eso se creará un archivo de configuración en /etc/ndiswrapper. Puedes ver que el driver esté instalado:
```
sudo ndiswrapper -l
```
luego carga el módulo ndiswrapper:
```
sudo modprobe ndiswrapper
```
escribe la configuración para modprobe para que cargue ndiswrapper cuando se active el wifi:
```
sudo ndiswrapper -m
```
Si lo anterior funciona y tienes wifi, entonces debes hacer que el sistema cargue ndiswrapper al inicio editando:
```
sudo gedit /etc/modules
```
y agregas al final del archivo "ndiswrapper".

---

### Post by korba on 2009-09-10
[[COLOR=#339900]**Carlos C**[/COLOR]]("http://ubuntuforums.org/member.php?u=469233"), lo que me comentas es más o menos lo que vengo haciendo. Creo que es alguna historia rara de la versión 9.04. Te pongo el resultado de los comandos que me indicas por si hubiese algo raro:
> root@pc-sobremesa:~# ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
[COLOR=RoyalBlue]prisma02 : driver installed
    device (15A9:0002) present[/COLOR]

root@pc-sobremesa:~# modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

root@pc-sobremesa:~# ndiswrapper -m
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
module configuration already contains alias directive

module configuration already contains alias directive

root@pc-sobremesa:~# gedit /etc/modules
He leído en las **Notas de la versión** lo siguiente, pero no sé si tiene algo que ver:
> **Ya no se admite la asignación del dominio de regulación inalámbrica mediante opción del módulo**

 Ubuntu 9.04 activa la infraestructura de regulación inalámbrica CRDA para controlar qué canales inalámbricos pueden usarse y son visibles en una ubicación particular. Si estaba usando anteriormente la opción del módulo en /etc/modprobe.d/options de forma similar a la descrita a continuación para permitir el acceso a ciertos canales de su ubicación local, es posible que su conexión inalámbrica deje de funcionar: 

[LIST]
[*][COLOR=RoyalBlue]options cfg80211 ieee80211_regdom=EU [/COLOR]
[/LIST]
Debería quitar esta opción del módulo del núcleo en la actualización a Ubuntu 9.04 y usar en su lugar el [COLOR=RoyalBlue]comando iw reg[/COLOR]. 
Sobre esto que he puesto no tengo ni idea a que se refieres si alguien lo entiende por favor que me explique si tengo que hacer algo. He probado [COLOR=RoyalBlue]iw reg[/COLOR], pero no lo tengo instalado y antes de instalarlo quiero saber para que sirve, así no ensucio demasiado el SO y las configuraciones. 

Gracias por el soporte :D , sigo con la guerra. A mi me da que es que en algún configuración debe de haber algo desactivado...

---

### Post by CdK1 on 2009-09-11
A mi parecer, es innecesario usar ndiswrapper si el CD de prueba te reconocio la red y tu hard de red nativamente... en tú caso haría..., poner el CD de prueba y ver que modulos cargó...ó, ver que hard de red inalámbrico tengo -aka lspci -vv- y buscar cual es e módulo correcto a instalar....

---

### Post by korba on 2009-09-13
> **CdK1 said:**
> A mi parecer, es innecesario usar ndiswrapper si el CD de prueba te reconocio la red y tu hard de red nativamente... en tú caso haría..., poner el CD de prueba y ver que modulos cargó...ó, ver que hard de red inalámbrico tengo -aka lspci -vv- y buscar cual es e módulo correcto a instalar....

Cuando probé con el CD de pruebas también usé ndiswrapper para cargar el driver. Por eso también lo uso tras instalar. He hecho un dmeg y he visto un error.
> [   10.010156] usbhid: v2.6:USB HID core driver
[   10.061988] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   10.236250] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   10.380043] usb 1-2: reset high speed USB device using ehci_hcd and address 2
[   10.416920] ppdev: user-space parallel port driver
[   10.467547] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   10.608337] input: Logitech Logitech Cordless RumblePad 2 as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0/input/input5
[   10.612099] logitech 0003:046D:C219.0001: input,hidraw0: USB HID v1.10 Gamepad [Logitech Logitech Cordless RumblePad 2] on usb-0000:00:0b.0-4/input0
[   10.612106] Force feedback for Logitech force feedback devices by Johann Deneux <johann.deneux@it.uu.se>

[   10.641525] ndiswrapper: driver prisma02 (SparkLAN,11/15/2004, 1.00.8.0) loaded
[   10.712228] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   10.712236] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   10.712423] HDA Intel 0000:00:10.1: setting latency timer to 64
[   10.845947] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138A, count: 3, return_address: f7f21fcb
[   10.845951] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xc0000001
[   10.845953] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x6d695442
[   10.845955] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x37

[   10.969095] psmouse serio1: ID: 10 00 64<4>logips2pp: Detected unknown logitech mouse model 62
[   11.144131] ndiswrapper (mp_init:219): couldn't initialize device: C0010006
[   11.144137] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   11.144146] ndiswrapper (mp_halt:262): device f67e8500 is not initialized - not halting

[   11.144149] ndiswrapper: device eth%d removed
[   11.144164] ndiswrapper: probe of 1-2:1.0 failed with error -22

[   11.147182] usbcore: registered new interface driver ndiswrapper
Con el CD de prueba y ndiswrapper:
> [  611.825099] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  611.992040] usb 1-2: reset high speed USB device using ehci_hcd and address 2
[  612.134133] ndiswrapper: driver prisma02 (SparkLAN,11/15/2004, 1.00.8.0) loaded
[  613.738486] wlan0: ethernet device 00:90:4b:fb:63:66 using NDIS driver: prisma02, version: 0x30311, NDIS version: 0x501, vendor: 'WL-682 802.11g USB Adapter', 15A9:0002.F.conf
[  613.738581] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  613.749225] usbcore: registered new interface driver ndiswrapper
[  618.395428] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  714.692841] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  725.384031] wlan0: no IPv6 routers present


Estoy aburrido con esto y es que sin red no puede ser. De todas formas gracias por la respuesta, sigo googleando también. Creo que he leído a alguien que le ha pasado lo mismo, el problema es que no he visto la solución.

No sé si es algún rollo de la blacklist que carga otro driver o algo así, pero bueno seguiré un poco más porque apatece bastante cambiar el SO. :)

---

