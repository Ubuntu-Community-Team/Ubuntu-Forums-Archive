---
title: "Profundidad de colores"
date: 2009-01-25
forum: Hardware
---

### Post by JUTGtgRB7z on 2009-01-25
Hola a todos, soy nuevo en GNU/Linux, por consecuencia en Ubuntu y en el foro.:p Vayamos al problema, a la hora de configurar mi placa de video (GeForce 8400 GS) el controlador (versión 177) no me deja elegir una profundidad de 32 bits de colores, lo máximo que soporta es 24 bits. Tengo Ubuntu x64 Intrepid ¿Esto es algo que se puede resolver o es algo congénito del sistema? Es importante para mí una mayor profundidad ya que manipulo imágenes usualmente. Espero puedan ayudarme, gracias.

---

### Post by guillermolisi on 2009-01-25
> **pmzerdan said:**
> Hola a todos, soy nuevo en GNU/Linux, por consecuencia en Ubuntu y en el foro.:p Vayamos al problema, a la hora de configurar mi placa de video (GeForce 8400 GS) el controlador (versión 177) no me deja elegir una profundidad de 32 bits de colores, lo máximo que soporta es 24 bits. Tengo Ubuntu x64 Intrepid ¿Esto es algo que se puede resolver o es algo congénito del sistema? Es importante para mí una mayor profundidad ya que manipulo imágenes usualmente. Espero puedan ayudarme, gracias.
La profundidad maxima de colores existente real es 24 bits. Los 32 se logran agregando lo que se llama canal Alfa a los 24 existentes.

O sea que en Linux, la maxima profundidad de colores es de 24 y tenes canal Alfa incluido (para transparencias y otros efectos).

Para mas informacion te sugiero veas, por ejemplo, este link que no necesariamente es ley pero sirve para orientarse.

[http://www.guia-ubuntu.org/index.php?title=Cambiar_la_profundidad_de_color](http://www.guia-ubuntu.org/index.php?title=Cambiar_la_profundidad_de_color)

---

### Post by staar on 2009-01-25
epa, un uimpero como yo :D :D ;), bueno te cuento, en realidad lo de los 32 bits de profundidad de color de windos es un mito, en realidad son 24 bits que corresponden al color y 8 bits que corresponden al alpha o trasparencias, pero, por alguna razon, windos lo suma, en cambio linux toma la profundidad de color (24 bits) y a la trasparencia la trata como una propiedad o una caracteristica

[http://en.wikipedia.org/wiki/Color_depth#32-bit_color]("http://en.wikipedia.org/wiki/Color_depth#32-bit_color")

saludos ;)

---

### Post by JUTGtgRB7z on 2009-01-25
> **guillermolisi said:**
> La profundidad maxima de colores existente real es 24 bits. Los 32 se logran agregando lo que se llama canal Alfa a los 24 existentes.

O sea que en Linux, la maxima profundidad de colores es de 24 y tenes canal Alfa incluido (para transparencias y otros efectos).

Para mas informacion te sugiero veas, por ejemplo, este link que no necesariamente es ley pero sirve para orientarse.

[http://www.guia-ubuntu.org/index.php?title=Cambiar_la_profundidad_de_color](http://www.guia-ubuntu.org/index.php?title=Cambiar_la_profundidad_de_color)

Ni siquiera tuve que leer el link, gracias por la pronta respuesta.;)

---

