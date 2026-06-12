---
title: "Netbook y touchpad no reconocido en Jaunty"
date: 2009-09-08
forum: Hardware
---

### Post by netingsdc on 2009-09-08
Estimados; he recibido un hermoso netbook Commodore K80000 y, como vengo haciendo desde hace tiempo, particioné HDD. Preparé un pendrive con el Jaunty 9.04 y procedí a instalarlo. Pero me doy con que no puedo hacer que reconozca el touchpad. ¿alguna idea o sugerencia?
Saludos cordiales

Arnaldo de la Colina

---

### Post by pablo.s on 2009-09-08
Podrías probar si tiene
el mismo problema con
UNR?

---

### Post by netingsdc on 2009-09-08
> **pablo.s said:**
> Podrías probar si tiene
el mismo problema con
UNR?

Bajaré la UNR a ver como vá
Gracias por la sugerencia

---

### Post by netingsdc on 2009-09-09
> **netingsdc said:**
> Bajaré la UNR a ver como vá
Gracias por la sugerencia

Ya baje UNR, el touchpad funcionó unos minutos. Al reiniciar no lo volví a poder activar. Probé varios reinicios y no pasó nada.

---

### Post by pablo.s on 2009-09-09
Tendríamos que ver que
sale cuando escribis en una
terminal
```
lsusb
```
y lo pegas en un nuevo post.

---

### Post by netingsdc on 2009-09-13
lsusb respondió:


Bus 001 Device 004: ID 0bda:0156 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 002: ID 0ac8:3420 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 062a:0000 Creative Labs Optical mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

aclaro que la anteúltima línea corresponde al mouse optico que le enchufé para poder trabajar.

Saludos

---

