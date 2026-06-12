---
title: "ubuntu 12.04 no anda la salida de 2 monitores"
date: 2012-05-28
forum: Hardware
---

### Post by gabak on 2012-05-28
buenas
instale desde cero el ubuntu 12.04 y tengo dos monitores LCD de 19 wide y me tira este error.
tengo una placa ATI basica de 512mb ram una salida dvi y otra vga
alguna idea como se puede solucionar?
Veo en los monitores la misma imagen pero no los puedo separar. 

gracias por adelandado!!


No se pudo aplicar la configuración seleccionada para las pantallas
el tamaño virtual requerido no se ajusta al espacio disponible: requerido=(2720, 768), mínimo=(320, 200), máximo=(1360, 1360)

Y después, cuando acepto este error:

Fallo al aplicar la configuración: %s
GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3: el tamaño virtual requerido no se ajusta al espacio disponible: requerido=(2720, 768), mínimo=(320, 200), máximo=(1360, 1360)



pd: no se porque me aparecen las caritas

---

### Post by gnusci on 2012-05-28
Instala el driver ATI:

[http://ubuntuforums.org/showthread.php?t=1982640](http://ubuntuforums.org/showthread.php?t=1982640)

---

### Post by gabak on 2012-05-28
gracias por tu pronta respuesta.
pero ya lo tengo instalado pero no me muestra la opcion de xinerama para extender el monitor


> **gnusci said:**
> Instala el driver ATI:

[http://ubuntuforums.org/showthread.php?t=1982640](http://ubuntuforums.org/showthread.php?t=1982640)

---

### Post by gnusci on 2012-05-28
Ya intentaste reconfigurando:

$ sudo aticonfig --initial

reinicia.

$ sudo amdcccle

---

### Post by gabak on 2012-05-29
todo funciono de maravillas gracias

---

### Post by evolquez on 2012-10-02
Buenos días, tengo el mismo problema que gabak pero aun no logro resolverlo.

Tengo Ubuntu 12.04.1 instalado y posteriormente tamibien tengo los drivers de vídeo instalado pero al momento de conectar mi monitor LG Flatron w2243s vía VGA no puedo clonarlos ni tampoco reconoce los drivers.

Si alguien puede ayudarme a llegar a la solución se lo agradecería mucho

---

