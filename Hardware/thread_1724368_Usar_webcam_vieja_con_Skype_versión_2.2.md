---
title: "Usar webcam vieja con Skype versión 2.2"
date: 2011-04-08
forum: Hardware
---

### Post by rojojuan on 2011-04-08
Comento esta experiencia por si a alguien puede servirle.
Tengo una webcam logitech QuickCam Express, muy vieja.
Estuve usando Skype con: Sistema – Preferencias – Menu Principal – Internet – Skype – Propiedades – Skype-Wrapper
Al actualizar Skype a la versión actual (2.2), aparecida en estos días, me arroja un error, citando que el directorio Skype-wrapper no existe.
Pude solucionar el problema y tener video. 
Consulté con google las posibilidades y encontré la siguiente forma:
Sistema – Preferencias – Menu Principal – Internet – Skype – Propiedades - 
Comando y colocar:      env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

### Post by lserranojaral on 2011-04-08
Yo tengo problema con una webcam VX-3000, no da video, despues de actualizar a skype 2.2.

Intenté tu sugerencia y no funcionó. :(

no sé que hacer.

Gracias de todos modos por el tip.

---

