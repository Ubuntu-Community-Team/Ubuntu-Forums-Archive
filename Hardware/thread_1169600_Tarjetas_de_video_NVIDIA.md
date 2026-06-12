---
title: "Tarjetas de video NVIDIA"
date: 2009-05-25
forum: Hardware
---

### Post by Iced_R on 2009-05-25
Para instalar controladores de tarjetas de video NVIDIA:

Descubrí que funciona mejor el driver de la comunidad de Ubuntu. Ese lo seleccionas desde los controladores privativos (si no me equivoco, Sistema > Administración > Controladores de Hardware). Instalas la versión que el sistema te recomienda y Ubuntu se encarga del resto. Simple, fácil, y con un par de clicks XDD. 

Ahora, si quieres instalar el de la página oficial (para usar en otro sistema, como puede ser Fedora) necesitas los compiladores del sistema (en Debian me pasó que faltaron cosas como el make o el build-essential, pero en Ubuntu vienen por defecto). 

1.- **sudo /etc/init.d/gdm stop** para detener el Gnome Display Manager. Si usas KDE, cambia **gdm** por **kdm** que es el KDE Display Manager 

2.- Ejecutar el archivo (que debería ser un .run) por consola. Como la orden anterior mata los procesos gráficos, ves simplemente una consola a full screen xDDD. Para ejecutarlo, te posicionas en el directorio donde está el archivo (Escritorio? en donde esté XD) y lo ejecutas con **sudo sh archivo.run** 

3.- Windows mode: Amén+Aceptar+Siguiente xD 

4.- Levantar el modo gráfico de nuevo con **sudo /etc/init.d/gdm start** o si corresponde, kdm por gdm. 

Y eso es todo. Simple, fácil, y hasta bonito XDD.

Saludos.

---

