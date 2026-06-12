---
title: "Saca el rendimiento escondido de tu vieja ATI Radeon 7X00 y similares"
date: 2009-05-22
forum: Hardware
---

### Post by AlexDDR on 2009-05-22
> [I]:KS "El siguiente post lo he migrado a peticion de Carlos C. desde el antiguo foro de ubuntu-cl.org, y lo he traido hasta acá, pero debido a los avances en materia de driver y xorg de ubuntu 9.04 algunos comando pueden o son innecesarios. Osea solo lo he  completamente probado en Ubuntu 9.04 ya que algunos comandos los he ido actualizando en el tiempo y me he actualizado a ubuntu 9.04 y es la mejor versión que he probado de ubuntu, asi que ya no los puedo probar en versiones anteriores. Además he aprovechado de reorganizarlo y actualizar varias partes"
El antiguo post se encuentra aquí
[http://foros.ubuntu-cl.org/viewtopic.php?t=7050&postdays=0&postorder=asc&start=0](http://foros.ubuntu-cl.org/viewtopic.php?t=7050&postdays=0&postorder=asc&start=0)
[/I]

    Hola ha todos busqué y busque hasta que encontre la forma de mejorar el redibujado de las aplicaciones de pantalla en GNOME, que siempre habia criticado lo lento del redibujado de las aplicaciones del escritorio, además de lo lento que funcionaba firefox y otras aplicaciones. cuento corto he encontrado la forma de acelerar bastante las cosas.

Todo esta basado en que XAA no es adecuado ya como metodo de renderizado, lo que provoca lento desempeño de las aplicaciones y uso de la CPU para tareas graficas. De modo que en a modo de idea y Bug en launchpad se reporto que era la hora de cambiar de forma predeterminada a EXA en ubuntu 9.04 (antes el predeterminado era XAA). Pero de todas formas eso no basta ya que en mi ati radeon 7000, el escritorio redibuja a trompicones y completa gtkperf en 27 segundos. Osea algo anda mal con EXA tal cual como viene configurado. 

**=;>  Esta solución es sólo para el driver libre "radeon", osea en tarjetas que funcionen con este driver de manera "óptima", tanto 2d como 3d, como por ejemplo desde la ATI 7x00 hasta las 9x00 y personalmente la he probado en la radeon 7000**


Primer Paso: Mejorando el Rendimiento 2D
--------------------------------------------

Primero deben instalar GTKPERF, que es un programa para medir el rendimiento "real" de GTK como si de una aplicacion real se tratara. Para instalar el sguinete comando (creo que solo disponible en ubuntu 9.04, pero se puede bajar de su pagina , buscar en google)

> sudo apt-get install gtkperf

Se instala en Aplicaciones--> Herramientas de Sistema

Y ejecutenlo con el boton Start , con 100 test round y Test All, es decir como viene predeterminado, y memoricen o guarden en un archivo cuanto demora en terminar osea los detalles, pongan especial atencion en las pruebas que mas se demora, ya uqe son justamnete esas las que se produce el incremento mas sustancias en rendimiento.


les dejo una copia de mi configuracion del XORG para que la prueben,

para editarlo en la cosola pongan
Código:

> sudo gedit /etc/X11/xorg.conf


Ubiquen las seccion "Device" las lineas que tienen que agregar son "AccelMethod" y "MigrationHeuristic", la opcion greedy la cambie por always,  ya que me tope con esa opción de pura casualidad, y me dio mejores resultados que greedy, pero pueden probar ambas, sobre las otras opciones que están ahi les digo que no es necesario ponerlas pero igual pueden ir probándolas, ya que a mi me han dado buenos resultados.

> 
Section "Device"
	Identifier	"Configured Video Device"
Option "EnablePageFlip" "True"
Option "AccelDFS" "True"
Option "AccelMethod" "EXA"
Option "RenderAccel" "on"
#Option "MigrationHeuristic" "greedy"
Option  "MigrationHeuristic" "always"
EndSection


[COLOR="Red"]**Actualización: en ubuntu 9.04 las opciones migrationHeuristic no producen mejora positiva, asi que deben probar y verificar resultados**[/COLOR]

Al final guardan los cambios y reinician el pc o el entorno grafico

ahora de vuelta en el escritorio y sin ninguna aplicacion abierta ejecuten gtkperf igual que antes, en mi caso baje a 15 segundos y los textos se ven fluidos , y rapidos, fue una bajada de mas de 10 segundos , lo que es simplemente expertacular!!!


Por favor cuentenme sus resultados ya que me he demorado bastante tiempo en encontrar esta solucion y he buscado en los bugs de PAA launch pad en ingles por una solucion, ademas de investigar sobre el problema por harto tiempo y reclamado tambien jejeje, y muchas veces siempre he recibido la respuesta de nooo, si a mi me funciona perfecto todo, no existe tal problema, y la verdad que el problema esta en XAA que es antiguo y los problemas de los drivers que con exa tiene que seguir mejorando pero por lo menos ahora no hay perdida de rendimiento con respecto a XAA en 3d ni en 2d, la cosa es que a mi me ha dejado bastante contento y tranquilo.

Segundo paso: Mejorando el rendimiento 3D
-------------------------------------

Antes que todo deben instalar "drifconf" 

> sudo apt-get install driconf

se instala en SISTEMA--> Preferencias , con el nombre 3D Acceleration, el icono dice DRI

Deben activar el "hyperz" y en mi caso de pasar de 3 a 2 el numero de unidades texturas usadas (tengo una antigua radeon 7000 para las mas modernas el valor predeterminado debe ser mejor, osea el 3) se pierde con probar. Ademas en Tuberia TLC, poner "usar tuberia tlc por software". Deben salir, y reiniciar el computador o las X

[COLOR="Red"]**Actualización: al menos en Ubuntu 9.04, solo la opcion Hyperz parece mejorar el rendimiento.**[/COLOR]

para probar los cambios ejecutar en consola antes y despue de ejecutar los cambios para poder medir el incremento

> glxgears


Yo en mi PC pase con el driconf de tener 450 a 850 fps en Glxgears aprox, ninguna otra version de Ubuntu habia logrado esto, deben ser los cambios y las revisiones al Xorg y a los drivers en el camino a implementar las nuevas tecnologias que se vienen.  Como dato les cuento que con el metodo  XAA con estos cambios me aumentaba el glxgears de 470 a 530

De todas formas prueben en juegos o aplicaciones 3d para evaluar mejor el rendimiento, ya que GLXGEARS NO ES UN BENCHMARK

saludos


De aqui en adelante , durante el 2009 espero que salga el driver ati libre , con soporte DRI2, GEM , y KMS. Osea las cosas mejorarán aun más, ahora que ati esta dejando de lado el driver propietario para las tarjetas incluso no tan antiguas como la mia, pero no de ultima generacion esto se vuelve de suma importancia para los usuarios de ATI, puesto que la ultima version del driver propietarior y posteriores soportara solo las ati HD hacia arriba.


-----------


Si tiene problemas con el incio del entorno grafico, prueben editando el xorg desde consola con nano apretando CONTROL+ALT+F2, se loguean como usuario y escriben

> sudo nano /etc/X11/xorg.conf

aunque antes de que se arrepientan comprueben si esta instalado o instalenlo con 

> sudo apt-get install nano


Lo digo porque al copiar de una web las opciones tuve problemas con las comilla debido a la codificacion de texto (aparecia como un cuadrado) asi que lo cambie por las comillas y lo guarde con CONTROL+O, y sali con CONTROL+X, se reinicia con "sudo reboot"


Como han de suponer si no se manejan bien con las cosas expuestas aca y presentan fallas de rendimiento con respecto a windows, mejor dejar las cosas tal como estan predeterminadamente, pero siempre es posible volver a las cosas como estaban volviendo al xorg.conf anterior o simplemenete comentando con # las lineas agregadas. 

Prueben en sus ATI y me comentan los resultados o ideas
Saludos  ):P :popcorn:

--------------------------------

PD: si siguen sintiendo lento firefox, instalen e l plugin de firefox flash block y veran como flash es el causante de esa lentitud de firefox

[https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)

con eso tendran el control de cual animacion ejecutar de las paginas, es decir solo las que les interesen, ademas pueden crear una lista blanca para los sitios permitidos, como por ejemplo youtube (para no andar apretando a cada rato el boton

---

### Post by Carlos C on 2009-05-26
Tengo Jaunty y la tarjeta de mi presario v2000 es la siguiente:
```
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
```Decidí no instalar los drivers binarios y darle una oportunidad a los libres y por primera vez tengo compiz de entrada, bien por jaunty.

Al ejecutar driconf no tengo la opción "hyperz", supongo que es porque mi tarjeta es muy mala. De todas maneras hice los cambios para mejorar el rendimiento 2D. Antes de modificar nada GtkPerf me dio el siguiente resultado:

```
GtkPerf 0.40 - Starting testing: Tue May 26 09:39:14 2009

GtkEntry - time:  0,30
GtkComboBox - time:  5,19
GtkComboBoxEntry - time:  4,02
GtkSpinButton - time:  0,54
GtkProgressBar - time:  0,65
GtkToggleButton - time:  0,74
GtkCheckButton - time:  0,38
GtkRadioButton - time:  0,52
GtkTextView - Add text - time:  1,72
GtkTextView - Scroll - time:  0,94
GtkDrawingArea - Lines - time:  2,39
GtkDrawingArea - Circles - time:  1,69
GtkDrawingArea - Text - time:  2,08
GtkDrawingArea - Pixbufs - time:  0,63
 --- 
Total time: 21,80
```Luego de añadir el parámetro Option "AccelMethod" "EXA" el resultado fue este:

```
GtkPerf 0.40 - Starting testing: Tue May 26 09:45:36 2009

GtkEntry - time:  0,25
GtkComboBox - time:  4,98
GtkComboBoxEntry - time:  3,19
GtkSpinButton - time:  0,45
GtkProgressBar - time:  0,51
GtkToggleButton - time:  0,60
GtkCheckButton - time:  0,32
GtkRadioButton - time:  0,44
GtkTextView - Add text - time:  1,35
GtkTextView - Scroll - time:  0,79
GtkDrawingArea - Lines - time:  1,99
GtkDrawingArea - Circles - time:  1,45
GtkDrawingArea - Text - time:  1,56
GtkDrawingArea - Pixbufs - time:  0,48
 --- 
Total time: 18,37
```No es tan espectacular, pero es una mejora.

---

### Post by ClarkXP on 2009-05-26
esa opcion servirá para una geforce 5200FX??
cuando llegue a mi casa pruebo y les cuento, 

tengo el xorg generado por nvidia, si funciona les cuento

---

### Post by AlexDDR on 2009-05-26
@carlos: sip, l oque pasa es que en jaunty viene preconfigurado para EXA, y si mejoró algo fue gracias  otras opciones, yo tengo acceso a un Pc que no puedo instalar Ubuntu, pero puedo correr el live cd y tiene una xpress200 reconocida como ati 1150 en win2 y si bien funciona compiz se nota que la grafica está a limite, siendo que deberia funcionar normal al menos.

El asunto es que el driver libre hace poco que pudo tener 3d en esos chips y aun esta muy bajo el rendimiento que deberia tener. Al hacer la prueba de GTKperf  tenias compiz activado? ya que Gtkperf es como u nbenchmark real, osea mide el sistema completo, CPU , GPU+driver y tambien mejora dependiendo el tema GTK que tengas.

Te recomiendo desactivar compiz, y probar con otros temas GTk, algo debe estar mal, ya que yo obtengo 15 segundos con una tarjeta muy muy vieja y con un cpu duron 1600 que es alrededor la mitad de un athlon 64 3000+ en rendimiento. En el cp con un penium dualcore 2000MHZ y una nvidia 8400 el test lo termina en 4.5 segundos. Al final este rendimiento afecta el rendimiento general del sistema ya que las aplicaiones aunque vayan rapido, no desliegan el contenido rápido y eso hace que todo el sistema funcione mas lento.

como te iba con el driver de ATi (fglrx) ? ya que ahora que ATI abandonó a sus chips antiguos en el soporte del driver privatico, la esperanza viene de las especificaciones liberadas por ati y el desarrollo del driver libre, por lo que ahora en adelantes y las siguiente versiones de ubuntu el driver libre será tu unico amigo

mira aca, el diferente rendimiento delos motores o temas GTK

[http://gianvito.wordpress.com/2008/02/20/gtk-engines-benchmarks-whats-the-fastest/2/](http://gianvito.wordpress.com/2008/02/20/gtk-engines-benchmarks-whats-the-fastest/2/)

saludos

---

### Post by AlexDDR on 2009-05-26
> **ClarkXP said:**
> esa opcion servirá para una geforce 5200FX??
cuando llegue a mi casa pruebo y les cuento, 

tengo el xorg generado por nvidia, si funciona les cuento

No te va a funcionar, ya que el driver propietario nvidia tiene sus  propias opciones para pasarle a traves del xorg, solo los drivers libre comparten algunas de las opciones

---

### Post by AlexDDR on 2009-05-27
Si me olvidaba, otra cosa que afecta el rendimiento del entorno grafico es el hinting y el alisado de las fuentes, por eso si usan alisado de sub pixel completo el rendimiento decaerá, pero si lo usan en leve las aplicaciones reaccionarán un poco más rápido, pero todo esto en una maqina lenta como la mia, talvez no importe mucho en maquinas poderosas.

---

### Post by Carlos C on 2009-05-28
Ok, mañana me comprometo con mas feedback, voy a sacar compiz y ver como anda la cosa, ahora no puedo porque no estoy en mi casa. De todas maneras mi tarjeta es pésima, es cosa de buscar en internet y verás que es así. Mi laptop tampoco es muy bueno, es un compaq v2415la, de los antiguos de la linea v2000.

---

### Post by AlexDDR on 2009-05-28
trata cambiando el tema GTK a uno mas liviano, hay algunos que hacen mejor la pega en unos aspectos que en otros, por otro  lado otro aunque no son los mas rapido  andan suave con firefox

en general un aspecto en el que por l omenos en mi PC ati radeon 7000 muere es en el addtext

si ejecutas este comando veras a tu pc sufrir en algun aparte de seguro

gtkperf -a -c 1000


este fue el resultado en el mio con el tema darkroom (es ese cafe entero) y GTK muere en add text, y se nota al cargar mucho texto en firefox, he visto mucho mejores resultados en otras tarjetas de video por ahi en internet, pero igual creo que en ese aspecto GTK falla un poco

alejandro@duron:~$ gtkperf -a -c 1000
GtkPerf 0.40 - Starting testing: Thu May 28 03:02:56 2009

GtkEntry - time:  1,82
GtkComboBox - time: 40,48
GtkComboBoxEntry - time: 24,30
GtkSpinButton - time:  5,79
GtkProgressBar - time:  8,55
GtkToggleButton - time:  4,88
GtkCheckButton - time:  5,03
GtkRadioButton - time:  9,71
[COLOR="Red"]GtkTextView - Add text - time: 106,28[/COLOR]
GtkTextView - Scroll - time: 14,86
GtkDrawingArea - Lines - time: 15,58
GtkDrawingArea - Circles - time: 11,75
GtkDrawingArea - Text - time: 22,34
GtkDrawingArea - Pixbufs - time:  7,15
 --- 
Total time: 278,50

Quitting..


Ojala este listo luego el port del driver radeon en UXA para ver mejorado el rendimiento

SAludos

---

### Post by pelaolinux on 2009-08-30
Hola!! 
e echos estas prueba con mi tarjeta de vídeo Radeon 9200 y los resultado fueron los siguientes:

al principio con GtkPerf me reconocia esto :

> 
GtkPerf 0.40 - Starting testing: Sun Aug 30 05:54:34 2009 
  
 GtkEntry - time:  0,73 
 GtkComboBox - time: 19,07 
 GtkComboBoxEntry - time: 16,90 
 GtkSpinButton - time:  1,76 
 GtkProgressBar - time:  1,83 
 GtkToggleButton - time:  2,75 
 GtkCheckButton - time:  1,28 
 GtkRadioButton - time:  1,67 
 GtkTextView - Add text - time:  5,62 
 GtkTextView - Scroll - time:  4,03 
 GtkDrawingArea - Lines - time: 10,65 
 GtkDrawingArea - Circles - time:  6,37 
 GtkDrawingArea - Text - time: 28,53 
 GtkDrawingArea - Pixbufs - time:  3,94 
  ---  
 Total time: 105,19
 y luego añadí  
 
> Identifier "Configured Video Device"
Option "EnablePageFlip" "True"
Option "AccelDFS" "True"
Option "AccelMethod" "EXA"
Option "RenderAccel" "on"
#Option "MigrationHeuristic" "greedy"
Option "MigrationHeuristic" "always"y los resultado fueron estos : 

> 
GtkPerf 0.40 - Starting testing: Sun Aug 30 06:26:46 2009 
  
 GtkEntry - time:  0,77 
 GtkComboBox - time: 16,48 
 GtkComboBoxEntry - time: 14,18 
 GtkSpinButton - time:  1,65 
 GtkProgressBar - time:  2,19 
 GtkToggleButton - time:  1,85 
 GtkCheckButton - time:  1,14 
 GtkRadioButton - time:  1,48 
 GtkTextView - Add text - time:  5,39 
 GtkTextView - Scroll - time:  1,89 
 GtkDrawingArea - Lines - time:  8,94 
 GtkDrawingArea - Circles - time:  5,67 
 GtkDrawingArea - Text - time: 23,27 
 GtkDrawingArea - Pixbufs - time:  3,47 
  ---  
 Total time: 88,46
 fueron muchos mas bajos que desde ante que asiera todo y los fps siguieron en lo del principio que era  como 340 a 530 . Después no podía quedarme conforme por que al parecer todo seguía igual los juegos y muchas aplicaciones me funcionaban igual y luego de horas y horas de seguir investigando  llege al punto de dejar la editacion del fichero /etc/X11/xorg.conf de la siguiente manera:


> Section "Device" 
     Identifier    "Configured Video Device" 
     Option        "AGPMode" "2" 
     Option     "EnablePageFlip" "True" 
     Option     "TripleBuffer" "true"  
     Option     "DynamicClocks" "off"  
     Option     "AccelDFS" "True" 
     Option     "AccelMethod" "EXA" 
     Option     "RenderAccel" "on" 
 EndSection
  añadí la opcion &#8220;AGPMode&#8221; &#8220;X&#8221; que es una de las más recomendadas, controla la velocidad del puerto AGP lo que aumenta o disminuye la tasa de transferencia de información. Tiene que ir configurada dependiendo las X que aguante la placa madre en el puerto AGP, en el caso mio puse dos aun que mi placa madre aguanta 4 mi procesador lo impide y causa que no pueda aguantar mas de 2.


 También añadí la opcion "TripleBuffer" "true" que Sólo vale la pena si usas Compiz, Beryl o Compiz Fusión.

y luego ise lo siguiente: 

 Para mejorar la cantidad de FPS. 
 1. - Instalamos todas las dependecias para poder compilar mesa. 
 
 > sudo apt-get install autoconf 
 > sudo apt-get build-dep mesa  > 
sudo apt-get install libxmu-dev libdrm-dev x11proto-dri2-dev lib libxi-dev 
  

2. - Descargamos las fuentes de mesa con el radeo-rewrite: 
 
 > git clone git://anongit.freedesktop.org/git/mesa/mesa 
 > cd mesa 
 > git branch radeon-rewrite origin/radeon-rewrite 
 > git checkout radeon-rewrite 
 
3. - Procedemos a ejecutar el siguiente comando: 
 
> . /autogen. Sh --prefix=/usr --with-dri-drivers=radeon,r200,r300 
 

 

 Y luego de todo esto nuevamente abri GtkPerf y los resultados fueron estos: 



> GtkPerf 0.40 - Starting testing: Sun Aug 30 08:01:48 2009 
  
 GtkEntry - time:  0,75 
 GtkComboBox - time: 16,24 
 GtkComboBoxEntry - time: 13,60 
 GtkSpinButton - time:  1,59 
 GtkProgressBar - time:  1,60 
 GtkToggleButton - time:  2,11 
 GtkCheckButton - time:  1,16 
 GtkRadioButton - time:  1,41 
 GtkTextView - Add text - time:  4,79 
 GtkTextView - Scroll - time:  3,04 
 GtkDrawingArea - Lines - time:  8,97 
 GtkDrawingArea - Circles - time:  5,67 
 GtkDrawingArea - Text - time: 22,48 
 GtkDrawingArea - Pixbufs - time:  3,38 
  ---  
 Total time: 86,82 
y los fps subieron a 530 a 1032 que igual fue mucho mejor pero haun no puedo lograr lo que quiero que mis juegos y muchas cosas mas se puedan verse corruptamente.
Saludos!!! seguiré investigando este tema asta que pueda ver todo funcionando correctamente asta los vídeos y los flash que aparesen en paginas web.

---

