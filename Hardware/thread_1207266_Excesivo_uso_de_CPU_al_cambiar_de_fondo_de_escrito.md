---
title: "Excesivo uso de CPU al cambiar de fondo de escritorio"
date: 2009-07-08
forum: Hardware
---

### Post by Sortega on 2009-07-08
Saludos ubunteros, primero que nada pido disculpas si este tema no va aca pero tengo el siguiente problema. 
Tengo Ubuntu 9.04 en un notebook Acer Aspire 3690 con Intel GMA 950 corriendo con Compiz, el problema es que cuando quiero cambiar de fondo de escritorio el consumo de CPU llega al 100% y se demora en cambiar el fondo, y mas aun el sistema responde lento por algunos segundos despues de cambiado el fondo.

Probe con metacity y lo mismo, estoy usando el driver de Intrepid.

¿Alguien tiene algun problema similar?

Saludos

---

### Post by Carlos C on 2009-09-07
Hola, revisando el foro di con este thread. ¿Continuas teniendo este problema? ¿Es el único problema de desempeño que demuestra la tarjeta?
Saludos.

---

### Post by AlexDDR on 2009-09-07
a mi me pasaba con una tarjeta radeon 7000, al cambiar el fopndo de pantalla iba a muy lento( como 2 cuadros por segundo), cuando es una transicion suave osea un crossfade de las imagenes, hasta donde se era debido al mal soporte de opengl o malos driver (culpa de ATI) de la tarjeta, ya que no psoporta opengl 2.X, tambien se que la GMA 950 soporta opengl 1.4, pero no pense que le ocurria el mismo problema

el problema tambien es apreciable en las transiciones de xbox media center XBMC, lo que me sigue confirmando que es un problema de opengl, pero no tengo los conocimiento para asegurarlo

Con unas nvidia serie  8 y 9 no tengo problemas y con la integrada intel x3100 tampoco, por lo que creo que es el soporte de opengl inferior a la  version 2

talvez alguien me lo pueda confirmar o desmentir lo que digo, pero si no le pasa a las gma950 lo que describe el usuario, debe ser problema de drivers y deberia si esta usando jAunty ver el post de intel y jaunty de aui mismo en el foro

[http://ubuntuforums.org/showthread.php?t=1166388](http://ubuntuforums.org/showthread.php?t=1166388)

saludos

---

### Post by Sortega on 2010-01-03
Actualmente estoy usando Karmic Koala con el mismo notebook, aun hay un leve consumo de CPU pero mucho menor al que tenia en Jaunty, cuando usaba Jaunty recuerdo que estaba el problema con UXA en Intel y recurria a usar la configuracion de Intrepid.
Al no usar actualmente Jaunty no se si este error al cambiar el fondo de escritorio estara solucionado.

Saludos

---

### Post by moreback on 2010-01-04
Que responda lento puede ser que el núcleo se puso a hacer paginación de la memoria a disco y eso es algo que hace que el pc se cuelgue por segundos. ¿Cómo andamos de RAM? ¿Cuánta tienes disponible? Si estás cerca de lo que tienes instalado físicamente entonces creo que deberías pensar en ampliarla.

Saludos.

---

### Post by AlexDDR on 2010-01-04
yo no creo que se deba a la memoria RAM, ya que en el computadr que me pasaba tenia un GIGA de ram, y en karmic mejoro ese punto, pero la mejora vino porque ya no tienen efecto fade al cambiar el papel tapiz, sino que cambia mas rapido y consume menos cpu en mi caso tambien.

y como tengo una tarjeta de video nvidia y esta otra ati 7000 (driver libre) con que pasaba, asumo que va mas relacionado con los drivers y su calidad.

saludos

---

### Post by moreback on 2010-01-04
En todo caso AlexDDR, le pregunta a [Sortega]("http://ubuntuforums.org/member.php?u=838530") :-P ya que tiene una Intel y el driver es bastante bueno.

Saludos.

---

### Post by Sortega on 2010-01-04
Tengo en el notebook 1 giga de ram, mediante 2 de 512 mb. Cuando cambiaba de fondo de escritorio siempre me fijaba en el uso de CPU y en memoria, CPU era el que se iva por las nubes la memoria aumentaba levemente el cache pero nada mas.

Saludos

---

### Post by AlexDDR on 2010-01-04
sip , porque el driver intel dio muchos dolores de cabeza en jaunty por los cambios agresivos en su desarrollo que no compatibilizaban con el kernel de jaunty y la incorporacionde varias tecnologias

ahora la cosa anda bien  de nuevo sin ningun esfuerzo extra de configuracion de EXAs  o UXAs ni kernels

---

### Post by moreback on 2010-01-04
De hecho ahora es UXA por defecto, pero que creo que unos modelos quedaron fuera, pero no parece ser este el caso.

En todo caso en estos tiempos 1GB de RAM es bastante poco.

Saludos.

---

