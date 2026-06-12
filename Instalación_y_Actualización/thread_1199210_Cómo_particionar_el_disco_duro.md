---
title: "Cómo particionar el disco duro"
date: 2009-06-28
forum: Instalación y Actualización
---

### Post by Carlos C on 2009-06-28
Creo que es buena idea tener un hilo dedicado a este tema. Es uno de los problemas que tiene el que se empieza a familiarizar con Ubuntu y que genera bastantes dudas. Propongo discutir acá lo que creemos es una manera óptima de particionar el disco duro. Esta discusión, me parece, debe considerar lo siguiente:


[LIST=1]
[*]No existe una manera única y universal de particionar el disco duro, depende en gran medida de nuestras necesidades y preferencias.
[*]Cada propuesta debe ser argumentada, es decir, explicar por qué se particiona de esa manera y por qué se prefieren ciertas opciones antes que otras.
[*]Este hilo no es para resolver problemas que se tengan al particionar o instalar Ubuntu (para eso se debe publicar un thread aparte). Lo que sí se puede hacer es manifestar dudas que las mismas propuestas de particionamiento generen.
[*]Todo el que participa o pregunta debe tener una idea básica de lo que se está hablando. En caso de dudas, antes de preguntar, primero se debe mirar la Guía Ubuntu:
[/LIST]
[INDENT][http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro](http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro)
[/INDENT]
Si el tema no le interesa a nadie, pues lo cierro y punto ;).

---

### Post by flucoe on 2009-06-30
Yo encuentro que el tema es super interesante, sobre todo en el proceso de "prueba y error" que implica empezar con Ubuntu.

En mi caso siempre he optado por particionar manualmente (no me gustan mucho las "cajas negras" que hacen las pocas cosas que se hacer) y dejar /home en partición aparte, aún cuando cada cierto tiempo (definido como dos o tres versiones de Ubuntu entre cada ocasión) decido borrar absolutamente todo y partir de cero.

¿Por qué /home en partición aparte? Simplemente para poder instalar de forma limpia cada vez que quiera. Es tan simple como para tener "la opción" de hacer lo que quiera, y como siempre, el tener opciones vale. Si quiero borrar todo puedo hacerlo, pero si no quiero, también puedo hacerlo. Como no necesito más particiones, puedo usar una de ellas (lógicas) en /home.

En resumen, luego de varias pruebas he optado por algo como esto


[LIST=1]
[*]/: Partición primaria con algo así como 6144 megas. Nunca he llenado esta partición, pero la última vez me di cuenta que estaba usando cerca de 5000, luego me di un poco de margen.
[*]Swap: 2gb
[*]El resto a /home, aunque tiendo a tener todo en discos externos y pocas cosas en el interno.
[/LIST]
Hasta ahora siempre he usado ext3 para / y para /home, pero estoy pensando si valdrá la pena pasar a ext4. Por lo que he leído, mis necesidades no lo requieren, pero dejo planteada la duda.
Saludos,

---

### Post by jorval on 2009-07-07
Hola amigos, al igual que Flucoe y por los mismos considerandos tengo 3 particiones en mi disco duro, una para la raíz, otra para swap y la tercera para /home. 
Lo que me extraña es la poca lectura que tiene este tema de tanta importancia para el que recién se inicia en Ubuntu. En otro tema puse como poner /home separado de la raíz y también nadie le ha dado esférica. ¿Que sucederá? los nuevos ubunteros ya llegan sabiendo todo lo referente a particiones ¿o qué?

---

### Post by AlvaroV on 2009-07-09
> **jorval said:**
> Hola amigos, al igual que Flucoe y por los mismos considerandos tengo 3 particiones en mi disco duro, una para la raíz, otra para swap y la tercera para /home. 
Lo que me extraña es la poca lectura que tiene este tema de tanta importancia para el que recién se inicia en Ubuntu. En otro tema puse como poner /home separado de la raíz y también nadie le ha dado esférica. ¿Que sucederá? los nuevos ubunteros ya llegan sabiendo todo lo referente a particiones ¿o qué?

Jorval quizás tiene que ver con el hecho de que al existir tantas forma de respaldo de información externas, en realidad ya no es imperioso separar el Home de /. Antes si te echabas el disco duro perdías todo pero ahora ya no. Yo por ejemplo a excepción de la musica tengo todo respaldado en mi cuenta Gmail.

---

### Post by crissoriano on 2011-11-15
Hola! Soy un poco novata en la realización de particiones del disco duro y necesito un poco de ayuda:

Me  acabo de comprar un ordenador sobremesa nuevo, un i5 con 750GB de disco  duro y 4GB de RAM, con Windows 7. Quiero tener W7 junto con el nuevo  Ubuntu 11.10, teniendo en cuenta que utilizare muy poco W7, me gustaría  asignarle 50GB. A Ubuntu (/) le asignaré 15GB, que creo que es  suficiente (corregidme si no es así) y para los documentos (/home) el  resto de capacidad, 685GB.

Todo iba bien hasta que cuando tenía  que distribuir el espacio, me doy cuenta de que W7 está repartido en 3  particiones primarias, sda1, sda2 y sda3, con capacidades de 35MB, 48GB y  13GB, respectivamente. Al ser 3 particiones primarias, sólo puedo hacer  1 partición primaria más. Pues bien, ¿qué hago? Pensé en dos posibles  opciones, que no sé cuál elegir o ni tan siquiera si son posibles,  debido a mi inexperiencia:
1) ¿Hago una partición primaria para / y una lógica para /home? ¿O al revés? 
2)  ¿Redistribuyo las particiones NTFS para W7 para que queden máximo en 2  hacer otras 2 primarias, una para / y otra para /home? ¿Habría peligro  en redistribuir las 3 particiones de W7 en 2?

Y una última duda, he leído que teniendo 4GB de RAM no me es necesario hacer partición swap, ¿es cierto?

Tengo un poco de lío con todo esto, pero estoy segura que me podréis ayudar. Muchas gracias de antemano!!

Saludos!

Cris.

---

### Post by BillyBoa on 2011-11-15
> **crissoriano said:**
> Hola! Soy un poco novata en la realización de particiones del disco duro y necesito un poco de ayuda:

Me  acabo de comprar un ordenador sobremesa nuevo, un i5 con 750GB de disco  duro y 4GB de RAM, con Windows 7. Quiero tener W7 junto con el nuevo  Ubuntu 11.10, teniendo en cuenta que utilizare muy poco W7, me gustaría  asignarle 50GB. A Ubuntu (/) le asignaré 15GB, que creo que es  suficiente (corregidme si no es así) y para los documentos (/home) el  resto de capacidad, 685GB.

Todo iba bien hasta que cuando tenía  que distribuir el espacio, me doy cuenta de que W7 está repartido en 3  particiones primarias, sda1, sda2 y sda3, con capacidades de 35MB, 48GB y  13GB, respectivamente. Al ser 3 particiones primarias, sólo puedo hacer  1 partición primaria más. Pues bien, ¿qué hago? Pensé en dos posibles  opciones, que no sé cuál elegir o ni tan siquiera si son posibles,  debido a mi inexperiencia:
1) ¿Hago una partición primaria para / y una lógica para /home? ¿O al revés? 
2)  ¿Redistribuyo las particiones NTFS para W7 para que queden máximo en 2  hacer otras 2 primarias, una para / y otra para /home? ¿Habría peligro  en redistribuir las 3 particiones de W7 en 2?

Y una última duda, he leído que teniendo 4GB de RAM no me es necesario hacer partición swap, ¿es cierto?

Tengo un poco de lío con todo esto, pero estoy segura que me podréis ayudar. Muchas gracias de antemano!!

Saludos!

Cris.

Te aviso para un problema que existe.

Windows solo reconoce su sistema NTFS y no el Ext4 de Linux. Al revés, Linux reconoce ambos sistemas.

En este caso los datos que tendrás en la partición Linux de 685G no podrás verles a través de Windows.

Otro problema que formatear Windows es un rollo y normalmente te faltará el CD-DVD original para hacerlo. Al contrario puedes formatear Linux en un pispas y teniendo tus datos en la partición /home, solo formateas la partición del sistema.

Por eso te recomiendo que formatees la partición 685G en NTFS y que dejes para /home unos pocos gigas. La partición esta, la podrás utilizar en ambos sistemas como almacenamiento y backup.

---

### Post by BillyBoa on 2011-11-15
> **crissoriano said:**
> 
Y una última duda, he leído que teniendo 4GB de RAM no me es necesario hacer partición swap, ¿es cierto?


Eso es verdad pero de todas maneras el sistema necesita muchos recursos y a veces utiliza toda la RAM cuando haces copias de discos etc. Entonces la normativa es que asignes el doble de tu RAM como Swap y en tu caso 8G.

---

### Post by crissoriano on 2011-11-15
> **BillyBoa said:**
> Te aviso para un problema que existe.

Windows solo reconoce su sistema NTFS y no el Ext4 de Linux. Al revés, Linux reconoce ambos sistemas.

En este caso los datos que tendrás en la partición Linux de 685G no podrás verles a través de Windows.

Otro problema que formatear Windows es un rollo y normalmente te faltará el CD-DVD original para hacerlo. Al contrario puedes formatear Linux en un pispas y teniendo tus datos en la partición /home, solo formateas la partición del sistema.

Por eso te recomiendo que formatees la partición 685G en NTFS y que dejes para /home unos pocos gigas. La partición esta, la podrás utilizar en ambos sistemas como almacenamiento y backup.


Muchas gracias!!!

---

