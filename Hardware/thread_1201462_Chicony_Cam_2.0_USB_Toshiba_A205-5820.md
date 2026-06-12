---
title: "Chicony Cam 2.0 USB Toshiba A205-5820"
date: 2009-07-01
forum: Hardware
---

### Post by jpoeta on 2009-07-01
Hola queridos amigos de Argentina LocoTeam :guitar:
Ya tengo casi un mes con ubuntu casi todos mis problemas solucionados y disfrutado del mejor Software del Mundo.
Uno de los únicos problemas que sigo teniendo es con el redimiendo de mi cámara integrada en mi laptop, pese a que funciona tengo problemas con la oscuridad si mi cuarto no esta bien iluminado simplemente la imagen se vuelve negra. En el sistema operativo del 666 Windows Vista, tenía el driver que me permitía configurar la cámara en modo nocturno.
Disculpen la molestia, les agradesco de antemano alguna información o la solución total del problema.

Atentamente

Jpoeta

;)
Laptop Toshiba A205-5820
Cámara Integrada Chicony USB 2.0
Ubuntu 9.04

---

### Post by pablo.s on 2009-07-01
> **jpoeta said:**
> 
Uno de los únicos problemas que sigo teniendo es con el redimiendo de mi cámara integrada en mi laptop, pese a que funciona tengo problemas con la oscuridad si mi cuarto no esta bien iluminado simplemente la imagen se vuelve negra.

Ese mismo problema lo tienen
todas las cámaras, tanto de video
cómo de foto.
La captura de imágen, funciona
con un principio muy sencillo:
Al lente le llega luz. La luz que se
refleja (primariamente) de los
objetos que tenga enfrente.
Si la luz es poca, hace falta que el
diafragma (o el iris) de la cámara
esté más abierto. Si la luz es mucha,
hace falta que esté mas cerrado,
para compensar y que no se
sobreexponga la imagen. Pues bien,
en ese engendro que son las webcam,
se balancea toda esta ecuación con
un sensor pequeño, una lente muy
simple y practicamente ningun
diafragma (mejor dicho iris).
Entonces hace falta que lo que la
cámara no puede hacer (compensar
la ganancia para que no se vea
oscuro), lo aportemos nosotros con
suficiente luz. Con una lámparita de
40 W alcanza.
Con respecto a lo del modo nocturno,
no sé si el controlador de V4L lo tiene.
Saludos.

---

### Post by jpoeta on 2009-07-01
He instalado todo lo V4L con el synaptic, pero como uso el V4l y qué es en realidad.
Gracias por la ilustración 
Jpoeta:guitar:

---

### Post by pablo.s on 2009-07-01
[V4L]("http://es.wikipedia.org/wiki/Video4Linux") significa Video for Linux.
Se encarga de manejar las 
entradas de video y si ya lo
tenés instalado y además
funciona la webcam, quiere
decir que está todo OK,
excepto por el tema de la
iluminación.
Saludos.

---

