---
title: "Error al iniciar Ubuntu"
date: 2011-02-05
forum: Hardware
---

### Post by elbixo on 2011-02-05
Hola, el otro dia instalé la version 10.10 de Ubuntu y todo iba a la perfeccion. Ahora, no se que ha pasado que cuando selecciono el SO Ubuntu en vez de cargarme la interfaz grafica se me abre la terminal y me pide usuario y contraseña...A partir de ahi puedo moverme, todo por consola, mediante mis archivos pero no entiendo porque se me abre la terminal y no se ni como arreglarlo para que arranque normalmente ni como salir de la terminal. Gracias!

---

### Post by guillermolisi on 2011-02-05
Contanos como es el hardware de tu maquina, principalmente que placa de video estas usando y que monitor.

Esa instalacion esta al dia o aun tenes paquetes por actualizar ?

---

### Post by elbixo on 2011-02-05
Mi ordenador es un portatil con una tarjeta gráfica nVidia Geforeze 310M. Y la pantalla es de 15.3"....

El SO si esta actualizado ya que nada mas instalarlo, como ya dije me funcionaba todo a la perfeccion y lo actualice. Asique no me quedaba nada mas por instalar.

---

### Post by asterix77 on 2011-02-07
Ejecuta en la terminal lo siguiente:

$startx

Con eso inicias el gestor gráfico, pega acá lo que salga. Quizás haya algún error en el arranque del mismo.

Sería bueno que también adjuntaras la salida de lo siguiente:
$lspci | grep VGA

Con eso se tendrán más pistas para ver que problema hay.

Saludos

---

### Post by granjero on 2011-02-07
> El SO si esta actualizado ya que nada mas instalarlo, como ya dije me funcionaba todo a la perfeccion **y lo actualice**. Asique no me quedaba nada mas por instalar.

Por lo que contás este problema surgió luego de una actualización.

Fijate si booteando con la versión anterior del kernel te funciona?

Esto lo hacés cuando muestra el grub.

salud!

---

