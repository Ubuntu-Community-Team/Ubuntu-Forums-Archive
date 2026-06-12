---
title: "[SOLVED] Escuchar el mic frontal en notebook compaq"
date: 2009-02-04
forum: Hardware
---

### Post by ideafix on 2009-02-04
Buenas gente, que tal, hace rato que no tenia problemas pero esta vez me maree. Ahora que me pase a las notebooks, tengo una compaq v3918. El tema es asi, la entrada de microfono funciona pero hasta ahi nomas. No escucho lo q hablo cuando enchufo el mic, pero se q algo agarra porq si grabo con algun programa de grabacion toma la entrada, pero como si tomara un solo canal (no en estereo) :(.
La salida de lspci da esto:
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
Probe todas las combinaciones que me da el control de volumen, pero nada.
Los microfonos incorporados (los q estan arriba de la pantalla) andan de 10, asi que ni idea. Estoy bastante perdido.
Desde ya gracias:D

---

### Post by ideafix on 2009-02-11
Aporto mas datos a la causa: Fui a Sistema>Preferencias>Sonido y trate con todas las combinaciones posibles, pero no pasa nada, no escucho la entrada de linea. Lo curioso es q cuando le digo probar en el desplegable de Captura de Sonido es como que por un segundo parece que arranca, pero luego..nada. Sigo googleando pero los poquisimos post con problemas similares estan sin resolver. Saludos.

---

### Post by ideafix on 2009-04-07
la tercera es la vencida....
estaba pensando, no habra algun programa q haaga un by-pass digamos, entre la entrada del mic y la salida de auriculares? Ya que asi no encuentro nada, por ahi por algun prgrama "emule" de alguna manera esto.

---

### Post by pablo.s on 2009-04-07
Y como sabés que el microfono funciona?
Probaste con otro? No será ese el problema?

---

### Post by ideafix on 2009-04-08
Lo se porque

> No escucho lo q hablo cuando enchufo el mic, pero se q algo agarra porq si grabo con algun programa de grabacion toma la entrada, pero como si tomara un solo canal (no en estereo)

Lo de un solo canal era el cable ja perdon no me di cuenta q era jack mono.

---

### Post by pablo.s on 2009-04-08
Hola: No entiendo cual es el problema
realmente. No escuchás lo que grabás?
No se que programa usas para grabar,
asi que no te puedo ayudar. No aclarás
lo suficiente, cuando uno graba digamos,
con Audacity, tiene lo que se llama
"retorno" pero no logro dilucidar que 
pasa con lo que estás probando.

A ver si pintás un poco mejor la
cuestión, contá que es lo que tratás de
grabar, que placa es, que micrófono
usás, que software... 
Saludos.

---

### Post by ideafix on 2009-04-16
a ver, voy por pasos:
mi placa es
 . salida del lspci:
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
 . salida de lshw:
*-multimedia
          description: Audio device
          product: MCP67 High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel

La notebook trae microfonos integrados en la pantalla, a los costados de la webcam, funcionan perfecto. Trae una entrada de microfono, en la parte del teclado digamos, al frente. Bien, cuando enchufo un microfono ahi, supuestamente si habilito el control de volumen del mic y lo subo deberia escuchar por los parlantes integrados lo q capte el mic. Eso no sucede.
Probe: con un microfono normal, el de pc tipico. Con el cable de mi bajo, directo, y desde la salida del amplificador. Conectando la salida de mi radio. En todos los casos sucede q si abro el Grabador de Sonido NO ESCUCHO que estoy grabando, pero VEO q la barra de nivel se mueve. Al finalizar de grabar, si le doy reproducir, AHI SI escucho lo que grabe normalmente, como si escuchara un mp3 o algo.
Como no he encontrado solucion a esto (salvo las q aclare q probe y no funcionaron, y creo q me falto nombrar una q tenia q editar un archivo y poner intel en algun lado, q tampoco funciono) pense que podria haber un programa q: capte lo q entra por el microfono, y lo envie a la salida de auriculares, la que esta en el frente al lado de la entrada de microfono. Espero q me haya quedado mejor. Gracias!!!

---

### Post by pablo.s on 2009-04-17
> **ideafix said:**
> 
Como no he encontrado solucion a esto (salvo las q aclare q probe y no funcionaron, y creo q me falto nombrar una q tenia q editar un archivo y poner intel en algun lado, q tampoco funciono) pense que podria haber un programa q: capte lo q entra por el microfono, y lo envie a la salida de auriculares, la que esta en el frente al lado de la entrada de microfono. Espero q me haya quedado mejor. Gracias!!!

Probate TODOS estos programas:

--Audacity
--Jokosher
--Ardour

Y si te dedicás a grabar mucho
podés considerar la instalación
de [Ubuntu Studio]("http://ubuntustudio.org/downloads"), que es una
distribución especializada para
músicos.

---

### Post by ideafix on 2009-04-29
Con Audacity pude hacer en parte lo que queria. Escucho y grabo al mismo tiempo, asi tuve que dejar la configuracion

[[IMG]http://img301.imageshack.us/img301/2177/pantallazogat.th.png[/IMG]](http://img301.imageshack.us/my.php?image=pantallazogat.png)

Ahora tengo otra duda. Jack control no sirve para lo que quiero? . O sea, esta bien esto de escucharme, pero el tema de estar grabando constantemente.... Y si por ejemplo quiero usar un programa como Creox, estoy muerto. Igual, algo es algo. Gracias!!!

---

### Post by pablo.s on 2009-04-29
Jack control es un panel de control
para el servidor de sonido jack, que
es de baja latencia y lo utilizan
algunos programas, pero Audacity
no. Creo que es un servidor para
tareas MIDI.

---

### Post by ideafix on 2009-05-10
Ahi probe, pero no tengo el soporte para tiempo real (necesito el kernel rt), asi que voy a probar el Ubuntu Studio (tengo el musix, pero no consigo nada nuevo.). Gracias, igual no doy al tema como solucionado, porq en realidad estoy viendo alternativas. Si encuentro alguna solución luego la posteo. Saludos!!

---

### Post by ideafix on 2009-07-01
Solucionado.

Con ayuda de JACK Control logre exactamente lo que queria. Paso a describir

1: abrir JACK Control
2: click en Iniciar
3: click en Conexiones
4: establecer las conexiones asi (es arrastrar desde el panel derecho al izquierdo, como un juego de uniendo con lineas ja)

[[IMG]http://img188.imageshack.us/img188/1354/pantallazoapr.th.png[/IMG]](http://img188.imageshack.us/i/pantallazoapr.png/)

y listo, estan escuchando lo que entre por la captura frontal de la notebook.

Un par de observaciones:
-Lo probe en Ubuntu Studio, porque lei que necesitaba soporte para real time en el kernel para que JACK funcionara bien. Pero en versiones anteriores de Ubuntu 7.x andaba, asi que no se cuanto sera cierto. Creo que la clave es configurarlo bien. Yo lo tengo asi, despues de googlear un poco :
[[IMG]http://img21.imageshack.us/img21/2779/pantallazo1h.th.png[/IMG]](http://img21.imageshack.us/i/pantallazo1h.png/)

-Si abren otro programa (por ejemplo Hydrogen) les aparecera como opcion en los desplegables. Entonces hacen lo mismo y pueden tocar arriba de las bases q armen o cosas asi ;)

Saludos!!!

---

### Post by pablo.s on 2009-07-01
Eh, tarde pero seguro!
Te animás a escribir un
tutorial bien bien detallado 
para que los compañeros
aprendan cómo se hace
la configuración de Jack?

---

### Post by ideafix on 2009-07-11
Sigo tarde pero seguro ja! La verdad que no me siento capaz como para hacer una guia sinceramente, lo mio es lo que se diria...verguenza deportiva jaja.

Lo que puedo sugerir son unos links que me ayudaron (hay bastante en ingles), y decir que por lo que vi la configuracion de jack depende de la placa que tengamos, lo que lleva a un sinfin de configuraciones distintas. Y otro tanto aparecen cuando se busca reducir la latencia. Mucho tocar y probar hasta que ande. Paciencia, a mi me llevo bastante ;) pero ahora se disfruta. Saludos!

[http://www.musix.org.ar/wiki/index.php/Audio-Edicion-Es#2.29_Configuramos_JACK](http://www.musix.org.ar/wiki/index.php/Audio-Edicion-Es#2.29_Configuramos_JACK)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://www.musix.org.ar/wiki/index.php/JACK](http://www.musix.org.ar/wiki/index.php/JACK)

[http://www.64studio.com/quickstart_jack](http://www.64studio.com/quickstart_jack)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

---

