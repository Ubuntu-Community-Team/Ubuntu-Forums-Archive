---
title: "Problema en instalación UBUNTU netbook."
date: 2010-12-16
forum: Instalación y Actualización
---

### Post by iKultrun on 2010-12-16
Hola!

Soy nuevo en el foro, pues conocí UBUNTU hace unas semanas. Un amigo mio instaló ubuntu en su netbook, pues windows lo tenía harto. A mi me ha pasado lo mismo, ya no soporto windows en ningún aspecto.

Revisando y leyendo cosas sobre UBUNTU versión netbook he decidido instalarlo en mi netbook aspire one con 2gb ram, 250 gb HDD, procesador intel atp, N450 (1.66 ghz, 512 cache).

Sin embargo logré realizar solo los primeros pasos que son armar en USB con el instalador de UBUNTU, y luego arreglar la BIOS para que logré arrancar el instalador. Luego me encontré con el problema de las particiones, pues seguí esta guia: [http://sliceoflinux.com/2010/10/10/instalar-ubuntu-10-10-paso-a-paso/](http://sliceoflinux.com/2010/10/10/instalar-ubuntu-10-10-paso-a-paso/)

Lo que me ocurrió es que al elegir la opción "Especificar particiones manualmente" noté que ya existian 3 particiones en mi netbook (que vendrían de fabrica).
La primera partición tenía unos 100 MB. La segunda algo así como 20 gigas y la tercera como 190.

¿Que hago? Yo quiero conservar Windows quizás con unos 50gb, y lo demás Ubuntu. Que paso debo seguir?

Mi otra duda consiste en que partición quedaría almacenada mi musica, fotos, trabajo, etc. Podré acceder a ese contenido desde cualquier particion?

Gracias por ayudar a un hueon que no cacha nada.. o muy poco! ajajaj

---

### Post by iKultrun on 2010-12-16
[IMG]http://img692.imageshack.us/i/2foto0020.jpg/[/IMG]

Esa es la imagen de las 3 particiones. Que tengo que hacer ahora? H

---

### Post by moreback on 2010-12-16
Creo que la clave está en achicar una partición de Windows a 50GiB como quieres, luego del espacio libre hacer una partición de swap de unos 4GiB (el doble de tu RAM) y el resto podría ser para montar el / de Ubuntu.

Ahora podrías explicarnos más que tienes en esas particiones, para poder decirte si las puedes borrar o no.

Saludos.

---

### Post by iKultrun on 2010-12-17
Si es que realmente no se que hay en cada partición. Como te digo no cacho mucho de computación... ¿Como puedo ver eso?

Es que realmente Windows me falla a cada rato y quiero cambiar a Ubuntu de apoco.

---

### Post by iKultrun on 2010-12-17
> **moreback said:**
> Creo que la clave está en achicar una partición de Windows a 50GiB como quieres, luego del espacio libre hacer una partición de swap de unos 4GiB (el doble de tu RAM) y el resto podría ser para montar el / de Ubuntu.

Ahora podrías explicarnos más que tienes en esas particiones, para poder decirte si las puedes borrar o no.

Saludos.

Y de cuanto dejo la partición home?

---

### Post by moreback on 2010-12-17
Uff esa es una pregunta muy difícil de contestar, el espacio dependerá del uso que le des a tu Ubuntu. Si te pasas finalmente de seguro unos 100GiB te serían buenos, pero si no lo vas a usar tanto no es necesario tanto espacio, 20GiB podrían estar Ok y mantienes los archivos de música y películas [COLOR=White]porno[/COLOR] en otra partición con NTFS de intercambio.

Saludos.

---

### Post by iKultrun on 2010-12-18
> **moreback said:**
> Uff esa es una pregunta muy difícil de contestar, el espacio dependerá del uso que le des a tu Ubuntu. Si te pasas finalmente de seguro unos 100GiB te serían buenos, pero si no lo vas a usar tanto no es necesario tanto espacio, 20GiB podrían estar Ok y mantienes los archivos de música y películas [COLOR=White]porno[/COLOR] en otra partición con NTFS de intercambio.

Saludos.

Muchas gracias!
Pero disculpa lo chano en computación... Pero el uso de mi computador es para escuchar musica (almaceno unos 80-100 gigas de musica) más archivos de oficina (clases, apuntes, trabajos). Super basico en verdad, sin embargo no se el espacio que debo darle a cada partición y además que hago con las 3 particiones que actualmente tengo!

sorry lo hincha weas!

---

### Post by iKultrun on 2010-12-18
Ahora intenté hacer las particiones, tenía ya todo "definido" y el instalador de linux no me permitió re dimensionar el espacio de la partición grande. Me sorprendí e intente con Gparted, sin embargo Gparted me señalo este error:

*warning: the disk has bad sector. This means physical damage on the disk surface caused by deterioration, manufacturing faults or other reason. The reliability of the disk may stay stable or degrade fast. We suggest making a full backup urgently by running 'ntfsclone --rescue... 'then run 'chkdsk /f/r' on windows and reboot it twice! Then yoy can resize ntfs safely by aditionally using the bad sectors options of ntfs resize.*

Intenté hacer lo que me sugirió, realizando los pasos en el CMD pero me dijo de inmediato que no tenía permisos suficientes y que tenia que estar en un modo más elevado. Realmente ya no se que hacer con el tema!

Gracias de todas formas!

---

