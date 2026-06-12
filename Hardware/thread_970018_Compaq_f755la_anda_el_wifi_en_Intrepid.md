---
title: "Compaq f755la anda el wifi en Intrepid?"
date: 2008-11-03
forum: Hardware
---

### Post by lega on 2008-11-03
Se que somos varios en el foro que tenemos esta notebook, en mi caso probé el live cd y me figuraba el driver habilitado, sin embargo no detectaba la conexion de casa, como la notebook la usa mi esposa no quiero arriesgarme a instalarlo y que despues no funcione, salvo que quiera divorciarme ;) pero por ahora no esta en mis planes.

Entonces pregunto, alguien que haya instalado Intrepid puede decirme como le ha ido con este modelo o similar, placa de video, wireless, sonido, ya que esta,la 756 y alguna otra tienen el mismo hardware o parecido?

Gracias

---

### Post by hictio on 2008-11-03
Hola, yo tengo una Compaq F700, con un WiFi:
Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Y me anduvo perfecto sin ninguna necesidad de compilar paquetes extra~nos (el 1er Ubuntu que uso en que anda)
Lo publique en un thread en ingles, ahora pongo las instrucciones aca en espanol.

---

### Post by faktorqm on 2008-11-04
Yo lo hice aca para 8.04.
Para 8.10 firman que anda? miren que lo publico eh!!

---

### Post by vk-cdg on 2008-11-04
Según leí, en 8.10 (no se la primera vez) pero cada vez que se actualice el kernel se recompilan AUTOMATICAMENTE todas las cosas que se hayan compilado a mano alguna vez.

Debería andar. Lo que no se es si la primera vez hay que compilarlo a mano o se hace automáticamente también.

---

### Post by benjamin_linux on 2008-11-04
Hola,

yo tengo la f754la, son prácticamente iguales. Si bien me detectó la placa Atheros no me funcionó tampoco (sí me funcionó -de una- la placa de video nvidia, no tuve que instalar los drivers envy como en Hardy :D :D :D).

Igualmente,
compilé madwifi siguiendo esta guía

[http://losmundosdeyupi.wordpress.com/2008/11/03/wifi-atheros-ar242xar5007eg-en-ubuntu-intrepid-ibex/](http://losmundosdeyupi.wordpress.com/2008/11/03/wifi-atheros-ar242xar5007eg-en-ubuntu-intrepid-ibex/)

y funciona sin problemas.

---

### Post by hictio on 2008-11-04
Una pregunta todos los modelos que estan posteando aca de Compaqs tienen el mismo chip para el WiFi?

---

### Post by lega on 2008-11-04
en mi caso
> lspci | grep Wireless

me devuelve lo siguiente:

> Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by niko_3100 on 2008-11-04
Yo tengo una broadcom que la hice andar con los drivers del windows xp, con ndiswrapper y modprobe

---

### Post by luks911 on 2008-11-04
> **benjamin_linux said:**
> Hola,

yo tengo la f754la, son prácticamente iguales. Si bien me detectó la placa Atheros no me funcionó tampoco (sí me funcionó -de una- la placa de video nvidia, no tuve que instalar los drivers envy como en Hardy :D :D :D).

Igualmente,
compilé madwifi siguiendo esta guía

[http://losmundosdeyupi.wordpress.com/2008/11/03/wifi-atheros-ar242xar5007eg-en-ubuntu-intrepid-ibex/](http://losmundosdeyupi.wordpress.com/2008/11/03/wifi-atheros-ar242xar5007eg-en-ubuntu-intrepid-ibex/)

y funciona sin problemas.

Che, no hace falta compilar nada para las F755, 754 y creo que 756, para el chipos atheros, bah.
No funciona el driver restringido, el ath_hal, que carga por defecto. Pero lo que hay que hacer, como puso hictio, es instalar linux-backports-modules-intrepid (si no equivoco el nombre). En Controladores de Hardware aparecerá un nuevo driver, el módulo que se carga se llama ath5k.

Saludos

---

### Post by hictio on 2008-11-04
> **luks911 said:**
> Che, no hace falta compilar nada para las F755, 754 y creo que 756, para el chipos atheros, bah.
No funciona el driver restringido, el ath_hal, que carga por defecto. Pero lo que hay que hacer, como puso hictio, es instalar linux-backports-modules-intrepid (si no equivoco el nombre). En Controladores de Hardware aparecerá un nuevo driver, el módulo que se carga se llama ath5k.

Saludos

Estan aca los pasos: [Intrepid: WiFi Compaq F700 (AR242x) funcionando](http://ubuntuforums.org/showthread.php?t=970055), y, por lo menos en la Compaq F700. no hay que compilar nada. solo deshabilitar, rebootear, instalar, rebootear, disfrutar.

---

### Post by benjamin_linux on 2008-11-04
Era más simple hacer eso que compilar madwifi :P

Gracias :)

---

### Post by hictio on 2008-11-05
> **benjamin_linux said:**
> Era más simple hacer eso que compilar madwifi :P

Gracias :)

Puede ser, si, pero ademas, el beneficio mas grande es que -bueno, es de suponer ;) - que al instalarlo de esta forma al driver, cuando continues haciendo updates con tu Intrepid, la cosa deberia seguir funcionando.

---

