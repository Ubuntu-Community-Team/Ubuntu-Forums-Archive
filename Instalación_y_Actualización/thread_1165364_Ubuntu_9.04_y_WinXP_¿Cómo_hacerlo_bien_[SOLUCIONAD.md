---
title: "Ubuntu 9.04 y WinXP ¿Cómo hacerlo bien? [SOLUCIONADO]"
date: 2009-05-20
forum: Instalación y Actualización
---

### Post by Matnet on 2009-05-20
Leí este artículo:
[URL="http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro"]
http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro[/URL]

pero no me quedó claro, porque me parece que sugiere instalar Ubuntu y WinXP paralelamente. El problema es que el computador que voy a usar ya tiene un WinXP instalado, y no quiero borrarlo (bueno, yo si, mi familia es la que no quiere)

Estaba pensando en particionar el disco desde windows (con norton partition magic) y luego usar esa partición, pero no sé si GRUB funcionaría así.

Actualmente WinXP usa el disco desde el byte 0, y al ser de 250 GB (con 53.7 GB usados), un despalzamiento de partición será lentiiisiiimoooo

El disco está ahora formateado en NTFS

[[IMG]http://www.knol.cl/thumbs/sshot7.png[/IMG]]("http://www.knol.cl/v_sshot7.png.htm")

y esta es la info. que creo será necesaria.

espero tener una pronta respuesta porque no quiero instalar WUBI o esperar al proximo formateo del WinXP (porque se que lo habrá)

Agradecido de antemano

MatNet

---

### Post by RafaelG on 2009-05-20
hola, bueno te comento que yo soy relativamente nuevo con Ubuntu comenze con el 8.10 y ahora estoy en el 9.04 la verdad no me procupe mucho por las particiones en mi caso particular ya que al descargar ubuntu se graba un CD el cual despues trae todo el OS y unas sencillas instrucciones para las particiones del disco y al encender  te aparece el Grub para elegir que OS quieres iniciar, mi caso es parecido ya que comparto Ubuntu y windows vista, yo le di 30GB a Ubuntu de un disco duro de 160GB lo restante lo deje en Windows Vista y hasta el momento he probado sin ningun problema Ubuntu y puedo decir que  realmente es un OS muy bueno. el Notebook se ha comportado realmente super bien con los dos OS que tengo instalado. Suerte con tu instalacion.;)

---

### Post by Carlos C on 2009-05-20
Matnet, de todas maneras la Guía Ubuntu te sirve. Si te fijas en lo que ahí se indica, primero debes instalar Windows, así que estás listo, ahora debes seguir el resto de los pasos. De hecho te recomiendo que hagas lo siguiente, que es básicamente lo mismo que dicen en la guía ubuntu:


[LIST=1]
[*]Defragmenta tu disco duro desde windows.
[*]Entra a Ubuntu con el LiveCD y modifica su partición de manera que quede el espacio libre en donde instalarás Ubuntu. Me refiero a que encojas la partición liberando espacio al final del disco, no a que desplazes la partición ya que **windows no partirá si no está instalado desde el sector 0**. Para modificar las particiones puedes usar el Editor de Particiones Gparted que viene instalado en el LiveCD. El espacio libre lo puedes dejar sin formato.
[*]Instala Ubuntu desde el LiveCD usando la opción de usar el espacio libre o la opción manual. En caso de usar esta última te recomiendo separes el espacio en tres particiones:
[/LIST]
[INDENT]
[LIST]
[*]Partición uno: de unos 5 a 10 gigas, con sistema de archivos ext3 o ext4, en donde se instalará el sistema, montada en "/".
[*]Partición dos: de un tamaño igual al doble de tu ram, que usarás como área de intercambio, con sistema de archivos linux-swap.
[*]Partición tres: montada en "/home", que usará el resto del espacio libre, destinada a contener todos tus archivos personales. Nuevamente el sistema de archivos puede ser ext3 o ext4.
[/LIST]
[/INDENT]Con eso no perderás windows y Grub te permitirá escoger con qué sistema partir.
Saludos.

---

### Post by Matnet on 2009-05-21
> **Carlos C said:**
> Matnet, de todas maneras la Guía Ubuntu te sirve. Si te fijas en lo que ahí se indica, primero debes instalar Windows, así que estás listo, ahora debes seguir el resto de los pasos. De hecho te recomiendo que hagas lo siguiente, que es básicamente lo mismo que dicen en la guía ubuntu:


[LIST=1]
[*]Defragmenta tu disco duro desde windows.
[*]Entra a Ubuntu con el LiveCD y modifica su partición de manera que quede el espacio libre en donde instalarás Ubuntu. Me refiero a que encojas la partición liberando espacio al final del disco, no a que desplazes la partición ya que **windows no partirá si no está instalado desde el sector 0**. Para modificar las particiones puedes usar el Editor de Particiones Gparted que viene instalado en el LiveCD. El espacio libre lo puedes dejar sin formato.
[*]Instala Ubuntu desde el LiveCD usando la opción de usar el espacio libre o la opción manual. En caso de usar esta última te recomiendo separes el espacio en tres particiones:
[/LIST]
[INDENT]
[LIST]
[*]Partición uno: de unos 5 a 10 gigas, con sistema de archivos ext3 o ext4, en donde se instalará el sistema, montada en "/".
[*]Partición dos: de un tamaño igual al doble de tu ram, que usarás como área de intercambio, con sistema de archivos linux-swap.
[*]Partición tres: montada en "/home", que usará el resto del espacio libre, destinada a contener todos tus archivos personales. Nuevamente el sistema de archivos puede ser ext3 o ext4.
[/LIST]
[/INDENT]Con eso no perderás windows y Grub te permitirá escoger con qué sistema partir.
Saludos.

Muchas gracias, pero todavía tengo una duda: desfragmenté mi disco y encontré que mi archivo de paginación (pagefile.sys) está al final del disco; mi pregunta es: ¿que pasa si elimino la paginación al crear el espacio para ubuntu en este lugar?, y sí no debo borrar el pagefile, ¿puedo moverlo hasta la mitad del disco, aproximadamente? si es así ¿cómo?

nuevamente gracias de antemano

MatNet

---

### Post by vargux on 2009-05-21
Hola... lo único que debes hacer es redimensionar el espacio de la partición de windows.... Y crear las particiones que te mencióno [COLOR=Green]**Carlos C**[/COLOR], en el espacio sobrante.

Alto más, no es recomendable, tener una partición swap de intercambio mayor a 1 Gb, ya que, no es necesaria tanta memoria de intercambio.
Si tienes 2 Gb de memoria RAM, entonces con 1 Gb destinada a la partición de intercambio (swap) es más que suficiente....

Otra cosa, es también recomendable, aunque no estrictamente necesario, tener una partición de datos en windows, separada de la partición del sistema operativo.

Para el sistema windows, más juegos y todo el software a utilizar, con unos 50 Gb, viendo tu disco duro, es más que suficiente (si necesitas más, por si instalas uno 4 juegos [COLOR=Red]*full gráficos*[/COLOR] a la vez, entonces aumentas el tamaño :P).


[I][B] Recapitulando (más mis consejos):
[/B][/I]> 
Partición 1: Sistema Windows: 50 Gb; sistema de archivos NTFS
Partición 2: Datos Windows: 180 Gb; sistema de archivos NTFS ó Fat32
Partición 3: Sistema Ubuntu (montada en la raiz del sistema, la base de todo, *[COLOR=Red]/[/COLOR]*): 10 Gb; sistema de archivos ext3 ó ext4
Partición 4: Intercambio (swap): 1 Gb máximo (siempre el doble de la RAM); sistema de archivos linux-swap
Partición 5: Datos Ubuntu (monstada en el sector *[COLOR=Red]/home[/COLOR]*): 9 Gb; sistema de archivos etx3 o etx4  Esta es una recomendación, pero los valores de tamaño de las particiones pueden modificarse a gusto...


Por otro lado, también se puede instalar Ubuntu sólo creando una partición *[COLOR=Red]/[/COLOR]*, para el sistema operativo, y crear otra partición para la memoria de intercambio.
*Esta es la forma más simple de instalar Ubuntu, o cualquier GNU/Linux.*


Saludos....

Fabián.

---

### Post by moreback on 2009-05-21
Ojo que la swap se utiliza cuando el computador hiberna, por lo que se necesita que tenga un tamaño mayor que la RAM para que toda la info quepa dentro de la swap. Usuarios de notebooks deberían tener esto en cuenta.

Saludos.

---

### Post by CarlosRuiz on 2009-05-21
Holap:

Te recomiendo este Link:
[http://carlosruizortega.wordpress.com/2008/08/04/instalar-windows-y-ubuntu-en-tu-pc/](http://carlosruizortega.wordpress.com/2008/08/04/instalar-windows-y-ubuntu-en-tu-pc/)

Estoy seguro de que te servirá... xD

Saludoooos :P

---

### Post by Matnet on 2009-05-21
De manera bastante curiosa, surgío ahora la necesidad de formatear el computador, y aprovecharé la oportunidad para instalar jaunty

Por si les interesa, recopile sus consejos y me formé una imagen mental del disco:

*Del byte 0 a los 50 GB **Windows XP [C:]** (50GB)
** Archivo de Paginación (pagefile.sys) de 3.71 GB
*De los 50 GB a los 150 GB **Documentos Windows [D:]** (100GB)
*De los 150 GB a los 175 GB **Ubuntu 9.04 [/]** (25GB)
*De los 175 Gb a los 247 GB **Ubuntu Home [/home]** (72GB)
*De los 247 Gb a los 250 Gb **Linux-Swap** (3GB)

Si por alguna razon el espacio se aparece disminuido (lo que me pasa frecuentemente en NTFS, donde muestra 232GB) pienso descontarlos de Documentos Windows

Muchas gracias por su ayuda, este tema va para los solucionados

---

### Post by moreback on 2009-05-21
> **Matnet said:**
> Si por alguna razon el espacio se aparece disminuido (lo que me pasa frecuentemente en NTFS, donde muestra 232GB) pienso descontarlos de Documentos Windows

Ok, vamos de nuevo con lo de [las diferencias entre los GB y los GiB]("http://es.wikipedia.org/wiki/Kibibyte"):

Si tu disco dice que es de **250GB**, entonces debes considerar que esto significa que tiene realmente (saca la calculadora) 250.000.000.000 bytes y entonces comienza a dividir por 1024:

250.000.000.000 bytes = 244.140.625 KiB = 238418,579 MiB = **232,83 GiB**.

Y esto lo explica todo.

Saludos.

---

