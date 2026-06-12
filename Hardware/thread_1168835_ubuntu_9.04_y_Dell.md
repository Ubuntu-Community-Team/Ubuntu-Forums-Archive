---
title: "ubuntu 9.04 y Dell"
date: 2009-05-24
forum: Hardware
---

### Post by capcabgue on 2009-05-24
```

```Hola a Todos,

Que bueno es esta nueva "casa" del foro, me costo un poco como inscribirme y hacer un post (quizas me equivoque y les pido disculpa)....pero volviendo al tema:

Alguien sabe como va ubuntu 9.04 en un Notebook dell Inspiron 1525??, hice la prueba conun liveCD y la pantalla se veía mucho mas chica (como si estuviera en VB y aún no hubiera instalado los guestAddition), como puedo asegurarme que todo este bien??

Gracias

---

### Post by Patriciologico on 2009-05-24
Hola capcabgue,

[Mira este enlace]("https://wiki.ubuntu.com/LaptopTestingTeam/Dell") Hay tres pruebas realizadas con Dell Inspiron 1525, comparalas para que te hagas una idea.

Saludos!

---

### Post by RafaelG on 2009-05-24
Hola Capcabgue bueno yo tengo un Dell Vostro 1510 con Ubuntu 9.04 y Windows Vista hasta el momento trabaja todo perfecto solo tiene un Pequeno detalle con la tarjeta grafica: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) la cual esta en la lista negra de Ubuntu por su inestabilidad segun Examenes hechos, pero bueno aca mismo en el Foro hay una manera de como sacarla de Blacklist y utilizar UXA para que  trabaje correctamente con Ubuntu.

---

### Post by Elkan76 on 2009-05-24
Rafael, yo uso ese mismo equipo en la pega, y efectivamente durante un tiempo Ubuntu 9.04 deshabilito Compiz debido a problemas, sin embargo, en las últimas actualizaciones reestableció su funcionamiento.
Revisa que tu equipo este actualizado para descartar este problema.

Saludos.

---

### Post by capcabgue on 2009-05-25
Gracias por los datos, pero como vi en el link que me envió patriciologico, no lo voy a instalar ya que necesito 2 pantallas para trabajar y en 9.04 aún nno esta testeado, quizas cuando tenga más tiempo para configurar y reconocer todo haré la prueba.

Bueno Muchas gracias por los datos de todas maneras

---

### Post by Patriciologico on 2009-05-26
> **capcabgue said:**
> Gracias por los datos, pero como vi en el link que me envió patriciologico, no lo voy a instalar ya que necesito 2 pantallas para trabajar y en 9.04 aún nno esta testeado, quizas cuando tenga más tiempo para configurar y reconocer todo haré la prueba.

Bueno Muchas gracias por los datos de todas maneras

Si haces la prueba recuerda que puedes publicar tu propio testing, en la wiki ubuntu.

Saludos!

---

### Post by ClarkXP on 2009-05-26
creo que pagondel tiene un dell con ese chipset, estoy casi seguro.
ayer en Duoc de Alonso de ovalle instalé su notebook con un datashow epson
y ningun problema para espejar ventanas por lo menos para presentaciones a 1024x768.
no he probado extender el escritorio.

con aceleracion grafica no he probado.


con otros notebook (con chipset ati hd3200) he tenido un par de problemas, pero solo basta con reiniciar el entorno gráfico y bajar la resolucion a 800x600 y luego volver a subirla a 1024x768 y queda bien, corriendo aceleracion despues de un rato se cae el entorno grafico.

---

### Post by pagondel on 2009-05-28
Tal y como dice mi amigo ClarkXP tengo un dell 1525 con ese chipset.
1- Tube dramas con la aceleracion grafica, pero nada que [ESTO](http://ubuntuforums.org/showthread.php?t=1166388) no pueda arreglar ;)
2- Tube dramas con el wifi (Intel 3945ABG), pero se arregla haciendo un:
```
sudo modprobe iwl3945
```
3-y finalmente Ubuntu no me reconoce el Jack del microfono, para eso:
```
sudo nano /etc/modprobe.d/alsa-base.conf
```
y agregamos la siguiente linea al final:
```
options snd-hda-intel model=dell-bios
```

Y si, los multiples monitores andan super bien ;)

Saludos!

---

### Post by capcabgue on 2009-06-10
Hola:

Bueno gracias por los datos y como dije hice un upgrade desde la 8.10 que tenia a jaunty, hasta ayer todo funcionaba, instale skype, google earth y virtualbox, que son los sw que más problemas me dan.
Lo malo fue que anoche me pidio un upgrade y desinstalar unoss paquetes, que como buen hijo de guin2 acepté sin leer con mayor detenimiento, hecho esto y reiniciado el pc (como se indicaba) me dejo de funcionar Interent (wifi y por red) y cuando lanzo skype me dice que hay problemas de playback....
Para solucionar lo del wifi hice lo que indicó pagondel eso de:

sudo modprobe iw13945, pero me dice 
FATAL: Module iw13945 not found.

Si hago click en el administrador de redes me sale una ventana indicando:
""Please contact your system administrator to resolve the following problem
SIOCGIFFLAGS error: No such device "

Alguien me puede ayudar con estos problemas??

Gracias

---

### Post by capcabgue on 2009-06-10
> **capcabgue said:**
> Hola:

Si hago click en el administrador de redes me sale una ventana indicando:
""Please contact your system administrator to resolve the following problem
SIOCGIFFLAGS error: No such device "


Este problema lo solucione, ya no me sale el error y si hago click en el administrador de redes solo me reconoce Lo con la ip de mi pc 127.0.0.
Las ethernet alambrica nii inalambrica las logra ver ni reconocer, no tengo idea de como conectarme a Internet (a no ser que pida prestado un PC).
Alguien sabe lo que tengo que hacer para que me reconozca o me conecte a internet por cable o wifi y en caso de hacer un install de algo, como si no tengo internet??

Gracias y ojala me puedan ayudar

---

### Post by pagondel on 2009-06-11
> **capcabgue said:**
> Hola:

Para solucionar lo del wifi hice lo que indicó pagondel eso de:

sudo modprobe iw13945, pero me dice 
FATAL: Module iw13945 not found.


es una L, iwL3945, no un 1 ;)
Saludos!

---

### Post by asilvan on 2009-06-11
Yo tengo un inspiron 1525 y tengo un pequeño problema....
realicé una instalación limpia, tenia problemas con mi aceleracion grafica y compiz, lo solucione (estaba en la lista negra la tarjeta), todo parece funcionar bien con los efectos de escritorio, PERO... los videos se ven con pequeñas lineas horizontales, como cortes, en las escenas de mas movimiento o con muchas luces (cosa que no me pasa en windows xp)...
habilite UXA, pero parece que por ahi no va la cosa...


alguna idea de lo que puede ser?

---

### Post by Carlos C on 2009-06-12
A ver, creo que este thread está empezando a irse para cualquier parte. La pregunta inicial de capcabgue era si tendría problemas instalando 9.04 en su dell. Creo que se le dio toda la información que necesitaba (se nota la buena voluntad de todos en este foro), pero creo que debería abrir otro thread para acotar cualquier duda o problema relacionado con su sistema.

asilvan, por favor abre un thread diferente en donde expongas tu situación, la idea es mantener el orden para que la información sea accesible a quienes tengan un problema similar.

Espero que nadie se lo tome a mal, únicamente lo digo para que el foro no se desordene. ;)

Gracias!

---

### Post by asilvan on 2009-06-13
OK, no hay problema, ¿como enojarme? ;)

disculpa, tienes razón, estaba desordenando el tema...

---

