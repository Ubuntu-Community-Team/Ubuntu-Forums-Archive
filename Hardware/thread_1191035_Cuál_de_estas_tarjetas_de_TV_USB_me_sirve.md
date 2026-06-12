---
title: "Cuál de estas tarjetas de TV USB me sirve"
date: 2009-06-18
forum: Hardware
---

### Post by vtssrm on 2009-06-18
Uso Ubuntu 9.04 en un netbook y quiero comprar una tarjeta de TV USB, no me importa que incorpore control remoto o radio FM, sólo necesito la TV. Me pregunto si ALGUNO de estos modelos que tiene PC-FACTORY me sirve:

Advantek Capturadora USB TV ATV-U700-HD c/Remoto
[http://pcfactory.cl/ficha.php?id=e86c6b80-9500-44d3-94cd-0693aab9581d](http://pcfactory.cl/ficha.php?id=e86c6b80-9500-44d3-94cd-0693aab9581d)

o

Sapphire Capturadora USB WONDER TV c/Remoto
[http://pcfactory.cl/ficha.php?id=12541133-f75c-4863-8490-fc62399fd5de](http://pcfactory.cl/ficha.php?id=12541133-f75c-4863-8490-fc62399fd5de)

o

Kworld Capturadora USB PlusTV - USB Stick
[http://pcfactory.cl/ficha.php?id=835852c1-1e86-41b1-ab5e-407521cdbe06](http://pcfactory.cl/ficha.php?id=835852c1-1e86-41b1-ab5e-407521cdbe06)

Gracias.

---

### Post by nopersona on 2009-06-18
Mira, acá hay una lista de tarjetas soportadas.

[http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.bttv](http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.bttv)

Acá un hilo interesante de los usarios Linux de la IX región. 

[http://gulix.cl/foro3/eleccion-tarjeta-tv-usb-para-ubuntu-8-10-t1264.html](http://gulix.cl/foro3/eleccion-tarjeta-tv-usb-para-ubuntu-8-10-t1264.html)

También te dejo el wiki de  linuxtv.org

[http://linuxtv.org/wiki/index.php/Main_Page](http://linuxtv.org/wiki/index.php/Main_Page)

Suerte!

---

### Post by vtssrm on 2009-06-18
> **nopersona said:**
> Mira, acá hay una lista de tarjetas soportadas.

[http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.bttv](http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.bttv)

Acá un hilo interesante de los usarios Linux de la IX región. 

[http://gulix.cl/foro3/eleccion-tarjeta-tv-usb-para-ubuntu-8-10-t1264.html](http://gulix.cl/foro3/eleccion-tarjeta-tv-usb-para-ubuntu-8-10-t1264.html)

También te dejo el wiki de  linuxtv.org

[http://linuxtv.org/wiki/index.php/Main_Page](http://linuxtv.org/wiki/index.php/Main_Page)

Suerte!

Busque en la lista de tarjetas y no las encontre... significa que hay que descartarlas?
En el hilo que dejaste hacen referencia a la tarjeta Genius TVGO A03 que YA SE SABE que no tiene soporte en Ubuntu...

Gracias.

---

### Post by Patriciologico on 2009-06-19
Lo importante es el chip que trae la tarjeta de tv, la mia pctronix trae un Philips Semiconductors SAA7130 y funciona bien, eso si el control remoto nunca he intentado configurarlo. Por otro lado dicen que aun mejor soporte tiene el chip BTTV.

Saludos

---

### Post by kurilox on 2009-06-19
Hola, yo tambien ando buscando una targeta de TV USB y estaba mirando las mismas que posteo vtssrm en especial esta [TARGETA,]("http://pcfactory.cl/ficha.php?id=e86c6b80-9500-44d3-94cd-0693aab9581d") pero tengo otra duda: 
Si compro una C. de TV digital (ATSC) recivira alguna señal digital?, porque tengo entendido que en chile no hay señales digitales, almenos por ahora y ademas ATSC es la norteamericana y chile aun no se decide por las 3 bandas (americana, europea, japonesa), quisas se decidan por la europea y tenga que dejarla tirada.
¿Conviene comprarla ?

Si es posible vtssrm, me gustaria que dijieras por cual te inclinaste y me dices si te funciono en Ubuntu. Desde ya muchas gracias.

EDIT: Leyendo el manual de referencia de la targeta usa este chip. Textual "Recividor usa los chipset avanzados microtune + Auvitek", alguno ha probado es tipo de chip?

---

### Post by giov on 2009-06-19
Tengo una Gennius tvgo a03...   como la puedo hacer funcionar en linux???   no kiero perderla...  por que ta casi nueva

---

### Post by vtssrm on 2009-06-19
> **kurilox said:**
> Hola, yo tambien ando buscando una targeta de TV USB y estaba mirando las mismas que posteo vtssrm en especial esta [TARGETA,]("http://pcfactory.cl/ficha.php?id=e86c6b80-9500-44d3-94cd-0693aab9581d") pero tengo otra duda: 
Si compro una C. de TV digital (ATSC) recivira alguna señal digital?, porque tengo entendido que en chile no hay señales digitales, almenos por ahora y ademas ATSC es la norteamericana y chile aun no se decide por las 3 bandas (americana, europea, japonesa), quisas se decidan por la europea y tenga que dejarla tirada.
¿Conviene comprarla ?

Si es posible vtssrm, me gustaria que dijieras por cual te inclinaste y me dices si te funciono en Ubuntu. Desde ya muchas gracias.

EDIT: Leyendo el manual de referencia de la targeta usa este chip. Textual "Recividor usa los chipset avanzados microtune + Auvitek", alguno ha probado es tipo de chip?

Creo que si vemos el punto de si conviene comprarla porque recibe ATSC, esta claro que no, pero tu haces referencia a que trae el chip microtune y viejo ese chip esta soportado. Podrías por favor pegar el enlace del documento que leíste para poder confirmarlo a la brevedad ya que por lo menos yo no necesito que reciba señal digital, a mi me basta con que se la pueda con la señal analógica.

---

### Post by vtssrm on 2009-06-19
> **giov said:**
> Tengo una Gennius tvgo a03...   como la puedo hacer funcionar en linux???   no kiero perderla...  por que ta casi nueva

Compañero por lo poco que se esa tarjeta no es posible hacerla funcionar, pero te pido que no te des por vencido y que _**por favor**_ abras un nuevo tema con tu problema, así podemos tener el foro más organizado.

---

### Post by kurilox on 2009-06-20
Hola vtssrm, el documento que leí es este "[Documento]("http://www.advanteknetworks.com/spanish/support/atvu700hd/ATV-U700-HD%20Spanish.pdf")" el cual lo encontre en la [pagina del fabricante]("http://www.advanteknetworks.com/spanish/products/tvtuners/atvu700hd.html") en seccion "Soporte - Manual". En cuanto a que el chip microtune ahora que me dices que esta soportado buscare mas informacion para echarlo andar sin ningun problema aunque aun no la he comprado.

Edito:
 Buscando como configurar la targeta, he encontrado [muchos manuales]("http://elmundoen3d.blogspot.com/2008/11/capturadorora-de-tv-saa713x-en-ubuntu.html") para otro tipo de targetas donde hacen referencia a:

La lista de tuner soportados son los siguientes:[FONT=monospace]
     tuner=45 - Microtune 4049 FM5[/FONT] [FONT=monospace]
     tuner=49 - Microtune 4042 FI5 ATSC/NTSC dual in (este creo que seria)
pero en "[/FONT]La lista de tarjetas soportadas (al kernel 2.6.27)" no hace referencia a la targeta ni al chip aver si me aclaras la pelicula :P 
Si encuentras algo de como configurarla te pido que lo publiques.
[FONT=monospace] [/FONT]
Saludos.

---

