---
title: "[SOLUCIONADO] Recomponer el panel superior del escritorio"
date: 2009-07-03
forum: Instalación y Actualización
---

### Post by jorval on 2009-07-03
Hola amigos. Hace unos días algo hice que desordenó mi panel superior Ubuntu 8.04. Podrán notar que los íconos del parlante, la fecha y el botón de salir están casi en el centro del panel. He tratado de moverlos a su ubicación original, extremo derecho, y no lo puedo hacer. ¿Alguna sugerencia? Gracias.

[[IMG]http://img178.imageshack.us/img178/9564/pantallazoh.th.png[/IMG]]("[URL=http://img178.imageshack.us/i/pantallazoh.png/)"][[IMG]http://img178.imageshack.us/img178/9564/pantallazoh.th.png[/IMG]](http://img178.imageshack.us/i/pantallazoh.png/)[/URL]

---

### Post by aolivares on 2009-07-04
Desmarcaste la opción bloquear al panel??

---

### Post by jorval on 2009-07-04
aolivares. Sí, pero los parlantes y el calendario no se mueven, el botón de salida logré desplazrlo. Saludos.

---

### Post by CdK1 on 2009-07-04
No te hagas problemas y borra los directorios del gnome rm -r ~/.g*

---

### Post by jorval on 2009-07-04
CdK1. ¿Cómo puedo ver los directorios de gnome que borraría con ese comando?

---

### Post by CdK1 on 2009-07-04
en tu $HOME/

CdK1@Caturra:~$ ls .g     ==> Tabulador
.gconf/          .gnome2/         .gstreamer-0.10/ 
.gconfd/         .gnome2_private/ .gvfs/           
CdK1@Caturra:~$ ls .g

---

### Post by jorval on 2009-07-04
CdK1. Gracias, me dió esto:

jorval@jorval-laptop:~$ ls .g
.gconf/          .gnashrc         .googleearth/    .gtk-bookmarks
.gconfd/         .gnome2/         .gpilotd/        .gvfs/
.gimp-2.4/       .gnome2_private/ .gpilotd.pid     
.gksu.lock       .gnupg/          .gstreamer-0.10/ 

Mi duda es si hago: ```
rm -r ~/.g* 
``` ¿No se borrarán todos esos archivos? ¿Podrías explicármelo? Saludos.

---

### Post by CdK1 on 2009-07-04
Claro, se borrar los archivos, directorios que empiecen con .*, una vez hecho eso, reinicias Gnome y configuras de nuevo...

---

### Post by jorval on 2009-07-04
Gracias CdK1, pero preferiría, si la hay, alguna otra sugerencia que no me haga configurar de nuevo Gnome. Saludos.

---

### Post by CdK1 on 2009-07-04
En ese caso borra esos elementos del panel y agrégalos de nuevo...

---

### Post by moreback on 2009-07-05
Después de desbloquearlos yo los muevo con el botón de medio del mouse (rueda). Si uso también las mayúsculas, puedo empujar varios applets a la vez.

PD: Cdk1, tu solución es muy drástica, te sugeriría que pensaras en soluciones menos invasivas antes de postear, la mayoría no quiere perder sus configuraciones.

---

### Post by jorval on 2009-07-05
¡Sí! funcionó. Muchas gracias Moreback. Los moví a su posición original apretando el botón central del mouse. Antes probé lo de arrastrarlo apretando Mayúsculas pero no funcionó. Damos esto por solucionado y agradezco a los que ayudaron. Saludos.

---

