---
title: "problema instalacion de ubuntu 10.04 con cd alternate"
date: 2010-05-06
forum: Instalación y Actualización
---

### Post by jcartagena on 2010-05-06
Acudo a su sabiduría para resolver un problema que tengo. Comienza la historia: desde hace varios años que uso ubuntu regularmente y sin problemas, ahora quise actualizar desde la version 8.04 a la 10.04, debido a que el cdrom de mi laptop funciona cuando quiere, decidi hacer el upgrading usando la imagen iso de la version alternate de 10.04 como dice en la web de ubuntu ([http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)). Todo iba de maravillas, monte la imagen del disco, fue reconocida y comenzó la actualizacion, pero al final de esta aparece un mensaje que decia: "fail install", yo no la tome mucho en cuenta y cerré esa ventana, luego me apareció otra ventana que me pedia reiniciar el ordenador para que la instalacion terminara, hago eso y en un par de segundos la pantalla se fue a negro, yo veía que el ordenador mostraba actividad, pero la pantalla esta en negro.... luego de varios minutos donde no hubo respuesta, decidi apagar el pc para luego encenderlo..... entonces aparece grub dandome la opcion de arrancar con ubuntu 10.04...... escogo la opcion y me aparece el nuevo logo de ubuntu como si se estuviera cargando, PERO ABAJO DE ESO SALE UN MENSAJE QUE DICE QUE EL HDA4 NO EXISTE O NO ESTA DISPONIBLE...... tan tan...... eso sería todo...... bueno espero que alguien me pueda orientar con una solucion para esto, debido que desde ese dia he tenido que trabajar en windows (el que tengo en otra particion en mi laptop)... ademas mi manejo con linux no es tan avanzado.....

alguna ayuda?????

de antemano muchas gracias

jc

---

### Post by CdK1 on 2010-05-09
En tu lugar intentaría esto:

Reiniciar con un Live CD
Verificar el Sistema de Archivos con fsck
Revisar los kernels instalados (dpkg -l | grep linux-image)
Revisar el Grub (/boot/grub/menu.lst) 
Hacer partir con un kernel antiguo


Luego, JAMAS actualizaría vía CD, es una pérdida de tiempo, bajando el CD e instalando, una verdadera basura..., en su lugar, edito el sources.list y actualizo vía consola..., es más que sabido que la mayoría de usuarios que actualiza vía CD siempre tienen dramas, en fin, espero te sirva...

---

### Post by asterix77 on 2010-05-10
Yo mis últimas 4 versiones, siempre he descargado el live cd, y nunca he tenido dramas, de que no me arranque a la primera. Lo que sí he tenido que hacer, es configurar manualmente algunas cosas, tales como mi acceso a internet, driver de mi tarjeta de video para lograr la resolución deseada, y algunas otras par de cosas.

Nunca lo he hecho a través del gestor de actualizaciones, porque he leido que hay muchos problemas al hacerlo por esta vía.

El método que mencionas sobre editar el sources.list, no lo había escuchado, así es que sería bueno ahondar más en eso, si es que tienes algún link sería bueno que lo pegues, a lo mejor efectivamente tiene más ventajas, sobretodo ahora que me voy a actualizar a lucyd.

Saludos

---

### Post by jcartagena on 2010-05-12
Estimados:

bueno logré solucionar el problema, pero fue de una manera algo grosera.....lo unico que hice fue lograr correr el live cd e instalar sobre lo que había, de hecho no perdí datos ni los usuarios........esop

muchas gracias


jc

---

