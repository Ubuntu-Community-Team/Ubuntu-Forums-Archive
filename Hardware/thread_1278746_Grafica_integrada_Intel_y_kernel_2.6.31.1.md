---
title: "Grafica integrada Intel y kernel 2.6.31.1"
date: 2009-09-29
forum: Hardware
---

### Post by EnriqueK on 2009-09-29
Mi PC tiene Mother Asus con gráfica integrada Intel y como presenta problemas con Compiz, decidí probar con descargar el kernel 2.6.31.1 desde el sitio [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) , se instaló sin problemas, pero al reiniciar con dicho kernel, presentaba pantalla negra y no funcionaba el teclado y posiblemente tampoco el mouse, lo único que pude hacer es pulsar el botón reset e iniciar con el kernel antiguo.
Como se que dicho kernel será el que traerá la próxima versión de Ubuntu, ¿habrá alguna manera de saber si mi equipo podrá usar Ubuntu 9.10?.
La verdad es que no entiendo el por que de estos problemas con las gráficas Intel si los drivers de las mismas son distribuidas en código fuente, mi preocupación se incrementa por el hecho de que tuve problemas similares con mi anterior equipo que también contaba con gráfica Intel, en aquella ocación no pude instalar Intrepid.

---

### Post by pablo.s on 2009-09-29
Los drivers de Intel están
actualizados? Qué chip tiene
el motherboard?

---

### Post by EnriqueK on 2009-09-29
El Chip es 945GC(A2)/ICH7  de Intel , supongo que el driver estará actualizado , en todo caso el problema lo tengo con el hernel que vendrá en Ubuntu 9.10 , actualmente funciona bien salvo Compiz.
Mi placa la podés ver en 
[http://latin.asus.com/search.aspx?searchitem=1&searchkey=p5gc-mx%2F1333](http://latin.asus.com/search.aspx?searchitem=1&searchkey=p5gc-mx%2F1333)

---

### Post by pablo.s on 2009-09-29
Hay unos drivers un poco más
actualizados que los que trae
Jaunty (supongo) que son los
de este PPA

```
**deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main #xorg-edgers PPA **[FONT=Droid Serif, serif][SIZE=1][COLOR=Red]
**[COLOR=Black] deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main #xorg-edgers PPA[/COLOR]**[/COLOR][/SIZE][/FONT]  
```

Puede ser que instalando estos 
drivers funcione. Porque los drivers
de Intel no los trae el núcleo, lo que 
trae es DKMS.

---

### Post by EnriqueK on 2009-09-30
Gracias, pero no me sirvió, instalé las actualizaciones y cuando reinicio el sistema, el puntero del retón desaparece , mejor dicho se hace invisible t no pude hacerlo aparecer, así que renuncié en continuar y repuse una imagen de respaldo que hice con clonezilla antes de meter mano con estas modificaciones.
Espero que cuando salga KK solucione estos problemas y no haga honor al nombre de sus siglas.

---

### Post by luks911 on 2009-09-30
EnriqueK,
Una sugerencia, iniciá con el kernel "viejo" y actualizá usando los repositorios que te pasó Pablo. Es lo que hago con una Intel, aunque distinta a la tuya.
Contá también cuál es el problema con Compiz para ver si hay alguna alternativa.

Un saludo

---

### Post by sitiomatic on 2009-10-04
Cada maquina es un mundo. 
A mi todos los problemas con el video intel en 9.04 se me arreglaron al instalar el kernel 2.6.31, creo que tambien actualice el xserver-xorg-video-intel, no me acuerdo de donde lo saque pero ahora en cada actualizacion me viene actualizar el xorg-video-intel.
Por si te sirve, la version que tengo instalada ahora es 2:2.9.0 del 30 de setiembre 2009.

---

### Post by aledruetta on 2009-10-04
La forma más sencilla de saber en este momento si Karmic va a funcionar en tu equipo es bajar la alfa que salió el 1 de octubre y probar el livecd.
Y la forma más sencilla de probarlo es bajar la iso y crear un disco usb de inicio con la herramienta que trae Jaunty. De esa forma no quemás un cd. 
Yo tengo Intel integrada y hasta ahora está funcionando mejor que en Jaunty. No es la perfección, pero está mejor.

---

### Post by EnriqueK on 2009-10-05
Me había olvidado de comentarlo, el caso es que descargué el Karmic alfa 6 Live Cd y funcionó bien, inclusive me da la impresión de que tiene mejor calidad de imagen que con Jaunty.

---

### Post by pablo.s on 2009-10-05
> **EnriqueK said:**
> inclusive me da la impresión de que tiene mejor calidad de imagen que con Jaunty.

Si, bueno, a mi me pasó algo
parecido. Los temas musicales
se escuchan mejor. De veras.
No quería postearlo en el thread
de Karmic porque me pareció
que me iban a tomar el pelo...

---

### Post by aledruetta on 2009-10-05
Ahí va una traducción Google del nuevo controlador Intel que viene en Karmic:

"Nueva arquitectura Intel controlador de vídeo disponibles para las pruebas 

El controlador de vídeo Intel ha cambiado desde el "método de EXA" la aceleración a la nueva "UXA". Esto soluciona problemas importantes de rendimiento de Ubuntu 9.04, pero podría utilizar más pruebas para cualquier marca regresiones que puede traer. 

 Comentarios sobre el nuevo modo "kernel configuración" está también muy apreciada. Esto reducirá el modo de conmutación de vídeo parpadeo en el arranque, y dramáticamente acelerar suspender / reanudar. Por favor, consulte las instrucciones y la página de comentarios para más detalles."

Ya está le versión Beta de Karmic, que anda mejor que la Alpha 6.

---

### Post by sitiomatic on 2009-10-05
Yo tambien probe hoy el live cd de la beta.
Tengo panico al upgrade despues de lo que me paso con 9.04, mas ahora que solo tengo ubuntu en mi maquina y todo lo que haga es sin red.
KK anduvo bien, ningun problema con el video intel, wifi, red, sonido y demas cosas basicas.
Igual voy a esperar a que salga la version final y me baje clonezilla para clonar el disco por si algo falla. :)

---

### Post by faktorqm on 2009-10-08
> **sitiomatic said:**
> Yo tambien probe hoy el live cd de la beta.
Tengo panico al upgrade despues de lo que me paso con 9.04, mas ahora que solo tengo ubuntu en mi maquina y todo lo que haga es sin red.
KK anduvo bien, ningun problema con el video intel, wifi, red, sonido y demas cosas basicas.
Igual voy a esperar a que salga la version final y me baje clonezilla para clonar el disco por si algo falla. :)

¿Que haces Sergio? Todo bien? Espero que si. Espero verte en fabrica de fallas 2009 con 9.10 instalado xD

Para no hacer todo ese manejo de datos, lo que tendrias que hacer es tener 3 particiones en total, una para /, otra para /home, y la ultima para swap. Si tenes todo junto y tenes algun problema moris ahi mismo. Salu2!!!

---

### Post by sitiomatic on 2009-10-08
Hola!! como estas
Asi lo tengo, en 3 particiones distintas y ya estoy usando el kernel 2.6.31 en 9.04 desde que salio, asi que supongo que el upgrade sera sencillo y sin problemas. 
Ahora estoy encaprichado con KDE pero eso esta en otro post.
Abrazos

---

