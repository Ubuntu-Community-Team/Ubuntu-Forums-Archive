---
title: "Problema con mi tarjeta de video ATI Radeon 9200!"
date: 2009-08-28
forum: Hardware
---

### Post by pelaolinux on 2009-08-28
hola amigos! 
Bueno mi problema es el siguiente: 
tengo instalado ubuntu 9.04 y mi tarjeta de video no funciona correctamente o mejor dicho no funciona con la misma capacidad que la ago funcionar en Windows... pero el problema que tengo es que los juegos que igual no piden muchos requisitos y en mi computador se deberian verse excelente, se me ven muy cortados o se quedan pegados y luego también pensé y creo que puede ser por que necesitan instalar los driver. Bueno al final me diriji a la pagina de ATI para descargar los driver para linux y me encontré con algunas sorpresas las cuales eran que todos los driver que salían ahí eran paquetes de instalación  .run y los .rpm y no eran compatible al instalarlos en ubuntu 9.04  y luego estaba revisando el gestor de instalación de aplicaciones en ubuntu  y me salia un controlador ATI y luego lo instalarle y me salia un mensaje que no era compatible la aplicación … 
bueno al final lo único que deseo es poder jugar algunos juegos sin la necesidad de utilizar windows y también quiero aprender como configurar mi tarjeta de video …. 

el windows yo a mi tarjeta de video le tengo instalado el driver Radeon 9250 que es compatible con mi tarjeta y me gustaria saber como se puede instalar … en algunos foros e visto que ATI ya no presta soporte para linux pero yo se que hay alguna forma como hacer para que funcione correcta mente y sacarle mas provechos también a los entornos gráficos y aplicaciones como compiz fusion que tengo instalado en ubuntu …. 

Saludos!!  :confused:

---

### Post by Carlos C on 2009-08-29
Tenemos un thread que esta como sticky que te recomiendo mirar:

[http://ubuntuforums.org/showthread.php?t=1166846](http://ubuntuforums.org/showthread.php?t=1166846)

Saludos.

---

### Post by pelaolinux on 2009-08-29
gracias señor Carlos C .... 
lo probare y veré que tan eficaz puede ser .... Siempre creí que editando ese fichero en la carpeta X11 podría mejorar el rendimiento y yo siempre le agregaba parámetros que veía en distintos lugares y al final no eran muy eficaz pero por lo que leí y tengo la esperanza que esto servirá ..... 
pero ahora tengo otro problema ... 

Saludos!

---

### Post by pelaolinux on 2009-08-30
> **Carlos C said:**
> Tenemos un thread que esta como sticky que te recomiendo mirar:

[http://ubuntuforums.org/showthread.php?t=1166846](http://ubuntuforums.org/showthread.php?t=1166846)

Saludos.


                                 Hola Carlos C!

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

### Post by Carlos C on 2009-08-30
Hola. Veo que también respondiste en el otro hilo. Trata de no publicar dos veces, basta con que en este post añadas un enlace al otro thread, así no se duplica la información y no se generan confusiones ;)

Sobre los videos en flash, yo siempre instalo el paquete ubuntu-restricted-extras. Hay gente que puede no estar de acuerdo conmigo, pero en el caso de mi computador el plugin de flash que se instala con ese paquete es el que me da el mejor rendimiento.
Saludos.

---

