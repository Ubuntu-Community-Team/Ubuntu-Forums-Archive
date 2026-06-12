---
title: "Ubuntu solo reconoce 4.5GB's en ram y tengo 5.5GB's"
date: 2009-08-30
forum: Hardware
---

### Post by Fire_C10 on 2009-08-30
HOla! Me instale ubuntu 9.04 x64, tengo aprox. 6GB's de RA, de los cuales la tarjeta ATI me consume 512mb, lo que me da como un total de **5.5GB's** de RAM libre aprox.

El problema radica en que ubuntu solo me reconoce **4.5GB **y el otro 1GB sobrante esta desperdiciado y no se donde quedo xD.

Alguien me puede decir como soluciono este problema?

---

### Post by Hei Ku on 2009-08-30
Que te dice el BIOS del motherboard?

---

### Post by Fire_C10 on 2009-08-30
> **Hei Ku said:**
> Que te dice el BIOS del motherboard?

Me dice que tengo un poco mas de 6gb en ram.

Me diste la idea de reiniciar la configuración de la bios y resulto que ahora me reconoce 5.3GB's de RAM, tambien baje el overclock. Ahora esta mas aceptable, pero mi pregunta es donde quedan los 256MB,¿Que acaso se lo reserva el Kernel de Linux?.

---

### Post by guillermolisi on 2009-08-30
> **Fire_C10 said:**
> Me dice que tengo un poco mas de 6gb en ram.

Me diste la idea de reiniciar la configuración de la bios y resulto que ahora me reconoce 5.3GB's de RAM, tambien baje el overclock. Ahora esta mas aceptable, pero mi pregunta es donde quedan los 256MB,¿Que acaso se lo reserva el Kernel de Linux?.
Con reiniciar la configuracion del BIOS te referis a volverla a los valores de fabrica, los optimos (segun su fabricante), a otro estado que este considerado dentro de las posibilidades de ese BIOS ?

Tomaste nota de como estaba configurado antes ?

De que hardware estamos hablando (marca. modelo, tecnologia, etc.) ?

---

### Post by Fire_C10 on 2009-09-05
> **guillermolisi said:**
> Con reiniciar la configuracion del BIOS te referis a volverla a los valores de fabrica, los optimos (segun su fabricante), a otro estado que este considerado dentro de las posibilidades de ese BIOS ?

Tomaste nota de como estaba configurado antes ?

De que hardware estamos hablando (marca. modelo, tecnologia, etc.) ?


No tome nota de como estaba configurado antes xD, solamente volvi a la configuracion de fabrica. Mi placa madre es una ASUS M3A78 PRO.
[B]
Aqui una imagen de la memoria que me marca el Bios:[/B]

[IMG]http://img2.pict.com/8f/a9/b7/1575092/0/320/imagen041.jpg[/IMG]

---

### Post by Mister X on 2009-09-05
hay direcciones de memoria por encima de los 3GB que son usados para direccionamiento de dispositivos, osea la memoria en sí está libre, pero no es aprovechable, te puede estar pasando esto
hay varias aproximaciones para resolver el problema, cada una con sus desventajas, es un tema algo complicado...

no sé mucho mas porque solo tengo 2GB :)

---

### Post by juancarlospaco on 2009-09-05
Una de dos, 
o no es de 64Bit el SO, Mother, micro;
o la placa de video no tiene la ram integrada en la placa y te come RAM de la PC.

---

