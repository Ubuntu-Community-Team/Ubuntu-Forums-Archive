---
title: "clear CMOS"
date: 2012-01-21
forum: Hardware
---

### Post by Vero1 on 2012-01-21
Tengo un grave problema.
Configuro la BIOS para la secuencia de arranque pero no me lo respeta. Me toma los cambios pero no los respeta. 
Yo quiero tener como primer arranque CD/DVD pero por default sale primero uno de mis discos duros que contiene Windows.
Cuando hago el cambio en la BIOS y reinicio, me pide el CD de ASUS. Actualiza la BIOS según este CD pero luego pasa lo de antes. Arranca con HDD.
Necesito me indiquen cómo se hace un clear CMOS que, me dijeron, podría solucionar el problema.

Mi Placa Madre es ASUS P5KPL-Am SE.

Desde ya muchas gracias.

Saludos.
p.d.
Aclaro que saqué la pila y la volví a colocar, pero no hubo cambios.

---

### Post by granjero on 2012-01-21
hola, hiciste un upgrade del BIOS con la descarga de la página de asus?

Salud!

---

### Post by Vero1 on 2012-01-21
Hola granjero,

No, no hice nada todavía.

saludos

---

### Post by EnriqueK on 2012-01-21
Cuando tengo este tipo de problemas "raros", usualmente los resuelvo con desconectar el equipo de la toma de electricidad, o sea desenchufandolo por un par de minutos, esto es así por que por mas que tengas el equipo apagado, siempre hay partes que consumen energía.
Respecto al reseteo de bios, tendrás que consultar el manual de tu placa base o también podés descargarlo de internet si es que no lo tenés, este es un tema algo delicado y que varía en cada placa base.

---

### Post by Vero1 on 2012-01-22
Hola EnriqueK,

Lo de desenchufar ya lo hice cuando saqué la pila pero todo sigue igual.
Entré en BIOS y le puse el default setting(porque me comentaron que el default setting indica como primer arranque CD/DVD) pero tampoco surtió efecto.
Si le pongo como primer arranque CD/DVD me sale una leyenda que pide el CD de ASUS y hasta que no lo pongo y copia los settings de allí, no puedo entrar en el SO. Debido a ésto le puse el default que hace arrancar con el HDD. Pero debo arreglar ésto urgente, comprenderás por que.
No tengo manual de la Placa Madre, así que veré en Internet.
Yo quería hacer clear CMOS porque tengo entendido que si cambio de pins, por unos segundos, un pequeño componente que viene y que está cerca de la pila, eso hace un clear CMOS, pero tengo que encontrar exactamente donde está.
Bueno, gracias por tu tiempo.

Saludos

---

### Post by EnriqueK on 2012-01-22
Creo que es este el manual de tu Mobo
[http://static.highspeedbackbone.net/pdf/E4236_P5KPL-AM%20SE_u.pdf](http://static.highspeedbackbone.net/pdf/E4236_P5KPL-AM%20SE_u.pdf)

---

### Post by Vero1 on 2012-01-22
Efectivamente EnriqueK,

Muchas gracias. En la página 16 está indicado lo que necesito.

No sé si hoy, pero haré el cambio correspondiente.

Despues te informo.

saludos

---

### Post by Vero1 on 2012-01-27
Hola EnriqueK,

Por fin hice el clear CMOS pero de nada valió.
No sé por qué motivo BIOS no me respeta la secuencia de arranque, cosa tan importante.
Desenchufé, saqué la pila, cambié de lugar el(no recuerdo el nombre ahora) y lo volví a colocar como estaba a los 10 segundos, como se indica. 
Cambié la hora que se había borrado y traté de poner la secuencia de arranque que yo quiero pero sigue sin aceptar.
La verdad es que ya no sé qué hacer.
Lo que sí pude hacer es un disco USB de arranque, por si acaso.
El CD de Asus tiene un tool para actualizar. No sé si probar con éso.
Hay manera de hacer un backup de BIOS? por cualquier problema?

gracias y saludos

---

### Post by alfplayer on 2012-01-27
Hola.

> **Vero1 said:**
> Si le pongo como primer arranque CD/DVD me sale una leyenda que pide el CD de ASUS y hasta que no lo pongo y copia los settings de allí, no puedo entrar en el SO. Debido a ésto le puse el default que hace arrancar con el HDD. Pero debo arreglar ésto urgente, comprenderás por que.

Esto es muy raro. Podés darnos más información de esto? Qué texto aparece pidiendo el CD de Asus?

---

### Post by hectorivand on 2012-01-28
En el arranque, aprentando F8, F9, F11 o F12, (alguno de ellos) te abre un menú para que elijas desde que dispositivo queres bootear. 

Si tu bios esta jodida y no te guarda los cambios, ese puede un buen Workaround hasta que puedas actualizar la Bios.

Saludos
Nacho

---

### Post by Vero1 on 2012-01-28
Hola nacho,
Yo entro al BIOS con la tecla Supr sin problemas.
Mi problema es lo que comenté en mi post.

Gracias por tu tiempo.

saludos

---

### Post by Vero1 on 2012-01-28
Hola alfplayer,

Lo que me sale en pantalla es:

Bad BIOS checksum
Starting BIOS recovery
Checking for CD-ROM

Entonces yo inserto el CD de Asus y lo reconoce, comenzando primero por Erasing y despues Configuring.
Cuando termina pide que apague la computadora y lo vuelva a encender para recuperar el SO.

En el mismo BIOS hay en Tools una herramienta que aparentemente actualiza la BIOS pero que no me he atrevido a usar.

gracias y espero tengas algun comentario sobre todo ésto.

saludos

---

### Post by hectorivand on 2012-01-28
> **Vero1 said:**
> Hola nacho,
Yo entro al BIOS con la tecla Supr sin problemas.
Mi problema es lo que comenté en mi post.

Gracias por tu tiempo.

saludos

No Vero, no estoy diciendo que entres al Bios, que entres al menú de booteo desde el cual vas a poder seleccionar desde donde queres bootear, usb, disco, óptico, etc.

Investigando un poco te confirmo que con F8 cuando enciendes el equipo te va a salir un menú de booteo.

Saludos
Nacho

---

### Post by alfplayer on 2012-01-28
Esto se había discutido... [http://ubuntuforums.org/showthread.php?t=1777271]("http://ubuntuforums.org/showthread.php?t=1777271").

Mirá mi último comentario.

---

### Post by Vero1 on 2012-01-28
Alfplayer, leí lo que me comentas y sí le puse Load Default pero en lugar de poner como default CD/DVD pone mi primer disco HDD y ahí empieza el problema que comento.

Para mi todo se debe al Bad Cheksum del BIOS.

Ahora veré lo que me comenta nacho y volveré.

---

### Post by alfplayer on 2012-01-28
Me refería a este comentario: [http://ubuntuforums.org/showpost.php?p=10932373&postcount=12]("http://ubuntuforums.org/showpost.php?p=10932373&postcount=12")

Es probable que la pila esté vieja, y haya que cambiarla.

---

### Post by Vero1 on 2012-01-28
Alfplayer,

La pila no es vieja, es del año pasado y se la puse yo nueva.

---

### Post by Vero1 on 2012-01-28
nacho,

he probado F8 y le marqué, como primer arranque CD/DVD.
Lo que pasó fue que al reiniciar, me salió otra vez la bendita leyenda de pedir el CD de Asus...

Vuelvo a preguntar: hay alguna forma de "guardar" los datos de la BIOS por si me falla la herramienta de actualización?

---

### Post by alfplayer on 2012-01-28
> **Vero1 said:**
> Alfplayer,

La pila no es vieja, es del año pasado y se la puse yo nueva.

OK, supongo que la que pusiste nueva fue después que te dieron el nuevo motherboard.

Si no es el la pila sería un problema más serio.

---

### Post by Vero1 on 2012-01-28
alfplayer,

Sabes si hay alguna forma de hacer un resguardo de los datos de la BIOS?

Porque voy a tener que usar la herramienta que viene en la BIOS para hacer una actualización porque así no puedo seguir, como te imaginarás.

Otra cosa.
Teniendo en cuenta todos los problemas que tengo con la secuencia de arranque, hice un booteable en un Pendrive, de Ubuntu.
Ahora bien, En la BIOS no figura nada en USB o sea que el Pendrive no se reconoce.
Quise bootear con él pero no pasa nada.
Tenés idea de cómo hay que configurar BIOS para que reconozca el Pen?

Disculpa tanta cosa pero ya me salen canas verdes con todo ésto :(

---

### Post by biale on 2012-01-28
Normalmente la misma herramienta que se usa para cambiar el BIOS sirve para hacer un backup del mismo sin actualizarlo. Deja un archivo en alguna unidad Fat, por ejemplo un pendrive. 

Con respecto al Pendrive, sería bueno probarlo en otra máquina por si no hubiera quedado OK.

Observo que los problemas "arrancan" con la unidad de CD/DVD. No es imposible que la unidad este comenzando a fallar y lo demuestre de esa manera. Sería el punto mas debil de la cadena...

---

### Post by alfplayer on 2012-01-28
Los pendrives aparecen muchas veces como discos rígidos (HDD). Podés probar eso.

No creo que tengas guardada una configuración importante en el BIOS. Si hiciste "Load setup defaults" igual ya lo volviste a cero. Yo diría que no te ocupes de eso. No es importante.

Además, actualizar no garantiza que se arregle el problema. Es más, yo no creo que lo arregle. Si no es la pila hay una falla en el motherboard en mi opinión.

---

### Post by Vero1 on 2012-01-29
biale,

Los discos rígidos que aparecen en BIOS son los que tengo(2) y nada mas.

En cuanto al Pen funciona correctamente, ya está probado.

Debe ser que mi BIOS o Mother no soportan los Pen para bootear, aunque sí para grabar y leer. Así que no entiendo.

En cuanto a las unidades de CD y CD/DVD(tengo 2) funcionan correctamente.

En fin, agradezco tu buena voluntad.

Saludos

---

### Post by Vero1 on 2012-01-29
alfplayer,

Lo de los discos HDD se lo contesté a biale :D (es que ya estoy re-mareada con todo ésto)

Lo que decís con respecto a la posible falla en el mother, lo que pasa, no pasa desde el principio. En un principio todo estaba ok. Como la mother está fuera de garantía, no me haría gracia ir al técnico...

Bueno, creo que voy a probar actualizar de todas maneras, ya que la BIOS es del año 2008 si no me equivoco, así que ya tiene sus añitos no?

Agradezco tu voluntad de ayudar.

Si se llega a arreglar con la actualización(que no sé todavía cuando voy a atreverme a hacerla) volveré.

saludos

---

### Post by EnriqueK on 2012-01-29
Lo que te quieren decir es que al momento del booteo en vez de pulsar  la tecla para entrar al setup del bios, pulsa otra, parece ser la F8  de esa manera entras a un selector temporal de dispositivos de arranque como son los pendrives y seguramente los lectores de CD/DVD, para hacer esto debes tener colocados ya sea el pendrive o  el LiveCD. En mi caso por ejemplo que tengo una Mobo Asrock debo pulsar F12 , única forma que tengo para poder arrancar desde  un USB ya que en el selector normal situado en el setup del BIOS, no tengo esta opción.
Antes de flasher el BIOS sugiero intentar con
1.- Cambiar la pila
2. Para descartar que sea problemas de la unidad óptica, prueba en arrancar desde un Live CD pero con el HDD desconectado
3.- No vendría mal una buena limpieza de conectores con alcohol.

---

### Post by biale on 2012-01-29
> En cuanto al Pen funciona correctamente, ya está probado.

Intente decir "puede bootear correctamente"

> Debe ser que mi BIOS o Mother no soportan los Pen para bootear

De acuerdo con que no todas la Moth ni todos los Pendrives sirven para bootear. Una mother Intel mañosa en ese sentido que recuerdo es del año 2003. Con mothers (de marca) del 2008/9 para adelante en principio sin problemas. Y no todos los pendrives son iguales.

Estoy de acuerdo con Enriquek y agregaría que antes de flashear hay que estudiar bien no solo el proceso en si sino tambien que es lo que las nuevas versiones de BIOS arreglan o mejoran.

---

### Post by alfplayer on 2012-01-29
> **Vero1 said:**
> Debe ser que mi BIOS o Mother no soportan los Pen para bootear
Me parece muy improbable.

> **Vero1 said:**
> Lo que decís con respecto a la posible falla en el mother, lo que pasa, no pasa desde el principio. En un principio todo estaba ok. Como la mother está fuera de garantía, no me haría gracia ir al técnico...
Pero si es como creo, por un mensaje del otro hilo, esto empezó poco después de cambiar el motherboard (es el mismo problema de bad checksum), y el problema siempre estuvo después de esa vez (o no?), por lo que el problema sería responsablidad del técnico. Si es así sigo diciendo que me parece buena idea que ese técnico se haga cargo. Aunque el tiempo de la garantía de la reparación haya pasado, el problema empezó poco después de la reparación, por lo que tal vez te tome el motherboard igual.

> **Vero1 said:**
> Agradezco tu voluntad de ayudar.
De nada.

---

### Post by Vero1 on 2012-01-29
En realidad no fue una reparación sino el cambio de mother.
La anterior se había quemado, por lo que hubo que cambiar por una nueva.

En fin, agotaré todas las instancias y si no hay mas remedio acudiré al técnico, aunque ya veo que dado el tiempo transcurrido, no se va a hacer cargo de nada.

Gracias alfplayer.

---

### Post by Vero1 on 2012-01-29
EnriqueK,

Trataré de hacer lo que me decís y gracias.

---

### Post by Vero1 on 2012-01-29
Hola biale,

Si, he leído que no todas las BIOS y Mothers reconocen las Pendrives.

Si bien mi BIOS es Asus, no es nueva y no tiene la opción del Pen.

En fin. Veré al final qué hago.

Gracias.

---

### Post by alfplayer on 2012-01-29
Lo de probar con otra pila me parece buena idea también. Si el problema siguió puede pasar que la pila nueva estaba fallada o descargada como la vieja.

---

### Post by Vero1 on 2012-01-29
alfplayer,

ok, probaré con una nueva y les cuento.

saludos

---

### Post by Vero1 on 2012-02-04
Hola,

Nada pasó. Sigo como antes.

saludos

---

### Post by alfplayer on 2012-02-04
Con la batería nueva hacé "Load Setup Defaults" de nuevo. Si sigue sin funcionar otra cosa fácil para probar no se me ocurre.

---

### Post by alfplayer on 2012-02-04
Leí que puede ser por un problema de energía. Si usas placa de video podés decir cuál es y qué fuente tiene la PC.

---

### Post by Vero1 on 2012-02-04
Hola alfplayer,

Probé con batería nueva y como si nada.

Por otro lado un amigo me comentó que convendría hacer una actualización de la BIOS porque aparentemente no es prolema de configuración sino que falla directamente el programa de BIOS.

Así que estoy viendo la página de ASUS por la actualización.

Gracias por tus aportes.

saludos

---

### Post by EnriqueK on 2012-02-04
En el manual de la Mobo que has descargado con el enlace que te puse anteriormente, debe estar explicada la forma de actualizar la bios, no busqu&#7811;s otro lugar diferente ya que es un proceso  delicado .

---

### Post by Vero1 on 2012-02-05
Hola EnriqueK,

No, no busco otras fuentes.
Voy a hacer lo que dice el manual.

Gracias

---

### Post by Vero1 on 2012-02-20
Hola a todos,

Por fin ayer pude actualizar BIOS, con la opción del mismo AsusUpdate,(que está en Windows) pero no por Internet(que no me funcionó) sino con un archivo que bajé previamente de Asus, correspondiente a mi Mother.
Lo hizo todo muy rápido así que ahora ya puedo cambiar la secuencia de arranque, como quería y me lo respeta.

Gracias a todos los que intentaron ayudarme.

saludos

---

### Post by EnriqueK on 2012-02-20
No se, capaz que digo cualquier cosa, pero por lo que leí en  tu fdisk -i, el disco sda es de 40 Gb, ese disco debe rondar por los 10 años, debería estar tocando el arpa, o sea no sería nada raro de que sea el causante de tus problemas. probá con abrir el equipo, desconectá a ese HDD y arrancás usando el Supr Grub2 Disk, es muy posible que de esa manera puedas arrancar Ubuntu ya que lo tienes en el otro disco.
Si lo anterior funciona, cabiá ek HDD sda.

---

### Post by Vero1 on 2012-02-21
Hola EnriqueK,
Mirá, el disco de 40Gb contiene Windows y el Grub. No funciona al 100% pero me saca de apuros, como en esta ocasión que justamente estoy en Windows porque el otro disco de 80Gb donde está Ubuntu, no me permite ingresar porque informa OUT OF DISK.
Justamente, tuve que usar el SGD para que me salga el Grub y así poder entrar en Windows y pedir socorro, porque no sé como arreglar el Out of disk que me indica.
Lo raro es que dice hda1(que es este disco de donde estoy escribiendo), salvo que out of disk se refiera al Grub.
Así que enviar este disco para que toque el arpa me parece injusto:D

saludos

---

### Post by EnriqueK on 2012-02-21
Para salir de dudadas de que el DD de 40 cause el problema es que te sugerí que abras el equipo , desconecnectes el dd y trata de arrancar con el SG2D el de 80 Gb donde está Ubuntu.
Si lo anterior no va, prueba con arrancar con el Live Cd, habilitas los repositorios. y luego instala siempre en la sesión Live Cd el paquete "testdisk", luego lo ejecutas mediante sudo testdisk. pero antes de todo esto,investiga en la red sobre el uso de este programa ya que es muy poderoso y un mal manejo puede ser fatal, yo lo usé una vez y me arregló mi tabla de particiones en dos segundos.

---

### Post by Vero1 on 2012-02-21
Bueno, ya no sé qué pensar. Estoy otra vez en Ubuntu.Me salió el Grub ahora.El sistema lo veo muy inestable. Necesitaria una herramienta que revisara TODO y determinara donde está la falla. Pienso que no es el disco de 40 ya que utilizo Windows sin problemas. En fin. Seguiré indagando.

gracias

---

