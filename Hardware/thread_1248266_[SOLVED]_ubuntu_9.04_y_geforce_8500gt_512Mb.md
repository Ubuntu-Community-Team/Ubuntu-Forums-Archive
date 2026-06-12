---
title: "[SOLVED] ubuntu 9.04 y geforce 8500gt 512Mb"
date: 2009-08-24
forum: Hardware
---

### Post by pachecojuancarlos on 2009-08-24
hola gente: quiero preguntar porque es imposible ejecutar  tvtime luego de instalar esta tarjeta, es mas aun no le dije (porque no se) al sistema que la tiene y ya me causo problemas, aca mando cuando ejecute tvtime en consola

tvtimer
bash: tvtimer: orden no encontrada
juan@juan-desktop:~$ tvtime
Ejecutando tvtime 1.0.2.
Leyendo la configuración de /etc/tvtime/tvtime.xml
Leyendo la configuración de /home/juan/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

juan@juan-desktop:~$ 

como no se bien ingles no se que comandos ejecutar para que la tome agradeceria cualquier ayuda o sugerencia tambien aclaro que la tarjeta es opcional es decir la puedo cambiar por una ati pero creo que seria lo mismo porque no se como configurarla, finalmente les cuento que tvtime andaba joya con la placa de video que tiene la placa base que una P5KPL-AM, y salvando el problema que jamas pude hacer andar la radio ni escuchar el sonido de los vhs del reproductor por mi capturadora, lo demas siempre anduvo masa masa sobre todo trabajando en gimp, bueno espero ayuda muchas gracias

---

### Post by josecuervo86 on 2009-08-24
Primera pregunta: instlaste los drivers de la placa? Eso se hace en **Sistemas>Administracion>Controladores de hardware**. Allí van a aparecer los drivers compatibles con tu placa. Selecciona uno y luego reinicia. Fijate si despues de instalar los drivers el problema se soluciona

Saludos

---

### Post by pachecojuancarlos on 2009-08-25
josecuervo86: primero gracias por la ayuda con la instalacion del driver volvio a funcionar tvtime como si nada claro con una deficnicion de imagen muy superior,aca el problema de la tarjeta se acabo, yo pense que seria mas dificil, ahora disculpa la molestia me podrias indicar los pasos a seguir( o donde lo podria conseguir) para escuchar la fm y poder escuchar el sonido del reproductor de vhs, ya que imagen tuve siempre y muy buena pero no se como se graban en el disco y el sonido tampoco se como se graba de la radio y capaz que es algo simple que como no se hacerlo bueno, te mando la caracteristica de la capturadora: es una ENCORE TV TUNER PRO ENL TV-FM, el sistema la reconocio, en fin gracias por cualquier ayuda

---

### Post by Hei Ku on 2009-08-25
Esa consulta tiene que ir en un thread aparte. La consulta original ya esta resuelta y no estan relacionadas.

Pregunta resuelta. Thread cerrado.

---

