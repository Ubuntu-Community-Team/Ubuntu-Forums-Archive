---
title: "Problema al redimensionar partición a la izquierda."
date: 2009-08-13
forum: Hardware
---

### Post by daggaz on 2009-08-13
Hola.

Bueno, estoy pasando por un mal rato. Soy nuevo por aquí, antes pertenecía a la comunidad de Ubuntu-es que de un día para el otro desapareció.
Mi problema es el siguiente:
Resulta que a pesar de tener un bonito DD de 300Gb particionado en dos (o más), para Windows/Ubuntu, dejé de usar Windows y se hecho a perder solito. Pero me daba igual. Hasta hace poco tiempo que me vine a quedar sin espacio en el Disco Duro (trabajo con audio y video).
Quise aumentar el tamaño de mi parición de Ubuntu eliminando la de Windows (que era creo que la primer partición del disco duro), y pues fue imposible.
Busqué información y no encontré mucho; así que publiqué un post en el foro de Ubuntu-es y tuve una respuesta bastante acertada. Justo cuando me disponía a imprimir el tutorial me di cuenta que no había más Ubuntu-es. Así que decidí esperar.
Hoy mi DD se llenó de nuevo y me puse a borrar basura, pero me colmó la paciencia y busque en el caché de Google mi post.
Me di a la tarea de seguir el siguiente tutorial:
> Redimensionar Partición Hacia la Izquierda

Enviado por daggaz el Sáb, 25/07/2009 - 23:34 Foro general

Hola.
Ya hace algunos meses que trabajo con Ubuntu y me deshice por completo de Güindous, por que según era pirata (¡mentira!), y bueno, luego de algún tiempo mi disco duro (DD) se empezó a llenar. Es el momento en el que tengo 45 Gb absurdos al inicio de mi DD.
Intenté aumentar el tamaño de la partición para Ubuntu para que usara todo el Disco pero no he podido. La Swap está entre el espacio en blanco y Ubuntu; sumado a esto el espacio en blanco está al inicio de mi disco, y por ahí me enteré de que es complicado eso de aumentar tamaño de una partición hacia la izquierda, no sé si por cuestiones del Swap o por que tendría que desfragmentarse todo el DD.
No quiero formatear el espacio vacío para hacer otro disco externo simulado (o como se le llame); En realidad lo que quiero es aumentar mi espacio destinado a Ubuntu, pues me quedan como 7 Gb de espacio y como trabajo con audio y video, esto es un verdadero dolor de cabeza; esos 45Gb más me vendrían muy bien.
¿Alguna opción que no sea Partitio-Magic? (no tengo más Güindous)
‹ Ubutnu 9.04 se cuelga o se pega No puedo hacer más pequeñas algunas ventanas ›
» Inicie sesión o regístrese para enviar comentarios
Opciones de visualización de comentarios
Seleccione la forma que prefiera para mostrar los comentarios y haga clic en «Guardar las opciones» para activar los cambios.
Imagen de Gabriel Muñoz - gmunioz
Live-cd
Enviado por Gabriel Muñoz -... el Dom, 26/07/2009 - 00:15

Hola dag...:

Inicia el ordenador con el live-cd.

Desmonta las particiones.

Carga el editor de particiones.

Borra la particion de intercambio y la

de Windows.

Crea al comienzo una nueva partición swap. 
El sistema de archivos es intercambio. 
¿Cuanto debería de pesar? 
Hay opiniones encontradas, 
particularmente uso 1 giga mas entre 1 y 2 estaría bien, 
no más de 2 gigas.

Aumenta el tamaño de tu partición con el resto

libre.

Aplica los cambios.

Averigua la uuid de tu partición ampliada.
sudo fdisk -l
(Para averiguar el nombre de las particiones)
sudo vol_id --uuid /dev/sdxx
Para averiguar la uuid de la partición

Monta la partición de ubuntu.

Edita el archivo /etc/fstab

Cambia al nuevo valor de /dev/sdax

correspondiente a swap

controla la uuid de tu partición de ubuntu

si cambio, cambiala por los valores correctos.

sudo gedit /etc/fstab
luego busco el valor: «/dev/sdax» ¿y luego? ¿qué le pongo?
Buscas algo como:
# none was on /dev/sda6 during installation
UUID=0c91d704-8d26-46a8-a39c-b2c8bf663922 none swap sw 0 0
Dado que si borras y vuelves a crear, /dev/sda6 pasaria a ser
quizas /dev/sda1 cambias el 6 por el 1 o lo que sea y el valor
que sigue a UUID= por el nuevo que corresponde

Lo mismo para la partición de Ubuntu , / si bien seguirá
siendo la misma /dev/sdax, su uuid quizás haya cambiado.

Guarda el archivo y reinicia.

Saludos.
Gabriel.

Hice todo esto hasta la parte en la que debo aumentar el tamaño de la partición. Todo iba muy bien, tardó cerca de una hora (o un poco más) y entonces recibí el primer mensaje de error. Guardé el resumen pero ahora no lo encuentro ¿es necesario? Lo intenté una vez más y lo mísmo. Luego intenté solo mover la partición hacia la izquierda y otro error justo un minuto antes de que terminara: Decía que había habido un error al mover unos números. 
Bueno, lo intenté guardar (el resumen) en otro USB pero no pude, y creí que podría encontrarlos después; pero no puedo. Tendría que iniciar de nuevo con el Live-CD (Live-USB) y buscarlos, me supongo. 
En fin, al momento de reiniciar no hubo problemas; pero mi partición sigue pegada al final de mi DD y no puedo usar este maldito espacio vacío que dejó Windows.

---

### Post by staar on 2009-08-13
serían importantes los reportes del error, como para darnos una ides de que puede estar pasando, la swap ya la moviste?

saludos

---

### Post by daggaz on 2009-08-13
OK.
Definitivamente amo Ubuntu. Sí algo así hubiera sucedido en Güindos estaría frito.
De nuevo inicié en modo Live y encontré los reportes, son tres y los tres son un tanto diferentes.
En el primero intenté seguir los pasos uno por uno según me había indicado Gabriel, pero al momento de aumentar el tamaño fue cuando vino el error. La segunda vez básicamente hice lo mismo pero volviendo a desmontar todo, incluida la swap. Y la tercera vez solo intenté recorrer la partición a la izquierda sin aumentarla de tamaño.
> 
GParted 0.4.3
 Libparted 1.8.8
    **Mover /dev/sda5 a la izquierda y ampliarlo de 266.56 GiB a 296.14 GiB**  01:49:16    ( ERROR )             calibrar /dev/sda5  00:00:00    ( ÉXITO )             [I]ruta: /dev/sda5
inicio: 66123603
fin: 625137344
tamaño: 559013742 (266.56 GiB)[/I]          calcular el tamaño nuevo y la posición de /dev/sda5  00:00:00    ( ÉXITO )             [I]inicio solicitado: 4096638
fin solicitado: 625137344
tamaño solicitado: 621040707 (296.14 GiB)[/I]       [I]nuevo inicio: 4096638
nuevo final: 625137344
tamaño nuevo: 621040707 (296.14 GiB)[/I]          comprobar errores en el sistema de archivos en /dev/sda5 y (si es posible) arreglarlos  00:16:08    ( ÉXITO )             ***e2fsck -f -y -v /dev/sda5***             [I]Paso 1: Verificando nodos-i, bloques y tamaños
Paso 2: Verificando la estructura de directorios
Paso 3: Revisando la conectividad de directorios
Paso 4: Revisando las cuentas de referencia
Paso 5: Revisando el resumen de información de grupos

  326958 inodes used (1.87%)
   18067 non-contiguous files (5.5%)
     439 non-contiguous directories (0.1%)
         # de nodos-i con bloques ind/dind/tind: 50377/14372/2
64116469 blocks used (91.76%)
       0 bad blocks
       6 large files

  272081 regular files
   30199 directories
      69 character device files
      26 block device files
       4 fifos
     661 links
   24557 symbolic links (21357 fast symbolic links)
      13 sockets
--------
  327610 files
[/I]       [I]e2fsck 1.41.4 (27-Jan-2009)
[/I]             mover partición a la izquierda  00:00:10    ( ÉXITO )             [I]inicio antiguo: 66123603
fin antiguo: 625137344
tamaño antiguo: 559013742 (266.56 GiB)[/I]       [I]nuevo inicio: 4096638
nuevo final: 563110379
tamaño nuevo: 559013742 (266.56 GiB)[/I]          mover el sistema de archivos a la izquierda  01:32:47    ( ERROR )             realizar comprobación de sólo lectura  01:32:47    ( ERROR )             usando algoritmo interno       leídos 559013742 sectores       buscando tamaño de bloque óptimo             leer 65536 sectores usando un tamaño de bloque de 128 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.749519 segundos*          leer 65536 sectores usando un tamaño de bloque de 256 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.618095 segundos*          leer 65536 sectores usando un tamaño de bloque de 512 sectores  00:00:00    ( ÉXITO )             *65536 de 65536 leídos*       *0.711528 segundos*          leer 65536 sectores usando un tamaño de bloque de 1024 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.623462 segundos*          leer 65536 sectores usando un tamaño de bloque de 2048 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.606668 segundos*          leer 65536 sectores usando un tamaño de bloque de 4096 sectores  00:00:00    ( ÉXITO )             *65536 de 65536 leídos*       *0.592623 segundos*          leer 65536 sectores usando un tamaño de bloque de 8192 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.727926 segundos*          leer 65536 sectores usando un tamaño de bloque de 16384 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.697125 segundos*          leer 65536 sectores usando un tamaño de bloque de 32768 sectores  00:00:00    ( ÉXITO )             *65536 de 65536 leídos*       *0.79509 segundos*          leer 65536 sectores usando un tamaño de bloque de 65536 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.748773 segundos*          El tamaño de bloque óptimo es 4096 sectores (2.00 MiB)          leer 558358382 sectores usando un tamaño de bloque de 4096 sectores  01:32:40    ( ERROR )             *532823918 de 558358382 leídos*       *Error al leer el bloque en el sector 599602881*          533479278 sectores leídos             deshacer el último cambio en la tabla de particiones  00:00:11    ( ÉXITO )             mover partición a la derecha  00:00:11    ( ÉXITO )             [I]inicio antiguo: 4096638
fin antiguo: 563110379
tamaño antiguo: 559013742 (266.56 GiB)[/I]       [I]nuevo inicio: 66123603
nuevo final: 625137344
tamaño nuevo: 559013742 (266.56 GiB)[/I]             mensajes de libparted    ( INFO )             *Error de entrada/salida durante la lectura en /dev/sda*          ========================================

> 
GParted 0.4.3
 Libparted 1.8.8
    **Mover /dev/sda5 a la izquierda y ampliarlo de 266.56 GiB a 296.14 GiB**  01:49:12    ( ERROR )             calibrar /dev/sda5  00:00:00    ( ÉXITO )             [I]ruta: /dev/sda5
inicio: 66123603
fin: 625137344
tamaño: 559013742 (266.56 GiB)[/I]          calcular el tamaño nuevo y la posición de /dev/sda5  00:00:00    ( ÉXITO )             [I]inicio solicitado: 4096638
fin solicitado: 625137344
tamaño solicitado: 621040707 (296.14 GiB)[/I]       [I]nuevo inicio: 4096638
nuevo final: 625137344
tamaño nuevo: 621040707 (296.14 GiB)[/I]          comprobar errores en el sistema de archivos en /dev/sda5 y (si es posible) arreglarlos  00:16:15    ( ÉXITO )             ***e2fsck -f -y -v /dev/sda5***             [I]Paso 1: Verificando nodos-i, bloques y tamaños
Paso 2: Verificando la estructura de directorios
Paso 3: Revisando la conectividad de directorios
Paso 4: Revisando las cuentas de referencia
Paso 5: Revisando el resumen de información de grupos

  326958 inodes used (1.87%)
   18067 non-contiguous files (5.5%)
     439 non-contiguous directories (0.1%)
         # de nodos-i con bloques ind/dind/tind: 50377/14372/2
64116469 blocks used (91.76%)
       0 bad blocks
       6 large files

  272081 regular files
   30199 directories
      69 character device files
      26 block device files
       4 fifos
     661 links
   24557 symbolic links (21357 fast symbolic links)
      13 sockets
--------
  327610 files
[/I]       [I]e2fsck 1.41.4 (27-Jan-2009)
[/I]             mover partición a la izquierda  00:00:10    ( ÉXITO )             [I]inicio antiguo: 66123603
fin antiguo: 625137344
tamaño antiguo: 559013742 (266.56 GiB)[/I]       [I]nuevo inicio: 4096638
nuevo final: 563110379
tamaño nuevo: 559013742 (266.56 GiB)[/I]          mover el sistema de archivos a la izquierda  01:32:36    ( ERROR )             realizar comprobación de sólo lectura  01:32:36    ( ERROR )             usando algoritmo interno       leídos 559013742 sectores       buscando tamaño de bloque óptimo             leer 65536 sectores usando un tamaño de bloque de 128 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.631471 segundos*          leer 65536 sectores usando un tamaño de bloque de 256 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.673949 segundos*          leer 65536 sectores usando un tamaño de bloque de 512 sectores  00:00:00    ( ÉXITO )             *65536 de 65536 leídos*       *0.577654 segundos*          leer 65536 sectores usando un tamaño de bloque de 1024 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.557822 segundos*          leer 65536 sectores usando un tamaño de bloque de 2048 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.838146 segundos*          leer 65536 sectores usando un tamaño de bloque de 4096 sectores  00:00:00    ( ÉXITO )             *65536 de 65536 leídos*       *0.625954 segundos*          leer 65536 sectores usando un tamaño de bloque de 8192 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.73879 segundos*          leer 65536 sectores usando un tamaño de bloque de 16384 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.798874 segundos*          leer 65536 sectores usando un tamaño de bloque de 32768 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.73628 segundos*          leer 65536 sectores usando un tamaño de bloque de 65536 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.866691 segundos*          El tamaño de bloque óptimo es 1024 sectores (512.00 KiB)          leer 558358382 sectores usando un tamaño de bloque de 1024 sectores  01:32:28    ( ERROR )             *532825966 de 558358382 leídos*       *Error al leer el bloque en el sector 599604929*          533481326 sectores leídos             deshacer el último cambio en la tabla de particiones  00:00:11    ( ÉXITO )             mover partición a la derecha  00:00:11    ( ÉXITO )             [I]inicio antiguo: 4096638
fin antiguo: 563110379
tamaño antiguo: 559013742 (266.56 GiB)[/I]       [I]nuevo inicio: 66123603
nuevo final: 625137344
tamaño nuevo: 559013742 (266.56 GiB)[/I]             mensajes de libparted    ( INFO )             *Error de entrada/salida durante la lectura en /dev/sda*          ========================================

> 
GParted 0.4.3
 Libparted 1.8.8
    **Mover /dev/sda5 a la izquierda**  06:48:47    ( ERROR )             calibrar /dev/sda5  00:00:00    ( ÉXITO )             [I]ruta: /dev/sda5
inicio: 66123603
fin: 625137344
tamaño: 559013742 (266.56 GiB)[/I]          calcular el tamaño nuevo y la posición de /dev/sda5  00:00:00    ( ÉXITO )             [I]inicio solicitado: 4096638
fin solicitado: 563110379
tamaño solicitado: 559013742 (266.56 GiB)[/I]       [I]nuevo inicio: 4096638
nuevo final: 563110379
tamaño nuevo: 559013742 (266.56 GiB)[/I]          comprobar errores en el sistema de archivos en /dev/sda5 y (si es posible) arreglarlos  00:16:14    ( ÉXITO )             ***e2fsck -f -y -v /dev/sda5***             [I]Paso 1: Verificando nodos-i, bloques y tamaños
Paso 2: Verificando la estructura de directorios
Paso 3: Revisando la conectividad de directorios
Paso 4: Revisando las cuentas de referencia
Paso 5: Revisando el resumen de información de grupos

  326958 inodes used (1.87%)
   18067 non-contiguous files (5.5%)
     439 non-contiguous directories (0.1%)
         # de nodos-i con bloques ind/dind/tind: 50377/14372/2
64116469 blocks used (91.76%)
       0 bad blocks
       6 large files

  272081 regular files
   30199 directories
      69 character device files
      26 block device files
       4 fifos
     661 links
   24557 symbolic links (21357 fast symbolic links)
      13 sockets
--------
  327610 files
[/I]       [I]e2fsck 1.41.4 (27-Jan-2009)
[/I]             mover partición a la izquierda  00:00:11    ( ÉXITO )             [I]inicio antiguo: 66123603
fin antiguo: 625137344
tamaño antiguo: 559013742 (266.56 GiB)[/I]       [I]nuevo inicio: 4096638
nuevo final: 563110379
tamaño nuevo: 559013742 (266.56 GiB)[/I]          mover el sistema de archivos a la izquierda  06:32:11    ( ERROR )             realizar comprobación de sólo lectura  06:32:11    ( ERROR )             usando algoritmo interno       leídos 559013742 sectores       buscando tamaño de bloque óptimo             leer 65536 sectores usando un tamaño de bloque de 128 sectores  00:00:00    ( ÉXITO )             *65536 de 65536 leídos*       *0.668828 segundos*          leer 65536 sectores usando un tamaño de bloque de 256 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.673815 segundos*          leer 65536 sectores usando un tamaño de bloque de 512 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.700045 segundos*          leer 65536 sectores usando un tamaño de bloque de 1024 sectores  00:00:00    ( ÉXITO )             *65536 de 65536 leídos*       *0.568217 segundos*          leer 65536 sectores usando un tamaño de bloque de 2048 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.605313 segundos*          leer 65536 sectores usando un tamaño de bloque de 4096 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.726192 segundos*          leer 65536 sectores usando un tamaño de bloque de 8192 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.784087 segundos*          leer 65536 sectores usando un tamaño de bloque de 16384 sectores  00:00:00    ( ÉXITO )             *65536 de 65536 leídos*       *0.809109 segundos*          leer 65536 sectores usando un tamaño de bloque de 32768 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.783541 segundos*          leer 65536 sectores usando un tamaño de bloque de 65536 sectores  00:00:01    ( ÉXITO )             *65536 de 65536 leídos*       *0.957409 segundos*          El tamaño de bloque óptimo es 1024 sectores (512.00 KiB)          leer 558358382 sectores usando un tamaño de bloque de 1024 sectores  06:32:04    ( ERROR )             *532825966 de 558358382 leídos*       *Error al leer el bloque en el sector 599604929*          533481326 sectores leídos             deshacer el último cambio en la tabla de particiones  00:00:11    ( ÉXITO )             mover partición a la derecha  00:00:11    ( ÉXITO )             [I]inicio antiguo: 4096638
fin antiguo: 563110379
tamaño antiguo: 559013742 (266.56 GiB)[/I]       [I]nuevo inicio: 66123603
nuevo final: 625137344
tamaño nuevo: 559013742 (266.56 GiB)[/I]             mensajes de libparted    ( INFO )             *Error de entrada/salida durante la lectura en /dev/sda*          ========================================



---

### Post by daggaz on 2009-08-21
Se suma un feo problema:
No sé si Linux puede funcionar sin swap, pero parece que ya no me la reconoce, y en apariencia todo está bien. El único problema es ahora mi PC no puede hibernar. Cuanto lo intenta aparece una consola y dice que no se encontró la Swap, la pantalla se queda negra por unos segundos y después aparece el cuadro de incio de sesión.
¿Alguien sabe que pdoría hacer? Tampoco he conseguido redimensionar mi partición hacia la izquierda :<

---

### Post by daggaz on 2009-08-21
Ésta es una captura de pantalla de cómo se ve mi disco en Gparted; ya sé que sebe estar en Live-mode para poder hacer cualquier cambio, es solo para que se entienda mejor mi situación : /
[IMG]http://img512.imageshack.us/img512/6323/pantallazoisx.png[/IMG]

---

### Post by staar on 2009-08-21
primero, antes podías hibernar? porque el código para la hibernación que hay en el kernel no está demasiado desarrollado, muchas veces falla (por ejemplo en mi pc no puede) existe otro método, pero requiere la instalación de un kernel modificado (el tuxonice)

despues, los errores (de I/O) que te salieron al redimensionar pueden indicar que o el disco o el cable de datos están fallando, te recomendaría que bajes la herramienta de diagnóstico del fabricante de tu disco y le hagas un chequeo completo...

saludos

---

### Post by daggaz on 2009-08-21
Pues antes podía hibernar sin ningún problema, de hecho cuando quedaba poca batería prefería que el equipo hibernara en vez de apagarse, por que así me evitaba la perdida de datos o cualquier cosa. 
Y en cuanto a las herramientas de diagnóstico que mencionas, es una HP, buscaré en la p&#501;ania HP a ver que hay para Linux (si es que hay algo)...
Además, me parece que ya le hace falta un servicio a mi Lap, por que se está empezando a calentarse de más y luego se cuelga o se apaga sin previo aviso cuando es un día muy caluroso : / Creo que el ventilador puede estar sucio... 

¡Gracias!

PD: No cerraré el tema hasta resolver bien todo esto.

---

### Post by EnriqueK on 2009-08-21
El Gparted no es capaz de editar particiones tomando /cediendo espacio de particiones situadas a la izquierda , solo lo puede hacer si se encentrq a la derecha o sea al final y colindante .
Veo dos posivles soluciones
1.- Te conseguíns algún Live de win como ser el Hiren's Boot CD , usas el Partirion Magic y movés el espacio vacío al final y de paso borrás y creas otra Swap por que la ubicación que tiene no la veo bien,  o sea creo que no deberñia estar en la primer partición. Luego de terminado esto y que puede durar muchísimo , inicias tu equipo con el Live CD de Ubuntu y ahora si Gparted podrá actuar tomando espacio de la particiñon no asignada.
2.- Otra posibilidad es que simplemete formatees el espacio  no asignado en EXT3 , luego le das los permisos al punto de montaje y hacé que monte al inicio .

---

### Post by daggaz on 2009-08-21
Bueno. En teoría sí es posible hacer esto con Gparted. Por qué lo hizo casi todo. 
Voy a probar eso que me dices, el problema será conseguir el disco de Güindous; me supongo que lo venden en miles de dólares como es su costumbre. Si no buscaré por la red a ver qué encuentro; pero la verdad prefiero no meterme con Güindous por ahora.
Gracias

---

