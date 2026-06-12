---
title: "HD o SSD"
date: 2010-11-22
forum: Hardware
---

### Post by losoollenos on 2010-11-22
Hola, muy buenos días a tod@s....

Estoy pensando en dejar mi actual disco rígido exclusivamente para almacanamiento, y cargar los sistemas en otro más rápido.
Quería saber qué opinan sobre los SSD; según descripciones, las velocidades de lectura-escritura estaría arriba de 275 mb, aunque en alguna comparación que pude encontrar por la red (no encontré mucho en verdad, tampoco sé dónde averiguar de este tema), lo mejor de SSD anda por los 140 mb, contra un Seagate Cheetah que estaría en los 170 mb lectura-escritura maso.
Justo tengo un amigo que me lo traería de EE.UU; el SSD, vi el Corsair de 128 gb, en 240 dólares, y el Cheetah de 300 gb alrededor de 250.

Consejos, comentarios y sugerencias bienvenidos !!!!

Muchas gracias y hasta pronto

---

### Post by alfplayer on 2010-11-22
Pero que información buscás?

---

### Post by losoollenos on 2010-11-22
Gracias alfplayer por responder,

Bueno yo lo que pude encontrar es un poco contradictorio: las descripciones de los SSD llegan a decir que escriben a más de 275 mb (por lo menos el modelo que comenté), una pregunta sería que tan cierto es ésto, ya que también comenté la comparación que encontré que seguía dando al seagate cheetah como más veloz.
Qué balance hacen ustedes sobre ventajas y desventajas; leí que la vida útil se ve reducida porque siempre escriben el mismo sector, sin embargo aseguran en las descripciones los fabricantes, una duración superior a la del disco tradicional.
Por orto lado se que me faltan conocimientos para comparar más concienzudamente estos elementos, por eso insisto que serán bienvenidas cualquier sugerencia, consejo al respecto.

Muchas gracias

---

### Post by alfplayer on 2010-11-22
También hay que tener en cuenta que algunas velocidades de los SSD disminuyen gradualmente con el uso normal. No soy experto en SSD, pero también podría variar según el sistema de archivos utilizado. El fabricante probablemente siempre informa las velocidades máximas que es cuando todavía no se usó.

Hay muchas reseñas y benchmarks de SSDs en la web.

---

### Post by losoollenos on 2010-11-22
Seguiré buscando entonces.....aparte del videito que compara los tiempos de arranque en el xp, hasta ahora no logro separar la paja del trigo jeje, en cuánto a ventajas-desventajas "reales". La contra que inglés no entiendo.

Saludos y muchas gracias

---

### Post by z37a on 2010-11-22
La gran ganancia de la SSD es el tiempo de acceso, es casi inmediato, mas allá de la velocidad de lectura/escritura, accede al sector del disco enseguida (ya que no es un disco), y ahí se re nota la diferencia!!!!

Ahora la gran contra de la SSD es la vida útil, suelen tener ciclos de lecto-escritura de 100.000 usos, cada bloque tras esa cantidad de usos queda inutilizable (ojo se van quemando de a uno, no todo el SSD entero!!!!), si bien los HDDs tienen un MTB de 10000 horas están muy cerca ahora, y hay algunos SSD de 1.000.000 de ciclos, como también los hay de 10.000!!!!

Consejo trate SSD, pero la SWAP mandala al otro disco! Si no la vida util del mismo baja enseguida.

---

### Post by losoollenos on 2010-11-22
Gracias z37a, lo voy a tener en cuenta !!!!
La swap es necesaria con 4gb de ram?

saludos

---

### Post by guillermolisi on 2010-11-23
Cuando particiones vas a necesitar marcar una particion Swap, asignale 512Mb asi no usas mucho espacio.

4Gb de RAM puede ser mucho o poco, depende del uso que le des a la maquina y el swapping comienza cuando alcanzas cierto porcentaje de uso de RAM, no necesariamente cuando llegas al 100%. Este porcentaje puede ajustarse modificando el valor asignado ([swappiness]("https://help.ubuntu.com/community/SwapFaq"))

---

### Post by losoollenos on 2010-11-23
Gracias Guillermo, 

Si, normalmente le asigno ese valor al 10%, aunque en uso normal (emesene, vlc, firefox) no pasa del 20 % de uso de ram, y con el JDownloader del 30 %. En realidad ahora mismo no estoy con partición swap, es si o si crear una?, perdón si me voy de tema.....

saludos

---

### Post by biale on 2010-11-23
¿Cuanta RAM estas usando actualmente? ¿hibernación? ¿Maquinas virtuales?

También podes probar haciendo un "swapoff" para anular el uso de swap y ver que pasa.

> Estoy pensando en dejar mi actual disco rígido exclusivamente para almacanamiento,

De ese disco podrias restar 4 Gbytes de swap...

> porque siempre escriben el mismo sector

Algunos (no se si todos) utilizan un algoritmo para ir balancendo los sectores físicos usados y equilibrar el desgaste. También recuerdo que hay dos tecnologías (o metodologías?), una mas duradera que la otra.

Recuerdo que los valores reales para ese tipo de discos son bastante inferiores a los teóricos. Pero si va a venir a valores "USA"...

---

### Post by guillermolisi on 2010-11-23
> **losoollenos said:**
> Gracias Guillermo, 

Si, normalmente le asigno ese valor al 10%, aunque en uso normal (emesene, vlc, firefox) no pasa del 20 % de uso de ram, y con el JDownloader del 30 %. En realidad ahora mismo no estoy con partición swap, es si o si crear una?, perdón si me voy de tema.....

saludos

Ojo con las mediciones del uso de RAM. No todas las herramientas disponibles miden el consumo de RAM de la misma forma. Algunas consideran buffers, cache, etc. como parte del consumo del usuario y otras solamente lo que ocupan los procesos de usuarios especificamente hablando, lo cual si bien es cierto, no es exacto.

De hecho, Linux trata de utilizar toda la RAM que tenga disponible para mejorar su rendimiento y no necesitar acceder al disco rigido en busca de nuevos bloques de datos. Si lo tiene en memoria, mejor. Por eso la mayor parte de la RAM ocupada (para maquinas con 1Gb o mas) corresponde a buffers y cache del SO.

---

### Post by losoollenos on 2010-11-23
Gracias por tu respuesta biale, me tiraste un montón de data para averiguar.
Con respecto a lo que me preguntás, de paso le digo a Guillermo, estoy con 4 gb de RAM,; el monitor de Gnome, por ejemplo ayer que estuve bajando unas pelis con JDownloader, más Firefox-vlc-emesene, marcaba 1.3 gb de consumo.
Máquinas virtuales no uso, no se a que te referís con hibernación. 

Muchas gracias !!!!

---

### Post by biale on 2010-11-23
Mas o menos así: se bloquean los dispositivos, se almacenan todos los contenidos de la RAM en la SWAP y luego se apaga el procesador. Cuando se reinicia el procesador se toman los contenidos de la swap y se reinicia la máquina en tiempo record. Es evidente que no lo estas usando!

Hay algún material sobre discos SSD en el sitio de Western Digital y tambien algunos benchmarks en la red. Además consumen (y calientan) menos, muy interesante para las notebooks.

---

### Post by biale on 2010-11-23
Algún dato sobre performance...

[http://www.tomsguide.com/us/netbook-upgrade-ssd,review-1481-2.html](http://www.tomsguide.com/us/netbook-upgrade-ssd,review-1481-2.html)

---

### Post by losoollenos on 2010-11-23
En inglés lo único que entiendo son los números jajajaj, pero parecen buenos estos SSD.......

---

