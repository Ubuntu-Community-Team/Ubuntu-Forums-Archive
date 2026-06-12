---
title: "Problemas con placa de video"
date: 2010-05-09
forum: Hardware
---

### Post by jorgeosvaldo on 2010-05-09
Hola, tengo un problema, soy nuevo en esto y tengo una PC en la cual probé un live cd de ubuntu que me mostró las bondades del sistema. Era una versión 7, no tuve problemas con la placa de video, por defecto me tomó a 1024x768 y todo estaba OK.
Ayer me bajé de la página de Ubuntu la versión 10.4, directamente lo instalé y cuando inicia el sistema la máxima resolución que encuentro es 800x600, además de otra de 900x600 creo, pero de las conocidas la máxima es esa de 800x600.
He ingresado a varios foros y buscado en google una solución al tema, pero no la he encontrado. En varios lugares me dicen que debo modificar el archivo xorg.conf en la carpeta /etc/X11, pero mi sistema no tiene ese archivo.
La placa es una SIS y quisiera si alguien me puede ayudar lo agradezco de antemano.
Gracias.
Jorge

---

### Post by santiago79 on 2010-05-10
Mira primero re recomiendo que instales el driver de video de tu placa SIS con el comando lspci te va a decir el modelo.
después si no sabes de que manera instalar el driver o ya lo tenes. te recomiendo crear el XORG 
mira yo una vez tenia el mismo problema y lo cree para una placa intel, el proceso debe ser el mismo lo único que tendrás que editar algunos datos de tu placa. te dejo el link del foro donde lo solucione

[http://www.ubuntu-es.org/?q=node/120136](http://www.ubuntu-es.org/?q=node/120136)

en este momento el foro no esta funcionando pero pronto va a volver a funcionar.
si no te dejo otra alternativa que es con el comando 
$xrandr --output VGA --mode 1024x768 --rate 75
bueno lee esto que te explica mucho mejor

[http://ubuntulife.wordpress.com/2009/03/07/tip-ajustar-la-resolucion-de-pantalla-en-ubuntu/](http://ubuntulife.wordpress.com/2009/03/07/tip-ajustar-la-resolucion-de-pantalla-en-ubuntu/)

---

### Post by jorgeosvaldo on 2010-05-10
Gracias Santiago, voy a seguir tus consejos y luego comento lo que me ocurrió.

---

### Post by guillermolisi on 2010-05-12
Acaba de salir publicado [esto]("http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html"), en Ingles, para placas de video SIS.

No provee aceleracion 3D pero parece que si da un buen desempeño 2D. Cuestion de probar.

---

### Post by jorgeosvaldo on 2010-05-13
Hola muchachos, gracias por las ayudas, con respecto a lo que me sugeriste Santiago ninguna de las opciones me funcionó, ahora voy a probar con ese tutorial para SIS que me sugiere Guillermo, luego de las pruebas les voy informando que va pasando.
 
Gracias a todos por la invalorable ayuda.
 
Jorge

---

### Post by jorgeosvaldo on 2010-05-14
Hola Santiago y Guillermo, he probado todo lo que ustedes me han sugerido y nada ha funcionado, sigue sin poder aumentar la resolución a 1024x768. Realmente no encuentro una solución, es una lástima porque sino voy a tener que instalar una versión 7, que con esa funcionaba, sino volver a la porquería de Windows.
Les agradezco la atención y si alguien sabe como solucionarlo le pido que me brinde una ayuda.
Les reitero mi placa es una SIS 661/741/760.
Gracias.
Jorge

---

### Post by santiago79 on 2010-05-14
mira fijate bien lo del 
# xrandr

lee los comentarios de el pagina que te deje porque a mi me pasaba igual y leí todos y ahí me oriente a solucionarlo 
tenes que fijarte bien el monitor que te detecta por eso
aveces te detecta como defaut o vga o vga1 entonces cuando agregas el modo no te deja

---

