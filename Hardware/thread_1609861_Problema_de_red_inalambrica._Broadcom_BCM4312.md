---
title: "Problema de red inalambrica. Broadcom BCM4312"
date: 2010-10-30
forum: Hardware
---

### Post by aantinao on 2010-10-30
Hola a todos

Soy nuevo y sordo. Me encanta mucho a usar Ubuntu porque soy novato entonces quiero aprender más en linux. Tengo un problema de red inalámbrica no funciona bien porque esta desactivado. Descargué todas las actualizaciones en el cable de red (rj45). Adjunto las imágenes. ¿Como soluciona esto?.

Atentamente

Saludos cordiales

---

### Post by themasterdark on 2010-10-31
Según tu captura del escritorio, estaria apagada la red inalámbrica, asegurate de que este encendida desde el mismo hardware, me refiero a si tu notebook/netbook posee algun "boton o switch" para encender la red inalambrica verifica eso, ya que el driver para tu broadcom aparece instalado, cualquier consulta no dudes en escribir.

---

### Post by aantinao on 2010-10-31
> **themasterdark said:**
> Según tu captura del escritorio, estaria apagada la red inalámbrica, asegurate de que este encendida desde el mismo hardware, me refiero a si tu notebook/netbook posee algun "boton o switch" para encender la red inalambrica verifica eso, ya que el driver para tu broadcom aparece instalado, cualquier consulta no dudes en escribir.


Hola

Mi notebook tiene un botón para encender. Encendí el botón de red inalámbrica, pero todavía esta desactivado. Adjunto el imagen.

Muchas gracias.

---

### Post by asterix77 on 2010-10-31
Puedes encenderla también a través de la consola, ya que en mi caso por ejemplo, no tengo un switch de encendido, sino que se activa por una combinación de teclas, que al cambiarme a jaunty desde windows, no me funcionaba, por lo que recurrí a la consola para solucionar el tema.

#sudo ifconfig wlan0 up

De todos modos creo que faltan más antecedentes, ya que por ejemplo, deduzco que te quieres conectar a tu acces point para salir a internet y no puedes, excepto cuando te conectas por cable.

Deberías enviar lo que te sale con el siguiente comando.

#sudo ifconfig      (para ver si te reconoce tu inalámbrica)

¿están bien configuradas las propiedades de tu acces point y contraseñas?

Saludos

---

### Post by benja22 on 2010-10-31
Tal vez no tienes instalado el firmware de tu tarjeta inalambrica...

---

### Post by aantinao on 2010-10-31
> **benja22 said:**
> Tal vez no tienes instalado el firmware de tu tarjeta inalambrica...

Hola amigos

[asterix77]("http://ubuntuforums.org/member.php?u=840386"), de acuerdo a lo pedido. Adjunto la imágen (Pantallazo-2)

[benja22]("http://ubuntuforums.org/member.php?u=863194"), instalé los packages bcmwl-kernel-source y b43-fwcutter, pero no pude instalar el package firmware-b43-installer porque tiene un error. Adjunto las imágenes (Pantallazo-3-4-5).

Estoy conectado con el cable de red (RJ45) funciona muy bien, pero las redes inalámbricas esta desactivado. :confused:

Saludos cordiales !!!!

Gracias

---

### Post by themasterdark on 2010-11-01
Ese error se debe a que no es el instalador del firmware para tu tarjeta (también la mía), debe instalar el paquete

firmware-b43-lpphy-installer

Saludos cuentamos como va todo

---

### Post by RafaelG on 2010-11-01
Estimado,

Te recomiendo que para poder optimizar la ayuda de los colegas podrias postear tu **lspci**  y asi poder identificar cual es tu tarjeta inalambrica. Ahora por el Switch inalambrico que mostraste  aparentemente es un Notebook Dell es caso de ser  asi te recomiendo revises el siguiente post:

[http://ubuntuforums.org/showthread.php?t=1312873&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=1312873&highlight=Broadcom)

Saludos!

---

### Post by aantinao on 2010-11-02
> **RafaelG said:**
> Estimado,

Te recomiendo que para poder optimizar la ayuda de los colegas podrias postear tu **lspci**  y asi poder identificar cual es tu tarjeta inalambrica. Ahora por el Switch inalambrico que mostraste  aparentemente es un Notebook Dell es caso de ser  asi te recomiendo revises el siguiente post:

[http://ubuntuforums.org/showthread.php?t=1312873&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=1312873&highlight=Broadcom)

Saludos!

Hola a todos

Estoy un poco complicado porque no pude solucionar el problema. Mi notebook marca Dell modelo 1320. 
Ya lo hice, pero no me dio resultados :-(.  Creo que disminuye la potencia de hardware.

Tengo la información de lspci:

aantinao@aantinao-laptop:~$ lspci
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
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
1a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)


Saludos cordiales!!!


Atentamente

---

### Post by aantinao on 2010-11-02
> **RafaelG said:**
> Estimado,

Te recomiendo que para poder optimizar la ayuda de los colegas podrias postear tu **lspci**  y asi poder identificar cual es tu tarjeta inalambrica. Ahora por el Switch inalambrico que mostraste  aparentemente es un Notebook Dell es caso de ser  asi te recomiendo revises el siguiente post:

[http://ubuntuforums.org/showthread.php?t=1312873&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=1312873&highlight=Broadcom)

Saludos!

Hola a todos

Estoy un poco complicado porque no pude solucionar el problema. Mi notebook marca Dell modelo Vostro 1320. 
Ya lo hice, pero no me dio resultados :-(.  Creo que disminuye la potencia de hardware.

Tengo la información de lspci:

aantinao@aantinao-laptop:~$ lspci
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
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
1a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)


Saludos cordiales!!!


Atentamente

---

### Post by benja22 on 2010-11-02
Encontré esto 
[http://ubuntuforums.org/showthread.php?t=1312873](http://ubuntuforums.org/showthread.php?t=1312873) 
¿sera tu mismo problema?
---
por lo visto tu tarjeta inalambrica es la BCM4312
¿por que no intentas desintalar los drivers y volver a instalar el firmware?
quizás el firmware que instalas no es el correcto para tu tarjeta de red
---
mira esto [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/655111](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/655111)
dice que este bug se arregla con jockey

---

### Post by RafaelG on 2010-11-03
> **aantinao said:**
> Hola a todos, Estoy un poco complicado porque no pude solucionar el problema. Mi notebook marca Dell modelo 1320. Ya lo hice, pero no me dio resultados :-(.  Creo que disminuye la potencia de hardware.Tengo la información de lspci:
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)



aantinao,

Yo tambien tengo un Dell pero es Vostro 1510, la verdad que no he tenido disminucion en mi alcanze en mi red inalambrica de hecho trabaja a la perfeccion, ahora mi pregunta es hiciste lo inicado en el post que te recomende de ser positiva tu respuesta podrias postear en formato HTML lo que arroja la consola, me imagino que la ejecucion de los comando lo hace conectado con un cable a la red para que puedas descargar lo necesario.

Recuerda que una ves que ejecutas los comando indicados debes reiniciar la maquina para que surta efecto los cambios realizados como tambien procupate de que en el icono de red inalambrica en el panel superior hacer click y activar la red inalambrinca con eso se deberia activar la conexion inalambrica.

Si no me equiboco el kernel nuevo segun tengo entendido tiene la tarjeta inalambrica que tienes en blacklist por lo que quitando "#" sacaria tu tarjeta de la blacklist podrias probar con esta opcion tambien aunque se supone que la tarjeta esta en la blacklist por que con el nuevo kernel la tarjeta inalambrica es inestable por ese motivo esta en blacklist hasta que salga del proceso.

En resumen cuentas estaremos atentos a tu respuesta, Saludos!!!

---

### Post by Carlos C on 2010-11-04
> **aantinao said:**
> 
Ya lo hice, pero no me dio resultados :-(.  Creo que disminuye la potencia de hardware.



¿Qué fue lo que hiciste?

Antes de hacer cambios, desinstalar o instalar algo, te recomiendo averiguar si tu tarjeta es soiportada por el driver b43. No todas las tarjetas bcm43 funcionan con dicho driver. Para verificarlo debes escribir en el terminal:
```
lspci -vnn | grep 14e4
```Te saldrá algo como esto:
```
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [COLOR=DarkRed][14e4:4318][/COLOR] (rev 02)
```Donde [COLOR=DarkRed][14e4:4318][/COLOR] es la parte que te importa, ya que con ese valor debes verificar en la lista siguiente si es un modelo soportado por el módulo b43:
[URL="http://linuxwireless.org/en/users/Drivers/b43#Supported_chip_types"]
http://linuxwireless.org/en/users/Drivers/b43#Supported_chip_types[/URL]

Nos dices cómo te fue con eso.
Edito el título del thread.

Saludos.

---

### Post by asterix77 on 2010-11-04
Al parecer ¿se trataría de un bug en Maverick??

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/655111/+activity](https://bugs.launchpad.net/ubuntu-release-notes/+bug/655111/+activity)

Al parecer una posible solución aparece en un foro de debian, [http://forums.debian.net/viewtopic.php?f=30&t=52587&start=15](http://forums.debian.net/viewtopic.php?f=30&t=52587&start=15).

Donde indican instalar el paquete [COLOR=black]
[/COLOR]**[FONT=Arial][SIZE=3][COLOR=black]firmware-b43-lpphy-installer[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3]para extraer el firmware[/SIZE][/FONT]**

[http://packages.debian.org/squeeze/firmware-b43-lpphy-installer](http://packages.debian.org/squeeze/firmware-b43-lpphy-installer)

Espero que te pueda servir

Saludos.

PD: Acá otro link en un sitio de ubuntu (maverick)  [http://www.ubuntuupdates.org/packages/show/246638](http://www.ubuntuupdates.org/packages/show/246638)

---

### Post by RafaelG on 2010-11-10
> **aantinao said:**
> [benja22]("http://ubuntuforums.org/member.php?u=863194"), instalé los packages bcmwl-kernel-source y b43-fwcutter, pero no pude instalar el package firmware-b43-installer porque tiene un error. Adjunto las imágenes (Pantallazo-3-4-5).


Yo creo que el b43-fwcutter no es lo que necesita tu tarjeta de hecho estuve indagando un poco en el tema y el Driver para tu tarjeta inalambrica en el recomendado por Broadcom en la siguiente pagina y en la instrucciones indica que si tienes instalado el b43-fwcutter traera condlifcto. 

Te recomiendo leas la siguiente pagina 
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

y las instrucciones correctas para la instalacion del driver estan en el siguiente Link
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

Segun los pantallasos que pusiste tienes instalado el Driver correcto que el el Broadcom STA y esta activado pero puede que donde instalaste el b43 ahora tienes conflicto, bueno en definitiva te recomiendo le heches un vistazo a las paginas de Broadcom donde te indica cual es Driver correcto para tu tarjeta

Saludos!

---

