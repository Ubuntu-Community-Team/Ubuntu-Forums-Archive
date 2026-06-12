---
title: "[SOLVED] Webcam Euro Case 1.3Mpixel SN9C201"
date: 2009-08-16
forum: Hardware
---

### Post by jvgonza on 2009-08-16
Estoy intentando instalar (en Ubuntu 9.04) una Webcam Marca Euro Case de 1.3 megapixel  Modelo Iron.
Al realizar un lsusb detecta lo siguiente:

Bus 001 Device 004: ID 0c45:627b Microdia PC Camera (SN9C201)
Bus 001 Device 002: ID 054c:01bd Sony Corp. MRW62E Multi-Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 1266:6302  
Bus 003 Device 002: ID 15d9:0a33  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Si alguien la ha configurado les agradeceria si pueden pasarme el dato de donde bajar los drivers.

Saludos y Muchas gracias.
Javier

---

### Post by guillermolisi on 2009-08-16
Fijate si [lo que se hablo en este thread]("http://ubuntuforums.org/showthread.php?t=756439&highlight=microdia") sirve para tu caso, tambien sobre chips Microdia.

---

### Post by luks911 on 2009-08-17
> **jvgonza said:**
> Estoy intentando instalar (en Ubuntu 9.04) una Webcam Marca Euro Case de 1.3 megapixel  Modelo Iron.
Al realizar un lsusb detecta lo siguiente:

Bus 001 Device 004: ID 0c45:627b Microdia PC Camera (SN9C201)
Bus 001 Device 002: ID 054c:01bd Sony Corp. MRW62E Multi-Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 1266:6302  
Bus 003 Device 002: ID 15d9:0a33  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Si alguien la ha configurado les agradeceria si pueden pasarme el dato de donde bajar los drivers.

Saludos y Muchas gracias.
Javier
Esa cámara aparece en el listado de las que funcionan con este[0] driver. Acá[1] están las instrucciones para compilarlo e instalarlo, lo hice con una de las càmarasd del listado y funciona bien.
Las instrucciones están bastante claras. Pero cualquier cosa preguntá. 

[0] [http://groups.google.com/group/microdia](http://groups.google.com/group/microdia)
[1] [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

---

### Post by jvgonza on 2009-08-22
> **luks911 said:**
> Esa cámara aparece en el listado de las que funcionan con este[0] driver. Acá[1] están las instrucciones para compilarlo e instalarlo, lo hice con una de las càmarasd del listado y funciona bien.
Las instrucciones están bastante claras. Pero cualquier cosa preguntá. 

[0] [http://groups.google.com/group/microdia](http://groups.google.com/group/microdia)
[1] [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)



Gracias a tus indicaciones pude reconocer la webcam en mi ubuntu 9.04.  El unico tema es que las imagenes se ven en tonos de grises.  Puede ser que sea un tema de configuracion de norma? Si es esto aun no encontre de donde cambiarlo.

Muchisimas gracias.
Javier

---

### Post by luks911 on 2009-08-22
Acá[0] mencionaban el mismo problema. ¿La probaste ejecutando gstreamer-properties y en la opción "Entrada predeterminada" de la pestaña video?
A mí no me pasó pero es un modelo distinto. También bajé el guimicrodia que aparece en el thread del link de arriba pero no logré que cambiara nada de la imagen.
Busqué pero no encontré nada sobre eso, sí otros problemas. Si es un bug del driver, lo que podés hacer es volver a bajarlo y compilarlo esperando que se haya actualizado (es decir desde el paso 1 y luego desde el 4 del instructivo). De todos modos, la última actualización es del 18 de agosto.

[0] [http://ubuntuforums.org/archive/index.php/t-1127093.html](http://ubuntuforums.org/archive/index.php/t-1127093.html)

---

### Post by jvgonza on 2009-08-23
> **luks911 said:**
> Acá[0] mencionaban el mismo problema. ¿La probaste ejecutando gstreamer-properties y en la opción "Entrada predeterminada" de la pestaña video?
A mí no me pasó pero es un modelo distinto. También bajé el guimicrodia que aparece en el thread del link de arriba pero no logré que cambiara nada de la imagen.
Busqué pero no encontré nada sobre eso, sí otros problemas. Si es un bug del driver, lo que podés hacer es volver a bajarlo y compilarlo esperando que se haya actualizado (es decir desde el paso 1 y luego desde el 4 del instructivo). De todos modos, la última actualización es del 18 de agosto.

[0] [http://ubuntuforums.org/archive/index.php/t-1127093.html](http://ubuntuforums.org/archive/index.php/t-1127093.html)


Es raro pero hoy volvi a cargar el driver para probarlo y se ven bien los colores.  Instale el guimicrodia y la imagen cambia al mover los controles.
Es raro pero lo unico que cambio con la prueba inicial (en que se veia en blanco y negro) es que la pc fue reiniciada.
Bueno, sin mucha logica pero mi problema se soluciono.

Desde ya muchas gracias por responder.

Saludos!
Javier

---

