---
title: "como se instala adecuadamente ubuntu teniendo un particionado"
date: 2009-06-27
forum: Instalación y Actualización
---

### Post by zhelo on 2009-06-27
resulta que tengo 70 de disco libre solo para ubuntu y 50 lwindows, aveces pienso que windows me trae problemas a ubuntu, por que instale un ubuntu amd64 y me tira errores en paquetes y cosas asi, entonces me puse a pensa que quisas yo instalo mal ubuntu
y queria saber cual es la forma adecuada de instalarlo asi como les estoy expicando
desde ya gracias

---

### Post by Patriciologico on 2009-06-27
Zhelo, nos hablas de un supuesto "aveces pienso que windows me trae problemas a ubuntu", es dificil sin algun error en concreto dirigir la ayuda. La forma correcta de instalar la puedes encontrar en la guia ubuntu por ejemplo. Tampoco dices cual es tu forma de instalar para saber si hay un fallo en tu metodo.

Esperando mas Informacion,

Saludos!

---

### Post by zhelo on 2009-06-27
> **Patriciologico said:**
> Zhelo, nos hablas de un supuesto "aveces pienso que windows me trae problemas a ubuntu", es dificil sin algun error en concreto dirigir la ayuda. La forma correcta de instalar la puedes encontrar en la guia ubuntu por ejemplo. Tampoco dices cual es tu forma de instalar para saber si hay un fallo en tu metodo.

Esperando mas Informacion,

Saludos!

mi forma de instalar es esta:

70 gb:

un 69%-->sist. ext3 trasacio. Punto de montaje: /


un 23%---> sistema ext trasacio. Punto de montaje: /home

un 6%--->area de intercambio. Punto de montaje: (nada)

---

### Post by radixs on 2009-06-27
> **zhelo said:**
> mi forma de instalar es esta:

70 gb:

un 69%-->sist. ext3 trasacio. Punto de montaje: /


un 23%---> sistema ext trasacio. Punto de montaje: /home

un 6%--->area de intercambio. Punto de montaje: (nada)

mmmm... uuuuuuuuuuuuu compañero tay mas perdido que el teniente luciano bello xD...

Una pregunta para que quieres 69% del disco en "/" la verdad no entiendo y un 23% para /home ??????????????????????????????????????????????? la verdad nose.

Yo tengo mi / solo de 10GB, anda bien con 8GB, mi home con 80GB y mi swap con 2GB, yo creo que eso seria algo mas razonable no crees???

Ademas te recuerdo leer un poquito mas, te lo digo enserio ya que todo lo que guardas en tu escritorio, usuario, etc... se va derechito a la /home por ende esta es la que deberia tener mas espacio si tienes el disco particionado asi, no crees???

PS: a la hora que posteas eso en un foro de Debian te cuelgan :P, pero como estamos en uno de ubuntu te ayudamos ;)

---

### Post by aolivares on 2009-06-27
Yo tengo la misma tabla que Radixs.
Con 10 GB en / basta y sobra

---

### Post by Carlos C on 2009-06-27
Concuerdo con lo dicho (aunque tratemos de no perder la calma, este tema no es tan trivial como nos parece luego de que lo dominamos "bien") con 10 Gib en "/" basta. Zhelo, ¿existe alguna razón para que dejes tanto espacio en tu partición montada en "/"? también existe la posibilidad de que hayas confundido las particiones y sea al revéz :confused:

Saludos.

---

### Post by zhelo on 2009-06-27
> **Carlos C said:**
> Concuerdo con lo dicho (aunque tratemos de no perder la calma, este tema no es tan trivial como nos parece luego de que lo dominamos "bien") con 10 Gib en "/" basta. Zhelo, ¿existe alguna razón para que dejes tanto espacio en tu partición montada en "/"? también existe la posibilidad de que hayas confundido las particiones y sea al revéz :confused:

Saludos.


compañero es que yo lei en un foro que un loco usaba el 69% de su disco para x proceso, el 23 para y proceso y el resto para z proceso.....

soy super noob para esto :S

---

### Post by Carlos C on 2009-06-28
Zhelo, lo mejor es que leas la siguiente página con mucha atención:

[http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro](http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro)

Por favor lee eso completo y con atención.

Saludos.

---

### Post by CdK1 on 2009-06-28
Todo depende si sabes bien en que ocuparas el espacio, ejemplo:

Si vas a usa un sistema como Desktop, usa un particionamiento guiado, no te hagas problemas; a su vez si quieres "jugar" con "Linux", te recomiendo que tengas ciertas "garantpias" si apsa algo. E n mi caso tengo todo particionado, cosa que si por X motivo me echo el sistema, no pierdo "todo";

Caturra:/home/CdK1# fdisk -l /dev/sda

Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfce09344

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda3            1217       14593   107450752+   5  Extendida
/dev/sda5            4873       14593    78083901   83  Linux
/dev/sda6            1217        1459     1951834+  82  Linux swap / Solaris
/dev/sda7            1460        1824     2931831   83  Linux
/dev/sda8            1825        2310     3903763+  83  Linux
/dev/sda9            2311        4872    20579233+  83  Linux

Las entradas de la tabla de particiones no están en el orden del disco
Caturra:/home/CdK1#

---

### Post by moreback on 2009-06-28
> **CdK1 said:**
> Las entradas de la tabla de particiones no están en el orden del disco
Tampoco se ve ordenado el listado ese, ¿por que mejor no lo encierras dentro de [code] y [ /code]?

---

### Post by zhelo on 2009-06-28
por lo que he podido ver he instaldo ubuntu correctamente en mi espacio libre...
pero sinceramente lo que busco es la solucion ami problema principal
"por que cada ves que bajo un programa en ubuntu, los paquetes me salen malos?"
yo crei que yo instakla mal ubuntu y eso me causaba el problema :/

---

### Post by Carlos C on 2009-06-29
¿Estás usando ext4?

---

### Post by radixs on 2009-06-29
> **Carlos C said:**
> ¿Estás usando ext4?

No veo que si usara EXT4 sea el problema ya que mi particion ***/ ***tanto como la ***/home*** estan creadas en EXT4.

---

### Post by zhelo on 2009-06-29
> **Carlos C said:**
> ¿Estás usando ext4?

uso ext3

---

### Post by Carlos C on 2009-06-29
> **radixs said:**
> No veo que si usara EXT4 sea el problema ya que mi particion ***/ ***tanto como la ***/home*** estan creadas en EXT4.
Las mías también, pero se sabe que ext4 tiene sus riesgos, todavía no es tan estable como ext3. Ahora, está claro que no es el caso porque usa ext3.

---

### Post by zhelo on 2009-06-29
> **Carlos C said:**
> Las mías también, pero se sabe que ext4 tiene sus riesgos, todavía no es tan estable como ext3. Ahora, está claro que no es el caso porque usa ext3.

y si lo usara se arregla ese problema?

---

### Post by moreback on 2009-06-29
> **zhelo said:**
> y si lo usara se arregla ese problema?

Na que ver, tú tienes ext3, lo cual está bien, déjalo tal cual.

Ahora estoy pensando que tu problema es tu conexión a internet que no te baja completos los archivos y de ahí tus errores.

¿Qué conexión a Internet tienes?

---

### Post by zhelo on 2009-06-30
> **moreback said:**
> 

¿Qué conexión a Internet tienes?

inalambrica a mi hogar, pero el que los pauqtes de los programas descargados esten rotos es debido a la conexion osea que si me conecto a con cable cambia, y se acaba el problema?... seran los servidores (yo uso el servidor de descarga chileno)??

---

### Post by moreback on 2009-06-30
Ciertamente conectarse por cable es más confiable que hacerlo inalámbricamente.

No creo que sean los servidores, si no estaríamos todos con problemas.

Prueba con el cable y ve qué tal anda.


Saludos.

---

### Post by zhelo on 2009-06-30
> **moreback said:**
> Ciertamente conectarse por cable es más confiable que hacerlo inalámbricamente.

No creo que sean los servidores, si no estaríamos todos con problemas.

Prueba con el cable y ve qué tal anda.


Saludos.

tendria que entrara  formartear eso, por que un error de un pauqte hizo que no pudiera entar a ubuntu, lo que me extraña arto es que tengo amigos que usan ubuntu y bajan con wifi toas sus cosas y no les pasa el mismo error... segun ella es un error de ..algo de "codiigo 8", o algo asi, no me dijeron que era solo me dijeron quew le preguntara al santo (google)

---

### Post by Carlos C on 2009-06-30
> **zhelo said:**
> tendria que entrara  formartear eso, por que un error de un pauqte hizo que no pudiera entar a ubuntu, lo que me extraña arto es que tengo amigos que usan ubuntu y bajan con wifi toas sus cosas y no les pasa el mismo error... segun ella es un error de ..algo de "codiigo 8", o algo asi, no me dijeron que era solo me dijeron quew le preguntara al santo (google)

Creo que tu amiga se refirió a un error de capa 8. Te está diciendo que el error es tuyo, no del sistema.

---

### Post by radixs on 2009-06-30
> **Carlos C said:**
> Creo que tu amiga se refirió a un error de capa 8. Te está diciendo que el error es tuyo, no del sistema.

xD!

[B][I]Error de Capa 8 = Error de Usuario



[/I][/B]

---

### Post by zhelo on 2009-07-01
> **radixs said:**
> xD!

[B][I]Error de Capa 8 = Error de Usuario



[/I][/B]

resulta que ese chiste no me lo sabia xD
lo supe hace poco... pero tambien estaba pensando lo mismo
quisas soy yo quien crea los problemas......
pero es bastante raro, por que al menos una vez intalado ubuntu no hago nada malo.. solo aplico actualzaiciones automaticas y aveces esos mismos paquetes vienen malos.... y nuevamente a formatear por culpa de ese problema.....
por eso me he puesto a pensa ruq puede ser que yo instalo mal el SO

---

### Post by moreback on 2009-07-02
> **zhelo said:**
> resulta que ese chiste no me lo sabia xD
lo supe hace poco... pero tambien estaba pensando lo mismo
quisas soy yo quien crea los problemas......
pero es bastante raro, por que al menos una vez intalado ubuntu no hago nada malo.. solo aplico actualzaiciones automaticas y aveces esos mismos paquetes vienen malos.... y nuevamente a formatear por culpa de ese problema.....
por eso me he puesto a pensa ruq puede ser que yo instalo mal el SO

Creo que tu problema radica en que no entiendes lo que lees o simplemente tienes problemas con el inglés. Esto impide que sigas las instrucciones en pantalla y por eso después te queda la escoba.

¿Haz pensado en hacer un curso de inglés?

Saludos.

PD. te lo digo en buena, no es webeo.

---

### Post by zhelo on 2009-07-02
ingles???, cacho arto de ingles, pero que tiene que ver ??
si con suerte lo unico que ta en ingles es open office y la terminal
si el problema es que no leo la cosas que dice el terminar por que no comprendo los terminos....


----------------------------------------------------------------------------------------------------------------------------------------------
nunca he copiado un disco en ubuntu si en windows y al menos no he tenido problemas con eso (una vez paso algo pero ya se soluciono), en ubuntu solo he tenido problemas con la instalacion de paquetes, ya que todos vienen rotos, al mover archivos no he tenido error...

---

### Post by CdK1 on 2009-07-02
He visto dos pantallazos con "dpkg ....." eso tienes que ejecutarlo, además ya que tienes tantos dramas de packages, tú disco está bueno?

---

### Post by radixs on 2009-07-02
Mencionaste que tienes amigos con ubuntu y no tienen problemas,  creo que como son mas cercanos a ti podrian darte un mano ;)

---

