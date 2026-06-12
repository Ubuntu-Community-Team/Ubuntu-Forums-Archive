---
title: "De monitor 1024*768 a widescreen"
date: 2008-10-26
forum: Hardware
---

### Post by nahuel_89p on 2008-10-26
Hola foro, en poco tiempo quizas cambie de monitor, y tenia una duda al respecto.
Ahora uso un 15 pulgadas flat 1024*768, y todo anda perfecto. Quería saber si es 100% seguro que me va a funcionar un wide de 19 pulgadas. No vaya a ser que lo compre al dope...
Segun lo que leí no es tan automatica la cosa, medio como que tengo que meterme en el xorg.conf o algo asi (el servidor grafico).
Ah, y dicho sea de paso, tengo una placa de video ATI 3100 (creo que radeon) integrada a la placa madre. (Esta placa de video corre al windows vista en resolucion wide perfectamente).
Como es en ubuntu?
Gracias

---

### Post by hictio on 2008-10-26
El metodo vieja escuela es que averigues en internet los modos verticales y horizontales de refresh rate de tu futuro monitor.
Con esos valores, editas tu archivo /etc/X11/xorg.conf, por ejemplo, esos son los valores que uso en un monitor Samsung:

```

Section "Monitor"
        Identifier      "Samsung SyncMaster 920NW"
        VendorName      "Samsung"
        Modelname       "920NW"
        Horizsync       30-81
        Vertrefresh     56-75
EndSection

```


Para la resolucion, lo mismo pero en la seccion:
```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Samsung SyncMaster 920NW"
        Device          "NV11 [GeForce2 MX/MX 400]"
        Defaultdepth    24
        Option          "AddARGBGLXVisuals"     "True"

        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1280x1024" "1280x960" "1024x768" "800x600"
                Viewport        0 0
        EndSubSection
EndSection

```

Reinicias X Window, Ctrl + Alt + Backspace, y tendria que empezar a usar los valores nuevos.

Hacele un backup antes de editar el archivo xorg.conf original:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.fecha

```

Igual, creo yo, a esta altura con todo tan desarrollado y avanzado en Ubuntu y con los drivers de video, dependiendo la tarjeta de video, y que tan moderno sea el monitor, gran parte del trabajo lo hacen ellos automaticamente, en mi laptop con una tarjeta de video NVIDIA semi ******a, conectado al mismo monitor Samsung, y usando el programa "NVIDIA X Server settings", detecto todo solo, y me permitio settear el monitor secundario, el Samsung, a una resolucion mayor que el LCD de la laptop, y ademas, settearlo no como mirror, sino como un monitor independiente, todo sin siquiera reiniciar X, estamos viviendo en el futuro!
Lo unico que no me parecio logico es que el programa para hacer todo eso 'nvidia-settings', no se instala por default cuando instalas los drivers de NVIDIA de Canonical/ Ubuntu.

Perdon, me fui por las ramas :)

---

### Post by Hei Ku on 2008-10-26
Lo primero que tenés que hacer es agarrar el manual de tu placa de video, y el manual del monitor, y comparar los modos disponibles a ver si son compatibles.
Si lo son, entonces despues es solo tocar el xorg.conf para poner el modo correcto.

---

### Post by nahuel_89p on 2008-10-26
Gracias por la respuesta rapida. A mi me convencería mas un modo gráfico, mejor... 
si entro a "preferencias"--> "resolucion de la pantalla", veo que puedo cambiar la resolución, pero no me deja mas de 1024*768, lo cual me parece raro ya que la placa de video que uso se banca resoluciones mayores (no se si de algun modo detecta que mi monitor es de 15 pulgadas, y que por eso quizas no me muestra para elegir esas mayores resoluciones, comentenme acerca de eso).
La otra es bajarme algun programa de ATI, onda lo que tenes vos, que use el driver de video para setear la resolucion wide...
Y si, a esta altura, andar tocando archivos de configuracion me parece medio retrogrado... y lo peor es que no se si comprar o no el monitor ya que no estoy seguro de que me vaya a andar... no tendria que pasar eso.
de todos modos repito, es seguro 100% que va a funcionar, sabiendo que ya anduvo el wide con vista?

Esto me sale del xorg.conf 

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Gracias por las sugerencias

P.D: mientras escribia ^esto^ respondio Hei Ku. Con respecto a tu comentario, cabe creer que si son compatibles ya que ese monitor (wide) y esta placa (ati 3100) funcionaron de 10 bajo win vista.

---

### Post by hictio on 2008-10-26
> La otra es bajarme algun programa de ATI, onda lo que tenes vos, que use el driver de video para setear la resolucion wide...

Pero no lo tenes instalado ya? Es decir, estas usando 1024x768 porque el monitor actual no permite mayor resolucion?
En mi caso, con tarjetas NVIDIA en las dos maqs que tengo con Ubuntu, tuve que instalar si o si los drivers de Ubuntu para que funcione (no solo la resolucion, sino tambien los Desktop Effects, etc).

Que driver esta usando X actualmente?

---

### Post by nahuel_89p on 2008-10-26
> **hictio said:**
> Pero no lo tenes instalado ya? Es decir, estas usando 1024x768 porque el monitor actual no permite mayor resolucion?
En mi caso, con tarjetas NVIDIA en las dos maqs que tengo con Ubuntu, tuve que instalar si o si los drivers de Ubuntu para que funcione (no solo la resolucion, sino tambien los Desktop Effects, etc).

Que driver esta usando X actualmente?

Si, tengo los drivers de ati instalados, no se cuales son, se instalan automaticamente; los efectos de escritorio de compiz andan un lujo, perfectamente, 3-d tambien, video, todo, absolutamente todo, y rapido. 

Y estoy usando 1024*768 porque mi monitor es de 15 pulgadas, yo nada mas intuía que si mi placa soporta resoluciones wide mayores (que sí lo hace ya que lo hizo con windows vista y un monitor wide 19`), al menos me figurarían en la lista de resoluciones disponibles en "preferencias"--> "resolucion de la pantalla", pero como no me aparecen resoluciones mayores a 1024, tiendo a creer que es porque de alguna manera ubuntu "detecta" que mi monitor es de 15 pulgadas. En caso de que me debieran figurar las resoluciones top de esta placa, algo pasa ya que no me figuran.

La pregunta es, ¿figuraran esas resoluciones cuando enchufe el wide?
...o ¿no hay algun programa de ATI (programa con interfaz grafica, no hablo del driver), que le "diga" al driver y a la placa la resolucion de salida? 

Si no, a tocar el xorg.conf


P.D: si ejecuto "displayconfig-gtk" me aparece, ademas de la lista de resoluciones, otra lista de tipos de monitores, wide, etc, por lo que asumo que va a bastar solo con eso para luego configurar la resolucion:)
Creo que ahi termina todo entonces, gracias.

---

### Post by sajnox on 2008-10-26
> **nahuel_89p said:**
> La pregunta es, ¿figuraran esas resoluciones cuando enchufe el wide?
...o ¿no hay algun programa de ATI (programa con interfaz grafica, no hablo del driver), que le "diga" al driver y a la placa la resolucion de salida? 


Cuando enchufes un monitor wide creo que automaticamente te lo detecta y actualiza resoluciones soportadas, sino con reconfigurar el xorg en forma automatica no tenes ningun problema

(Hablo por experiencia, pase de un 17" a uno de 20" wide)

---

### Post by Kabezon on 2008-10-26
Te lo debería agarrar al toque, yo pasé de un 17 flat a un 22 widescreen flat sin dramas. De última hacete fácil la vida y dejá que Envy te configure xorg automáticamente.
> sudo apt-get install envyng-gtk

---

### Post by hictio on 2008-10-26
Para las tarjetas ATI hay algo como 'nvidia-settings'? Digo, especialmente como para settear monitores secundarios, etc.

---

### Post by Hei Ku on 2008-10-27
Si usas el driver privativo hay un panel de control de ATI. Si usas el libre, podes usar el xrandr, o grandr para configurar todo eso.

---

