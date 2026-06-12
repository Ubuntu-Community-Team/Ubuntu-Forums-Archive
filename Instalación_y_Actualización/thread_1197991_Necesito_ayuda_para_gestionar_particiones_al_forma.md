---
title: "Necesito ayuda para gestionar particiones al formatear."
date: 2009-06-26
forum: Instalación y Actualización
---

### Post by Ogroberto on 2009-06-26
Hola muchachos he instalado Ubuntu 8.10 varias veces en distintos equipos, pero jamás lo hice en modo manual.

El asunto es que no sé cómo hacerlo, no sé configurarlas ni editarlas.

Decidí hacerlo en modo manual, ya que hice una partición para establecer un espacio de 20GB para poner el contenido del CD. Pero me imaginaba que con el mismo sistema de formateo no iba a tener problemas la próxima vez que necesite reinstalar el sistema en mi laptop. Aunque para mi sorpresa me pedía una nueva partición y no hay manera de que use la partición anterior para lo que la usé anteriormente.

Leí y me enteré de que sólo puedo utilizar la partición que creé con el gestor gráfico de Ubuntu para instalación de SO, si es que la reinstalo de modo manual.

Miren acá están mis imágenes para que vean las particiones, para que me puedan informar acerca de cómo lo puedo hacer en la configuración y formateo de cada una.

Ésto es lo que me sale en Sistema>Administración>Editor de Particiones:
[http://www.imagechile.net/vista.php?id=img5_1246064655i.jpg](http://www.imagechile.net/vista.php?id=img5_1246064655i.jpg)

Y ésto es lo que me sale en Gestor de Instalación:
[http://www.imagechile.net/vista.php?id=img4_1246067096v.jpg](http://www.imagechile.net/vista.php?id=img4_1246067096v.jpg)

Y en Manual:
[http://www.imagechile.net/vista.php?id=img4_1246067183d.jpg](http://www.imagechile.net/vista.php?id=img4_1246067183d.jpg)

Desde ya les agradezco amigos, por favor ayúdeneme.

---

### Post by gmunioz on 2009-06-26
Hola ogro...:

Marcas manual.

Eliges que quieres hacer:

Editar: Indicas sistema de archivos y punto de montaje, si cambias

de sistema de archivos te formateará la partición

Borrar: para luego crear otras.

Por como tienes el sistema, aparentemente 

/dev/sda1 es /, en general conviene formatear

/dev/sda6 es /home, si quieres conservar tus configuraciones

no la formatees

/dev/sda5 y /dev/sda7 son swaps, deberias eliminarlas y crear 

una nueva con el espacio de ambas

**Edito: 11 gigas de swap es un desperdicio, con solo 1 giga es suficiente.**

Trabaja con tranquilidad, pues hasta que no confirmes los cambios

no se producira ninguna alteración de las particiones existentes.

---

### Post by diegogto on 2009-06-26
Si quieres instalar ubuntu en el de 20 GB, haz lo siguiente:
En la misma parte de la imagen 3 (preparar el disco en forma manual) haz clic en "formatear" y si no mal recuerdo te preguntará el punto de montaje, tienes que ponerle "/" (le estarás indicando que a esta partición instalarás ubuntu).

si no resulta eso, borra la partición de 20 GB y crea una nueva partición, indicándole que el punto de montaje es "/"

Los 2 swaps los puedes juntar para hacer un sólo swap (borras ambas particiones y creas una cuyo "punto de montaje es swap)

Así de sencillo.

Cuéntanos como te va. Saludos!

---

### Post by radixs on 2009-06-27
> **Ogroberto said:**
> 
Desde ya les downgrade amigos, por favor ayúdeneme.


Men nos están difícil como piensas, tampoco es por ser pesado pero en web hay una gran cantidad de manuales e informacion al respecto....

Pero bueno!
Echa una miradita [***"AQUI"***]("http://opcionlibre.wordpress.com/%C2%BFcomo-instalar-ubuntu/") y ve como te va ;), suerte!!!

---

