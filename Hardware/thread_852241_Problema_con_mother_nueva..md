---
title: "Problema con mother nueva."
date: 2008-07-07
forum: Hardware
---

### Post by madelaki on 2008-07-07
Hace unos dias nomas cambie la mother y surgio un problema al bootear. Nunca lo hubiera relacionado con la placa madre pero nunca antes habia pasado hasta que la cambie. Veran, cuando HH llego a la Beta desinstale todo (excepto Windows XP), elimine las particiones y lo instale con Wubi (otro soft que queria probar). Todo iba lo mas bien hasta que cambie la mother por una BIOSTAR NF615-M2B. Ahora, al bootear, la PC no me responde cuando presiono una tecla hasta que termine de cargar Windows, asi que no puedo usar el GRUB de Windows (que por cierto funciona sin el mas minimo problema). Es problema de la mother? En ese caso hay alguna solucion?

---

### Post by luchardi on 2008-07-07
Chequeaste que el orden de booteo de los discos sea el mismo que estaba en tu antiguo Motherboard?

Entiendo que GRUB no lo ves ni siquiera que inicia de 0 Guindous, bueno de ser así como yo lo entendí posiblemente sean los discos y el orden de booteo. Sinó disculpas si te entendí mal.

---

### Post by madelaki on 2008-07-07
El problema de que no responda a las teclas es general, no solo del GRUB de Windows (que por cierto lo veo). Hasta que no estoy dentro de Windows, no responde.

---

### Post by luchardi on 2008-07-07
Ehhh... es PS2 o USB el teclado? Si es USB probá diferentes Ports si es PS2 posiblemente esté funcionando mal el mother.

---

### Post by Hei Ku on 2008-07-07
Si el teclado es USB, fijate en el setup del mother que suelen tener un modo Legacy, para que te reconozca el teclado durante el booteo.

---

### Post by Mauro22 on 2008-07-07
O si es inalambrico USB, tenes que habilitar, como dijeron, la controladora USB desde el BIOS

---

### Post by madelaki on 2008-07-07
Por el amor de dios, que es eso de soporte para USB deshabilitado por default? Anyways, lo habilite y funciona a la perfeccion, gracias gente.

---

