---
title: "Recuperar una partición del disco"
date: 2011-01-25
forum: Hardware
---

### Post by valucha on 2011-01-25
[COLOR="DarkOrchid"]Hola!!, estoy medio desesperada porque me parece que perdí todas todas mis cosas.
Les cuento más o menos que hice:
Tengo un disco de 80 donde está Ubuntu y uno de 320 donde está Windows por un lado, y mis archivos por el otro.
HOy, queriendo hacer que Ubuntu montara al incio mi partición de mis archivos, entré en Sistema->Administracion->Utilidad de los discos y seleccioné en la partición de mi disco la opción "arrancable" que era lo que yo tenía entendido que era que me lo montaba al incio.
Evidentemente no es asi porque ahora ese disco está vacío y se llama "Disco duro de 320 GB:Reservado para el sistema", y no puedo acceder desde Windows ni Linux.
Borré todos mis datos o hay alguna forma de recuperarlo?
Sé que en última instancia puedo correr algún programa (o llevarlo a alguien que sepa) y que recupere los datos que no se sobreescribieron todavía.
Pero la verdad que de gila, no sé qué hice todavía y no sé si tengo las cosas o no.

Una buena señal es que si hago click derecho en el disco me dice que tengo 24gb ocupados que (creo) es lo que ocupan todas mis cosas.
Pero una mala es que desde Windows me dice que ese disco tiene 0b ocupados.

Lo raro es que creo yo, la única forma de borrar todo definitivamente es formateando y yo nunca le dije que formatee nada, así que no sé.
Espero que me puedan ayudar, 

MIL GRACIAS!!!


Edito: Estuve buscando y me puse a investigar con el testidisk y los archivos están :) !! Pero no puedo acceder a ellos.
El error que me tira es:
[IMG]http://lh6.ggpht.com/_6cY1w30PhQc/TT7QnM5DEqI/AAAAAAAABL4/tJBhoqg8fmo/testdisk.png[/IMG]

[/COLOR]

---

### Post by fedeavila on 2011-01-30
Supongo que ya lo habrás resuelto pero..

Me pasó algo similar a lo tuyo (de hecho mi post está abajo de este)

Lo que te puedo asegurar es que tus datos están ahí, así que quedate tranquila, lo que hay que hacer es arreglar la tabla de particiones de tu disco de 320GB y Testdisk es la herramienta que yo utilicé.

Si bien en mi post puse que lo arreglé "a medias" al final pude arreglarlo completamente :D (me faltaba designar el Master Boot Record) A todo esto mi disco era 1 sólo y de 500GB. Tuve que hacer el escaneo profundo y se demoró alrededor de una hora en finalizar.. Así que paciencia!

Si no entendí mal, pusiste a la unidad donde tenés tus documentos como una partición de arranque(¿?)

Según leí en foros esta herramienta siempre funciona, aún ya habiendo escrito mal la tabla en veces anteriores (como lo hice yo jaja) así que despreocupate. 
Si recordás más o menos cómo estaba particionado tu disco no te va a ser difícil detectar Windows por un lado y la unidad donde tenías tus documentos que debe ser D: o E:

Me encantaría decirlo con tecnicismos pero lo mío es el diseño no la informática :P

Fijate que en el menú principal de testdisk hay una opción para comprobar errores en la "geometría" del disco y..

PD: No entiendo por qué hiciste eso.. Desde Ubuntu directamente no te aparecía la unidad para montarla? 
O lo que querías hacer era que se montara automáticamente esa unidad cada vez que iniciabas Ubuntu? Si es esto último, [_este link_]("http://doc.ubuntu-es.org/Montar_particiones") quizás te pueda servir...



Un saludo! ;)

---

