---
title: "[HP PhotoSmar C4480]No puedo escanear"
date: 2009-05-17
forum: Hardware
---

### Post by rubioo on 2009-05-17
Bueno, ayer me compre una multifunción HP. Y anda de 10, la detecta y 
 todo, pero a la hora de escanear no se puede(y en win se puede)
 Estoy usando HPLIP

       Saludos

---

### Post by Hei Ku on 2009-05-17
Tenes instalado xsane? La impresion va por hplip, pero el scanner generalmente utiliza xsane, que si mal no recuerdo no viene instalado de entrada.

---

### Post by rubioo on 2009-05-17
Sisi, tengo instalado xsane. Cuando pongo escanear en HP Device Manager se
 abre xsane, pero en la pantallita de la multifunción me dice: 
 > 
 Error de escaneo.
 Intente digit. desde equipo o vea document.
 

---

### Post by Hei Ku on 2009-05-17
Que pasa si arrancas el xsane directamente? Deberias tenerlo en el menú de Gráficos.

---

### Post by rubioo on 2009-05-17
Si arranco xsane directamente me dice "escaneando dispositivos" y despues
 se abre el programa. Pongo para que empiece a escanear (desde la
 multifunción) y el programa no hace nada. Y me aparece en la pantallita de
 la multifunción el error que dije antes :confused:

---

### Post by Hei Ku on 2009-05-17
Parece que tenes un problema parecido al que yo tuve con mi impresora hasta ayer. La version de hplip que viene con ubuntu es vieja. Tenes que instalar la ultima del sitio de hplip. Con eso aparentemente sale andando.

Vos instalaste el hplip desde los repositorios, no? O sino, ya te vino instalado, cierto?

Probá bajar y correr el instalador de acá: [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by rubioo on 2009-05-17
Si, lo instale desde los repositorios.
 Pruebo lo que decis y vemos :)

---

### Post by rubioo on 2009-05-17
Instale lo que me dijiste pero sigue igual.
 Cuando pongo para que escanee tengo que hacer algo desde xsane?
 o directamente me va a aparecer lo que puse para escanear?

---

### Post by Hei Ku on 2009-05-17
Tenes que apretar el boton Explorar en el xsane. Por lo menos a mí no me escanea automaticamente.

---

### Post by rubioo on 2009-05-17
Que dolobu que soy ](*,) si pongo Explorar escanea, pero no en la ventana
 que aparece no se ve lo que puse para que escanee (se ve todo gris)

---

### Post by Hei Ku on 2009-05-17
El scanner hace algo? O sea, se mueve como si escaneara o no?

---

### Post by rubioo on 2009-05-17
Si se mueve y hace ruido.

---

### Post by rubioo on 2009-05-20
*BUMP*
 Revivo el post para preguntar si alguien me podía dar una mano con el
 escaner o que me digan que no saben y no moleste mas :P
 Porque la verdad no me gusta la idea de reiniciar cada ves que tengo que
 escanear, más ahora que prácticamente me despedí de windows

---

### Post by Hei Ku on 2009-05-20
Lo que pude ver es que generalmente la gente no tuvo problemas para usar ese scanner en ubuntu. podrias probar de ejecutar el xsane desde consola a ver si tira algo mas de info.

---

### Post by rubioo on 2009-05-21
Si lo ejecuto desde la consola, no me tira ningún error.
 Y cuando pongo Explorar, para que escanee me sale esto:

---

### Post by Hei Ku on 2009-05-21
Fijate que a la izquierda y abajo de Explorar aparecen las dimensiones de lo que va a explorar. Eso esta en 0cm x 27cm. Te aparece siempre así, o después de apretar Explorar se cambia? Me suena a que hay algo mal en la configuración del area de escaneo.

---

### Post by rubioo on 2009-05-21
Sabes que tenes razón, porque en la ventana que aparece cuando escaneo
 dice 1 x 809 pixeles. Pero como hago para configurarla?

          Saludos

---

### Post by Hei Ku on 2009-05-25
Anda al menu Ventana -> Mostrar Vista Previa
En la ventana de vista previa, Adquirir Vista Previa. Despues, tenes unos botones arriba para elegir el area de escaneo.

---

### Post by rubioo on 2009-05-26
Groso!!!!
 Hei Ku de verdad te digo, muchas gracias por ayudarme con este problema
 que tuve ya que ahora no tengo excusas para no usar Ubuntu :D


        Saludos y muchas muchas gracias de nuevo =D>:-({|=

---

### Post by Hei Ku on 2009-05-26
Anduvo? Era eso nomas?

Buenisimo!

---

### Post by rubioo on 2009-05-26
Sisi, ya funciona de 10. 
 

 Gracias, cualquier cosa molesto de nuevo :)

---

