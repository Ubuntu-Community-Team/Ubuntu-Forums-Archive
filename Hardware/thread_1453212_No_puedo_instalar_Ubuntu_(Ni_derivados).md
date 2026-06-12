---
title: "No puedo instalar Ubuntu (Ni derivados)"
date: 2010-04-12
forum: Hardware
---

### Post by RedesXX on 2010-04-12
Hola, hace ya un año que vengo experimentando con Linux teniendo una relación de amor-odio por la falta de compatibilidad y conocimiento. Actualmente cambie mi motherboard y el procesador por los de un familiar que actualizo completamente el harware de su PC. Me tente con instalar linux nuevamente para seguir aprendiendo, y me di con que no podía hacerlo ya que no puedo cargar el instalador, ni siquiera en el modo de compatibilidad. Probe con Ubuntu 9.10, Linux Mint 8 Helena y Elive 2 (No se cual es la distro madre de este) y, con todos me sucedió lo mismo. Puedo botear la PC con los cds y elegir la opción de instalación, pero al parecer siempre termina en error. En el caso de los dos primeros mi monitor muestra el centro de la pantalla con cuadrados combinados. Ni siquiera pude hacer funcionar el modo instalado desde Windows.
Tengo una placa base Asrock, un procesador Intel Pentium 4 de 2,52 Ghz, 1 GB de RAM, un par de discos duros con decenas de GB libres (incluso tenia una partición exclusiva para Linux)y una placa de vídeo GeForce 5500 FX con 256 de RAM. Se me ocurre que lo que puede estar teniendo conflictos es la Motherboard o la placa aceleradora ya que son versiones no reconocidas en la pagina de sus creadores. Es decir Nvidia y Asrock.
Si alguien puede instruirme al respecto estaré muy agradecido, y aclaro nuevamente que soy novato en el manejo especifico de linux.
Saludos y gracias desde ya.

---

### Post by guillermolisi on 2010-04-13
Fijate en el BIOS que opciones tiene en la opcion Plug & Play. Algunas tienen alternativas como WinVista, XP, Otros, ninguno. Si esta en alguna de Win cambiala a Otros y proba.

La placa de video es PCI, AGP, PCI-Express, otra tecnologia ?
La motherboard posee placa de video integrada ? Si es asi, cual es ? (aqui tendras que recurrir al manual de la motherboard o pasar el modelo exacto para buscarlo via Google).

Los discos son PATA o SATA ?

---

### Post by atari130xe on 2010-04-13
Me pasó algo similar con la PC de una amiga a quien le instalé Linux Mint, porque fué con la única que logré hacer una instalación sin grandes problemass. Su mother es de la misma marca (Asrock) le compré una AGP 8X de 256MB de ram (chip Nvidia) y por alguna razón parece ser que la que tiene integrada (que es un chip Intel) no se "desactiva" al insertar la placa AGP y solo con Mint (en modo compatibilidad) logré hacer una instalación "normal" y con compiz activado sin problema alguno, pero los mother asrock realmente no son de mi agrado, espero tengas suerte!

Esto está extractado del foro de Ubuntu-es:

> No conseguí la solución a este problema
Enviado por maanroji el Sáb, 11/10/2008 - 04:40

En un principio, la motherboard no parece ser tan compatible con Windows ni con Linux. Según el fabricante, la motherboard viene con una tecnología llamada AGI, que según reemplaza a la AGP, por lo que no es totalmente compatible con las tarjetas graficas.

Segundo, el kernel panic surgue cuando intentas iniciar cualquier distribución, ya sea Knoppix, openSUSE, Fedore, te tira el mismo error debido a la incompatibilidad AGI.

Tercera, aún desactivandolo por blacklist dicha tecnología tiene problemas con el AGP en la Radeon, por lo mismo de que la ranura de la AGP es AGI

En conclusión, las Motherboards AsRock son INCOMPATIBLES con AGP y con Linux en general.

Saludos

***Antes de preguntar ten la curiosidad de investigar más a fondo***

Markus Anton


el hilo completo es: [http://www.ubuntu-es.org/index.php?q=node/76961]("http://www.ubuntu-es.org/index.php?q=node/76961")

Una posible solución:

> Resolution:

Blacklist the conflicting VGA module, preventing it from being loaded during all subsequent boots.

   1. Go into your computer&#8217;s BIOS, (usually hit F2, Delete or F11 when booting (first black on white text screen), mine is F2)
   2. Set the Video card to VGA, save changes. On my BIOS this is done by going to the &#8220;Advanced&#8221; screen, selecting the &#8220;Resource Config&#8221; menu and choosing the &#8220;Primary Graphics Adapter&#8221; option, changing it from AGI (NVidia card) to VGA (internal).
   3. Plug your monitor into the integrated video port, and let Ubuntu start (it should!)
      Update: for Ubuntu 8.10
      After doing a fresh install of Ubuntu 8.10, I could get to the login screen, but my desktop wouldn&#8217;t load. You may follow this step for any version of Ubuntu:
      At the login screen, press CTRL+ALT+F1. You will be brought to a command line. Enter in your username and password (set from the install). Type in the following commands:

          sudo nano /etc/modprobe.d/blacklist
          type in the password you used to log in
          Use your arrow keys to scroll to the bottom of the file
          Add the text (without quotation) &#8220;blacklist intel_agp&#8221;
          Press CTRL+X to quit the editor, Y to save changes, and enter to keep the filename (blacklist)
          type sudo reboot
          proceed to step 6.

   4. Open up a terminal, and enter in the following to modify the blacklist file
      sudo gedit /etc/modprobe.d/blacklist
   5. Add the following to the end of the file, in a new line
      blacklist intel_agp
   6. Save, exit and shut down computer.
   7. Go into your computer&#8217;s BIOS again
   8. Set the video card back to AGI/PCI (I didn&#8217;t see a difference, AGI = Asrock&#8217;s equivalent to AGP)
   9. Reconnect monitor to video card
  10. After Ubuntu loads (which it should now!) , I recommend running the Restricted Drivers system tool and install the NVidia restricted driver, then reboot.


Hilo completo: [http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/]("http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/")

Si te fijás en el ultimo comentario de este último post en Inglés alguien encontró una posible solución con Karmic:
> An update for Ubuntu 9.10.
there is an high probability thath you&#8217;ll not boot live cd at all, cause kernel panic comes up since initrd loading.
So you can&#8217;t boot system at all.
You need to modify initrd.lz located in you live ISO.
here the link to a tutorial.
[https://wiki.ubuntu.com/CustomizeLiveInitrd](https://wiki.ubuntu.com/CustomizeLiveInitrd)

Simply extract the intird filesystem, and modify /etc/modprobe.d/blacklist.conf adding
blacklist intel_agp.
repack initrd.lz and remaster the ISO

espero te sirva!

---

### Post by RedesXX on 2010-04-13
Gracias por las posibles soluciones, ya voy a poner manos a la obra intentando modificar el cd de ubuntu; pero antes me sugirieron en el foro español utilizar el "alternate cd" (que dicho sea de paso parecen llamar, los expertos, "varita magica").
Aclaro nuevamente que la VGA integrada no sirve (mi hermanito la forzó y desoldó intentando desconectar el monitor). La reparación se volvía muy complicada por donde yo vivo así que la desgracia trajo como solución una placa aceleradora. Efectivamente los ""genios"" de Asrock decidieron complicar mas las cosas al inventar AGI en vez de AGP, así que es muy probable que ese sea el problema de compatibilidad.
Desgraciadamente no manejo muy bien el ingles pero no creo tener mayores dificultades con las instrucciones expuestas anteriormente por ustedes generosos miembros de la comunidad.
Pego unos datos que anexe en una copia de este post (mi ansiedad me llevo a buscar la respuesta mas rápida posible):
**Datos extras: La motherboard y el procesador eran compatibles con Rxart Linux (ya que la PC vino con ese sistema operativo). La salida VGA no sirve porque esta desoldada pero la placa aceleradora funciona bien. La placa base es una Asrock P4I45Gx_PE. Y por ultimo, ya he instalado Ubuntu y Linux Mint varias veces en otras PCs.**

---

### Post by faktorqm on 2010-04-14
huelo a problemas con el chipset y/o configuracion de BIOS. A esta chica le pasa lo mismo y tiene la misma mother que vos con ubuntu andando. ([http://ubuntuforums.org/showthread.php?t=1429322](http://ubuntuforums.org/showthread.php?t=1429322))

chequea que las siguientes opciones esten asi

plug & play OS: YES
HPET timer: NO
primary display: AGP

estan todas en distintas partes pero que al menos esas tres digan eso es un buen lugar para empezar.

Saludos.

---

### Post by RedesXX on 2010-04-15
Creo que no hay opciones para el Plug and Play, del HPET timer no se nada (la verdad que nunca lo vi) y con lo del Primary display "AGP" es imposible porque las tres opciones que tengo son "Internal VGA" (la cual esta rota), "PCI" (Placas prehistóricas y carisimas) y "AGI" la cual, considero el origen del problema según los comentarios anteriores; de todas formas lo reviso enseguida.
Ya mismo pruebo quemar el Alternate CD y tratar con ese, ya que ayer me quede sin cds tras un fallo de grabación -parece que la PC entendió mis intenciones y 'penso' "Linux? No de nuevo!" jaja.
En unas horas subiré los resultados de mis intentos, intentando seguir todas las recomendaciones que pueda aplicar. Les agradezco nuevamente por su tiempo y si no lo logro con estas indicaciones los dejare en paz, para no resultar molesto con la misma problemática.
Saludos y éxitos.

---

### Post by atari130xe on 2010-04-15
> **RedesXX said:**
> Gracias por las posibles soluciones, ya voy a poner manos a la obra intentando modificar el cd de ubuntu; pero antes me sugirieron en el foro español utilizar el "alternate cd" (que dicho sea de paso parecen llamar, los expertos, "varita magica").
Aclaro nuevamente que la VGA integrada no sirve (mi hermanito la forzó y desoldó intentando desconectar el monitor). La reparación se volvía muy complicada por donde yo vivo así que la desgracia trajo como solución una placa aceleradora. Efectivamente los ""genios"" de Asrock decidieron complicar mas las cosas al inventar AGI en vez de AGP, así que es muy probable que ese sea el problema de compatibilidad.
Desgraciadamente no manejo muy bien el ingles pero no creo tener mayores dificultades con las instrucciones expuestas anteriormente por ustedes generosos miembros de la comunidad.
Pego unos datos que anexe en una copia de este post (mi ansiedad me llevo a buscar la respuesta mas rápida posible):
**Datos extras: La motherboard y el procesador eran compatibles con Rxart Linux (ya que la PC vino con ese sistema operativo). La salida VGA no sirve porque esta desoldada pero la placa aceleradora funciona bien. La placa base es una Asrock P4I45Gx_PE. Y por ultimo, ya he instalado Ubuntu y Linux Mint varias veces en otras PCs.**

Si me decís lo que no entendés en Inglés yo te ayudo, solo mandame un mje por privado y listo.

---

### Post by leonardomdq on 2010-04-15
El mismo mother Asrock tiene mi sobrina en su maquina, no trae la opcion Plug and Play en la Bios ni AGP (solo AGI , Internal VGA y PCI) para seleccionar como primary display , solo como menciona RedesXX. 
El unico efecto de escritorio que pude lograrle activar fue transparencias y sombras en Metacity mediante compositing manager (desde gconf-editor) ya que no pude activarle los efectos 3D.

---

### Post by RedesXX on 2010-04-23
Finalmente e desistido, probe con el Alternate CD, poniendo una placa de video PCI (No PCI-E), cambiando de disco duro y no es posible.
Los problemas con el Alternate CD son porque me da un error al intentar hacer las particiones con el sistema de archivos EXT4 o EXT3 (probe ambos) especificamente para el punto de montaje "/" raiz. Y con la placa PCI sucede lo mismo que con la AGP (en la ranura AGI). Se carga hasta la selección de idioma y una vez iniciada la instalación solo errores visuales; en el caso de los instaladores con compatibilidad, en modo texto, salen diversos mensajes de erro y, especificamente para Linux Mint parece haber problemas de compatibilidad con el mouse USB, jaja la que me faltaba!
Me quedare con las ganas de probar Ubuntu 10.4 y Elive 2.0. Por lo menos hasta que adquiera una nueva PC, para entonces ya estaremos por Ubuntu 14.4 version paga y Windows liberado con .exe y Open Source. Jaja.
Saludos y gracias nuevamente, disfrutenlo quienes puedan.

---

### Post by atari130xe on 2010-04-24
Intentaste hacer esto?:

> yo tengo una asrock y la nvidia 5200. ya pase por esto pero TIENE solucion, vas a poder usar la nvidia y la aceleracion 3d. el problema no es la tarjeta de video sino la mother.
1)tenes que cambiar el arranque del video en el bios y en lugar de agi poner onboard, luego conectar el monitor a la tarjeta onboard. de esta manera podes instalar linux normalmente.
2)hay que agregar la tarjeta onboard a la lista negra de linux modificando /etc/modprobe.d/blacklist donde hay que agregar intel_agp.
3)instalar los drivers de video de la nvidia.
4)reiniciar, pero cambiar en el bios la salida de video para agp en lugar de onboard y conectar el monitor a la nvidia.
OJO! te va a dar error y no va a arrancar las X pero todavia falta.
5)cuando te tira el error ir a /etc/X11/xorg.conf y donde dice "Device" cambiar donde dice driver a i810(o algo asi) por nvidia.
6)listo, ahora deverias poder arrancar normalmente.

espero que hallas comprendido todo.


Hilo completo en:
[http://www.ubuntu-es.org/index.php?q=node/22993]("http://www.ubuntu-es.org/index.php?q=node/22993")

Mirà no sè como seràs vos de testarudo pero yo si lo soy jejeje y por ejmplo ahora estoy dandole pelea a la RC de Lucid Lynx y la pc de un amigo que tiene un chip de video integrado VIA Chrome y lucid en el arranque sencillamente se vuelve loco, adelante no bajes los brazos, te aseguro que se aprende mucho con estos problemas, luego te volvès canchero hasta que puedan aparecer algunos nuevos, pero sirve :)

---

### Post by RedesXX on 2010-04-28
Jaja, ese es el problema principal: El video "onboard" no funciona porque la salida VGA integrada esta des-soldada por un mal uso de mi hermanito menor.
Quizas lo pruebe con el Virtual Box, aunque evidentemente no es lo mismo para nada y, mucho menos con una PC con tan bajos recursos. Saludos!

---

