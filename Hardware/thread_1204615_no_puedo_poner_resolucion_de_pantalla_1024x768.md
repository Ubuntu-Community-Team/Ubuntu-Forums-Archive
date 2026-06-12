---
title: "no puedo poner resolucion de pantalla 1024x768"
date: 2009-07-05
forum: Hardware
---

### Post by jrodriguez on 2009-07-05
Hola, soy usuario nuevo de linux, instale la ultima version 9.04 en mi notebook compaq c751la, tiene drivers de video intel, lo raro es que me deja por defecto la resolucion 1280 x 800 (todo se ve demasiado pequeño para mi gusto, sobre todo las paginas web) y cuando trato de dejar la standar 1024 x 768, como que se achica y acorta la pantalla de los lados y no se que mas hacer. Pongo mi modelo de tarjeta grafica y mi xorg.conf:

lspci |grep VGA:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

xorg.conf:

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


Ojala me puedan orientar, saludos!

---

### Post by staar on 2009-07-05
mirá, los paneles de las notebooks son como los monitores lcd, son fabricados para una resolución óptima (tienen una determinada cantidad de 'puntos' que equivalen a pixeles), y deben usarse con ella para obtener nitidez y calidad de imagen, usados con cualquier otra resolución se ven mal, distorsionados, y no se recomienda...

si vos querés usar otra resolución, es tu elección, pero obviamente, si esta es menor a la recomendada, la pantalla se va a 'achicar', porque 1024x768 es una resolución 4:3, y 1280x800 es 16:10, y ubuntu trata de 'encajar' la resolución menor en el panel, pero sin distorsiones, usando cada 'punto' por pixel...

la verdad, desconozco si hay alguna forma de lograr que ubuntu 'estire' la resolución...

saludos

---

