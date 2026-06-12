---
title: "como pasar las fotos a la pc del celular samsung sgh-c425 en Ubuntu 8.04 ??"
date: 2009-03-24
forum: Hardware
---

### Post by seiya2050 on 2009-03-24
Hola

tengo un celular **Samsung Sgh-C425**, y quiero pasar las fotos a la pc, tengo **Linux Ubuntu 8.04** ¿como hago para instalarlo desde la terminal?

PD : enchufe el cable al usb pero no pasa nada, como con otros dispositivos q ya aparecen






salu2

---

### Post by ramiro_md on 2009-03-25
Con el dispotivo enchufado tira ```
lsusb
``` y postea lo que sale. 
Googleaste para ver si existe el driver libre de ese celular ?

---

### Post by seiya2050 on 2009-03-26
> **ramiro_md said:**
> Con el dispotivo enchufado tira ```
lsusb
``` y postea lo que sale. 
Googleaste para ver si existe el driver libre de ese celular ?

eso es lo que hice desde el principio y nada, busque en google y no hay nada de driver para Ubuntu :(



salu2

---

### Post by Jawsman on 2009-08-27
algun avance con esto?
estoy con el mismo problema...
Manu

---

### Post by guillermolisi on 2009-08-27
> **Jawsman said:**
> algun avance con esto?
estoy con el mismo problema...
Manu
Enchufa el celu y mostra la salida el comando "lsusb" (sin las comillas), a ver que y como reconoce. Pensa que cada PC puede ser un caso aparte.

---

### Post by Jawsman on 2009-08-28
...~$ lsusb
Bus 001 Device 003: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 6547:0232 Arkmicro Technologies Inc. ARK3116 Serial
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

gracias por la ayuda...

---

### Post by guillermolisi on 2009-08-28
> **Jawsman said:**
> ...~$ lsusb
Bus 001 Device 003: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 6547:0232 [COLOR=Red]Arkmicro Technologies Inc. ARK3116 Serial[/COLOR]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

gracias por la ayuda...
Ahi, marcado en color, esta la conexion a tu telefono.

La pagina del fabricante del chip dice:
> 
Details for ark3116 driver
( List devices with this driver )

Description    device driver for arkMicroChips ark3116 usb to serial converter (found in many mobile phone data cables)

Su link en [http://www.qbik.ch/usb/devices/showdr.php?id=215](http://www.qbik.ch/usb/devices/showdr.php?id=215) (en Ingles)

---

### Post by Jawsman on 2009-08-28
Perfecto, es el mismo cable que tengo yo...
ahora... alguna pista sobre como usar el driver 
para acceder a mi teléfono???

en realidad no sé si tengo instalado el driver tampoco
mil gracias

Manu

---

### Post by guillermolisi on 2009-08-28
> **Jawsman said:**
> Perfecto, es el mismo cable que tengo yo...
ahora... alguna pista sobre como usar el driver 
para acceder a mi teléfono???

en realidad no sé si tengo instalado el driver tampoco
mil gracias

Manu
Leyendo la informacion que hay a partir del link que te pase, encontre esto: > 18.06.2006 - ark3116 driver included in kernel 2.6.17 -> [kernel.org]("http://www.kernel.org/")

Esto significa que si estas usando ese kernel o superior (mas moderno) el driver esta incluido en el (o sea, ya esta instalado). Esto es asi desde el 18/06/2006.

Habria que indagar sobre como configurar el telefono para que sea reconocido por Ubuntu como disco removible (simil pendrive).

---

### Post by Jawsman on 2009-08-28
> **guillermolisi said:**
> 

Habria que indagar sobre como configurar el telefono para que sea reconocido por Ubuntu como disco removible (simil pendrive).

Genial guillermo, muchas gracias. voy a averiguar sobre el tema y si consigo avanzar posteo acá.

Manu

---

