---
title: "Problemas instalando Drivers NVIDIA"
date: 2009-06-18
forum: Hardware
---

### Post by jeko37 on 2009-06-18
Ayuda!!! soy nuevo en Ubuntu 9.04, decidi cambiarme de Windows a Ubuntu por un compañero de trabajo que me lo recomendo, configurar el equipo fue DIFICIL! realmente y ahora tengo un problema.

Resulta que ya tenia todo mi sistema listo y bien bonito (uso KDE) y se me ocurrio bajar el controlador de mi tarjeta grafica de Nvidia geforce 7100 para instalarla a pesar de que el driver que tenia preinstalado funcionaba de maravilla (queria actualizar el controlador)

mate el proceso kdm como decian en internet, instale el driver desde la consola y salio todo bien, pero al reiniciar me aparecio un cartel de error y la opcion de volver a una configuracion por defecto... eleji la de volver a la configuracion por defecto.

El cartel no me aparecio mas, el sistema inicio bien pero los controladores son los basicos, y no puedo volver a instalar el que estaba preinstalado.

Probe llendo al menu K/System/Hardware Drivers y elijo el controlador que siempre me aparece, lo instala sin problemas pero al reinciiar sigue todo como siempre.

el problema es que no puedo usar compiz, y los temas de las ventanas no se ven, y tambien de que las prestaciones son mucho menores con los drivers basicos

les envio lo que me tira el compiz:

Checking for Xgl: not present.
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log
Detected PCI ID for VGA:
Checking for texture_from_pixmap: Segmentation fault
not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present.
aborting and using fallback: /usr/bin/kwin
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Ayuda!!

---

### Post by ADICTOALMAXIMO on 2009-06-18
Mira yo actualise mi nvdia llendo a sistema, hardware y hay te dice si quieres instalarlo

fijate

---

### Post by faktorqm on 2009-06-18
> **ADICTOALMAXIMO said:**
> Mira yo actualise mi nvdia llendo a sistema, hardware y hay te dice si quieres instalarlo

fijate

Te esta diciendo que usa kde, no gnome.

jeko37: antes de intentar darte la solucion, quiero saber, ¿que necesidad tenias de actualizar el driver? probablemente ninguna, esa es la respuesta en el 99% de los casos. Hay un viejo dicho (supongo que no sos informatico, sino ya lo sabrias...) que dice "si anda, no lo toques". En este caso aplica por que recien estas empezando y si te andaba bien y con la aceleracion 3d y toda la bola, no deberias haberlo cambiado.

Cuando decis dificil, ¿a que te referis especificamente? esto te lo pregunto por que soy uno de los que hace los tutoriales sobre cosas en la comunidad y me interesaria tener algun feedback sobre que te paso cuando instalaste ubuntu. Yo separo, dificil, de "de facil resolucion", esto es, dificil, es compilar un kernel. un problema de facil resolucion es cuando no tenes la menor idea de que hacer, pero buscas en google, tiras 2 comandos en la consola y ya te anda todo. Ahora bien, hasta que no sabes eso, ese dato vale 1000 dolares, me explico? pero no es "dificil" sino que es un problema "de facil resolucion". 

Con respecto a tu post, ¿probaste envy-ng? Envy-ng es un programa grafico que te ayuda a instalarte el driver de ATI o Nvidia con 2 clicks, todo automaticamente. Lo podes buscar en el Adept si no lo encontras, o en la consola escribiendo

```
aptitude search envy
```

luego te dara todos los nombres de los paquetes que poseen la palabra "envy" (son dos si mal no recuerdo) y ahi haces:

```
sudo apt-get install a b
```

donde a y b son los nombres de los paquetes que te devolvio antes el comando de buscar separados por espacios.

Si no podes resolverlo, volve a postear y te seguimos ayudando. Salu2!

---

