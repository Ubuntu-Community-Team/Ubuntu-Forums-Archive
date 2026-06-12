---
title: "desistir del uso de la webcam???"
date: 2008-06-23
forum: Hardware
---

### Post by beatlina on 2008-06-23
Hola gente, me presento ante todo mi nombre es Betina, la beatlemaniaca, por eso lo de Beatlina...
Les cuento un poco mi problemita, que para muchos puede ser algo tillado, pero he leído todo lo que se puede leer por aquí por google, en todos lados y no logro nada.
Estoy utilizando por primera vez UBUNTU comence con esto nueva distro 8.04, y no logro hacer funcionar mi webcam, paso lo que me tira el lsusb a ver si alguien puede darme una mano:
Bus 001 Device 004: ID 06a2:0003 Topro Technology, Inc. 

Bien el problema se da cuando quiero ejecutar cualquier programa para ver la webcam y dice lo siguiente:
imposible abrir/dev/video0.
Mira si tu sistema tiene el driver de tu webcam o cambia de dispositivo en opciones->preferencias.

Obviamente trate de montar eso, tb de cambiarla de puerto, miles de cosas, no se mucho de compilar y esas cosas, para más datos que puedo dar estoy usando el kernel 2.6.24-17-generic.

Instale también los dos drivers más "genéricos" que parecen existir gspca y otro que no recuerdo el nombre pero nada...

Espero que alguien me pueda dar una mano....

gracias.

ps. ah por si sirve para algo la marca de la webcam es BITROM

---

### Post by Hei Ku on 2008-06-23
por lo que vi, todavia no esta soportada para linux. :(

---

### Post by sdm_cacto on 2008-06-23
Tengo una laptop dell, y me reconocio la webcam en seguida, en tu caso, googleando encontre esto:

> Primero mira aqui: [http://www.qbik.ch/usb/devices/devices.php](http://www.qbik.ch/usb/devices/devices.php)
 a ver si tu camara esta soportada... 
 Si no aparece, podrias intentar instalar varios drivers para webcams: (ov511, spca,pwc, etc...)  
 El problema es que los fabricantes de webcams no especifican con que chip trabajan.. eso lo hace mas dificil... incluso entre varios lotes de una misma camara pueden cambiar el chip!!


asiq si tenes tiempo intenta instalar esos drivers (ni idea como) y sino instalando cheese y sus dependencias. Suerte.

---

### Post by beatlina on 2008-06-23
Gracias gente muchas gracias, aun no lo solucione pero me encanta saber que hay gente como ustedes dispuesta a ayudar, me parece más que genial... 

La verdad es que más que nada por intuición a mi me pinta que tiene que ver con el mensajes este mas que con los drivers...

Imposible abrir/dev/video0.
Mira si tu sistema tiene el driver de tu webcam o cambia de dispositivo en opciones->preferencias.

---

### Post by faktorqm on 2008-06-23
Tambien podés probar con VLC. VLC en principio es un reproductor de videos, mp3, etc pero tambien te deja seleccionar /dev/video0, de hecho yo puedo ver ahi tanto mi webcam como mi capturadora de video. Sé que capaz no es la solucion pero... lo unico que tendrias que hacer es averiguar si saca fotos... :P mi webcam es una creative webcam plus usb (del año del ñaupa) y me la reconoce como ov511. Salu2!!

---

### Post by RJQ on 2008-06-24
Si no lo has hecho antes trata de cambiar los permisos y o el dueño de dev/video0, también correr los programas como administrador, en ocasiones estos simples pasos tienden a funcionar. (en linux encontré que usar una videocámara como webcam es mucho mas fácil en caso necesites otra opción. suerte!

---

### Post by beatlina on 2008-06-24
faktorqm Gracias por tu respuesta estoy instalando VLC luego te cuento sobre ello.

RJQ, te cuento que soy administrador@ del sistema y también dueña del dev/video0, tengo mi video camara pero no tengo idea si es posible hacerla funcionar como webcam, es una benq c800... gracias a todos por la ayuda... como dije antes es increible que haya gente con tantas ganas de ayudar!!!!

---

### Post by RJQ on 2008-06-26
> **beatlina said:**
> 
RJQ, te cuento que soy administrador@ del sistema y también dueña del dev/video0,
Aun como administradora trata de usar gksudo para abrir equis programa que necesites para el video, en mi caso este paso es indispensable (aun que automatizado con el rc.local)
> tengo mi video cámara pero no tengo idea si es posible hacerla funcionar como webcam, es una benq c800...
corrígeme si me equivoco pero ese modelo parece ser una cámara digital de fotografía  el problema aquí radica en el usb, disculpa que no fui mas especifico en mi comentario, la opción para video-cámara hace base en las conexiones firewire la cuales tienen buen soporte en Hardy, claro con video-cámaras digitales, para análogas es necesaria una tarjeta de video que haga digital la señal pero ese es otra historia...
volviendo a tu webcam tiene que haber una razón por la que no puede usar dev/video0 y generalmente es la falta de el driver, o el permiso, o inclusive puede estar bajo algún otro puerto y no nesesariamente dev/video0, siempre intenta la mas fácil primero...
> gracias a todos por la ayuda... como dije antes es increible que haya gente con tantas ganas de ayudar!!!!

es la fuerza de la comunidad, gran cantidad de usuarios tienden a aumentar las posibilidades de las soluciones... no se te olvide dar vueltas por todos los foros de el sitio. suerte!

---

