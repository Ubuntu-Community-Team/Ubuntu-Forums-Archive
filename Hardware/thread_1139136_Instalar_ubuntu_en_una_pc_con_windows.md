---
title: "Instalar ubuntu en una pc con windows"
date: 2009-04-26
forum: Hardware
---

### Post by sp33d3rs on 2009-04-26
*OK, ok, hay ochocientosmil artículos sobre esto, pero les cuento mi caso en particular por que no quiero sorpresas.*

Tengo 2 pcs, una con [COLOR="DeepSkyBlue"]windows[/COLOR] y la otra con [COLOR="DarkOrange"]ubuntu 8.1[/COLOR]
El tema es que la pc con linux la uso muy poco, quiero usar la que tiene windows (pc de mi casa, que uso siempre) con los 2 sistemas operativos (un dual boot).

Ahora, explico algo, por un problema que tuve con el grub hace mucho (experimentando instalar linux y desistalarlo, **así, a lo bruto y guazo**)
El problema es que lo del grub nunca lo pude solucionar.
Tengo dos discos duros, uno de 40gb IDE (pff, terrible cañito, viejo pero bueno) y uno de 150gb SATA(donde ahora esta win)
En esa epoca quise instalar un SO en un disco y el otro SO en otro disco. Nunca funciono :P.
Seguro por que lo hise pal Qlo... :lolflag:

En fin, mi solucion fue decirle a la madre que bootee desde el disco duro de 150gb, para eso tuve que reintalar windows, el cual me queda identificado como D: .#-o

_Entonces mi pc (si, si, mi quilombo), es así:_
1. Se enciende y bootea desde el disco duro de 150gb SATA
2. Windows arranca desde un disco duro D: (y no el tradicional C)
3. En el C:, tengo datos personales, y en el D: tengo el SO con los programas.

La realidad es que no me quiero reventar mucho la cabeza, lo que tengo ganas de hacer es dejar windows como está, e instalar ubuntu en el mismo disco duro que windows (en el SATA de 150gb) dejando intacto el C:

[CENTER]**[FONT="Arial Black"]Con todas estas particularidades, me dan una mano?[/FONT]**[/CENTER]
Me interesa mucho Ubuntu, pero hay ciertas cosas con windows que aun en ubuntu no estan (***me choque con muchos freekies fanáticos que me mostraron muchas alternativas pero _me molestan_, _no sean porfiados_, por el momento los voy a seguir usando, todo bien, pero yo trabajo con la pc, y si me piden un laburo, hasta que no le tome la mano o hasta que no este el soft que nesecito, o hasta que no lo modifique a mi gusto, tengo que entregarlo a tiempo, por ahora me quedo con muchos soft para windows, aunque quizas use mucho wine:))***

CHAS GRACIAS A TODOS


PD:
AMD Athlon 64 DUAL CORE 5000 +2.61ghz
1.00GB Ram [SIZE="2"](si, es poquito, pero cuando pueda la paso a 2gb)[/SIZE]
Geforce 8600gt 512mb
mother Asus, pero no me acuerdo el modelo

(me recomiendan un ubuntu en particular)

---

### Post by sp33d3rs on 2009-04-27
Tengo bajado el último(9.04), en la versión de 32 y la 64.
¿ Cuál elijo, la de 64, no?

---

### Post by josecuervo86 on 2009-04-27
Si queres evitarte un par de problemitas, yo elejiria la de 32. Te lo digo como usuario de 64.

---

### Post by dodle on 2009-04-27
Tal vez puedes usar [wubi](http://wubi-installer.org/).  Se instala por Windows.

---

### Post by sp33d3rs on 2009-04-27
> **josecuervo86 said:**
> Si queres evitarte un par de problemitas, yo elejiria la de 32. Te lo digo como usuario de 64.

Si che, por?

---

### Post by sp33d3rs on 2009-04-27
> **dodle said:**
> Tal vez puedes usar [wubi](http://wubi-installer.org/).  Se instala por Windows.

Pero es lo mismo que instalar el SO, es decir, la estabilidad y la forma de trabajar es la misma

Nooo... en la pagina de wubi no funciona la descarga!

---

### Post by zeroadrenaline on 2009-04-27
Bueno, primero quenada, si tenes ganas de instalar, defragmenta tu disco de Windows, el sata, porque vas a tener que particionar.
Segundo, si ya instalaste alguna vez, no creo que tengas problema en hacerlo nuevamente.
Las verciones actuales de *buntu detectan automaticamente sistemas ya instalados, y los incorporan al grub, con lo cual no vas a tener inconvenientes para bootear con cualquier sistema.
Cualquier cosa, hay mucha informacion sobre como agregar windows al grub para tener tu dual boot caminando.
Por ultimo, no mandes mensajes privados pidiendo socorro, no estan pensados para eso.

---

### Post by sp33d3rs on 2009-04-27
[SIZE="5"]QUE MAL[/SIZE]
**Para la ****** gente.**

Desp de desfragmentar, dejar un espacio sin particion con el Part Magic, instale ubuntu.

Desp se reinicio y me tiro
"error stage 1.5
erro grub
error 18"

y murio mi pc como me habia pasado hace mucho, desp de mucho ***** y pasar momentos transpirando, logre con el supergrub (grax  a Dios que lo habia bajado, funciono)

El problema es, lo que tenia en el C: se fue al *****, no veo nada, ni se donde esta (*lo que mas me calienta es que ni lo toque a ese disco durante la intalacion*)

El D: funciona bien, arranca win pero me quedo limitado a lo que lo particione 90gb.

Espero que me ayuden, me quedo una maquina medio pelo, y perdi ya muchos gb.

[SIZE="4"]**Nesecito ayuda urgente!!!!**[/SIZE]

---

### Post by clasificado on 2009-04-27
No había que usar el partition magic :S Nunca el partition magic, Malo el partition magic

clasificado

---

### Post by sp33d3rs on 2009-04-27
> **clasificado said:**
> No había que usar el partition magic :S Nunca el partition magic, Malo el partition magic

clasificado

y ahora que hago?

---

### Post by rubioo on 2009-04-27
Y si reinstalas grub, usando super grub disk?

   [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by Tosh78 on 2009-04-27
Primero proba con el Super Grub. Otra opcion es que arranques con el Live CD de Ubuntu, y veas si podes recuperar algo de tus datos y los pases a un disco externo o pendrive por las dudas.
Una vez que puedas arrancar wingarch, si queres instalar Wubi pones el CD que tenes de Ubuntu (ya viene con el Wubi) y solo te va a preguntar que queres hacer. Ahi elegi la opcion de instalar dentro de Win. 
Para mi es mejor instalarlo directamente que adentro de Win, pero te puede servir para usarlo un tiempo ver que te parece, acostumbrarte y despues lo instalas como la gente. 
Otra cosa, probaste de arrancar con el CD de win y elegir la opcion "reparar"?

---

### Post by sp33d3rs on 2009-04-27
> **rubioo said:**
> Y si reinstalas grub, usando super grub disk?

   [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

estoy fue lo único que logro que tenga win, ni quesea que algo me funque.
pero no logre mas que eso...

---

### Post by sp33d3rs on 2009-04-27
> **Tosh78 said:**
> Primero proba con el Super Grub. Otra opcion es que arranques con el Live CD de Ubuntu, y veas si podes recuperar algo de tus datos y los pases a un disco externo o pendrive por las dudas.
Una vez que puedas arrancar wingarch, si queres instalar Wubi pones el CD que tenes de Ubuntu (ya viene con el Wubi) y solo te va a preguntar que queres hacer. Ahi elegi la opcion de instalar dentro de Win. 
Para mi es mejor instalarlo directamente que adentro de Win, pero te puede servir para usarlo un tiempo ver que te parece, acostumbrarte y despues lo instalas como la gente. 
Otra cosa, probaste de arrancar con el CD de win y elegir la opcion "reparar"?

si, pero me llema a el D:/Windows y muere ahi, es decir, nose que hacer. En si, como dije en el encabezado, en el primer post, ubuntu lo tengo en otra pc, que mucho no uso, y la verdad que me encanta. Pero no por eso tengo que "obligar" a mi familia a migrar... por eso en esta pc quiero tener los dos SO.

---

### Post by sp33d3rs on 2009-04-27
Ya saque todos los datos importantes de la pc, mañana a la mañana, cuando vengo, puedo trabajar mas tranqui aun.

**No hay una forma de "reventar todo" y volver a cero de nuevo, es decir, 2 discos duros pelados absolutamente (y sin el ******* problema de grub)**

Mañana tengo la posiblidad de reinstalar todo de nuevo, realmente quiero tener mi dualboot, espero sepan darme una mano. *(jeje, o por lo menos no tener una pc con 120gb perdidos)*

---

### Post by staar on 2009-04-28
> **sp33d3rs said:**
> Ya saque todos los datos importantes de la pc, mañana a la mañana, cuando vengo, puedo trabajar mas tranqui aun.

**No hay una forma de "reventar todo" y volver a cero de nuevo, es decir, 2 discos duros pelados absolutamente (y sin el ******* problema de grub)**

Mañana tengo la posiblidad de reinstalar todo de nuevo, realmente quiero tener mi dualboot, espero sepan darme una mano. *(jeje, o por lo menos no tener una pc con 120gb perdidos)*

si, hay forma, con el editor de particiones desde el livecd de ubuntu, borras todas las particiones, despues instalas windows (primero), y con su instalador, creas la partición que quieras para él, dejando espacio libre para ubuntu, windows ta va a sobreescribir su cargador de arranque en el MBR, sobre el grub que tenes ahora, despues instalás ubuntu en el espacio libre y el instalador de ubuntu va a detectar windows y va escribir grub en el MBR ;-)...

algunas recomendaciones, usá un solo disco para instalar los dos sistemas, para evitar posibles futuros líos con el orden y los números de disco y partición, el otro disco dejalo para guardar datos...
si queres que ubuntu vaya aún más rápido, al particionar con el instalador de ubuntu, hacelo manualmente, así podés elegir ext4 como sistema de archivos (acordate que, mínimo, son 2 particiones, una swap y otra raíz '/', está última es la que podés poner como ext4 ;-) )

saludos

---

### Post by sp33d3rs on 2009-04-28
> **staar said:**
> si, hay forma, con el editor de particiones desde el livecd de ubuntu, borras todas las particiones, despues instalas windows (primero), y con su instalador, creas la partición que quieras para él, dejando espacio libre para ubuntu, windows ta va a sobreescribir su cargador de arranque en el MBR, sobre el grub que tenes ahora, despues instalás ubuntu en el espacio libre y el instalador de ubuntu va a detectar windows y va escribir grub en el MBR ;-)...

algunas recomendaciones, usá un solo disco para instalar los dos sistemas, para evitar posibles futuros líos con el orden y los números de disco y partición, el otro disco dejalo para guardar datos...
si queres que ubuntu vaya aún más rápido, al particionar con el instalador de ubuntu, hacelo manualmente, así podés elegir ext4 como sistema de archivos (acordate que, mínimo, son 2 particiones, una swap y otra raíz '/', está última es la que podés poner como ext4 ;-) )

saludos

1.Esto solucionaria los temas de grub?

2.es decir, si elimino las particiones desde el live, de ambos discos, desp quedaría como decía yo, "pelado, 0, de fabrica" no?

3.No me acuerdo como era el sistema de particiones de ubuntu, pero es muy intuitivo no, se borran fáciles las particiones (yo me acuerdo que en algunas había una especie de candidato gris), pero nunca probé borrar las particiones, es fácil?

4. OK, instalo windows en el sata de 150gb, de los cuales dejo, por ejemplo, 50gb para windows y 100gb para ubuntu (los 100gb los dejo aun sin particionar), instalo win y dejo todo eso ok. Ahora, pongo el cd de ubuntu... y desp me ayudas como sigo?

gracias por las molestias!!!

---

### Post by staar on 2009-04-28
> 1.Esto solucionaria los temas de grub?

el GRUB es un cargador de arranque, windows tiene el suyo (ni idea si tiene un nombre), los cargadores de arranque hacen eso, cargan sistemas, y generalmente se instalan en el MBR, Master Boot Record, una parte del disco independiente de las particiones...
cuando windows se instala, BORRA todo en el MBR, y pone SU bootloader, al instalar ubuntu borras este e instalas GRUB encima, que te permite cargar ambos sistemas (y muchos más :-D)...

> 2.es decir, si elimino las particiones desde el live, de ambos discos, desp quedaría como decía yo, "pelado, 0, de fabrica" no?

claaaro, si borras todas las particiones, te queda todo el disco como 'espacio libre' (en gris oscuro en el Editor de particiones)

> 3.No me acuerdo como era el sistema de particiones de ubuntu, pero es muy intuitivo no, se borran fáciles las particiones (yo me acuerdo que en algunas había una especie de candidato gris), pero nunca probé borrar las particiones, es fácil?

el Editor de particiones en ubuntu es un programa, que en realidad se llama g-parted, instalable en cualquier distro de linux, es un programa muy intuitivo, que te muestra una barrita que representa tu disco con sus particiones, para borrar una partición; click derecho sobre ella > borrar ;-) :-D, para modificar particiones, tienen que estar desmontadas, si son NTFS (filesystem de windos), ubuntu no las monta automáticamente, asi que al iniciar el livecd, podes directamente abrir el Editor de particiones (está en Sistema > Administración) y hacer lo tuyo :-D ...

> 4. OK, instalo windows en el sata de 150gb, de los cuales dejo, por ejemplo, 50gb para windows y 100gb para ubuntu (los 100gb los dejo aun sin particionar), instalo win y dejo todo eso ok. Ahora, pongo el cd de ubuntu... y desp me ayudas como sigo?

el particionador del instalador (!) de windos es medio feucho, podes usar el mismo Editor de particiones en el livecd, para crear la partición donde instalar windos; click derecho > nueva particion > tipo primaria, del tamaño que quieras, formato ntfs...

booteas con el cd de win, instalas eso ahi, toda la cosa, blabla....

vamos a lo bueno :-D, ubuntu (GNU/Linux en general)...

volvés a iniciar con el livecd, ponés instalar, llegás al paso de las particiones, elegí 'particionado manual', te aparece algo muy similar al Editor de particiones, en el espacio libre creas dos (2) particiones:
una, tamaño: masomenos la mitad de tu ram (768 MB), tipo: creo que era linux-swap o área de intercambio, punto de montaje: área de intercambio o algo asín :-P
otra, tamaño: el que te pinte, tipo: ext4, punto de montaje: / (si, una barra, el directorio raíz en sistemas unix, análogo, aunque MUY diferente a C:\ o C:\Windows), listo, seguis con la instalación...

para satisfacer tu curiosidad, en el último paso antes de comenzar a instalar, vas a tener un botón que dice Avanzado > click en él > te va a aparecer un diálogo que te informa que va a instalar el GRUB en el (hd0) (la MBR de tu disco, en términos entendibles por GRUB), dejalo asi que está bien ;-), al instalarlo va a ver el windos y lo va a agregar a su lista...

saludos

---

### Post by sp33d3rs on 2009-04-28
> **staar said:**
> el GRUB es un cargador de arranque, windows tiene el suyo (ni idea si tiene un nombre), los cargadores de arranque hacen eso, cargan sistemas, y generalmente se instalan en el MBR, Master Boot Record, una parte del disco independiente de las particiones...
cuando windows se instala, BORRA todo en el MBR, y pone SU bootloader, al instalar ubuntu borras este e instalas GRUB encima, que te permite cargar ambos sistemas (y muchos más :-D)...



claaaro, si borras todas las particiones, te queda todo el disco como 'espacio libre' (en gris oscuro en el Editor de particiones)



el Editor de particiones en ubuntu es un programa, que en realidad se llama g-parted, instalable en cualquier distro de linux, es un programa muy intuitivo, que te muestra una barrita que representa tu disco con sus particiones, para borrar una partición; click derecho sobre ella > borrar ;-) :-D, para modificar particiones, tienen que estar desmontadas, si son NTFS (filesystem de windos), ubuntu no las monta automáticamente, asi que al iniciar el livecd, podes directamente abrir el Editor de particiones (está en Sistema > Administración) y hacer lo tuyo :-D ...



el particionador del instalador (!) de windos es medio feucho, podes usar el mismo Editor de particiones en el livecd, para crear la partición donde instalar windos; click derecho > nueva particion > tipo primaria, del tamaño que quieras, formato ntfs...

booteas con el cd de win, instalas eso ahi, toda la cosa, blabla....

vamos a lo bueno :-D, ubuntu (GNU/Linux en general)...

volvés a iniciar con el livecd, ponés instalar, llegás al paso de las particiones, elegí 'particionado manual', te aparece algo muy similar al Editor de particiones, en el espacio libre creas dos (2) particiones:
una, tamaño: masomenos la mitad de tu ram (768 MB), tipo: creo que era linux-swap o área de intercambio, punto de montaje: área de intercambio o algo asín :-P
otra, tamaño: el que te pinte, tipo: ext4, punto de montaje: / (si, una barra, el directorio raíz en sistemas unix, análogo, aunque MUY diferente a C:\ o C:\Windows), listo, seguis con la instalación...

para satisfacer tu curiosidad, en el último paso antes de comenzar a instalar, vas a tener un botón que dice Avanzado > click en él > te va a aparecer un diálogo que te informa que va a instalar el GRUB en el (hd0) (la MBR de tu disco, en términos entendibles por GRUB), dejalo asi que está bien ;-), al instalarlo va a ver el windos y lo va a agregar a su lista...

saludos

MORTALLLLLL!

Gracioas viejo, ya lo imprimi, y me lo llevo pa casa.. mil gracias viejo!

Veo si queda, sino te ***** otra ves.. toy en porfiado quiero los dos SO andando!. Hasta que mi flia renuncie a win.. ahi si va a ser mas facil :D

---

### Post by faktorqm on 2009-04-28
bueno mi consejo es quiza un poco mas practico, aunque no esta mal lo que te dijo el compañero, se olvido de separar el /home.

Agarra el live cd de ubuntu, borra todas las particiones, reinicia.
Agarra el cd de xp, y cuando te pregunte a donde instalarlo ponele crear nueva particion, y despues ponele el tamaño que elijas (15 0 20gb si no usas muchos juegos deberia estar bien).
Cuando termina, pones el cd de ubuntu y cuando te pregunta por las particiones, ya tenes el espacio vacio para crearlas como mas te guste. Acordate que deben ser primarias siempre que sea posible, y separar el "/" del "/home". Así te quedaría:

windows-ntfs | linux-etx3 para / | linux-etx3 para /home | swap

No necesariamente el orden tiene que ser asi, y como recomendacion, para el / no dejes mas de 10gb, y el swap ponele el doble de tu ram si tenes 1gb o menos, si tenes 4gb con la mitad alcanza, y si tenes 2g deja 2g de swap y deja para el /home lo que sobre.
De esta manera, ya te anda todo de una con grub incluido. El boton de avanzado no hace falta, pues es el unico disco que tiene en el sistema.

El cargador de arranque de windows se llama NTloader (new technology loader, o cargador de tecnologia nueva) y no funciona de forma similar al grub, por que no respeta algunos estandares entonces a veces tenes problemas.

---

### Post by sp33d3rs on 2009-04-28
Funciono!!

Ok, estos son los tipeos desde ubuntu mientras instalo un par de soft que nesecito.

Me quedo diferenta a la ultima opinion... mi pregunta es.. funciona igual?

Me quedo el sharp de 624mb 
y me quedo el / de 100gb

ahora que me conviene hacer.. no me digan que reinstalar todo?


PD: Gracias gracias gracias por su ayuda

---

### Post by staar on 2009-04-28
funciona exactamente igual, no te hagas drama, lo que te recomendaba el amigo antes era separar el /home en una partición para él solo, eso es muy común, aunque algunos no lo hacemos...
el /home (sería el equivalente, otra vez, MUY diferente, a Documents and Settings en win XP) es el directorio de los usuarios, donde se guardan todas las configuraciones y documentos...
muchos lo separan para, en caso de tener que reinstalar el sistema (en /, otra partición), conservar los datos y configuraciones en el nuevo sistema...

saludos

---

### Post by faktorqm on 2009-04-28
Exacto, funcionar funciona igual, la cosa es que la primer cosa que necesites cambiar tenes que hacer un backup si o si, en cambio si separas el /home, con poner el mismo nombre de usuario y la misma contraseña siempre tenes el desktop EXACTAMENTE igual a como lo tenias antes (siempre y cuando este "libre de errores" el /home)

Salu2!

---

### Post by sp33d3rs on 2009-04-28
No hay problema tons, toy acostumbrado a windows, a que no puedas hacer backup, a que te reviente particiones... jaja, ustedes se olvidaron de eso.. de nuevo muchas gracias, ya configure el compiz, anda genial con los 2 monitores.

Instale la nvida y baje un par de juegos, el open arena va como piña.. jajaja.

Por otro lado, tuve unos lios con el mp3 pero ya lo solucione (Crei que el Aimp era lo mejor, pero el amarock es espectacular, muy buen sonido)

Estoy descubriendo aun a fondo mi sistema operativo... mañana seguiré viendo que hay, por ahora doy por cerrado este tema, y agradezco a todos lo que hicieron posible que mi pc funcione como corresponde.

CHAS GRACIAS GENTE!!!

---

### Post by sp33d3rs on 2009-10-28
Volllvi muchachos.. jeje, cada vez que me mando una macana termino aca :p

Ok, el problema era que estaba formateando un pendrive con virus de windows (obvios) y se ve que tipee mal en la consola o nose, en fin, rebente la partición de windows, asi que borre un monton de cosas (NOTA: cuando mi mujer se dio cuenta que le borre los archivos... ehhh, si alguien tiene un espacio en su casa y quiere darle techo a esta pobre novato, se lo agradezco), bueno, el tema que me enoje y format a todo!... jaja.

Vamos con un temita, tengo 2 discos de 160gb, 1 sata y 1 ide. Cuando pongo el cd de windchous, pasa que reconoce 160gb y 32gb, es decir, no ve el de 160 por completo (se aclara que ya entre por el live cd y le borre los formatos existentes a los discos, es decir, cuando puse windows reconocio los dos discos sin sistemas de extenciones, tube que crear las particiones).

Por el momento tengo:
100gb para win
60 sin particionar (donde voy a poner ubuntu)
y los otros 160 que nose por que windows reconoce solo 32...

Algo extraño, note que en la instalacion de windows (y antas de formatear en ubuntu) el live cd no me dejaba crear particiones ntfs, solo figuraban las fat16 y la 32 ¿por qué?... 

simplemente les queria comentar esto y ver si me pueden dar una mano con ese ide feo :P

Gracias gente!

(nota: desde hace casi un año tengo ubuntu y windows, es decir, tengo un sistema operativo y una consola de videojuegos) AGUANTE UBUNTU!:D

---

