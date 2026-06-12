---
title: "No wifi after suspend to ram"
date: 2005-06-13
forum: Hardware &amp; Laptops
---

### Post by granjerox on 2005-06-13
Recientemente siguiendo las instrucciones de [http://www.ubuntulinux.org/wiki/HoaryPM](http://www.ubuntulinux.org/wiki/HoaryPM) he activado la suspensión a ram de mi portatil centrino. Funciona muy rápido pero resulta que me apaga la tarjeta wireless intel 2200bg y no se volver a habilitarla. Al suspender se apaga la luz que indica en el portatil cuando está activa o no la tarjeta. Como si hubiera pulsado el boton (que funciona en windows pero en linux no lo tengo configurado) para conectar y desconectar la tarjeta. Mi portatil es el aopen 1556.

I'll try to traslate to english :

Recently following the instructions of [http://www.ubuntulinux.org/wiki/HoaryPM](http://www.ubuntulinux.org/wiki/HoaryPM) I have activated the suspension to ram of my centrino portatil.  It works very fast but after resume my intel wireless 2200bg is disabled and I don't know how to re-enable without rebooting.  As if it had pressed the button (that works in Windows but in linux I do not have it formed) to connect and to disconnect the card.  My portatil is aopen 1556

---

### Post by AMP on 2005-06-13
[QUOTE=granjerox]Recientemente siguiendo las instrucciones de [http://www.ubuntulinux.org/wiki/HoaryPM](http://www.ubuntulinux.org/wiki/HoaryPM) he activado la suspensión a ram de mi portatil centrino. Funciona muy rápido pero resulta que me apaga la tarjeta wireless intel 2200bg y no se volver a habilitarla. Al suspender se apaga la luz que indica en el portatil cuando está activa o no la tarjeta. Como si hubiera pulsado el boton (que funciona en windows pero en linux no lo tengo configurado) para conectar y desconectar la tarjeta. Mi portatil es el aopen 1556.

I'll try to traslate to english :

Recently following the instructions of [http://www.ubuntulinux.org/wiki/HoaryPM](http://www.ubuntulinux.org/wiki/HoaryPM) I have activated the suspension to ram of my centrino portatil.  It works very fast but after resume my intel wireless 2200bg is disabled and I don't know how to re-enable without rebooting.  As if it had pressed the button (that works in Windows but in linux I do not have it formed) to connect and to disconnect the card.  My portatil is aopen 1556[/QUOTE]
 lo siento pero me espanol no esta muy bien, pero

try going into the network pannel and activation the card that way.

---

### Post by granjerox on 2005-06-14
I tried that. I think it should be something about de power, because iwconfig detects de card and y can configure it. I've observed that iwconfig says "radio off". But when i try to activate it "sudo iwconfig eth1 txpower on" it don't let me.

---

### Post by luca_linux on 2005-06-15
You should install the latest version of ipw2200 driver (that is 1.0.4). There've been a lot of fixes (especially about the power management) since the version included in Hoary.
Look at this howto for more info: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

