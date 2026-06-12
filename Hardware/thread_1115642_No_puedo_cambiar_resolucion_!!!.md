---
title: "No puedo cambiar resolucion !!!"
date: 2009-04-04
forum: Hardware
---

### Post by PichonDePinguino on 2009-04-04
Hola gente !!! soy nuevo en esto de linux (un pichon!!). El tema es q acabo de instalar ubuntu 7.04 y anda perfecto! solo tengo el problema de q no puedo cambiar la resolucionde pantalla, solo me permite la fea resolucion de 640x480. Revise el archivo xorg.conf pero ahi si estan las opciones de otras resoluciones, no se cual sera el problema, tengo una placa de video integrada intel 82845 G/GL/GE/PB/GV, sera q tengo instalar los drivers? bueno espero alguien pueda ayudarme! mil gracias.

---

### Post by Monchix on 2009-04-04
Hola como andas, Te Felicito por estar probando Ubuntu, espero que sigas este camino que no te vas a arrepentir.
Bueno con respecto a tu problema, te paso unas soluciones que a mi me sirvieron, tendrias que probar y cualquier cosa avisa por este medio.

A- Proba esto:
[http://raulespinola.wordpress.com/2009/04/04/cambiar-resoluciones-de-pantalla-por-consola-en-linux/](http://raulespinola.wordpress.com/2009/04/04/cambiar-resoluciones-de-pantalla-por-consola-en-linux/)
De paso le hago un chivo a mi blog, espero te sirva.

B- Si lo de arribo no soluciono tu problema: 
 $ sudo dpkg-reconfigure xserver-xorg

Esto es para volver a configurar la pantalla de nuevo, una vez termine volve a probar lo de arriba, y elegi la resol. que estas buscando

Cualquier cosa avisa

---

### Post by staar on 2009-04-04
> **PichonDePinguino said:**
> Hola gente !!! soy nuevo en esto de linux (un pichon!!). El tema es q acabo de instalar ubuntu 7.04 y anda perfecto! solo tengo el problema de q no puedo cambiar la resolucionde pantalla, solo me permite la fea resolucion de 640x480. Revise el archivo xorg.conf pero ahi si estan las opciones de otras resoluciones, no se cual sera el problema, tengo una placa de video integrada intel 82845 G/GL/GE/PB/GV, sera q tengo instalar los drivers? bueno espero alguien pueda ayudarme! mil gracias.

una pregunta.. porque instalaste la version 7.04?, ese ubuntu tiene 2 años (por eso el 7.04, abril del 2007), y en linux y en esta distro 2 años es mucho tiempo, muchisimos errores y vulnerabilidades son corregidos en dos años, además del agregado de (bastantes) nuevas funcionalidades...
te recomiendo que, si podes, te consigas una version más nueva como la actual 8.10, o la 8.04 que es una LTS (tiene soporte y actualizaciones por más tiempo), sino podes esperar hasta fin de mes que sale la 9.04...

respecto a tu problema, si tenes una placa Nvidia, podes solucionarlo instalando nvidia-settings (suponiendo que hayas instalado los drivers privativos) y corriéndolo en una terminal con permisos de administrador ```
sudo nvidia-settings
``` y modificar la resolución desde ahí ;-)

saludos

---

### Post by PichonDePinguino on 2009-04-04
hola, sigo todavia sin resolver mi problema de resolucion. probe con el comando xrandr y solo me aparece la resolucion de 640x480. Despues trate de reconfigurar el xorg como dijiste y ahi se pudrio del todo. no arranco mas el modo grafico!!! asi q reinstale todo. habrá otra solucion? espero una respuesta amigo.
a me olvidaba en la lista de tarjetas graficas no aprarece intel, yo seleccione i810. sera la indicada?

---

### Post by Hei Ku on 2009-04-04
Por que no instalas algo mas nuevo? Vas a tener mejor suerte con los drivers.

---

### Post by Monchix on 2009-04-04
Como andas, evidentemente no te tomo todas las resoluciones de tu pc, lo mejor seria probar la version 8.04 que tiene mejor soporte, y esta muy buena (es la que yo uso) o si no la 8,10.

---

