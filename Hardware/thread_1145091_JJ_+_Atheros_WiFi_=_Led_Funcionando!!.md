---
title: "JJ + Atheros WiFi = Led Funcionando!!"
date: 2009-05-01
forum: Hardware
---

### Post by Mauro22 on 2009-05-01
Si!!


Con JJ anda la luz del wifi :D:D


"03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)"


Tantos meses sin que prenda... recien me di cuenta :D. Aguante JJ :lolflag:


Se que es post es al re p*d* pero estoy feliz :D

---

### Post by lega on 2009-05-01
En la notebook de mi señora Compaq F755, reconoció la placa desde el live cd de Kubuntu, cosa que me alegró muchiiiiisimo, ahora la lucecita no anda, no todo es posible, que va ser :) igual que levante el wifi de una es genial :)

---

### Post by Mauro22 on 2009-05-01
En el livecd no recuerdo que prendiera la luz... lo hubiera notado enseguida...

---

### Post by lega on 2009-05-01
No desde el livecd no prende, pero hice mención a eso porque con Intrepid no pasaba que levantara la conexion wifi desde el cd, con la instalación hecha tampoco prende, de todos modos mi señora esta contentisima con Kubuntu, no le importa demasiado la luz del led :) esas son cosas de uno que es un maniático :)

---

### Post by Mauro22 on 2009-05-01
> **lega said:**
> ... no le importa demasiado la luz del led :) esas son cosas de uno que es un maniático :)



No es algo que me preocupara pero me volvia loco de envidia en que en Ventanas andaba :S

---

### Post by luks911 on 2009-05-01
> **Mauro22 said:**
> Si!!


Con JJ anda la luz del wifi :D:D


"03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)"


Tantos meses sin que prenda... recien me di cuenta :D. Aguante JJ :lolflag:


Se que es post es al re p*d* pero estoy feliz :D

Pregunta totalmente inutil: ¿Qué módulo usa para esa placa ath5k o ath9k?

Gracias :lolflag:

---

### Post by z37a on 2009-05-01
Genial saber esto, en unos días voy a ponerle a mi laptop JJ y tengo una atheros, en II le pude hacer andar el led gracias a otro post de aca, espero que tambien me funcione bien!!!!

---

### Post by Mauro22 on 2009-05-01
> **luks911 said:**
> Pregunta totalmente inutil: ¿Qué módulo usa para esa placa ath5k o ath9k?

Gracias :lolflag:



Si me decis como hago para darme cuenta, te respondo.. jeje

---

### Post by luks911 on 2009-05-01
> **Mauro22 said:**
> Si me decis como hago para darme cuenta, te respondo.. jeje

Je, con 

```
sudo lshw -C network
```

Te va a dar datos de los dispositivos ethernet y wifi. En el de wifi fijate que dice en, si no me equivoco, driver. Gracias

---

### Post by Mauro22 on 2009-05-01
*-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4d:09:86:3f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.40 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn

---

### Post by luks911 on 2009-05-01
Muchas gracias. Es pura curiosidad nomás. Porque con el ath5k, el que puede usar mi placa, la luz no funciona.

---

### Post by Anak on 2009-09-21
> **Mauro22 said:**
> Si!!


Con JJ anda la luz del wifi :D:D


"03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)"


Tantos meses sin que prenda... recien me di cuenta :D. Aguante JJ :lolflag:


Se que es post es al re p*d* pero estoy feliz :D

¿Que es Jj? 
Tengo la misma tarjeta de red, y uso ath9k, el led parpadea, pero no se apaga cuando le das, siempre esta encendido.
¿Me puedes matizar como corregiste el error?

Gracias y un saludo

---

### Post by luks911 on 2009-09-21
> **Anak said:**
> ¿Que es Jj? 
Tengo la misma tarjeta de red, y uso ath9k, el led parpadea, pero no se apaga cuando le das, siempre esta encendido.
¿Me puedes matizar como corregiste el error?

Gracias y un saludo

Anak,

JJ es Jaunty Jackalope, es decir Ubuntu 9.04.
En cuanto al led, hasta donde sé, no responde usando los módulos ath5k ni ath9k.
Para poder hacerlo funcionar deberías reemplazar ath5k por madwifi, siempre que tu placa sea compatible. Aquí[0] se explica cómo instalarlo. Deberás fijarte luego de la instalación que esté desactivado ath9k y que madwifi (su módulo se llama ath_pci) no esté en el blacklist.
Luego de eso, la parte sencilla para que el led funcione: está en este[1] thread donde incluso hay un par de variantes para que el led parpadee con el tráfico o quede encendido.

[0] [http://www.ubuntugeek.com/new-madwifi-now-supports-ar2425-in-madwifi-trunk-branch.html](http://www.ubuntugeek.com/new-madwifi-now-supports-ar2425-in-madwifi-trunk-branch.html)
[1] [http://ubuntuforums.org/showthread.php?t=983511](http://ubuntuforums.org/showthread.php?t=983511)

---

### Post by Anak on 2009-09-21
> **luks911 said:**
> Anak,

JJ es Jaunty Jackalope, es decir Ubuntu 9.04.
En cuanto al led, hasta donde sé, no responde usando los módulos ath5k ni ath9k.
Para poder hacerlo funcionar deberías reemplazar ath5k por madwifi, siempre que tu placa sea compatible. Aquí[0] se explica cómo instalarlo. Deberás fijarte luego de la instalación que esté desactivado ath9k y que madwifi (su módulo se llama ath_pci) no esté en el blacklist.
Luego de eso, la parte sencilla para que el led funcione: está en este[1] thread donde incluso hay un par de variantes para que el led parpadee con el tráfico o quede encendido.

[0] [http://www.ubuntugeek.com/new-madwifi-now-supports-ar2425-in-madwifi-trunk-branch.html](http://www.ubuntugeek.com/new-madwifi-now-supports-ar2425-in-madwifi-trunk-branch.html)
[1] [http://ubuntuforums.org/showthread.php?t=983511](http://ubuntuforums.org/showthread.php?t=983511)

Gracias por solventarme las dudas luks911. El problema es que uso archlinux, y me meti en este foro, porque es el único que vi, que con esta tarjeta hizo funcionar el led. ath9k la verdad es que me funcionan bastante bien... el único problema el led, que se queda permanentemente en azul y parpadea cuando se conecta a una red, cuando su función es un chivato de on/off

Gracias de nuevo

---

