---
title: "Acer Aspire 5738"
date: 2010-10-18
forum: Hardware
---

### Post by Lutho on 2010-10-18
Tengo problemas con el touchpad, sobre todo cuando lo activo y lo desactivo.

de que forma puedo enfrentar ese problema
en ubuntu 10.04 LTS

alguna orientación
saludos comunidad.

---

### Post by nechus on 2010-10-18
Chócale!!!!!! Yo tengo el mismo Acer. Mi touchpad funciona, pero si lo desactivo no se vuelve a activar nunca más hasta que reinicio el equipo. En todo caso, como prefiero el mouse y nunca necesito desactivar el touchpad, no me da problemas.

¿Qué problema te da?

---

### Post by beren.olvar on 2010-10-18
Seria muy util ke describieras el problema.
podrias ademas adjuntar las partes relacionadas del output del comando "dmesg" cuando activas y desactivas el touchpad.

---

### Post by Lutho on 2010-10-18
explico con mas detalle.

el modelo acer aspire 5738 

[IMG]http://gallery.techarena.in/data/513/image125.jpg[/IMG]

al lado del touchpad tiene un botón, el cual se puede desactivar.
entonces muchas veces cuando uno presiona el botón para poder des habilitar el touchpad. Entonces ese mismo botón es quien activa nuevamente el touchpad.
Pero cuando lo vuelves a habilitar el touchpad no funciona.

mas menos esa es la problemática, si no tienes mouse usb, tienes que abrir la consola y reiniciar para que se vuelva ha activar.

---

### Post by beren.olvar on 2010-10-19
segun este post ([http://ubuntuforums.org/showthread.php?t=1154806](http://ubuntuforums.org/showthread.php?t=1154806)) en el foro en ingles, si reactivas el touchpad, y luego escribes en un terminal:

sudo modprobe -r psmouse
sudo modprobe psmouse

deberia volver a funcionar. Tambien dicen ke otra solucion es apretar ctrl+alt+f1 para ir a una consola virtual, y luego ctrl+alt+f7 para volver a tu servidor X. Una vez de vuelta el touchpad deberia funcionar.
Si entiendes algo de ingles te recomiendo ver el post ke te linkie y los bugreports a los ke hacen mencion.

---

### Post by Lutho on 2010-10-21
uuhh exelente, se agradece.
probe en desabilir el touchpad. siguido de eso probe los comandos 
sudo modprobe -r psmouse
sudo mmodprobe psmouse

y funciona.

muy agradecido.

---

