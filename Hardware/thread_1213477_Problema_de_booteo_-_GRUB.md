---
title: "Problema de booteo - GRUB"
date: 2009-07-14
forum: Hardware
---

### Post by johnny_99 on 2009-07-14
Buenas amigos. Tengo un problema que hasta ahora nadie me pudo ayudar de todas las personas y sitios que consulté.

Yo actualmente tengo Ubuntu 9.04 y Windows XP SP3 en una Acer Aspire 5100 5203.
El problema que me surge es que **a veces** (no pude establacer un patron, creo que sucede "aleatoriamente" por asi decirlo) no me carga el grub. O sea, prendo la pc y se queda la pantalla negra.
Esto empezo a ocurrir cuando una vez deshice la particion que habia creado en el disco, uniendolo nuevamente en uno. Volvi a particionarlo para ver si se solucionaba, reinstale sistemas operativos, hice todo lo que se me ocurrió y sigue pasando.

Podría ser un daño físico del disco?? El hdd regenerator me ayudaría en este caso??
Que podria probar??

Cualquier ayuda se agradece.
Desde ya gracias.
Saludos.

---

### Post by Hei Ku on 2009-07-14
La maquina es nueva o tiene ya un tiempo de uso? Es una laptop o desktop?

Te cuento que a mi me pasa en una Compaq Evo, que si la dejo desenchufada un rato después tarda un par de veces hasta que engancha el GRUB. Eso es porque la pila del BIOS esta agotada, y no toma la configuracion de los discos al iniciar por primera vez.

---

### Post by johnny_99 on 2009-07-14
Buenas, antes que nada te agradezco la rapidez de la respuesta.

La máquina es una laptop y efectivamente la compré usada en el mes de febrero. La maquina originalmente se adquirio en julio del año 2007.

Hay alguna manera de cerciorarme que la pila del BIOS esta agotada??, ya que quiero estar seguro que ese es el problema antes de reemplazarla.

Gracias.

---

### Post by Hei Ku on 2009-07-14
Cuando te pase eso, entra a la configuracion del BIOS y fijate la hora y fecha. En general vuelven al default, 1/1/1980 o algo asi.

---

### Post by johnny_99 on 2009-07-15
Me acabo de fijar y la hora es correcta. Puede que el problema sea que no este tomando el disco cuando bootea, o sea que no lo este reconociendo, si es asi no tendria que bootear y es logico que la pantalla se quede negra con el guioncito blanco titilando, creo yo.

Saludos

---

### Post by Hei Ku on 2009-07-15
Puede ser que no lo este reconociendo automaticamente. Fijate en el BIOS cómo esta configurado, si de forma manual o automatica.

---

### Post by johnny_99 on 2009-07-15
Buenas

No sabria decirte, en el setup no me aparece esa opcion, lo unico que me sale es el orden de booteo, que obviamente tengo al disco primero. Y en otra "pestaña" solo me dice el nombre y un codigo del disco. En ningun lado menciona lo que comentas :(

Saludos

---

