---
title: "problemas con los rigidos"
date: 2009-07-07
forum: Hardware
---

### Post by totaharry on 2009-07-07
tengo este problema cuando instalo la 9.04 me sale una pantalla y tarda mucho en cargar aclaro que antes no me pasaba la foto es con la 8.10 y con kubuntu tambien pasa sera el mother?

---

### Post by staar on 2009-07-07
muy probablemente sea el mother y algún bug del kernel, probá apretando F6 y añadiendo all_generic_ide a la línea de booteo del kernel...

saludos

---

### Post by guillermolisi on 2009-07-07
Fijate si en el BIOS esta habilitada la opcion de Delay para que comiencen a funcionar los discos.

Algunas placas, como Intel, solian tener esta funcionalidad como una opcion.

Esto lo digo porque el mensaje que mostras dice DRDY y luego habla de un Time Out. DRDY podria ser Driver Delay y eso podria causar el Tien Out al momento en que el SO quiere acceder al disco.

---

### Post by totaharry on 2009-07-08
mi mother es un ecs geforce6100sm-m le actualice el bios pero nunca me paso antes, un buen dia se me ocurre formatear y me encontre con esta sorpresa, ahora intente instalar vista y se me queda en la instalacion, podra ser la grabadora de dvd ya tiene mas de un año

---

### Post by guillermolisi on 2009-07-08
> **totaharry said:**
> mi mother es un ecs geforce6100sm-m le actualice el bios pero nunca me paso antes, un buen dia se me ocurre formatear y me encontre con esta sorpresa, ahora intente instalar vista y se me queda en la instalacion, podra ser la grabadora de dvd ya tiene mas de un año
Podria ser.

Para confirmar tenes dos opciones, de varias posibles: Probar con otra unidad confiable y/o usar la funcionalidad de prueba de integridad del Live-CD y ver que surge.

Igual mi pregunta anterior no pasaba por si el BIOS estaba actualizado o no sino por ver una funcionalidad que en algunas maquinas existe y en otras no.

---

