---
title: "problema de hardware con una lenovo sl500"
date: 2009-07-15
forum: Hardware
---

### Post by esekay on 2009-07-15
hola, soy nuevo actualmente instale ubuntu 9.04 en una laptop lenovo sl500 thinkpad, luego de la instalación me reconoció todo menos las hot keys y la antena wifi, segun he buscado en internet hay que instalarle un driver para que corran pero sinceramente he visto que es mas o menos complicado lo intenete varias veces y sin lograr nada, me gustaria como buscar solucion a este problema por que amo ubuntu y no queria mas windows vista en mi laptop, me gustaria saber la manera mas sencilla que la mima me reconosca y que me corra el hardware y pueda conectarme a internet con mi red wi fi, muchas gracias... ubuntu es de 32 bits.

---

### Post by Carlos C on 2009-07-15
en el terminal escribe:
```
lspci
```
y copia acá lo que te salga.
Saludos.

---

### Post by esekay on 2009-07-18
hermano aquí tiene lo que me salio gracias por la ayuda...



00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
0c:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
0d:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0d:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0d:00.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0d:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0d:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by Carlos C on 2009-07-18
Encontré un bug reportado relacionado con tus hotkeys, bluetooth y control de brillo:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/351586](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/351586)

Al parecer debes añadir los repos backports. Para eso edita tu archivo sources.list:
```
sudo gedit file:/etc/apt/sources.list 
```Busca las siguientes lineas:
```
# deb http://cl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
```y borra el signo "#" al inicio de cada linea. Con eso dejan de ser un comentario y el sistema las considera. Luego debes actualizar tus repos:
```
sudo apt-get update
```Pero como el thread es respecto a tu problema de wifi tratemos de no desordenarlo (si, soy culpable, lo sé). Entiendo que esa tarjeta debiera funcionar sin problemas en cuanto instalas Ubuntu. ¿Fue una instalación de cero o actualizaste?.
Escribe por favor en el terminal:
```
iwconfig
```y copia acá lo que te salga.
Saludos.

---

### Post by esekay on 2009-07-18
que mas hermanito muchisimas gracias!! muhi hice lo que pusiste en el post luego de actualizar que se debe hacer??  no he visto ningún resultado en las hotkeys y si hay algo que no tome encuaneta??  bueno hablando de el wifi esto fue lo que me dio

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

la instalacion que hice fue desde cero no actualice incluso descargue el ubuntu 9.04 hace poco y directo lo instale desde cero...thanks

---

### Post by CdK1 on 2009-07-18
Look [https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)

[http://gianlucamagalotti.wordpress.com/2009/02/16/lenovo-thinkpad-sl-series-hotkeys/](http://gianlucamagalotti.wordpress.com/2009/02/16/lenovo-thinkpad-sl-series-hotkeys/)

Sobre la Wifi, que te tira un dmesg al intentar conectarte a alguna red? que driver usaste y como lo instalaste?

---

### Post by esekay on 2009-07-19
hola, no le he instalado ningún driver solo hice la instalación de ubuntu y normalmente el reconoce todo el hardware pero en el caso de este modelo de laptop hay que instalarle los driver a parte para que  se active el wi fi que actualmente esta inactivo, lo que no entiendo es como instalarlo ya que soy nuevo en ubuntu..si podrian ayudarme  de una manera sencilla, me gustaria que fuera como windows que solo le das click y listo aqui hay que montar parches y usar repositorios y el terminal que no estoy acostumbrado, agradeso su ayuda...

---

### Post by Umanchuk on 2009-10-27
Hola bueno yo traigo un problema parecido tengo mi lenovo sl500 migre el sistema a ubuntu funciona el wifi y todo lo demas pero :S el monitor avces que muevo el mause elbrillo cambia por un segundo al igual que al intenar modificarlo solo me agarra como quien dice dos tonos de brillo uno opaco y otro un poco mas claro pero no me da pa mas si pudieran ayudarme se los agradeceria.

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0c:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
0d:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0d:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0d:00.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0d:00.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

### Post by comandozulia on 2010-05-18
buenas amigos mi lapto es una sl500 les cuento mi desgracia era como las 1230 de la noche y de repente la pantalla se puso negra la apague en su power directamente por que era tarde al otro dia la enciendo para ver que paso le doy a encender y veo que se ve opaco pero se ve algo de echo busque una linterna y se la pegue a la pantalla y tenia sus colores y todo lo demás y como la apague indebidamente le di al enter para que hiciera todo el proceso normal  y haci lo hiso pero nada continua haci pareciera que le bajaron el brillo o resolucion pero no es eso me meti en configuracion de pantalla colores y nada sera que se me daño la pantalla me la cheque un disque tecnico y me dijo que la banda flex esta todo en su lugar y que no sabe sera que alguien me puede decir que hago  se le agradece a quien pueda ayudarme gracias ya saben el problema bacicamente es que la pantalla se ve oscura se ve pero muy oscura y la puce en alto rendimiento no esta ahorrando energia ya entre en la configuracion de pantalla  ayudaaaaaaa...

---

