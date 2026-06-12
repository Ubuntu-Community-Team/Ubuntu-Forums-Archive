---
title: "video y resolucion"
date: 2009-03-27
forum: Hardware
---

### Post by daniland on 2009-03-27
Hola, instale ubuntu 8.04 en mi notebook bangho, pero no puedo modificar la resolucion de la pantalla, el chip de video es un sis mirage 3 según dice windows, no se como hacer para que reconozca ese video o que siga como ahora pero con más rsolución.
Espero una respuesta, muchas gracias.

Saludos


Daniel

---

### Post by hyperdude111 on 2009-03-27
To help others here is a rough English translation

-----------------------------------
Hello, I installed ubuntu 8,04 in my notebook computer bangho, but I cannot change the screen resolution, According to Windows the graphics card is a sis mirage 3, I do not recognize that video card but without the proper resolution it is hard to use.  I expect an answer, many thanks.  
-----------------------------------

---

### Post by gmunioz on 2009-03-27
Hola dan...:

Puedes intentar desde consola con xrandr

Para ejecutarlo, abres una consola (Aplicaciones - Accesorios Teminal) y escribes la orden:

sudo xrandr

Te dará una salida similar a esta:


Screen 0: minimum 320 x 175, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0*    51.0  
   832x624        52.0  
   800x600        53.0     54.0     55.0     56.0     57.0     58.0  
   720x405        59.0  
   720x400        60.0  
   680x384        61.0     62.0  
   640x480        63.0     64.0     65.0     66.0  
   640x400        67.0  
   640x350        68.0  
   576x432        69.0  
   512x384        70.0     71.0  
   416x312        72.0  
   400x300        73.0     74.0     75.0     76.0     77.0  
   360x200        78.0  
   320x240        79.0     80.0     81.0     82.0  
   320x200        83.0  
   320x175        84.0 

Es un listado de las resoluciones del monitor y de la actualmente en uso:

Para cambiar de resolución debes ejecutar en la consola la orden:

sudo xrandr -s N

Donde N es el número de la linea donde se encuentra la resolución que quieres aplicar comenzando desde la primer línea de resolución, que es 
la linea 0, siendo las siguientes 1, 2, 3 etc.

Por ejemplo para una resolución de 640 x 480 sería la orden:

sudo xrandr -s 6

Saludos.

---

### Post by guillermolisi on 2009-03-27
> **daniland said:**
> Hola, instale ubuntu 8.04 en mi notebook bangho, pero no puedo modificar la resolucion de la pantalla, el chip de video es un sis mirage 3 según dice windows, no se como hacer para que reconozca ese video o que siga como ahora pero con más rsolución.
Espero una respuesta, muchas gracias.

Saludos


Daniel
Para despejar dudas respecto del modelo de la placa de video, podrias mostrar la salida del comando lspci ?

---

### Post by josecuervo86 on 2009-03-28
Mira, anda a la terminal y pone

```
sudo /etc/X11/xorg.conf
```

Desplazate por el archivo hasta donde tenes enumeradas las resoluciones de panatalla y agrega en una linea la resolución que vos queres. Despues guarda el archivo y reinicia las X apretando Ctrl + Alt + Backspace

Ojala te sirva, igual googleando hay miles de tutoriales de como cambiar la resolución de la pantalla, y mucho mejor explicados que por mi :D

Adjunto imagen para que te ubiques:

---

### Post by infernus92 on 2009-03-28
van a hacer falta mas datos de los que estas dando... anda a un terminal y pone
```
lspci
```

y postea aca el texto que te salga

---

### Post by daniland on 2009-03-30
Hola Gracias a todos por sus respuestas, probe con el xandr pero no tengo resolucion mas que 800x600, eso supongo que es porque no esta instalado el chip de video, que luego puse lspci y me dio que es un sis 671/771, pero encontre que le puedo definir la resolucion y dejar el video que por defecto pone.Entonces lo edite con sudo.... xorg.conf y puse en "monitor"

HorizSync 30-107
VertRefresh 50-185

y de esa manera pude mejorar la resolución de pantalla. Luego con más tiempo trato de instalar el chip de video.

muchas gracias...

---

### Post by josecuervo86 on 2009-03-30
> Reason: mejoras ortograficas

**ortográficas** (es esdrújula)

jejeje :)

---

### Post by faktorqm on 2009-04-01
> **hyperdude111 said:**
> To help others here is a rough English translation

-----------------------------------
Hello, I installed ubuntu 8,04 in my notebook computer bangho, but I cannot change the screen resolution, According to Windows the graphics card is a sis mirage 3, I do not recognize that video card but without the proper resolution it is hard to use.  I expect an answer, many thanks.  
-----------------------------------

To help other go to your english forum section. we speak SPANISH ¬¬

Para ayudar a otros anda a tu seccion del foro en ingles. Nosotros hablamos ESPAÑOL ¬¬

---

### Post by clasificado on 2009-04-02
> **faktorqm said:**
> To help other go to your english forum section. we speak SPANISH ¬¬

Para ayudar a otros anda a tu seccion del foro en ingles. Nosotros hablamos ESPAÑOL ¬¬

Tampoco era necesario que echarle flí :lolflag:

Entiendo que el muchacho lo hizo de buena fe: en definitiva no reclamó por la traducción, sino que la hizo él mismo.

clasificado

---

### Post by guisheca on 2009-04-03
Yo hasta donde tengo entendido no existen drivers para linux de las placas sis, esto implica que no soporta aceleración gráfica. Si dios quiere esto dentro de poco se revertirá puesto que están trabajando en dicho driver.
Mientras tanto sólo podemos usar drivers genéricos que nos proporcionan mínimas funcionalidades.
Saludos.

---

### Post by guillermolisi on 2009-07-13
Acabo de leer en Planet Ubuntu-ar que hay un paquete.deb para placas de video SIS 771/671 que se realizo para Xorg 1.6

Mas info y el link para bajar el paquete en: 

[http://nacho.larrateguy.com.ar/2009/07/11/drivers-de-sis-771671-para-xorg-1-6-mandriva-2009-1-ubuntu-jaunty-9-04/](http://nacho.larrateguy.com.ar/2009/07/11/drivers-de-sis-771671-para-xorg-1-6-mandriva-2009-1-ubuntu-jaunty-9-04/)

---

