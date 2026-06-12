---
title: "Montar disquetera como usuario"
date: 2009-11-18
forum: Hardware
---

### Post by rojojuan on 2009-11-18
En Karmic tengo problemas para montar la disquetera. Puedo hacerlo como sudo sin problemas. 
Le cambié los permisos en /dev/fd0 y en media/flopyy0 (777), pero a pesar de esto cuando trato de montarla me dice que “no se pudo montar el lugar, no hay ningún soporte en la unidad.”
Alguna idea para solucionar esto?

---

### Post by rojojuan on 2009-11-20
Luego de los cambios de permisos, desde la consola toda anda bien. Al montar la disquetera en consola como usuario luego en Nautilus puedo desmontarla sin problemas.
La única cuestión que queda es que cuando se inicia Karmic e inmediatamente Nautilus, no aparece la disquetera y no se puede montar desde Nautilus, tengo que hacerlo desde la consola. Los discos rígidos aparecen sin inconvenientes.
Así me parece que es un problema de Nautilus. A alguien le pasa esto en Karmic?

---

### Post by aledruetta on 2009-11-20
> **rojojuan said:**
> En Karmic tengo problemas para montar la disquetera. Puedo hacerlo como sudo sin problemas. 
Le cambié los permisos en /dev/fd0 y en media/flopyy0 (777), pero a pesar de esto cuando trato de montarla me dice que “no se pudo montar el lugar, no hay ningún soporte en la unidad.”
Alguna idea para solucionar esto?

Disculpame que no te pueda ayudar, era sólo para preguntar ¿para qué se usa una disketera hoy día?

---

### Post by rojojuan on 2009-11-20
> **aledruetta said:**
> Disculpame que no te pueda ayudar, era sólo para preguntar ¿para qué se usa una disketera hoy día?

Te comento mi caso particular. Tengo tres PC ubicadas en distintos lugares. Dos de ellas no tienen puerto usb y necesito trasladar constantemente información en archivos de texto y poder trabajar con ella en cada uno de esos lugares. Los archivos son de tamaño reducido. Y este sistema me funciona muy bien.
Desconozco otras funcionalidades para disqueteras pero puedo imaginarme situaciones similares.

---

### Post by aledruetta on 2009-11-21
Entendí, gracias por la respuesta.

Ojalá que alguien te tire un dato para resolver el asunto.

Saludos.

---

### Post by rojojuan on 2009-11-24
Por si a alguien le sirve solucioné el problema creando un archivo bash, lo coloqué en el escritorio y desde allí monto la disquetera sin problemas.
No se si es lo técnicamente corresponde hacer pero funciona.

---

