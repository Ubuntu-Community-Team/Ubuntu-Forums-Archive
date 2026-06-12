---
title: "No puedo instalar WEBCAM, USB ID: 1b17:6111"
date: 2008-09-05
forum: Hardware
---

### Post by El Potro on 2008-09-05
Hola a todos!

Me compré una webcam Noganet 2mp y 480k, el asunto es que en windows funciona sólo instalando el driver que trae el cd, porque de por sí, la detecta como GENERIC WEBCAM. 

En Ubuntu 7.10, sólo me la detecta como 1b17:6111 (haciendo un lsusb)

Bien, la verdad es que no tengo idea para dónde disparar. ¿Qué puedo hacer? ¿Alguien ya compró y configurò esta cámara en linux?

¿No hay ningún driver disponible? Yo calculo que cualquiera que sea de 480k y de 2mp, genérico tiene que funcionar, aunque la verdad no quiero aventurarme a decir algo así, soy recién un principiante.

Por favor, denme una mano.

Muchas gracias,

Mauricio

---

### Post by faktorqm on 2008-09-05
Hay algo que no entiendo, vos decis que con lsusb te la detecta asi... ok, pero ¿con que programa la probaste? ¿como se ve? ¿con rayas? ¿se ve todo negro? la camara ¿"da señales de vida"? es decir, prende leds, hace ruido, algo? Salu2!

---

### Post by User21 on 2008-09-05
Probá instalando [Cheese]("http://www.gnome.org/projects/cheese/"), desde una terminal:
```
sudo apt-get install cheese 
```Debería aparecer el icono en alguno de los menues de aplicaciones. Con él, podes ver si la camara funciona, al menos, para empezar!!! Otra forma de detectar la camara es crear una videoconferencia via Flash en [http://www.tokbox.com](http://www.tokbox.com) (requiere crearse un usuario alli).

---

### Post by El Potro on 2008-09-05
Muchas gracias por ayudar!

Bueno, la cámara no responde en absoluto, está completamente muertita, ni una luz, ni nada.

Y ningùn programa me la toma, probé con este cheese y probé con otros de chat, EasyCam, y por el estilo y nada.

:confused::confused::confused:

---

### Post by faktorqm on 2008-09-05
Tenes una camara re jodida... ¿no la podes devolver? :lolflag:

El ID 1b17:6111 corresponde a la camara Webcam Crypto CME2+ Series II, y lo mas curioso es que los fabricantes ([http://www.crypto.gr](http://www.crypto.gr)) son de Grecia! acto seguido vi muchas respuestas en el foro de ubuntu de grecia (:o) que por supuesto no entiendo el idioma. 

La cosa es que encontre por otros lados que la camara algunos la hicieron andar con el driver gspca, pero las instrucciones estaban en ingles y para ubuntu 6.06, y la verdad no tengo tiempo justo ahora de traducirte el tutorial para 8.04 por que como te imaginaras hay que actualizar varias cosas y encima no tengo un gnu/linux cerca. En la pagina de gspca ([http://mxhaard.free.fr/](http://mxhaard.free.fr/)) el modelo aparece como no soportado (o sea, no aparece) pero dicen que anduvo igual (aclaro que la marca y modelo no eran esas, era una logitech creo).

Cualquier cosa lo podemos llegar a ver, calculo el lunes (me voy afuera) y anda investigando por v4l2 (video for linux 2) y por wxcam (programa manejador de camaras) a ver que pinta. Tambien podes probar VLC (solo te muestra la camara, en realidad es un reproductor de audio/video) pero capaz aunque sea sabes que es un problema de drivers/programa visor. Salu2!!

---

