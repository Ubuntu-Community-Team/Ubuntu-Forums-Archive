---
title: "UNICHROME en Ubuntu 8.10"
date: 2009-02-18
forum: Hardware
---

### Post by h9005 on 2009-02-18
Tengo una placa de video on board unicrhome igp pro en un amd2 64 k8m800. No se como activarla! Acá encontre algo pero no entiendo bien...

[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")


[http://packages.ubuntu.com/intrepid/xserver-xorg-video-openchrome]("http://packages.ubuntu.com/intrepid/xserver-xorg-video-openchrome")

---

### Post by guillermolisi on 2009-02-18
> **h9005 said:**
> Tengo una placa de video on board unicrhome igp pro en un amd2 64 k8m800. No se como activarla! Acá encontre algo pero no entiendo bien...

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)


[http://packages.ubuntu.com/intrepid/xserver-xorg-video-openchrome](http://packages.ubuntu.com/intrepid/xserver-xorg-video-openchrome)
Mira, hasta donde se y basandome en la experiencia propia y la de muchos otros que han intentado, esas placas de video, como la que mencionas, no funcionan y en el mejor de los casos logras aceleracion 2D solamente.

He leido oportunamente, tengo dos PCs con placas similares pero que van irian con el mismo driver, y algunos dicen que les funciono pero son los menos.

De tanto probar sin exito termine dejando una en modo VGA y a la otra le puse un placa nVidia 6200. Santo remedio y me dedique a otra cosa mas productiva.

Ademas, la pagina de OpenArena que tiene Asus deja bastante que desear (o sea, le dan bola pero solamente para cumplir, hasta ahi nomas).

---

### Post by h9005 on 2009-02-18
Uh que lo parió! Encima tengo la máquina en garantia asi que no uedo chantarle mi 6200!

---

### Post by h9005 on 2009-02-18
Fijense lo que sale en la consola:

:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by h9005 on 2009-02-19
Alguien sabe de que se trata esto?

[http://www.mesa3d.org/]("http://www.mesa3d.org/")

---

### Post by EnriqueK on 2009-02-20
No tengo experiencia en el tema de garantías, pero supongo que para que esta se mantenga vigente, tienes que cumplir las tareas de mantenimiento o sea limpieza interior del equipo y esa tarea la tienen que realizar en talleres autorizados , si esto es así, la próxima vez que lo lleves a que le pasen el soplete, aprovechas para que ellos te instalen la tarjeta gráfica, lógicamente esto con un acuerdo previo, no se si estoy diciendo burradas, pero la lógica me dice que si tu equipo se llegara a quemar por falta de limpieza interior, por mas vigente que se encuentre la garantía, no te va a servir.

---

