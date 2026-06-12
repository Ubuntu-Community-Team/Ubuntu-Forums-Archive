---
title: "[SOLVED] Presentacion y consulta de un principiante en Ubuntu."
date: 2009-08-03
forum: Hardware
---

### Post by Tio Bill on 2009-08-03
Bueno ante todo debo presentarme. Soy una persona con un entusiasta interés  por la informática; y autodidacta en el tema, o sea todo lo que sé lo aprendí solo. Soy un acérrimo defensor de Windows y es mi SO de cabecera y seguirá siéndolo siempre, pero como todo el que tiene un interés en el tema, no quiero cerrarme ante una sola opción,  y me ha entrado la curiosidad y deseo adentrarme en el mundo de Linux. Debo confesar que hasta hace poco sentía rechazo a probar algo de Linux mas que nada por los propios usuarios que en la mayoría de los casos y en los lugares que frecuento son insufriblemente fanáticos cerrados y en vez de atraer a la gente la alejan. Espero que acá no sea lo mismo. [COLOR="Blue"]**[SIZE="3"]Pero bueno, a mi consulta[/SIZE]**[/COLOR]. He adquirido el CDLive de Ubuntu y deseaba instalarlo en un rígido IDE de 160Gb que tengo recién formateado pero uno de los problemas es que Ubuntu no me lo reconoce, solo reconoce un disco Sata de 500Gb con una partición de 50Gb donde tengo instalado Windows Seven (Y en donde sí es reconocido el disco IDE)Quiero saber si tiene alguna solucion esto pues a ese disco lo quiero destinar para probar los SO Ubuntu, Fedora y algunos otros. Tengo mas problemas, como que no puedo conectarme a internet, y por ende no puedo descargar codecs necesarios para video y audio. tengan en cuenta que soy totalmente neófito en Linux y que no estoy familiarizado con su interfase, pero de poder instalarlo estoy deseoso de probarlo. Gracias.

---

### Post by guillermolisi on 2009-08-03
Bienvenido Bill :)

Una recomendacion de rutina: Por favor leer los mensajes sticky que hay en la seccion principal del foro de Argentina. No solo encontraras indicaciones que podras aprovechar para mejorar la comunicacion y el uso de esta herramienta de consulta sino tambien algunos enlaces de interes que te ayudaran a conocer mas y mejor Ubuntu.

En linea con esto y dado que son varios los temas que traes como consulta, te pido que por favor abras un thread/hilo por cada uno. De esa forma las respuestas seran mucho mas focalizadas en el tema y se facilita la busqueda que otros hagan sobre el mismo problema en busca de soluciones.

Vamos al tema disco rigido. IDE 160 Gb, este disco es reconocido adecuadamente por algun otro sistema operativo y por el BIOS de la maquina ?

Ese LiveCD que decis haber adquirido (pagaste por el ?) a que version de Ubuntu corresponde ?

Abri otro thread con el tema red, en la seccion Hardware. Despues vemos si queda ahi o el tema esta mas relacionado con Software.

---

### Post by Tio Bill on 2009-08-03
> **guillermolisi said:**
> Bienvenido Bill :)

Una recomendacion de rutina: Por favor leer los mensajes sticky que hay en la seccion principal del foro de Argentina. No solo encontraras indicaciones que podras aprovechar para mejorar la comunicacion y el uso de esta herramienta de consulta sino tambien algunos enlaces de interes que te ayudaran a conocer mas y mejor Ubuntu.

En linea con esto y dado que son varios los temas que traes como consulta, te pido que por favor habras un thread/hilo por cada uno. De esa forma las respuestas seran mucho mas focalizadas en el tema y se facilita la busqueda que otros hagan sobre el mismo problema en busca de soluciones.

Vamos al tema disco rigido. IDE 160 Gb, este disco es reconocido adecuadamente por algun otro sistema operativo y por el BIOS de la maquina ?

Ese LiveCD que decis haber adquirido (pagaste por el ?) a que version de Ubuntu corresponde ?

Abri otro thread con el tema red, en la seccion Hardware. Despues vemos si queda ahi o el tema esta mas relacionado con Software.

Gracias por las recomendaciones, voy a tenerlas en cuenta. Bueno voy a lo del disco rígido y abriré otro thread para los otros temas. Sí. El disco rígido IDE de 160 Gb es reconocido en Windows Seven y por la BIOS de mi mother, un Asus P5KPL_AM. Me expresé mal cuando dije adquirí el LiveCD, en realidad me lo pasó un amigo que lo descargó de la pagina de Ubuntu, y es la version 8.04.1 i3. La cuestión es, cuando arranco con el LiveCD me da las opciones de instalar o probarlo y otras. Lo pongo para probar y abre como cualquier SO pero no reconoce ese disco rígido, solo el de 500gb con su partición. Cuando intento instalar tampoco sale este disco como una opción. y como dije me interesa tener ese disco para ir probando las distintas distribuciones, ya que en la partición de 50Gb tengo W7 y lo uso como almacenamiento temporal mientras que la otra partición esta con todos mis archivos. Si necesitas mas datos decime. Gracias y saludos.

---

### Post by staar on 2009-08-03
bien, a que te referís con que no lo reconoce?, no sale en el menú Lugares? para asegurarnos, podés postear la salida de correr ```
sudo fdisk -l
``` en una Terminal (la encontrás en Aplicaciones > Accesorios)

también te recomendaría que pruebes una versión más nueva del SO (la 9.04 es la última, se baja desde [acá]("http://www.ubuntu.com/getubuntu/download"), se recomienda usar los torrents) porque la 8.04 ya tiene más de un año, y en ese tiempo linux avanza mucho, sobre todo en el soporte de hardware...

saludos

---

### Post by guillermolisi on 2009-08-03
El de 500Gb es SATAII ?

Como esta configurado el disco IDE en el BIOS ?

---

### Post by Tio Bill on 2009-08-03
> **guillermolisi said:**
> El de 500Gb es SATAII ?

Como esta configurado el disco IDE en el BIOS ? Si, es Sata II. Y el IDE esta configurado como Slave. El disco principal es el Sata II. **[SIZE="2"]staar[/SIZE]** ahora me fijo en lo que me decis y lo posteo. Y no, no aparece en el menu Lugares.

---

### Post by guillermolisi on 2009-08-03
> **Tio Bill said:**
> Si, es Sata II. Y el IDE esta configurado como Slave. El disco principal es el Sata II. **[SIZE=2]staar[/SIZE]** ahora me fijo en lo que me decis y lo posteo. Y no, no aparece en el menu Lugares.
La configuracion como slave del disco se hace en el mismo disco, a lo sumo cable de por medio.

Si no tenes otra unidad ni magnetica ni optica IDE, configuralo como Master (los discos poseen una indicacion de como colocar el puente/jumper para que el BIOS lo vea como Master).

Si tenes otra unidad y esta es Master (considerando que sea la unidad de CD, por ejemplo) coloca el disco como master y la unidad adicional IDE como slave.

---

### Post by Tio Bill on 2009-08-03
> **guillermolisi said:**
> La configuracion como slave del disco se hace en el mismo disco, a lo sumo cable de por medio.

Si no tenes otra unidad ni magnetica ni optica IDE, configuralo como Master (los discos poseen una indicacion de como colocar el puente/jumper para que el BIOS lo vea como Master).

Si tenes otra unidad y esta es Master (considerando que sea la unidad de CD, por ejemplo) coloca el disco como master y la unidad adicional IDE como slave.
Master! Capo! Era tan simple como eso, poner el IDE como master y ahora si que lo reconoce. Bueno ahora lo particioné en dos, una para Ubuntu y cuando este mas canchero probar alguna otra distribución. Lo que si el instalador me deja llegar hasta el paso 4 de 7, y me dice que defina  un archivo raíz desde el menu de partición. Probé con las opciones que se presentan en el menu pero no hay caso. ¿Alguna idea? Las particiones están en NTFS. Gracias. De todas maneras voy a seguir el consejo de **staar** y voy a descargar la ultima version.

---

### Post by staar on 2009-08-03
las particiones hacelas en un sistema de archivos nativo de linux, como ext4 (muy rápido, pero solo disponible en la última versión), ext3 (el por defecto), reiserfs o el que más te guste, a NTFS y sus limitaciones dejalas para Ventanas...

si hiciste particionado manual, tenés que especificar una partición con punto de montaje "/", para que el instalador sepa donde instalar el sistema, y otra partición (el tamaño de esta depende de la cantidad de ram que tengas) formateada como area de intercambio, para que el sistema tenga swap (o "memoria virtual" en Ventanas, y si pensas probar otras distros, cuando las instales también van a usar esa misma partición para la swap)

saludos

---

### Post by Tio Bill on 2009-08-03
> **staar said:**
> las particiones hacelas en un sistema de archivos nativo de linux, como ext4 (muy rápido, pero solo disponible en la última versión), ext3 (el por defecto), reiserfs o el que más te guste, a NTFS y sus limitaciones dejalas para Ventanas...

si hiciste particionado manual, tenés que especificar una partición con punto de montaje "/", para que el instalador sepa donde instalar el sistema, y otra partición (el tamaño de esta depende de la cantidad de ram que tengas) formateada como area de intercambio, para que el sistema tenga swap (o "memoria virtual" en Ventanas, y si pensas probar otras distros, cuando las instales también van a usar esa misma partición para la swap)

saludos
Ok master, cuando termine de descargar la ultima versión hago lo que me decís. O sea, a ver si entendí bien... debería darle formato con ext4 (para borrar NTFS)y especificar el punto de montaje "/".¿No? Y en cuanto al swap quedó una partición libre de aprox. 100Gb (La que debería formatear como "area de intercambio"). Tengo 4 Gb de memoria. Gracias y saludos.

---

### Post by guillermolisi on 2009-08-03
> **Tio Bill said:**
> Ok master, cuando termine de descargar la ultima versión hago lo que me decís. O sea, a ver si entendí bien... debería darle formato con ext4 (para borrar NTFS)y especificar el punto de montaje "/".¿No? Y en cuanto al swap quedó una partición libre de aprox. 100Gb (La que debería formatear como "area de intercambio"). Tengo 4 Gb de memoria. Gracias y saludos.
Para swap 100 Gb es un desperdicio. Normalmente no supera, como maximo, los 3Gb.

Si le indicas cual es la particion NTFS en la cual vas a realizar la instalacion y optas por el modo automatico, te particiona y formatea en ext3 "/" y swap. Para usar ext4 tenes que optar por particionado manual (solo con la version 9.04, las anteriores no soportan ext4).

---

### Post by Tio Bill on 2009-08-03
> **guillermolisi said:**
> Para swap 100 Gb es un desperdicio. Normalmente no supera, como maximo, los 3Gb.

Si le indicas cual es la particion NTFS en la cual vas a realizar la instalacion y optas por el modo automatico, te particiona y formatea en ext3 "/" y swap. Para usar ext4 tenes que optar por particionado manual (solo con la version 9.04, las anteriores no soportan ext4).Ok. Voy a explorar las opciones que tenga. ¿Debería entonces crear una particion pequeña para el swap?  Yo creía que a esa particion de 100Gb podría usarla también como almacenamiento. Disculpen mi ignorancia al respecto. Gracias y saludos.

---

### Post by guillermolisi on 2009-08-03
> **Tio Bill said:**
> Ok. Voy a explorar las opciones que tenga. ¿Debería entonces crear una particion pequeña para el swap?  Yo creía que a esa particion de 100Gb podría usarla también como almacenamiento. Disculpen mi ignorancia al respecto. Gracias y saludos.
La particion asignada a "swap" solo cumple esa funcion (de hecho para Windows, dicho sea de paso, tambien es altamente recomendable ya que aisla la fragmentacion de espacio en disco del resto de las particiones en ese SO) y no se puede usar para otra cosa.

---

### Post by pol666 on 2009-08-03
Hola fijate si te sirve mi captura. [http://i27.tinypic.com/w7ok8h.jpg]("http://i27.tinypic.com/w7ok8h.jpg")

sda1: es windows
sda2: es Kubuntu ( "/" - Sistema raiz ).. como veras, quedo un poco chica, yo le daria de 7 en adelante, .. yo conozco mis usos y se que mas de 5gb en sistema no uso.
sda3: es otra por si quiero probar un linux
(la 4ta particion es extendida por lo que hay más particiones dentro)
sda5: es Kubuntu ( "/home" ahí estan mis archivos y mis configuraciones "es como" Documents & Settings de Windows, pero puede ponerse en otra particion, de forma que cuando reinstale, conserve la configuracion identica )
sda6: Es la swap, no le pongas mas de 2gb, es suficiente.. y muchas veces si tenes bastante Ram, linux no la activa.

---

### Post by staar on 2009-08-04
de hecho, con 4gb de ram (y a menos que uses blender o algo que consuma mucha memoria) andaría bien con mucho menos de 2gb de swap, 512mb o 1gb como mucho, sino es un desperdicio de espacio al pepe (linux no es como Ventanas, la swap la toca muy poco, trata de mantener todo en la memoria física)

saludos

---

### Post by Tio Bill on 2009-08-04
No se que pasa, pero no puedo instalar la ultima versión de Ubuntu. Ya la descargué tres veces. La primera llegó hasta el paso 7 y empezó a instalar luego se llenó de errores y tuve que cancelar. La segunda se cortó a la mitad la descarga, y la tercera la quemé en cd pero directamente da error cuando elijo la opción de instalar o cualquier otra. Tuve que instalar la versión anterior. Debo reconocer que me cuesta adaptarme a su interfaz pues estoy acostumbrado a Windows que con un click ya está todo listo. Acá para conectarme a internet tengo que hacer malabares reiniciando de un SO a otro, buscando data en internet y probando sin resultados. Se lo atribuyo a mi ignorancia en el tema, pero quiero saber si con cada paso que voy a dar encontraré escollos similares, para estar preparado. Recuerden que estoy acostumbrado a un click y listo. Gracias y saludos.

---

### Post by guillermolisi on 2009-08-04
Fijate que cuando inicias la maquina con el LiveCD hay una opcion en el menu que te permite verificar la consistencia del CD para evitar problemas de instalaciones aparentemente buenas pero que despues resultan en cantidad de inconvenientes funcionales.

Tambien hay una opcion para probar la memoria RAM pero no creo que tengas inconvenientes por ese lado.

La unidad de CD habra quedado adecuadamente configurada ? No estara en conflicto con el disco IDE ? (siempre que la unidad optica sea tambien IDE).

---

### Post by Tio Bill on 2009-08-04
[INDENT]Estimado **Guillermo** he visto esa opción que me decís y he confirmado que los dos cds están mal, con errores. Uno lo grabé con Nero Burning Rom y el otro con Deep Burner. En cuanto a conflictos lo dudo, pues la unidad optica es Sata. ¿Hay alguna manera de actualizarse a la nueva versión, como un upgrade? Si no la hay no voy a instalar muchas cosas en esta por si luego debo formatear para una instalacion limpia. Que me recomendas para conseguir una buena imagen sin errores. Por otro lado te cuento que estoy escribiendo desde Ubuntu, puesto que ya logre configurar y conectarme. Algo tan simple como poner en el terminal **sudo pppoeconf**, y luego seguir las instrucciones.                                                         [SIZE=2]**pol666**[/SIZE] me sirvió la imagen que subiste e hice algo similar y particioné 2 partes de 15 Gb, una para Ubuntu, otra para probar otras distros y deje para Swap solo una particion de 1GB. El resto está como /home, para mis datos y archivos. Salvo por el tema de que no consegui una imagen sin errores este tema se podria dar por solucionado. No dudo que me me van a encontrar seguido por estos lares con mas consultas, pues le estoy tomando el gusto a Ubuntu. Gracias a todos por su ayuda. Gullermolisi, staar y pol666
[/INDENT]

---

### Post by staar on 2009-08-04
creo que ya te lo dije, pero es muy recomendable usar los torrent para bajar la iso, por varios motivos, la velocidad es excelente (ya que hay muchas semillas), no recargas los servidores, de paso ayudas a otros a bajarla (la comunidad es la base de este SO), y el protocolo torrent verifica cada parte (chunk) que baja, por lo que se elimina el riesgo de una imagen corrupta...

lo de "un click y listo" es relativo, personalmente me fue más fácil configurar mi conexión 3g en ubuntu que en Ventanas, pero todo depende de la forma que tengas de conectarte, con algunas puede ser un poco complicado (sobre todo si tenés el alfajor del diablo) y otras te las detecta automáticamente...

saludos

PD: un aviso, para que lo vayas incorporando, la "interfaz" de ubuntu es el entorno de escritorio Gnome, no es el único, existen otros como KDE, XFCE, etc y su manejo y aspecto son diferentes (no mucho), linux también se puede correr sin interfaz gráfica o con algún WM mínimo (que solo manejan ventanas, sin la cantidad de menúes y aplicaciones de configuración de los entornos de escritorio)

---

### Post by Tio Bill on 2009-08-04
> **staar said:**
> creo que ya te lo dije, pero es muy recomendable usar los torrent para bajar la iso, por varios motivos, la velocidad es excelente (ya que hay muchas semillas), no recargas los servidores, de paso ayudas a otros a bajarla (la comunidad es la base de este SO), y el protocolo torrent verifica cada parte (chunk) que baja, por lo que se elimina el riesgo de una imagen corrupta...

lo de "un click y listo" es relativo, personalmente me fue más fácil configurar mi conexión 3g en ubuntu que en Ventanas, pero todo depende de la forma que tengas de conectarte, con algunas puede ser un poco complicado (sobre todo si tenés el alfajor del diablo) y otras te las detecta automáticamente...

saludos

PD: un aviso, para que lo vayas incorporando, la "interfaz" de ubuntu es el entorno de escritorio Gnome, no es el único, existen otros como KDE, XFCE, etc y su manejo y aspecto son diferentes (no mucho), linux también se puede correr sin interfaz gráfica o con algún WM mínimo (que solo manejan ventanas, sin la cantidad de menúes y aplicaciones de configuración de los entornos de escritorio) Si, me lo habías comentado en uno de los primeros mensajes, y bajé por torrent la primer imagen con el Utorrent, que bajó rapidísimo pues como decís había muchas semillas, pero al comenzar a instalarse comenzaron los errores. Luego verifiqué el cd con la opcion del inicio y también daba errores. La segunda imagen la descargué con descaraga directa y no tardo mucho en cortarse la descarga, la tercera también la descargué asi pero se descargo completa, pero ni siquiera comenzó con la instalación, salía un error de Boot o algo asi, ni siquiera arrancaba mas allá del menu. Por otro lado no se si viste mi último mensaje pero ya logré conectarme, buscando en Google todo es posible. Gracias por tu tiempo.

---

### Post by pol666 on 2009-08-04
nero en mi caso, me hizo pensar que mi grabadora no funcionaba durante 1 año ya de 10 de copias, fallaban 7. Cuando instale linux le di un vistaso a K3B, nunca más una falla. Si ahora tenes una version anterior de ubuntu, podrias bajar el K3B e intentar desde ahí.

Plan B: Al contrario de windows (en realidad se deberia poder, aunqeu yo no pude) Ubuntu se puede instalar desde un pendrive muy facilmente con la aplicacion unetbootin.

Plan C: El envio de los cd de Ubuntu es gratuito, totalemente libre de costos, su promedio de demora es de 1 mes.

-------------------------------------

Aclaraciones:

1) sudo pppoe-conf antes se usaba, ahora creo que hay interfaz gráfica tanto en gnome como KDE, no lo se, tengo router.
2) Te reconozco, que adaptarse al cambio sin ayuda, cuesta uno y la mitad del otro, lo se y lo deben saber todos los que pasaron por esto. Mas allá de que cambies o no de SO, la satifacción por aprender y entender algo nuevo es incompensable. Así que espero que sigas adelante, y me alegro de que te haya servido mi particionado. Por cierto, si dejaste otro espacio para probar distribuciones te recomiendo alguna con KDE, como por ejemplo Open Suse, (esta la 11.1, y la 11.2 sale en Noviembre, con bastantes cambios)

---

### Post by Tio Bill on 2009-08-04
Ok [SIZE=2]**pol666**[/SIZE], voy a tenerlo en cuenta y probar ese programa para grabar los isos. Sabes una cosa, despues de tanta interfaz gráfica con Windows ahora me esta empezando a interesar esto de la terminal y sus comandos. Muchas gracias por la buena onda.

---

