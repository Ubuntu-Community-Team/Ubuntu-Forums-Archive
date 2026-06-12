---
title: "Drivers radeon y lucid muy lento y con crash..."
date: 2010-05-22
forum: Instalación y Actualización
---

### Post by DobleDP on 2010-05-22
bueno pues la consulta es...

 alguno ha tenido problemas con los drivers radeon (libres) en ubuntu 10.04 (lucid) en las tarjetas ATI, (especificamente en mi caso una xpress 200M) ...

personalmente he notado tristemente que en vez de mejorar esta nueva versión de ubuntu ha empeorado con respecto a aceleración gráfica y con varios juegos ni siquiera puedo arrancarlos (openarena -pantalla negra solo sonido-  warzone -graficos malas y muy lentos- neverball -capas del juego desaparecen- performous -el juego ahora esta muy lento y las canciones se descuadran con la letra por renderizado muy bajo- etc etc) pese que estos mismos juegos trabajaban bien en la versión anterior me gustaría saber si solo me ha pasado a mi o el problema es general con el driver radeon...

...y si alguien a logrado mejorar su rendimiento por mi parte una solución fue crear el xorg.conf con eso gane unos frames pero aun así noto un rendimiento muy pobre y peor que el que ya tenia... :(

---

### Post by asterix77 on 2010-05-24
Pues yo tengo la misma tarjeta ATI integrada en mi dell inspiron 1501, y no he tenido problemas tanto en karmic como ahora en lucid.

Corre el siguiente comando y pega el contenido acá (hazlo correr unos 7 segundos en tamaño pequeño, y otros 7 segundos más  en pantalla completa)

#glxgears


Además pega lo que salga de los siguientes comandos también:


#lspci | grep VGA 

#glxinfo | grep direct

Saludos

---

### Post by DobleDP on 2010-05-24
A pantalla completa:
dobled@dobled-laptop:~$ glxgears 
586 frames in 5.0 seconds
177 frames in 5.0 seconds
196 frames in 5.0 seconds
199 frames in 5.0 seconds
171 frames in 5.0 seconds

Con ventana normal:
dobled@dobled-laptop:~$ glxgears 
2102 frames in 5.0 seconds
1472 frames in 5.0 seconds
1729 frames in 5.0 seconds
1970 frames in 5.0 seconds
2381 frames in 5.0 seconds

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

direct rendering: Yes

Lo que me extraña es que muchas aplicaciones (juegos en su mayoria) que antes funcionaban bien, ahora ya no me funcionan o en el mejor de los casos me funciona pero muy lento o con problemas gráficos.

PD: las pruebas las hecho en XFCE sin ningún tipo de efecto gráfico activo.

---

### Post by asterix77 on 2010-05-24
Bueno parece que "todo" está bien, a mi los valores son un poco mejores

$ glxgears 
3753 frames in 5.0 seconds
3713 frames in 5.0 seconds
3934 frames in 5.0 seconds
3954 frames in 5.0 seconds
3952 frames in 5.0 seconds
1637 frames in 5.0 seconds
303 frames in 5.0 seconds
315 frames in 5.0 seconds
303 frames in 5.0 seconds
302 frames in 5.0 seconds
304 frames in 5.0 seconds

Para que compares:

#lspci | grep VGA 
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]


#glxinfo | grep direct
direct rendering: Yes

Recuerdo que cuando usé intrepid, busqué e instalé un driver de la página ATI, el cual me arregló el problema de la aceleración. En Karmic (y ahora también en Lucid) no lo usé porque se me activó enseguida.

Quizás deberías intentantar lo de la página de ATI (no garantizado eso sí)

[http://www.amd.com/la/Pages/AMDHomePage.aspx](http://www.amd.com/la/Pages/AMDHomePage.aspx)

Debes escoger placa madre/chipset

Saludos

---

### Post by asterix77 on 2010-05-24
Bueno parece que "todo" está bien, a mi los valores son un poco mejores

$ glxgears 
3753 frames in 5.0 seconds
3713 frames in 5.0 seconds
3934 frames in 5.0 seconds
3954 frames in 5.0 seconds
3952 frames in 5.0 seconds
1637 frames in 5.0 seconds
303 frames in 5.0 seconds
315 frames in 5.0 seconds
303 frames in 5.0 seconds
302 frames in 5.0 seconds
304 frames in 5.0 seconds

Para que compares:

#lspci | grep VGA 
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]


#glxinfo | grep direct
direct rendering: Yes

Recuerdo que cuando usé intrepid, busqué e instalé un driver de la página ATI, el cual me arregló el problema de la aceleración. En Karmic (y ahora también en Lucid) no lo usé porque se me activó enseguida.

Quizás deberías intentantar lo de la página de ATI (no garantizado eso sí)

[http://www.amd.com/la/Pages/AMDHomePage.aspx](http://www.amd.com/la/Pages/AMDHomePage.aspx)

Debes escoger placa madre/chipset

Saludos

---

### Post by asterix77 on 2010-05-24
Bueno parece que "todo" está bien, a mi los valores son un poco mejores

$ glxgears 
3753 frames in 5.0 seconds
3713 frames in 5.0 seconds
3934 frames in 5.0 seconds
3954 frames in 5.0 seconds
3952 frames in 5.0 seconds
1637 frames in 5.0 seconds
303 frames in 5.0 seconds
315 frames in 5.0 seconds
303 frames in 5.0 seconds
302 frames in 5.0 seconds
304 frames in 5.0 seconds

Para que compares:

#lspci | grep VGA 
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]


#glxinfo | grep direct
direct rendering: Yes

Recuerdo que cuando usé intrepid, busqué e instalé un driver de la página ATI, el cual me arregló el problema de la aceleración. En Karmic (y ahora también en Lucid) no lo usé porque se me activó enseguida.

Quizás deberías intentantar lo de la página de ATI (no garantizado eso sí)

[http://www.amd.com/la/Pages/AMDHomePage.aspx](http://www.amd.com/la/Pages/AMDHomePage.aspx)

Debes escoger placa madre/chipset

Saludos

---

