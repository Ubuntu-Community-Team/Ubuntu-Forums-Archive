---
title: "Al iniciar 'The system is running in low-graphics mode'"
date: 2013-04-21
forum: Hardware
---

### Post by matutegomez on 2013-04-21
Les hago una consulta, al prender la PC me aparece este cartel: 'The  system is running in low-graphics mode'. Ya probe todas las opciones que  te tira y no pude hacerlo arrancar. Probe bootear desde el cd de ubuntu  y lo reinstale, pero sigue lo mismo. Ahora estoy desde 'probar ubuntu'.  Me tiene mal este problemita, si me puden dar una mano se los  agradeceria. El disco de la pc esta casi lleno, y ayer instale un par de  actualizaciones, eso es lo unico que puede haber fallado creo yo. Gracias, saludos!

---

### Post by guillermolisi on 2013-04-22
Por favor, danos detalles sobre los componentes de tu PC y/o marca y modelo. Particularmente la placa de video y, si fuera posible, el chipset.

---

### Post by matutegomez on 2013-04-22
antes que nada, gracias por la respuesta. los componentes no los se excatamente, la compre hace unos meses en una casa de computacion que arma. esto es lo que me sale en los detalles: AMD Phenom(tm) II X4 850 Processor × 4. que yo recuerde tiene 500 gb de disco rigido y 4 gb de memoria ram. la placa de video creo que es on-board. te podria llamar por telefono? porque me tiene mal esto, necesito algunos archivos de la pc para laburar. saludos!

---

### Post by guillermolisi on 2013-04-24
Lamentablemente sin mayores detalles sobre el hardware de video que estas usando se hace practicamente imposible poder diagnosticar el problema e intentar una solucion.

---

### Post by matutegomez on 2013-04-24
en donde me puedo fijar lo que necesitas saber? te mande un mp. gracias, saludos!

---

### Post by guillermolisi on 2013-04-24
En una consola/terminal ingresa ```
sudo lspci
```te pedira una clave que es la misma que la de tu usuario y cuando la escribas no veras ningun efecto en pantalla por cuestiones de seguridad, asi que escribila tranquilo asi no te equivocas.

La salida de este comando la pegas en un nuevo post, en este thread.

Luego ingresas ```
sudo lshw
``` y tambien copias y pegas la salida (que sera sustancialmente mas larga que la primera).

Entre los dos resultados tendremos una radiografia del hardware de tu PC.

---

