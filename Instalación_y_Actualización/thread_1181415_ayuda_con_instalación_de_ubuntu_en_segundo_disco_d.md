---
title: "ayuda con instalación de ubuntu en segundo disco duro"
date: 2009-06-07
forum: Instalación y Actualización
---

### Post by rogonzab on 2009-06-07
hola, soy nuevo en esta comunidad y me gustaría pedirles ayuda con un problema.

Sucede que me conseguí un segundo disco duro para mi pc y quisiera instalar en él Ubuntu, porque hasta el momento tenía instalado xp y a través de wubi Ubuntu. No podía hacer la migración completa porque por motivos de trabajao en mi casa es necesaria una version de xp completamente funcional. Pero ahora quisiera ocupar este segundo disco duro instalando Ubuntu con todas las de la ley, pero me atasco en no saber bien como hacerlo. He leido en internet, pero nunca he encontrado algo que sea simple y consiso, es decir la instalación más básica que sea posible de Ubuntu en un segundo disco duro, ya que no soy ningún experto en eso de partir el disco y cosas así. 

Si me pueden ayudar se los agradecería infinitamente.

Gracias.

---

### Post by Carlos C on 2009-06-07
Te sugiero que mires esta página:

[http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro](http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro)

si no entiendes algo preguntas, pero será mucho más productivo para ti si lees esa página antes de preguntar.

Saludos.

---

### Post by rogonzab on 2009-06-08
> **Carlos C said:**
> Te sugiero que mires esta página:

[http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro](http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro)

si no entiendes algo preguntas, pero será mucho más productivo para ti si lees esa página antes de preguntar.

Saludos.


muchas gracias por la guia, me dejó más claro algunas cosas (p.e: la swap) pero sigo sin tener completamente claro ( o al menos lo suficientemente claro como para decidirme a hacerlo) como debo hacer para instalar ubuntu en mi segundo disco duro. La gran pregunta es ¿qué pasa cuando meto el cd de ubuntu? ¿le pongo instalar? pero ¿cómo puedo diferenciar en que disco tengo windows y en cual nada?

---

### Post by shellyanne on 2009-06-08
i wish i could read this :(

---

### Post by gmunioz on 2009-06-08
Hola rog....:

1- Inicia el ordenador con el cd de Ubuntu en la lectora.

2- En el menu elige instalar.

3- Cuando llegues a particionamiento elige manual.

4- Selecciona el segundo disco duro, seguramente /dev/sdb

5- Crea las siguientes particiones:

a- Una primaria, activa, sistema de archivos ext4, de 14 gigas,

punto de montaje /

b- Una lógica, sistema de archivos intercambio, de 1 giga, montaje por 

defecto (swap)

c- Una lógica, del resto disponible en el disco, sistema de archivos ext4

punto de montaje /home

Acepta los cambios, aplica.

Al finalizar el Grub se instalará por defecto en el mbr del primer disco,

con opción para otros operativos.

Saludos.

**Solo doy soporte para Ubuntu - 22 - mad karmic & gnome-shell user**

---

### Post by rogonzab on 2009-06-08
> **gmunioz said:**
> Hola rog....:

1- Inicia el ordenador con el cd de Ubuntu en la lectora.

2- En el menu elige instalar.

3- Cuando llegues a particionamiento elige manual.

4- Selecciona el segundo disco duro, seguramente /dev/sdb

5- Crea las siguientes particiones:

a- Una primaria, activa, sistema de archivos ext4, de 14 gigas,

punto de montaje /

b- Una lógica, sistema de archivos intercambio, de giga, montaje por 

defecto (swap)

c- Una lógica, del resto disponible en el disco, sistema de archivos ext4

punto de montaje /home

Acepta los cambios, aplica.

Al finalizar el Grub se instalará por defecto en el mbr del primer disco,

con opción para otros operativos.

Saludos.

**Solo doy soporte para Ubuntu - 22 - mad karmic & gnome-shell user**


Infinitas gracias. Voy a probar esa técnica  te cuento como me fue.

---

