---
title: "Mouse track-ball logitech marble"
date: 2009-08-06
forum: Hardware
---

### Post by prostata on 2009-08-06
Estoy usando un mouse Logitech marble, que me da los siguientes peroblemas:

A)bajo entorno wxp y una vez configurado funciona correctamente
B)bajo Jaunty también funciona pero la utilidad de escroleo navegando con FF aparece desactivada, no hay forma de escrolear la página por lo que debo acudir al ascensor de la web para subir y bajar y eso es algo no solo lento sino "atrasado?" si tanto en wxp como en jaunty en lineas básicas me sorprende que la opción de escroleo no se reconozca en Jaunty, he probado colocando un adaptador PS/2 pero tampoco consigo activar esa opción....y en jaunty no tengo forma de configurar el ratón pues seguro que los drivers son privativos...he mirado en google y tampoco veo nada que me permita arreglar la situación...alguno de vosotr@s puede indicarme cómo hacer escroleo con el mouse bajo Jaunty...??

En otra máquina con wxp y Jaunty me ocurre lo siguiente:

arrancado bajo wxp este me ignora dicho mouse, sin embargo bajo Jaunty si trabaja aunque con los problemas mencionados

---

### Post by Hei Ku on 2009-08-06
Podes abrir una consola, ejecutar lsusb y postear aca lo que te sale? De esa manera sabemos bien tu modelo de mouse y vemos que puede ser.

Dos aclaraciones: 
El problema es de tu mouse y deberias quejarte con los fabricantes por lo "atrasado" de su driver para linux. Obviamente te vamos a ayudar, pero el primer responsable de tu problema es el fabricante.
Sugerir a alguien que es atrasado al mismo tiempo que le pedis ayuda no es la mejor manera de empezar, no?

Quizas hoy tenga un dia sensible, pero sentí cierto maltrato, por eso lo menciono.

---

### Post by prostata on 2009-08-06
> **Hei Ku said:**
> Podes abrir una consola, ejecutar lsusb y postear aca lo que te sale? De esa manera sabemos bien tu modelo de mouse y vemos que puede ser.

Dos aclaraciones: 
El problema es de tu mouse y deberias quejarte con los fabricantes por lo "atrasado" de su driver para linux. Obviamente te vamos a ayudar, pero el primer responsable de tu problema es el fabricante.
Sugerir a alguien que es atrasado al mismo tiempo que le pedis ayuda no es la mejor manera de empezar, no?

Quizas hoy tenga un dia sensible, pero sentí cierto maltrato, por eso lo menciono.

A ver, "atrasado" no es el Jaunty, "atrasado" es el procedimiento manual de scrolear, ya que debo hacerlo por medio del ascensor de la web. Espero haber aclarado el concepto..

Saludos

---

### Post by guillermolisi on 2009-08-06
Por favor, mostranos la salida de la ejecucion del comando lsusb, asi vemos de que forma Ubuntu esta reconociendo tu trackball.

Solo para descartar otras limitaciones, probaste con un mouse que no sea USB, que sea PS/2 original y que tenga la ruedita para el scrolling ?

---

### Post by staar on 2009-08-06
primero que nada, andá a Sistema > Preferencias> Combinaciones de teclas y fijate si le podés asignar esa acción (no se si está) al botón correspondiente del mouse, sino, lo más probable es que tengas que usar algún programa como xbindkeys y configurar a mano que hace cada botón del mouse, buscá por el foro, que había un thread de otro usuario con problemas con los botones de su mouse (creo que era un Logitech también, pero no el mismo modelo) y que lo había solucionado...

saludos

---

