---
title: "Xubuntu en un viejo Ibook 2001"
date: 2009-09-19
forum: Hardware
---

### Post by daggaz on 2009-09-19
Hola.
Bueno, esto inició hace ya varios meses, cuando intenté instalar Ubuntu en mi viejo Ibook G3 con procesador PPC.
Bajé la versión para dicha arquitectura, pero tanto en el live CD como en la versión instalada en el DD había un extraño problema con el monitor, no sé si no reconocía el video o qué; el caso es que el monitor aparecía divido en cuatro, muy raro, en la parte inferior derecha se veía como una repetición de lo de arriba, como si fuera un mosaico de repetición de un pequeño monitor; las dos partes de la derecha (más pequeñas que las de la izquierda) estaban en negro.
Bueno, esto funcionó así por un rato hasta que me fastidió y le reinstalé el Mac OS X 3.9, cosa que no me gusta mucho por que no puedo instalar nada ya no hay ningún programa para esa versión de Mac OS.
Recientemente instalé Xubuntu en una muy vieja Dell y me gustó mucho como trabajaba, mucho más veloz incluso que el Win98 que tenía antes. Por lo tanto pensé que Xubuntu sería mejor para esta pequeña PPC que tiene como 220 de ram y unos 10 de disco duro; no recuerdo la velocidad del procesador, pero es un G3 si no mal recuerdo (puede ser G4).
El caso es que intento iniciar el Live CD (con la versión para PPC) y sucede el mísmo problema que con Ubuntu (el monitor partido en cuatro); luego inicio con una opción que es algo así como «videofonly» o algo así, y incia ahora sí con elmonitor completo pero con un horrible gris y azul, como siu tuviera solo dos colores, supogo que algún error en los colores, no sé. Era dificil de leer incluso, pero llego a la config del monitor y no hay nada que modificar.
Bajé despiués el alternate CD de Xubuntu 9.04 y lo intento instalaar, parece ir todo bien, pero la interfaz es muy... ¿como decirlo? poco amistosa. Todo me recuerda al viejo MSDOS, gris con rojo y azul y sin mouse.
Se trabó un buen rato revisando la «replica» en el 43%...Luego como una hora más instalando...
Por fin terminó y cuando me pidio reiniciar me topo con el mísmo problema de antes, un monitor dividido con una supuesta resolución de 600x800 que no puedo cambiar más que a 640x480 pero si aplico este cambio la imagen se vuelve blanca y no puedo ver nada más.
No sé si trate de un controlador privativo. ¿Alguien tiene alguna idea?
Si meaconsejan les pido que sean claros y me den instrucciones paso a paso, aún no soy un experto en esto de Linux.
Gracias

PD:
Estas son unas fotografías que tomé del monitor, no puedo hacerlo mediante captura de pantalla pues sale una captura normal.

[IMG]http://img17.imageshack.us/img17/2553/1004459l.jpg[/IMG]

[IMG]http://img42.imageshack.us/img42/8673/1004458o.jpg[/IMG]

---

### Post by Hei Ku on 2009-09-19
Probaste configurar a mano el xorg.conf con la resolucion y el refresco del monitor?

Si no sabes, vas a tener que conseguir los datos del monitor, y luego postea aca el contenido de tu archivo /etc/xorg.conf y te damos una mano.

Aunque con hardware tan viejo, quien sabe si anda.

---

### Post by daggaz on 2009-09-19
Hola.
Pues según he estado viendo en intenet en algunos foros sí hay personas que han logrado correr Linux en estas viejas maquinitas. Yo la quiero principalmente para navegar o escuchar música, tiene un lector de DVD y buena targeta de sonido.
Y bueno... busqué el archivo que mencionas pero no lo encontré, si lo abro mediante la terminal con mousepad me aparece un archivo en blanco. ?Qué significará esto? (Acabo de descubrir que no sé cómo escribir el signo de interrogación de apertura aquí, aún tengo muchas cosas que aprender).
Las propiedades del monitor (12" 1024 x 768) las encontré aquí:
[http://lowendmac.com/pb2/12in-ibook-g3-500-mhz.html](http://lowendmac.com/pb2/12in-ibook-g3-500-mhz.html)

---

### Post by Hei Ku on 2009-09-19
en una terminal poné:

cat /etc/X11/xorg.conf

---

### Post by daggaz on 2009-09-19
Intenté con ''Cat'' y no pasó nada, luego con sudo antes, pero igual. No me decía no haber encontrado nada, pero tampoco hacía nada. 
Luego probé con ''Catfish'' y resultó, buscó el archivo y encontró uno que pesaba 0kb, lo abro y está vacío igual que antes.
Algo está muy raro...
En caso de no resultar esto tampoco ?alguna otra distro de Linux que pueda funcionar para estos casos? : <

---

### Post by Hei Ku on 2009-09-19
cat, no Cat. Y para esa maquina, quizas puedas probar con Lubuntu, que esta en Alpha, pero anda bastante bien.

---

### Post by daggaz on 2009-09-20
Hola.
Bueno; de hecho sí escribí "cat" no "Cat ", perdón.
Y estube buscando información sobre Lubuntu, encontré cosas interesantes y una versión más estable llamada U-lite o Ubulite. El problema es que ningúna de estas distros funcionan con la arquitectura PPC : < O no es fácil de encontrar la forma de hacerlos funcionar.
Seguiré investigando y les contaré como me fue.
Ya se convirtió en un reto hacer revivir esta vieja máquina con la ayuda de Linux, de verdad no quiero tirarla al basurero.

---

### Post by pablo.s on 2009-09-20
Un problema puede ser que
los drivers que está utilizando 
sean los VESA. Fijate que este
modelo de Mac en particular
tiene una placa de video ATI
Rage Mobility 128, asi que una
de las cosas que debes constatar
es si está disponible algún driver
legacy para esta placa.
A partir de que encuentres el
driver lo que resta es configurar
a mano ciertos parametros del
xorg.conf, como dice Hei Ku.

---

### Post by daggaz on 2009-09-20
Ah, esto sí es nuevo. Voy a buscar ese driver.
Otra cosa es que no me está gustando mucho la cantidad de recursos del CPU que utiliza Xubuntu; Sé que es de lo más liviano, no sé si haya alguna mala configuración, pero es muy lento...

Gracias.

---

### Post by pablo.s on 2009-09-20
Es probable que si le
instalas desde Synaptic
todos los paquetes de
LXDE sea similar a Lubuntu.

---

### Post by josecuervo86 on 2009-09-20
> **pablo.s said:**
> Es probable que si le
instalas desde Synaptic
todos los paquetes de
LXDE sea similar a Lubuntu.

El otro dia probe en una VM la instalación basica de Ubuntu (solo consola) y arriba le "chante" LXDE y anda muy bien! Realmente es recomendable para maquinas viejitas.

---

