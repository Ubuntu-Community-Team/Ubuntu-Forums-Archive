---
title: "Sansa View no lee mp3 / no reconoce capacidad total del dispositivo"
date: 2009-05-31
forum: Hardware
---

### Post by fedeavila on 2009-05-31
Espero que alguien me pueda dar alguna ayudita.

Hace como 1 mes me compré un mp4 Sansa View de 16GB
Nunk le di formato... Hasta ayer (desde el propio dispositivo).
El tema es que ahora cuando lo conecto, si le agrego música no lo lee...

Tiene 2 modos de operar: MTP y MSC. El que yo usaba era el MSC (Mass Storage Class).
Y probé en el otro modo, Media Transfer Protocol, pero Ubuntu me dice que el dispositivo tiene capacidad total de 3.1GB (?)

Encontré [un blog]("http://www.micahcarrick.com/05-21-2008/sansa-view-ubuntu.html") que explica los cómos y por qué de este dispositivo pero no me ayudó en nada, instalé esos paquetes y lo detecta, todo bien... 
Pero en MTP el dispositivo es de 3.1GB y en MSC me dice que es de 16GB pero no lee ninguna canción.

Algo raro también es que cuando le cargo música (10GB aprox) en MSC el dispositivo reconoce que hay 10GB ocupados, pero la música no está! Me figura [EMPTY]

Dudo que alguien me pueda ayudar (salvo que tenga el mismo mp4 que yo) y lo peor es que creo que tendría que conectarlo a un equipo con Windows para ver que me salta. 
Tengo, pero con VirtualBox, y cuando habilito el puerto USB de Sansa, no pasa nada.

Gracias

---

### Post by josecuervo86 on 2009-05-31
Te hago una solo consulta y solo para descartar: los archivos son .mp3 no? Porque a mi una vez me paso lo mismo y no me di cuenta que los archivos que habia puesto eran .ogg que es el formato por defecto de Soundjuicer (si, todo ****** yo :P)

---

### Post by fedeavila on 2009-05-31
> **josecuervo86 said:**
> Te hago una solo consulta y solo para descartar: los archivos son .mp3 no? Porque a mi una vez me paso lo mismo y no me di cuenta que los archivos que habia puesto eran .ogg que es el formato por defecto de Soundjuicer (si, todo ****** yo :P)

si o sea no soy tan inutil jajaja

---

### Post by guillermolisi on 2009-05-31
> **fedeavila said:**
> Espero que alguien me pueda dar alguna ayudita.

Hace como 1 mes me compré un mp4 Sansa View de 16GB
Nunk le di formato... Hasta ayer (desde el propio dispositivo).
El tema es que ahora cuando lo conecto, si le agrego música no lo lee...

Tiene 2 modos de operar: MTP y MSC. El que yo usaba era el MSC (Mass Storage Class).
Y probé en el otro modo, Media Transfer Protocol, pero Ubuntu me dice que el dispositivo tiene capacidad total de 3.1GB (?)

Encontré [un blog]("http://www.micahcarrick.com/05-21-2008/sansa-view-ubuntu.html") que explica los cómos y por qué de este dispositivo pero no me ayudó en nada, instalé esos paquetes y lo detecta, todo bien... 
Pero en MTP el dispositivo es de 3.1GB y en MSC me dice que es de 16GB pero no lee ninguna canción.

Algo raro también es que cuando le cargo música (10GB aprox) en MSC el dispositivo reconoce que hay 10GB ocupados, pero la música no está! Me figura [EMPTY]

Dudo que alguien me pueda ayudar (salvo que tenga el mismo mp4 que yo) y lo peor es que creo que tendría que conectarlo a un equipo con Windows para ver que me salta. 
Tengo, pero con VirtualBox, y cuando habilito el puerto USB de Sansa, no pasa nada.

Gracias
Estuve leyendo la nota y los comentarios hechos a la misma.

La nota habla solo sobre la version de 8Gb y los comentarios hablan de problemas y frustraciones para las versiones de 16 y 32 Gb (varios no recomiendan la marca/producto).

Si no recuerdo mal, habia cierta recomendacion para usar pendrives de hasta 8Gb cuando se lo quiere usar como disco operativo/booteable. Tal vez esa recomendacion alcance a este tipo de dispositivos tambien por alguna limitacion a nivel de file system.

---

### Post by fedeavila on 2009-05-31
> **guillermolisi said:**
> Estuve leyendo la nota y los comentarios hechos a la misma.

La nota habla solo sobre la version de 8Gb y los comentarios hablan de problemas y frustraciones para las versiones de 16 y 32 Gb (varios no recomiendan la marca/producto).

Si no recuerdo mal, habia cierta recomendacion para usar pendrives de hasta 8Gb cuando se lo quiere usar como disco operativo/booteable. Tal vez esa recomendacion alcance a este tipo de dispositivos tambien por alguna limitacion a nivel de file system.

:-| $450

espero que esas recomendaciones estén dirigidas sólo a los usuarios de linux

yo cuando apenas me lo compré le cargué la música desde Windows 7 y si... tiene muchos problemas si no le actualizás el firmware con el soft de Sansa.

pero después de actualizarlo era una luz, para navegar entre carpetas y cambiar de canción, etc

el tema es que me llegaron después los cd's de ubuntu y lo instalé en todo el disco...

no sé qué hacer ahora :?

---

### Post by josecuervo86 on 2009-05-31
Virtualizate un Xp y santo remedio, te lo digo por experiencia propia ;)

---

### Post by guillermolisi on 2009-05-31
> **josecuervo86 said:**
> Virtualizate un Xp y santo remedio, te lo digo por experiencia propia ;)
Dijo que ya lo hizo con Vbox pero no le reconocia el dispositivo.

Lo que no dijo y pregunto ahora es: Que version de VBox usas/probaste ? La OSE o la cerrada ?

---

### Post by josecuervo86 on 2009-05-31
Perdon, no lei, eso me pasa por ir al grano de una :-?

---

### Post by fedeavila on 2009-05-31
> **guillermolisi said:**
> Dijo que ya lo hizo con Vbox pero no le reconocia el dispositivo.

Lo que no dije y pregunto ahora es: Que version de VBox usas/probaste ? La OSE o la cerrada ?

usé/USO la versión estándar que te descargás desde la web official.
pero el tema no es tener que necesitar windows para hacerlo andar.
el tema es por qué conecto el dispositivo en mtp y me dice que es de 3.1GB ¿? no tiene sentido...

y en msc sí me dice que es 16GB pero tengo meter 1 canción, desconectarlo. encenderlo, meterle otra, desconectarlo. encenderlo, meterle otra, desconectarlo... así hasta completar los 14GB de música. ](*,)

---

### Post by josecuervo86 on 2009-05-31
Te hago otra pregunta, virtualbox no te reconoce unicamente el mp4 o te pasa con todos los dispositivos? Si no te reconoce ninguno puede que tengas un problema similar al que yo tenia. Si es asi te busco la solución que la tengo guardada en algun favoritos :)

---

### Post by fedeavila on 2009-05-31
> **josecuervo86 said:**
> Te hago otra pregunta, virtualbox no te reconoce unicamente el mp4 o te pasa con todos los dispositivos? Si no te reconoce ninguno puede que tengas un problema similar al que yo tenia. Si es asi te busco la solución que la tengo guardada en algun favoritos :)

virtualbox reconoce el dispositivo USB-SANSA-VIEW, cuando lo tildo, WINDOWS XP, el sistema operativo en si, no se da cuenta... no sé... me pasa tambien con la webcam... así que puede ser eso... si es eso y me decís cómo arreglarlo... CAPAZ me salvás la vida... porque yo desde windows lo único que podría hacer fijarme si le puedo dar formato al dispositivo y bleh... 

la música la tengo en ubuntu, salvo que exista alguna manera de transferir la música desde ubuntu, que pase por virtualbox(?) y de ahí al mp4 ¿?

---

### Post by josecuervo86 on 2009-05-31
Claro, lo que te pasa es lo mismo que me pasaba a mi: los podes agregar desde virtualbox, pero Xp no se da cuenta.

Aca [0] esta la respuesta, tenes que modificar un archivito. Andate al punto 3 donde explica bien como hacerlo. En este mismo tuto, en el punto 7 te explica como crear un directorio compartido entre Xp y Ubuntu, que puede ser cualquier carpeta, aunque en tu caso talvez convendría que sea la de música ;)

[0] [http://www.ubuntu-es.org/index.php?q=node/62374]("http://www.ubuntu-es.org/index.php?q=node/62374")

---

### Post by fedeavila on 2009-06-01
> **josecuervo86 said:**
> Claro, lo que te pasa es lo mismo que me pasaba a mi: los podes agregar desde virtualbox, pero Xp no se da cuenta.

Aca [0] esta la respuesta, tenes que modificar un archivito. Andate al punto 3 donde explica bien como hacerlo. En este mismo tuto, en el punto 7 te explica como crear un directorio compartido entre Xp y Ubuntu, que puede ser cualquier carpeta, aunque en tu caso talvez convendría que sea la de música ;)

[0] [http://www.ubuntu-es.org/index.php?q=node/62374]("http://www.ubuntu-es.org/index.php?q=node/62374")

si... ya lo había leído... modificar el archivo 40-permissions.rules (que no se llama más así...) y cambiar el valor 0664 a 0666...

en el menú de dispositivos de vb me figuran ambos usb pero están DESHABILITADOS...

lo de la carpeta compartida también funcionó... pero... ya fue... jaja toy agregando los archivos carpeta x carpeta, desconectándolo mediante.. 

es un laburito pero... prefiero eso hasta que instale windows de nuevo y no sé... ver si puedo resolver algo desde ahí... :?

---

### Post by fedeavila on 2010-05-01
A (casi) un año de la creación de este Tema, lo marco como "Resuelto"
En esta nueva versión ya me reconoce los 16GB :D

---

### Post by guillermolisi on 2010-05-02
Premio a la constancia :)

---

### Post by fedeavila on 2010-05-02
> **guillermolisi said:**
> Premio a la constancia :)

Sabés que hacía ya un buen tiempo que no chequeaba esto..
Y cuando me acordé, crucé los dedos.. y.. "zas" veo en el escri: "Sandisk Sansa View -15GB-"

Casi me morí jajaja
Muy pero muy contento eh!

Toy buscando la manera de poder "retribuir" todo el laburo que se mandaron..

---

