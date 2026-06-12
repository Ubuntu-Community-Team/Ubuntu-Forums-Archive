---
title: "chequear rendimuebto de gráficas Nvidia"
date: 2012-10-08
forum: Hardware
---

### Post by EnriqueK on 2012-10-08
Resulta que luego de instalar los últimos controladores para gráficas Nvidia de la serie 304.xx como por ejemplo el x86_64-304.51 al ejecutar glxgears me muestra valores muy bajos o sea me sale esto
300 frames in 5.0 seconds = 59.880 FPS
300 frames in 5.0 seconds = 59.880 FPS
300 frames in 5.0 seconds = 59.881 FPS
En cambio si uso controladores de la serie 295.xx copmo por ejemplo el x86_64-295.75 los valores que me muestra son
50292 frames in 5.0 seconds = 10058.222 FPS
50224 frames in 5.0 seconds = 10044.617 FPS
50188 frames in 5.0 seconds = 10037.481 FPS
O sea la diferencua es mas que notable , es abismal, por eso quisiera saber si hay otra manera para tener una idea del rendimiento de la gráfica que no sea usando glxgears

---

### Post by dirty fingers on 2012-11-29
Estas haciendo mal las cosas...

Cuando se te clava en casi 60FPS es porque tenes activado el sincronismo vertical. Los cuadros por segundo son cada un barrido de pantalla para evitar "tearing".

Si queres comparar rendimiento de ambos controladores tenes que hacerlo en ambos casos con esta opción desactivada.

---

