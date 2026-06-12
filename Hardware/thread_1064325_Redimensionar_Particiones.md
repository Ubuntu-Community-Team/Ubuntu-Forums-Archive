---
title: "Redimensionar Particiones"
date: 2009-02-08
forum: Hardware
---

### Post by aregnando on 2009-02-08
Hola a todos, quisiera hacer la siguiente consulta ya que nunca hice esto y no se el resultado final, estuve leyendo algo y no se si hay posibilidad de perder información.
El tema es el siguiente: Tengo instalado Win XP en una partición de 62 Gb. y Ubuntu en sendas particiones de 7 Gb. el tema es que quiero achicar la partición del XP (ntfs) y agrandar las de Ubuntu (ext3) haciendolo desde el Live Cd con Gparted y moviendo las dimensiones de las particiones.
La pregunta es ¿Al redimensionar habrá posibilidad de perder algo de información?¿Que pasa con la porción de disco que antes ocupaba una partición ntfs y ahora sería ext3? Incluyo una captura del Gparted para ilustrar como están las particiones.
Si bien lei algo por ahi de esto no me quedó claro que grado de desastre puede ocurrir con esto.
Saludos.

---

### Post by euzkoarima on 2009-02-09
Hasta donde sé, el gparted te cambia el tamaño, pero si tenías datos de win en la parte que le estás "sacando" los perdés.

Para que eso no ocurra tenés que desfragmentar el disco primero, que te asegura que los datos estén al principio de la partición y el final de la misma está vacía. Recién ahi podes achicar tranquilo.

Con que desfragmentar, ni idea, pero seguro en el foro alguien sabe, creo que el HirenBootCd hace eso, pero hablo de oído no más.

En cuanto a agrandar la de linux, si corrés el final entiendo que está todo ok, nunca vi que alguien corriera el principio, que es lo que harías vos.

Bueno, lo dejo en manos de los que sepan más que yo.

Saludos,
Eduardo

---

### Post by faktorqm on 2009-02-09
Hola, vos queres achicar la ntfs y "estirar" la de ubuntu? con la ntfs no creo que tengas problemas, igual hace BACKUP siempre (si c t corta la luz durante el proceso bye bye particion) pero con la de ubuntu, el problema que vas a tener es que te va a mover los datos al principio desde donde hayas abadonado de la ntfs, tonces va a tardar muuuuuucho con riesgo que se te cuelgue la pc y pierdas el ubuntu.

Otra cosa, por que pusiste el /home y el swap es una extendida si tenes 4 particiones no mas? dentro de las posibilidades de cada uno, si solo hay 4 particiones se recom9ienda sean primarias. 

Explicate mejor que queres hacer x favor. Salu2!!!!!

---

### Post by aregnando on 2009-02-09
> **faktorqm said:**
> Hola, vos queres achicar la ntfs y "estirar" la de ubuntu? con la ntfs no creo que tengas problemas, igual hace BACKUP siempre (si c t corta la luz durante el proceso bye bye particion) pero con la de ubuntu, el problema que vas a tener es que te va a mover los datos al principio desde donde hayas abadonado de la ntfs, tonces va a tardar muuuuuucho con riesgo que se te cuelgue la pc y pierdas el ubuntu.

Otra cosa, por que pusiste el /home y el swap es una extendida si tenes 4 particiones no mas? dentro de las posibilidades de cada uno, si solo hay 4 particiones se recom9ienda sean primarias. 

Explicate mejor que queres hacer x favor. Salu2!!!!!

Hola Faktorqm, realmente cuando instalé Ubuntu la primera vez realmente no entendía mucho de particiones y mucho menos como realizar las mismas, la instalación la hice con la modalidad de instalación guiada y esa es la forma en que se particionó el disco, sigo sin ser experto en este tema de particiones y desconozco como hacer particiones primarias y extendidas ya que no tengo muy practicado el Gparted.
Lo que quiero hacer es tal como dije en el primer post, achicar la partición que contiene XP y agrandar las 2 particiones de Ubuntu (/ y /home) ya que tengo 25 Gb. libres en la partición ntfs, quería dejar libres solo 10 Gb.para XP y pasarle 15 Gb a Ubuntu mas o menos 3 Gb. para / y 12 Gb. para /home. No se si me explico correctamente. Disculpá mi ignorancia con respecto al tema de particionar discos pero soy totalmente autodidacta en lo que se refiere a computación y trato de acondicionar mi Pc lo mejor que pueda para sacarle el jugo sobre todo a Ubuntu que es el que uso todo el tiempo, el XP lo dejé porque a mi mujer e hija les cuesta dejar a Win.
Acepto concejos para lograr el mejor funcionamiento de Ubuntu.
Saludos.

---

