---
title: "Paquetes retenidos en Ubuntu 10.04"
date: 2011-04-06
forum: Instalación y Actualización
---

### Post by vladzur on 2011-04-06
Hola, he intentado actualizar los paquetes de ubuntu 10.04 y me aparece el mensaje:

Los siguientes paquetes se han retenido:
  ffmpeg libavdevice52 libavfilter0 libavformat52 libpostproc51 libswscale0
0 actualizados, 0 se instalarán, 0 para eliminar y 6 no actualizados.

¿Alguien sabe por qué se encuentran "retenidos"? y si saben cómo actualizarlos, se los agradecería mucho.

Saludos.

---

### Post by vladzur on 2011-04-06
Lamento ensuciar el foro con mi thread, pero ya encontré la solución

Simplemente 
```
$ sudo aptitude full-upgrade
```El problema de dependencias queda resuelto.

```
Los siguientes paquetes están ROTOS:
  libavcodec-extra-52 libavutil-extra-49 
Se instalarán los siguiente paquetes NUEVOS:
  libavcodec52{a} libavutil49{a} 
Se ELIMINARÁN los siguientes paquetes:
  libboo2.0.9-cil{u} libwebkit1.1-cil{u} podsleuth{u} 
Se actualizarán los siguientes paquetes:
  ffmpeg libavdevice52 libavfilter0 libavformat52 libpostproc51 libswscale0 
6 paquetes actualizados, 2 nuevos instalados, 3 para eliminar y 0 sin actualizar.
Necesito descargar 5594kB de archivos. Después de desempaquetar se usarán 9331kB.
No se satisfacen las dependencias de los siguientes paquetes:
  libavcodec-extra-52: Entra en conflicto: libavcodec52 pero se va a instalar 4:0.5.1-1ubuntu1.1.
  libavutil-extra-49: Entra en conflicto: libavutil49 pero se va a instalar 4:0.5.1-1ubuntu1.1.
Las acciones siguientes resolverán estas dependencias

Eliminar los paquetes siguientes:
libavcodec-extra-52
libavutil-extra-49

La puntuación es -172

¿Acepta esta solución? [Y/n/q/?] y

```Gracias de todas formas.

---

### Post by RafaelG on 2011-04-06
Otro computador libre!

---

