---
title: "Ubuntu 8.04 LTS configuración efectos gráficos e instalación de codecs de audio y vid"
date: 2009-02-20
forum: Hardware
---

### Post by anagramagia on 2009-02-20
Hola, qué tal?
Solicito ayuda porque no consigo habilitar los efectos gráficos para el escritorio en Ubuntu 8.04LTS Desktop edition para sistemas basados en Intelx86. La máquina cuenta con un micro amd 64 x2 core duo 5200+, 2gb de ram, y el adaptador gráfico que está integrado en el mother es nVidia GeForce 7050PV.
En Sistema>Administración>Controladores de hardware, aparece: nvidia_new habilitado pero su estado es “no está en uso”.
En el gestor de paquetes synaptic figura que el driver está instalado. No entiendo qué pasa.

Otro tema: instalación de codecs para reproducir formatos de audio y video no libres (mp3, por ejemplo). Intenté instalar los paquetes que descargué para un Xubuntu 8.04 LTS instalado en otra máquina pero no lo consigo, aparece un mensaje indicando que no se puede instalar. Tengo los paquetes y sus dependencias ya que en la otra máquina podía reproducir esos formatos luego de instalar los paquetes (por ej.: gstreamer0.10-plugins-ugly_010.7-3_i386.deb). Además, por ejemplo, abro synaptic y busco gstreamer pero entre los resultados que arroja no se encuentran los paquetes que necesito, por lo que no puedo marcarlos. Esto sí podía hacerlo en el Xubuntu de la otra pc. Aclaro que la pc no cuenta con una conexión a internet donde está instalado el sistema.

Por favor, ¿me podrían ayudar a encontrar una solución? 
Muchas gracias.

---

### Post by josecuervo86 on 2009-02-22
A ver si entendi: Vos desde synaptic queres instalar paquetes que estan en otra maquina? o sea queres instalarle los paquetes que habias bajado en otra maquina?
Segun tengo entendido no se puede, synaptic busca los paquetes pero en los repositorios donde se encuentran alojados. Y si como entendi, no tenes conexion a internet, no vas a poder bajar nada.

---

### Post by kornykyano on 2009-02-22
yo tbn estoy un poco confundido. Lo que entiendo es querer instar paquetes en Ubuntu pero descargándolos desde Xubuntu. Yo lo que haría es **Generar un script de descarga de paquetes** con Ubuntu y con ese script descargarlo con Xubuntu, volver a Ubuntu y **Añadir los paquetes descargados**. Todo lo haces desde Synaptic.

Saludos

---

### Post by josecuervo86 on 2009-02-22
Esa es una buena opcion. Aca te dejo un link donde te explican como hacerlo

[http://enavas.blogspot.com/2008/10/instalar-paquetes-en-un-ordenador-sin.html]("http://enavas.blogspot.com/2008/10/instalar-paquetes-en-un-ordenador-sin.html")

---

### Post by UbuntuNerd on 2009-02-22
"josecuervo86" gracias por ofreser esa link muy interesante yo ise algo similar para descargar los updates en synaptic mira [AQUI](http://my.opera.com/ubuntunerd1/blog/how-to-create-an-ubuntu-update-cd-dvd)

---

### Post by anagramagia on 2009-02-24
> **UbuntuNerd said:**
> "josecuervo86" gracias por ofreser esa link muy interesante yo ise algo similar para descargar los updates en synaptic mira [AQUI](http://my.opera.com/ubuntunerd1/blog/how-to-create-an-ubuntu-update-cd-dvd)
Gracias por sus respuestas. Voy a probar lo que sugieren, por lo pronto voy a ver los links.
Lamento haberme expresado mal, lo que quise decir es que en la pc con xubuntu (que tampoco tiene internet) cuando abría synaptic se mostraban muchos paquetes no instalados y que podía seleccionarlos para generar un archivo de texto con las direcciones de descarga para ir luego a un locutorio y bajarlas de ahí. El problema es que en el synaptic de ubuntu casi que sólamente aparecen los paquetes que están instalados.
Les comento que por lo pronto pude instalar de a uno gstreamer ugly y sus dependencias (es decir click sobre el paquete deb, y click en instalar una y otra vez) y puedo oir mp3.
De todos modos sigo con el tema de no poder utilizar los efectos de escritorio avanzados (el tan mentado cubo y otras delicias que aún desconozco)¿alguna idea?
Saludos.

---

### Post by josecuervo86 on 2009-02-24
Mira, lo primero que tenes que hacer es ir a esos dos "cuadraditos" que estan en la barra de abajo a la derecha (Area de trabajo) si es que todavia no la modificaste. Apretas boton derecho y entras en preferencias. Para que te aparezca el cubo tenes que tener 4 columnas. 
Despues anda al compiz manager (Sistema, Preferencias, Administrador de opciones Compizconfig), y selecciona "escritorio" del menu a la izquierda. Una vez ahi tenes que tildar la casilla que tiene el cubo y listo.
Para hacerlo andar tenes que mantener apretado el scroll del mouse o bien apretar:
"Ctrl + Alt + Boton izquierdo del mouse" aunque eso tambien lo podes modificar.
Espero que hayas entendido todo. Si tenes alguna consulta pregunta nomas

---

### Post by anagramagia on 2009-03-01
> **josecuervo86 said:**
> Mira, lo primero que tenes que hacer es ir a esos dos "cuadraditos" que estan en la barra de abajo a la derecha (Area de trabajo) si es que todavia no la modificaste. Apretas boton derecho y entras en preferencias. Para que te aparezca el cubo tenes que tener 4 columnas. 
Despues anda al compiz manager (Sistema, Preferencias, Administrador de opciones Compizconfig), y selecciona "escritorio" del menu a la izquierda. Una vez ahi tenes que tildar la casilla que tiene el cubo y listo.
Para hacerlo andar tenes que mantener apretado el scroll del mouse o bien apretar:
"Ctrl + Alt + Boton izquierdo del mouse" aunque eso tambien lo podes modificar.
Espero que hayas entendido todo. Si tenes alguna consulta pregunta nomas
Voy a probar eso. Mientras tanto te cuento que en la pc donde está instalado Ubuntu 8.04 LTS hay una adaptadora de video con chip nVidia GeForce 7050PV + nForce 630a integrada en un motherboarth Asus M2N-VM DVI.
Buscando en internet encontré una página ([http://www.alejandrox.com/2008/05/habilitar-compiz-fusion-en-ubuntu-hardy/)donde](http://www.alejandrox.com/2008/05/habilitar-compiz-fusion-en-ubuntu-hardy/)donde) se explicaba como averiguar si estaba activada la aceleración 3D utilizando el siguiente comando: 

xglinfo |grep direct

Si está activada la salida es:

direct rendering: Yes

Pero en mi caso la salida es:

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

OpenGL renderer string: Mesa GLX Indirect


En principio no entiendo cómo o dóndo setear LIBGL_DEBUG=verbose.
Luego tampoco sé si y cómo podría activar la aceleración 3d.

Otra prueba indicada en esa misma página para saber si funcionaba la aceleración 3D era ejecutar glxgears con el resultado de una ventana en la cual se ven tres engranajes 3D girando.

Esto último sí se pudo realizar.

---

### Post by anagramagia on 2009-03-19
Solucioné ámbos problemas:
Pude ver qué packages se pueden instalar desde synaptic luego de ir al menú configuración>repositorios y cambiar "Descargar desde: Servidor para Argentina" a "Descargar desde: Servidor principal" y santo remedio.


Respecto de la configuración de nVidia y compiz, instalé envyng.core y unas cuantas dependencias además del compizconfig-settings-manager y eso me permite girar la pantalla y cambiar de escritorio, unas ventanas gelatinosas, etc. Hay muchas opciones para probar.

---

### Post by josecuervo86 on 2009-03-19
Bien ahí. Si, las opciones de compiz son casi infinitas!

---

