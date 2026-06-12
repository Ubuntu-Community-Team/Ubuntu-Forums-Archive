---
title: "Problemas Broadcom BCM4311 (rev 02)"
date: 2009-12-18
forum: Hardware
---

### Post by mcisternas on 2009-12-18
Desde el momento que terminé de instalar y reiniciar Karmic Koala he tenido problemas con mi inalámbrica. El problema es el siguiente: cada cierto tiempo la tarjeta se me bloquea, su luz comienza a parpadear como loca y, finalmente, el sistema se me cae entero.

He revisado los logs y he encontrado algunos resultados que adjuntaré a este mensaje. Sé que hay soluciones, pero por lo menos a mí no me han funcionado. He instalado un par de veces el sistema, y el problema persiste. Mi notebook es un Compac Presario C708 LA.

```

**lspci**

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
**01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)**
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10
``````
**dmesg | grep b43**

[    2.249237] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.249249] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
[   17.372575] b43-phy0: Broadcom 4311 WLAN found (core revision 13)
[   18.980096] b43 ssb0:0: firmware: requesting b43/ucode13.fw
[   19.057219] b43 ssb0:0: firmware: requesting b43/b0g0initvals13.fw
[   19.215090] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   19.336800] Registered led device: b43-phy0::tx
[   19.336865] Registered led device: b43-phy0::rx
[   19.336895] Registered led device: b43-phy0::radio
[   19.337032] b43-phy0: Radio hardware status changed to DISABLED
[   19.366764] b43-phy0: Radio turned on by software
[   19.366770] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   29.836109] b43-phy0: Radio hardware status changed to ENABLED
[   30.016112] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   30.088824] Registered led device: b43-phy0::tx
[   30.088891] Registered led device: b43-phy0::rx
[   30.088922] Registered led device: b43-phy0::radio
```**cat messages | grep b43**```


 Dec 17 22:54:01 ubuntu kernel: [  626.548479] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Dec 17 22:54:01 ubuntu kernel: [  626.625301] Registered led device: b43-phy0::tx
Dec 17 22:54:01 ubuntu kernel: [  626.625385] Registered led device: b43-phy0::rx
Dec 17 22:54:01 ubuntu kernel: [  626.625465] Registered led device: b43-phy0::radio
Dec 17 22:54:01 ubuntu kernel: [  626.864123] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Dec 17 22:54:02 ubuntu kernel: [  626.940911] Registered led device: b43-phy0::tx
Dec 17 22:54:02 ubuntu kernel: [  626.940996] Registered led device: b43-phy0::rx
Dec 17 22:54:02 ubuntu kernel: [  626.941077] Registered led device: b43-phy0::radio
Dec 17 22:54:02 ubuntu kernel: [  627.176109] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Dec 17 22:54:02 ubuntu kernel: [  627.255769] Registered led device: b43-phy0::tx
Dec 17 22:54:02 ubuntu kernel: [  627.255854] Registered led device: b43-phy0::rx
Dec 17 22:54:02 ubuntu kernel: [  627.255936] Registered led device: b43-phy0::radio
Dec 17 22:54:02 ubuntu kernel: [  627.500096] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Dec 17 22:54:02 ubuntu kernel: [  627.572888] Registered led device: b43-phy0::tx
Dec 17 22:54:02 ubuntu kernel: [  627.572973] Registered led device: b43-phy0::rx
Dec 17 22:54:02 ubuntu kernel: [  627.573054] Registered led device: b43-phy0::radio
Dec 17 22:54:02 ubuntu kernel: [  627.800152] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Dec 17 22:54:02 ubuntu kernel: [  627.876876] Registered led device: b43-phy0::tx
Dec 17 22:54:02 ubuntu kernel: [  627.876961] Registered led device: b43-phy0::rx
Dec 17 22:54:02 ubuntu kernel: [  627.877044] Registered led device: b43-phy0::radio
```Si necesitan más información acerca de mi sistema o algún dato más específico, por favor avisar.

Muchas gracias!

---

### Post by asterix77 on 2009-12-18
¿La instalación la realizastes vía cd o por gestor de actualizaciones?. Instalastes el controlador privativo (Sitema --->Administración ---->Controladores de hardware) ------>activar uno de los dos que te aparecen (debieran aparecerte dos).

Saludos

---

### Post by mcisternas on 2009-12-18
> **asterix77 said:**
> ¿La instalación la realizastes vía cd o por gestor de actualizaciones?. Instalastes el controlador privativo (Sitema --->Administración ---->Controladores de hardware) ------>activar uno de los dos que te aparecen (debieran aparecerte dos).

Saludos

La instalación la realicé mediante un cd. Y sí, instalé el controlador privativo, aparecen dos y activé el primero.

Saludos.

[CENTER][IMG]http://mcisternas.wordpress.com/files/2009/12/pantallazo-controladores-de-hardware.png[/IMG]
[/CENTER]

---

### Post by Carlos C on 2009-12-18
Hola. Te sugiero que escribas en el terminal:

```
lspci -vnn | grep 14e4
```

y veas lo que te aparece. No todos los modelos de tarjeta funcionan bien con el módulo b43. Dependendiendo del resultado de ese comando si el módulo es el adecuado o no.

Saludos.

---

### Post by smo0th on 2009-12-18
Deshabilita el driver de sistema, usa  ```
sudo apt-get install bcm43xx-fwcutter
``` y reinicia la pc, si no se te habilita el driver en auto usa ```
sudo modprobe b43
``` e intenta conectarte a tu red.

---

### Post by Carlos C on 2009-12-18
> **smo0th said:**
> Deshabilita el driver de sistema, usa  ```
sudo apt-get install bcm43xx-fwcutter
``` y reinicia la pc, si no se te habilita el driver en auto usa ```
sudo modprobe b43
``` e intenta conectarte a tu red.

Pero cuidado, para que ese módulo funcione la tarjeta debe estar soportada y no siempre es el caso. Por eso es que le pido que primero corra el comando que antes propuse. De esa manera podrá verificar si su modelo es soportado por este módulo:

[http://linuxwireless.org/en/users/Drivers/b43#KnownPCIdevices](http://linuxwireless.org/en/users/Drivers/b43#KnownPCIdevices)

Saludos.

---

### Post by mcisternas on 2009-12-18
> **Carlos C said:**
> Hola. Te sugiero que escribas en el terminal:

```
lspci -vnn | grep 14e4
```y veas lo que te aparece. No todos los modelos de tarjeta funcionan bien con el módulo b43. Dependendiendo del resultado de ese comando si el módulo es el adecuado o no.

Saludos.

Carlos:

He hecho lo que me pediste y este es el resultado:

```
**lspci -vnn | grep 14e4**
01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [**14e4:4311**] (rev 02)
```

Por el momento estoy usando el Controlador Inalámbrico Broadcom STA hasta que encuentre una solución, pues el otro se taldeó toda la mañana.

Saludos

---

### Post by Carlos C on 2009-12-18
Por lo visto tu tarjeta sí está soportada, por lo tanto debería funcionar el módulo b43. Como dice smo0th te sirve el paquete *b43-fwcutter*. Según recuerdo, durante la instalación se te pide que aceptes descargar el firmware y entonces es cosa de reiniciar. Recuerdo un caso en que fue necesario tener el paquete* linux-restricted-modules* instalado para que ese módulo funcionara, pero esto ocurrió con una versión anterior a Karmic, por lo que no creo que eso siga siendo necesario. ¿Es ese paquete el que estás usando?

---

### Post by Carlos C on 2009-12-21
Buscando información encontré algo que puede servirte:

[http://www.ubuntugeek.com/fix-for-broadcom-4328-v3-wireless-problem-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/fix-for-broadcom-4328-v3-wireless-problem-in-ubuntu-9-10-karmic.html)

Saludos.

---

### Post by CdK1 on 2009-12-22
Lo que haría sería lo siguiente:

Borrar todo rastro del algún tipo de instalación anterior y:

1.- Actualizar y upgradear
2.- sudo aptitude install b43-fwcutter
3.- sudo ifconfig wlan0 up
4.- Para ver los problemas que puedan suceder, luego de estar conectado:

CdK1@Caturra:/$ cd var/log/
CdK1@Caturra:/var/log$ tail -f messages

Y ver, si es que ocurre, que dicen los logs cuando tienes problemas...

---

