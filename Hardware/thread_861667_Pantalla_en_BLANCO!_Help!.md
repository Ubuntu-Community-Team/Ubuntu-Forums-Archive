---
title: "Pantalla en BLANCO! Help!"
date: 2008-07-16
forum: Hardware
---

### Post by _kAz_ on 2008-07-16
Bueno esto no se si iba en Soft o en Hard.

La cosa es que ahora estoy en Gnome a prueba de fallos porque cada vez que accedo a Ubuntu cuando quiere cargar el escritorio se me queda la pantalla totalmente en blanco. Lo raro es que el escritorio esta, y tambien los programas, pero "por detras" de esa pantalla blanca. Cuando aprieto Ctrl+Alt+Supr por unos segundos aparece mi escritorio.

La macana fue querer instalar el soft propietaria de la placa de video ATI, pero como parecia no funcionar y me arrepenti volviendo al controlador privativo que viene con Ubuntu.

Reinicie y me dijo algo de la pantalla, a lo cual procedi a buscarla de una lista que se me abrio y luego de eso paso lo que cuento de la pantalla blanca.

Lo particular es que fije previamente en eso y la pantalla en el Ubuntu normal no decia ningun nombre, y ahora despues que hice eso si dice la marca del monitor y el tamanio (no tengo enie en a prueba de fallos).

Alguien que me pueda decir como solucionar esto please!
Sera el driver que instale o lo que cambie de la pantalla

**[SIZE="5"]EDIT[/SIZE]**

En la desesperacion busque poco en google, ya lo de la pantalla blanca se soluciono con esto:
```
sudo apt-get install xserver-xgl
```
Sin embargo es desastrosa la calidad grafica de los efectos del escritorio, ni hablar si quiero acceder a algun juego o algo por el estilo que todavia ni probe.
Dos preguntas:
1. Como hago para desinstalar en forma SEGURA :lolflag: los drivers que se instalaron en /usr/share/ati si no me equivoco
2. El teclado se me desconfiguro totalmente, no entiendo por que, si nada que ver. Alto quilombo hice, encima lo pongo en latino americano y no pasa naranja.

---

### Post by atari130xe on 2008-07-16
> **_kAz_ said:**
> Bueno esto no se si iba en Soft o en Hard.

La cosa es que ahora estoy en Gnome a prueba de fallos porque cada vez que accedo a Ubuntu cuando quiere cargar el escritorio se me queda la pantalla totalmente en blanco. Lo raro es que el escritorio esta, y tambien los programas, pero "por detras" de esa pantalla blanca. Cuando aprieto Ctrl+Alt+Supr por unos segundos aparece mi escritorio.

La macana fue querer instalar el soft propietaria de la placa de video ATI, pero como parecia no funcionar y me arrepenti volviendo al controlador privativo que viene con Ubuntu.

Reinicie y me dijo algo de la pantalla, a lo cual procedi a buscarla de una lista que se me abrio y luego de eso paso lo que cuento de la pantalla blanca.

Lo particular es que fije previamente en eso y la pantalla en el Ubuntu normal no decia ningun nombre, y ahora despues que hice eso si dice la marca del monitor y el tamanio (no tengo enie en a prueba de fallos).

Alguien que me pueda decir como solucionar esto please!
Sera el driver que instale o lo que cambie de la pantalla

**[SIZE="5"]EDIT[/SIZE]**

En la desesperacion busque poco en google, ya lo de la pantalla blanca se soluciono con esto:
```
sudo apt-get install xserver-xgl
```
Sin embargo es desastrosa la calidad grafica de los efectos del escritorio, ni hablar si quiero acceder a algun juego o algo por el estilo que todavia ni probe.
Dos preguntas:
1. Como hago para desinstalar en forma SEGURA :lolflag: los drivers que se instalaron en /usr/share/ati si no me equivoco
2. El teclado se me desconfiguro totalmente, no entiendo por que, si nada que ver. Alto quilombo hice, encima lo pongo en latino americano y no pasa naranja.

por lo poco que sé, cuando tenés problemas con Xorg se desconfigura el mouse, el teclado, etc. probaste con:
```
    sudo dpkg-reconfigure xserver-xorg -phigh


``` obviamente desde consola, luego que entres mas no sea en baja resolucion, tratá de re instalar el controlador pero esta vez, te sugiero lo hagas con EnvyNG si tenés Hardy (instala tanto Nvidia como ATI y lo hace muy bien al menos a mi me anda joya)

---

### Post by _kAz_ on 2008-07-16
> **atari130xe said:**
> por lo poco que sé, cuando tenés problemas con Xorg se desconfigura el mouse, el teclado, etc. probaste con:
```
    sudo dpkg-reconfigure xserver-xorg -phigh
``` 
obviamente desde consola, luego que entres mas no sea en baja resolucion, tratá de re instalar el controlador pero esta vez, te sugiero lo hagas con EnvyNG si tenés Hardy (instala tanto Nvidia como ATI y lo hace muy bien al menos a mi me anda joya)

Me sale esto
```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080716221715
```

---

### Post by _kAz_ on 2008-07-16
Gente esto se convirtió de suma urgencia.

Es IMPRESCINDIBLE desisntalar el controlador ATI propietario, ahora estarían corriendo ese más el privativo que viene con Ubuntu.

No se dan una idea del parto que significa navegar por internet, se tarda una eternidad en bajar el scroll de la pagina.

Ya no quiero saber mas nada con ATI, no lo vuelvo a hacer, pero por favor diganme como sacarlo de /usr/share/ati o de donde sea, así tengo la certeza que estoy utilizando un solo controlador.

---

### Post by Hei Ku on 2008-07-16
sudo apt-get remove xorg-driver-fglrx

sudo apt-get install xserver-xorg-video-ati

y despues probablemente tengas que pelear un poco con el xorg.conf para que te tome bien el driver libre.

---

### Post by [P]oli on 2008-07-17
Probá con el Envy, seguro te ayuda:
[Fijate (si podés) éste link también](http://www.codigogeek.com/2008/04/26/instalar-driver-nvidia-en-ubuntu-804-hardy-heron/). Es sobre cómo instalar Envy

---

### Post by _kAz_ on 2008-07-17
> **Hei Ku said:**
> **sudo apt-get remove xorg-driver-fglrx**

sudo apt-get install xserver-xorg-video-ati

y despues probablemente tengas que pelear un poco con el xorg.conf para que te tome bien el driver libre.

Hei Ku... si hago eso me desinstala lo que supuestamente quiero instalar: el controlador que se instala desde Sistema>Administración>Controlador de Hardware que viene predeterminado.

Lo que yo necesito desinstalar es el DRIVER que instale "MANUALMENTE" con el archivo que bajé desde la página de ATI, se llama **ati-driver-installer-8-6-x86.x86_64.run** y supuestamente está alojado en la carpeta /usr/share/ati.

Si elimino esa carpeta que pasaría?
> **'[P]oli said:**
> Probá con el Envy, seguro te ayuda:
[Fijate (si podés) éste link también](http://www.codigogeek.com/2008/04/26/instalar-driver-nvidia-en-ubuntu-804-hardy-heron/). Es sobre cómo instalar Envy

No pasó nada, no me desinstaló el driver :(

Para peor desinstale el xserver-xgl y primero volvimos a lo mismo (la pantalla blanca), después reinstalé un par de veces -porque no agarraba- el "driver ubuntu" desde Sistema>Administración>Controlador de Hard, y "mejoró", aunque no tanto porque la resolución mayor es de apenas 800x600.

Repito... **necesito desinstalar lo que se instaló con este archivo ati-driver-installer-8-6-x86.x86_64.run. Hay alguna manera???**

---

### Post by Hei Ku on 2008-07-17
Pone los pasos que seguiste para instalarlo manualmente, y ahi vemos.

---

### Post by _kAz_ on 2008-07-17
> **Hei Ku said:**
> Pone los pasos que seguiste para instalarlo manualmente, y ahi vemos.

Estemmmmmmmmmmmmmmmmm... como que ya es medio tarde :(

En este momento estoy desde el Live CD a punto de re-instalar, quise volver a como estaba, aunque funcionaran mal los efectos, pero no se qué paso que en lugar de pantalla blanca aparecieron rayas, rayas, y mas rayas. Esto no sería nada si esas rayas no aparecieran también en el modo a prueba de fallos de Gnome. En consecuencia no puedo hacer absolutamente nada ya que no veo nada de lo que estoy tocando o a que programa estoy entrando.
No me quedará otra que reinstalar, la verdad me siento profundamente frustrado, si bien fui yo quien se mando el moco de intentar instalar el driver oficial de ATI, fue a consecuencia de los cuelgues que ya se habían hecho insoportables.
Por lo pronto reinstalaré Ubuntu para recuperar los archivos y después pensaré bien si vuelvo a Windows, como dije la frustración con Ubuntu es bastante grande en este momento.

Por cierto... el driver "oficial" de ATI lo había instalado con el archivo run, es decir automáticamente, le di permisos de ejecución y realizo la instalación solo.

PD: alguna recomendación antes de reinstalar??? Creo que para no perder los arhivos sólo tengo que formatear la partición donde esta ubuntu y no el home, estoy en lo cierto?

---

### Post by [P]oli on 2008-07-17
Antes de reinstalar, fijate si podés abrir el archivo .run con el editor de textos
```

cd /carpeta/etcetc
gedit ati-driver-installer-8-6-x86.x86_64.run.

```

Si lo podés abrir, publicá el archivo, tal vez leyendo el instalador podamos hacer el desinstalador..

---

### Post by _kAz_ on 2008-07-17
> **'[P]oli said:**
> Antes de reinstalar, fijate si podés abrir el archivo .run con el editor de textos
```

cd /carpeta/etcetc
gedit ati-driver-installer-8-6-x86.x86_64.run.

```

Si lo podés abrir, publicá el archivo, tal vez leyendo el instalador podamos hacer el desinstalador..

No había forma... no podía ver nada de lo que hacía por las rayas que tenía el monitor.

Acabo de reinstalar y para completarla salio un DESASTRE, me formateó todo el /home (cuando lo instalé por primera vez eso no pasó), en consecuencia PERDÍ TODO.

Listo...

---

### Post by [P]oli on 2008-07-17
> **_kAz_ said:**
> No había forma... no podía ver nada de lo que hacía por las rayas que tenía el monitor.

Acabo de reinstalar y para completarla salio un DESASTRE, me formateó todo el /home (cuando lo instalé por primera vez eso no pasó), en consecuencia PERDÍ TODO.

Listo...

desde el live cd se podría haber bajado el archivo y se lo podía haber abiero, pero bueno, ya no se puede volver atrás :S..:(

---

### Post by alecleamas on 2008-07-22
Hola, por soy nuevo en el foro pero no tanto en Linux, al cual he regresado después de bastante tiempo.
Bueno, el problema es un bug del driver propietario de ATI, que si bien es pesadod en Hardy funciona mas rapido que en Gusty.
Para ATI son pantallas en blanco y para Nvidia pantallas en negro.
Estuve buscando en la red por una solución y no hay mucho.
Primero, el driver libre solo cubre los modelos mas viejos de ATI radeon para usar los efectos de Compiz.
Compiz por lo que recuerdo, si puede intenta arrancar por defecto, de ahí que muchas veces al encender aparezca la pantalla en blanco, cosa que no ocurre si el administrador es Metacity.
Cuando aparezca la pantalla en blanco y parece que los elementos están pero no se ven hay una solución para salir del paso que les puede funcionar:

Hacen clic sobre e fondo, para asegurarse que están en el escritorio y luego presionan Alt+F2, ahi escriben
metacity --replace y debería volver esl escrtorio, luego hay que fijar el administrador en Metacity.
Para configurar a inicial el driver: aticonfig --initial -f
El driver que mencionan es el último, en particular todo me funcionaba bien hasta que después de instalar Hardy del CD, se actualizó por primera vez el kernel y ahí se pudrio todo, con nuevas actualizaciones, nada, asi que debe ser alguna cosita en el xorg.conf

salu2

---

### Post by Hei Ku on 2008-07-22
Probaste con el radeonHD? Si bien es un poco mas inestable, anda mejor para las placas mas nuevas.

---

### Post by winterthurgines on 2009-05-06
> **alecleamas said:**
> Hola, por soy nuevo en el foro pero no tanto en Linux, al cual he regresado después de bastante tiempo.
Bueno, el problema es un bug del driver propietario de ATI, que si bien es pesadod en Hardy funciona mas rapido que en Gusty.
Para ATI son pantallas en blanco y para Nvidia pantallas en negro.
Estuve buscando en la red por una solución y no hay mucho.
Primero, el driver libre solo cubre los modelos mas viejos de ATI radeon para usar los efectos de Compiz.
Compiz por lo que recuerdo, si puede intenta arrancar por defecto, de ahí que muchas veces al encender aparezca la pantalla en blanco, cosa que no ocurre si el administrador es Metacity.
Cuando aparezca la pantalla en blanco y parece que los elementos están pero no se ven hay una solución para salir del paso que les puede funcionar:

Hacen clic sobre e fondo, para asegurarse que están en el escritorio y luego presionan Alt+F2, ahi escriben
metacity --replace y debería volver esl escrtorio, luego hay que fijar el administrador en Metacity.
Para configurar a inicial el driver: aticonfig --initial -f
El driver que mencionan es el último, en particular todo me funcionaba bien hasta que después de instalar Hardy del CD, se actualizó por primera vez el kernel y ahí se pudrio todo, con nuevas actualizaciones, nada, asi que debe ser alguna cosita en el xorg.conf

salu2

Buenas a todos. Este es mi primer mensaje en este fantastico foro y he elegido este post ya que meha ocurrido exactamente lo mismo. 

He seguido las indicaciones de este compañero y funciona perfectamente. Muchísimas gracias.

---

