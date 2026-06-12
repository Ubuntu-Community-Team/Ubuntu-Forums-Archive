---
title: "Pad Multi Touch"
date: 2008-08-31
forum: Hardware
---

### Post by her_48 on 2008-08-31
Hola

¿Hay alguien que haya  experimentado con pads multi-touch caseros en argentina?

Estuve haciendo algunas indagaciones en [http://www.nuigroup.com/](http://www.nuigroup.com/) donde figuran algunos tutoriales muy interesantes usando proyector, webcam e IRs.

 Pero antes de largarme a experimentar a lo grande hice una prueba piloto con un pad super economico que se describe en [http://www.youtube.com/watch?v=pQpr3W-YmcQ](http://www.youtube.com/watch?v=pQpr3W-YmcQ) y el software touchlib ([http://nuigroup.com/touchlib/](http://nuigroup.com/touchlib/)).

Bueno, si alguien hizo alguna prueba por estos lares me gustaría contactarme para intercambiar info.
Gracias, Hernán

---

### Post by User21 on 2008-09-01
Yo había intentado esto de la cajita multitouch en Win, hace un par de meses. No obtuve los resultados que hubiese deseado, ya que todo esto es muy experimental, especialmente con materiales que no son mas que REBUSCADOS intentos de suplir elementos de precisión manufacturados por empresas de tecnología de punta (muy restrictivas en cuanto a especificaciones técnicas). 
Pero voy a re intentarlo, con el** [tutorial]("http://www.multitouch.nl/documents/multitouchdisplay_howto_070523_v02.pdf")** que nos dan alli, el cual parece estar bien detallado y explicado, por lo que estuve leyendo recien. 
Mi correo es [email]nouserfound@gmail.com[/email] y realmente voy a probarlo.

---

### Post by User21 on 2008-09-16
En el archivo adjunto, está lo que obtuve con la información de [http://nuigroup.com/wiki/Installing_Touchlib_on_Ubuntu/](http://nuigroup.com/wiki/Installing_Touchlib_on_Ubuntu/)

Pero ahora ya no se más que hacer ni como ejecutarlo..!


AAAPH! Ya encontre como:
estan todos los ejecutables dentro de /usr/src/multitouch/demos/... por alli, los vas a ver en color verde en la consola..! Ahora me pongo a construir la cajita! :)

Ya tendré novedades de si funciona o no... u_U

---

### Post by User21 on 2008-09-16
Todos los ejecutables estan en /usr/src/multitouch/demos y en /usr/src/multitouch/src , siempre y cuando lo hayas hecho como hice en el archivo txt.

Para calibrarlo, usé el ejecutable /usr/src/multitouch/src/configapp y de alli, una vez obtenido el resultado de captura deseado,apretando enter se procede a la calibracion. Es muy importante el angulo y condiciones de luz, para conseguir un PUNTO DE CONTACTO (con los dedos, no?) preciso y capturable por el software. 

El proceso de calibración es algo DENSO, pero la cuestión es que con la webcam (o con la mia), no puedo obtener un FRAME o GRID de trabajo confiable, de modo que la calibración detecte los limites de captura y los 8, 12 o 16 o cuantos quieras, PUNTOS INTERMEDIOS de la parrilla de coordenadas. Por otro lado, SI DETECTA el movimiento y en consecuencia, mueve los PUNTOS que hay en los demos de los programas, y cosas asi. 

En algún punto de la instalacion me pidió OSC, que se puede compilar obteniendo el codigo fuente de su sitio oficial [http://www.audiomulch.com/~rossb/code/oscpack/]("http://www.audiomulch.com/%7Erossb/code/oscpack/") pero no es del todo importante. 

En definitiva, ahora no tengo el tiempo, los materiales y las herramientas, para intentar hacer un PAD preciso, pero deberia funcionar perfectamente. 
O soy un inutil, o los que usan la "cajita" son unos PROs. xD Por que hacen la cajita en minutos, y después tienen todo andando.

Ante cualquier consulta, no duden en preguntar, pero basicamente está todo el proceso en el archivo txt.
Llevar a cabo un TouchPad Casero PRECISO, requiere muuucho tiempo de ensayo y error, ademas de paciencia y materiales idóneos.

---

### Post by User21 on 2008-09-16
**Una idea totalmente radical**: Hacer que en lugar de puntos de contacto en una superficie, el software asuma spots de luz, como los "[BLOBS]("http://nuigroup.com/wiki/Blob_Detection/")". 
Colocando la webcam encima del monitor, y con una especie de guante con LEDS en la punta de los dedos, la webcam reconoce perfectamente los puntos de luz en un rectangulo inmediatamente frontal al centro de enfoque. Los leds deben ser lo suficientemente poderosos como para generar un punto de luz constante, pero no tan brillante como para saturar la lente. A la inversa del "tradicional" proceso de captura, en este método se necesita escasa luz ambiental.
Es funcional, pero nada "ergonómico" :P Además, si era dificil la calibración en una superficie, imaginense en al aire! xD

---

### Post by zeroadrenaline on 2008-09-17
Che muy bueno, yo andaba a la busqueda de algo parecido, nececito un tablet para poder escribir, y que interperte caracteres, como el touch screen de una palm, algo asi, para ahorrar papel cuando hago ejercicios para la facultad, la intencion es que me los guarde en formato texto, y no en imagen, asi pesan poco, pero si se puede en imagen, bueno un 8 bits en b & w no me joderia tanto.
Saben si se puede hacer algo asi en Ubuntu?.

---

### Post by ich.zazen on 2008-09-17
Si, se puede. No se si habrá un software que haga ya reconocimiento de carácteres a mano alzada, pero sinó... preparate para Integrar, negro!
Capaz te vendria bien echarle un vistazo a OCRA o a Kooka, para ver como funcianan, pero creo que vá' a tené' q laburar

---

### Post by ich.zazen on 2008-09-17
Estuve viendo un poco... existe CellWriter, en los repositorios oficiales, que capaz te sirven (les sirven), es para traducir de escritura de mano alzada a Texto Plano.
Es para echarle un ojo. (o una mano, ya que estamos) (si es alzada mejor)

---

### Post by daggaz on 2009-12-22
Hola.
Pues traté de incursionar en esto y fracasé rotundamente.
No puedo compilar el famoso programita y hasta moví algo que no debí haber movido. 
Junto a mi Update Manager hay un botón rojo que dice:
```
No se ha podido calcular la actualización
Ha ocurrido un problema imposible de corregir cuando se calculaba la actualización.

Por favor, informe de ésto como un fallo del paquete «update-manager» e incluya el siguiente mensaje de error:
'E:Error, pkgProblemResolver::Resolve generó cortes, esto puede haber sido causado por paquetes retenidos.'
```

Borré algunas cosas en los orígenes de software y ya...

En fin... Cuando trato de hacer cmake dice:

 ```
sudo cmake .
-- Checking GNUCXX version 3/4 to determine  OpenCV /opt/net/ path
CMake Error at CMakeModules/FindOpenCV.cmake:239 (MESSAGE):
  OpenCV required but some headers or libs not found.  Please specify it's
  location with OpenCV_ROOT_DIR env.  variable.
Call Stack (most recent call first):
  CMakeLists.txt:5 (FIND_PACKAGE)


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!
```



¿Alguno de ustedes pudo al final hacerla trabajar? ¿como sería sobre Karmic? Muchas de las dependencias parecen ya no existir o no ser compatibles : S

---

