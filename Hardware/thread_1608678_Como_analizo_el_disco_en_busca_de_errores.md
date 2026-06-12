---
title: "Como analizo el disco en busca de errores?"
date: 2010-10-29
forum: Hardware
---

### Post by Gpafundi on 2010-10-29
Buenas, tengo una PC portatil a la cual necesito hacerle un chequeo por errores. Algo asi como el CHKDISK de windows. ¿Cómo podría hacer eso mismo pero desde el livecd de Ubuntu 10.10?

---

### Post by guillermolisi on 2010-10-29
El equivalente al CHKDSK es fsck y hay que correrlo desde una terminal/consola sobre el disco sin montar, por ejemplo usando un LiveCD.

Tiene varias opciones que dependen del objetivo del analisis. Para una referencia rapida podes verlas ingresando "man fsck" en consola/terminal y luego decidir cuales son las mas adecuadas a tus propositos.

---

