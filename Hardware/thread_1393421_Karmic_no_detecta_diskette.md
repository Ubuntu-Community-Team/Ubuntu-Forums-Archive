---
title: "Karmic no detecta diskette"
date: 2010-01-29
forum: Hardware
---

### Post by prostata on 2010-01-29
No hay forma de que karmic me detecte el dipositivo de diskette, ni con la utilidad de discos. Tengo algunos de ellos muy antiguos y quisiera ver que hay dentro o formatearlos...¿qué puedo hacer..??

Saludos

---

### Post by rojojuan on 2010-01-29
> **prostata said:**
> No hay forma de que karmic me detecte el dipositivo de diskette, ni con la utilidad de discos. Tengo algunos de ellos muy antiguos y quisiera ver que hay dentro o formatearlos...¿qué puedo hacer..??

Saludos

A mi me funcionó creando un archivo bash, lo coloqué en el escritorio y desde allí monto la disquetera sin problemas.
No se si es lo técnicamente corresponde hacer pero funciona.
El contenido del script:
#!/bin/bash          
          mount /dev/fd0

---

### Post by mama21mama on 2010-01-29
[En mi blog]("http://mamalibre.eshost.com.ar/?q=content/floppy-en-ubuntu") hice una pequeña guia de mtool

Fijate si esta limpia las cabezas, proba pasarle un disquete limpiador, o si no tienes con una gamuza con 50% agua %50 alcohol; ojo no me hago responsable de la ultima liempieza, eso queda bajo tu responsabilidad.
Yo te recomendaría el disquete limpiador pero si sos precavido y no mojas tanto la franela eso ultimo te serviría.

---

