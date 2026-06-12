---
title: "fallo instalación kubuntu 8.10 - al llegar al 80% aprox. se apaga la pc"
date: 2009-05-01
forum: Hardware
---

### Post by anagramagia on 2009-05-01
No consigo terminar de instalar kubuntu 8.10 32bits porque al llegar a la parte de configuración de la hora, habiendo pasado aproximadamente el 80% del proceso de instalación, de golpe la computadora se apaga. Tres veces lo intenté y las tres veces con el mismo resultado. La última vez tuve la precaución de ver si antes del apagado aparecía algún mensaje en la consola y puse ctrl+alt+f1 un poco antes de llegar al punto antes mencionado. Y sí algo apareció, lástima que como la máquina se apaga inmediatamente lo que puedo comentar son algunas palabras sueltas que pude retener de un vistazo, decía algo similar a: wrong magic number, can't read superblock sda8, y algo que parecía estar mal con squashfs.
El disco está particionado así: sda1 (ntfs), sda2 (ntfs), sda5(swap), sda6 (ext3, ubuntu 8.04, root), sda7 (ext3, ubuntu 8.04, home), sda8 (ext3 ubuntu 8.04, usr) y la partición sda9 (ext3) que es donde quise ubicar kubuntu 8.10.
El cd de instalación lo obtuve en el flisol2009 y creo que no tiene problemas ya que en una máquina virtual sí logré instalarlo, y también porque desde ubuntu puse md5sum -c /media/cdrom/md5sum.txt y no saltó ningún error. Pero de todos modos antes de hacer eso había intentado verificar el cd desde el menú de la primer pantalla del live cd y ni bien le doy enter a la opción ¡¡se apaga la máquina!! No sé qué pasa.:confused:
Por favor, ¿me pueden ayudar a desentrañar este asunto?, me encantaría poder instalar kubuntu ya que me gustó mucho el escritorio KDE 4, y no tengo conexión a internet como para hacerlo de otra manera. Además, también en el flisol un chico muy amable me copió en un pendrive una iso de linuxmint 6 kde la cual pude probar en la máquina virtual y también tenía ganas de instalar pero vaya mi sorpresa cuando al hacerle la verificación de md5sum había errores, así que sigo con las ganas de kde 4.
Sobre lo de la falta de coincidencia en las sumas de control, ¿cuál puede ser el problema? ¿por qué si algo está mal, de todos modos el live dvd funciona? y ¿por qué si el live dvd se puede usar no se puede instalar?
Saludos...

---

### Post by pablo.s on 2009-05-01
Podés probar a formatear las
particiones en ReiserFS, antes
de instalar.

---

### Post by anagramagia on 2009-05-01
¿Por qué te parece que debo formatear las particiones en ReiserFS? ¿No debería funcionar con ext3? Además yo no quiero formatear las otras particiones, sólo la sda9 donde iría kubuntu.

---

### Post by pablo.s on 2009-05-01
> **anagramagia said:**
> ¿Por qué te parece que debo formatear las particiones en ReiserFS? 

Porque es un buen sistema journaling.
Yo lo uso hace mucho años ya. Para mi
Ext3/Ext4 ya casi ni son una opción.


> **anagramagia said:**
> ¿No debería funcionar con ext3? 

Si, es cierto, deberia funcionar, pero
no te está funcionando, cierto?
Mi sugerencia es esa.


> **anagramagia said:**
> Además yo no quiero formatear las otras particiones, sólo la sda9 donde iría kubuntu.

El error de la instalación te lo dá en
sda8, según veo. Vos decis que algo
parece estar mal con squashfs.
Squashfs es el sistema que usan las
distribuciones LiveCD para comprimir
el contenido que se va a instalar pero
a su vez habilitando que se pueda
descomprimir "al vuelo" cuando uno
necesita utilizar un programa durante
la sesión Live.
OK, vos ponés que sda8 es /usr, por lo
tanto te dice clarisimo que al instalar
los programas (supongo que a /usr/bin)
tiene un error de disco.
sda9 lo vas a usar como /home.

Pensalo, y fijate si no es mas sencillo.

---

### Post by josecuervo86 on 2009-05-01
OT: me acuerdo cuando instale linux por primera vez, por total descocnocimiento, lo instale en reiserFS. Quien hubiera dicho que el creador es un asesino :P

---

### Post by pablo.s on 2009-05-01
Cierto, pero seguro que con
cadena perpetua va a tener
suficiente tiempo como para
poder trabajar en una nueva 
versión de ReiserFS.

---

### Post by josecuervo86 on 2009-05-01
Al parecer va a vender la empresa para poder pagar el abogado que lo defiende :D

---

### Post by Hei Ku on 2009-05-02
Pablo y Jose, por favor mantengase en tema. [-o<

---

### Post by anagramagia on 2009-05-02
Pablo.S > El error de la instalación te lo dá en
sda8, según veo. Vos decis que algo
parece estar mal con squashfs.
Squashfs es el sistema que usan las
distribuciones LiveCD para comprimir
el contenido que se va a instalar pero
a su vez habilitando que se pueda
descomprimir "al vuelo" cuando uno
necesita utilizar un programa durante
la sesión Live.
OK, vos ponés que sda8 es /usr, por lo
tanto te dice clarisimo que al instalar
los programas (supongo que a /usr/bin)
tiene un error de disco.
sda9 lo vas a usar como /home.

¿qué puedo hacer para saber qué tipo de error puede tener la partición sda8?

Aclaro que cuando intento instalar kubuntu, en el particionado manual sólo elijo sda9 para que allí se ubique todo kubuntu, incluido /home. Las particiones sda6, sda7 y sda8 corresponden a mi instalación de ubuntu 8.04 que funciona ok. Por eso no entiendo bien por qué aparece ese mensaje sobre sda8.

---

### Post by pablo.s on 2009-05-02
Y bien bien te lo puede decir la
instalación Alternate, que los 
mensajes de error los muestra.

Vos en definitiva querés tener en
paralelo dos Kubuntu?

EDIT: Para saber que error tiene
sda8, podés correr el programa
fsck -a.

---

### Post by juanman on 2009-05-04
> **anagramagia said:**
> Además, también en el flisol un chico muy amable me copió en un pendrive una iso de linuxmint 6 kde

Seré muy amable, pero parece q poco efectivo :P
Es muy raro lo q te pasa. Los errores de squashfs generalmente indican q la imagen del cd es errónea (o la lectora lo lee mal); pero en este caso, parece q el cd está bien (nunca está de más limpiar el cd)...
Para el tema de sda8, probá pasándole un sudo fsck /dev/sda8
Y por las dudas, desmonta la partición antes de instalar (sudo umount /dev/sda8 )
Si te cansás de intentar con ese cd, habría q probar con otro (no sigas sufriendo con gnome! :P). Yo ahora tengo el kubuntu 9.04 de 64b en cd q andabas buscando en flisol (no pude conseguir el dvd aún). Si querés te hago una copia y lo pasás a buscar cuando vengas a capital... El sábado 16 de mayo, de 15 a 18hs, se va a hacer un "Bazaar de Soluciones"
en FM La Tribu; si vas, te lo puedo dar ahí. Y si no avisame por MP cuando vengas y coordinamos, que todavía te debo un cd con kde4 q ande...

Otro tema, te había comentado una página para descargar paquetes con sus dependencias, sin la necesidad de armar un script de descarga... La dirección es [http://webuspc.appspot.com/](http://webuspc.appspot.com/)
También hay una versión más actualizada y con más opciones, pero hay q instalar el programa en la pc [http://code.google.com/p/uspc/](http://code.google.com/p/uspc/)

> **anagramagia said:**
> 
Sobre lo de la falta de coincidencia en las sumas de control, ¿cuál puede ser el problema? ¿por qué si algo está mal, de todos modos el live dvd funciona? y ¿por qué si el live dvd se puede usar no se puede instalar?
Saludos...

La suma de control va a fallar si el archivo defectuoso es, por ej, un icono o documentación (en ese caso, el live cd se podrá usar y tal vez instalar) o si es el kernel (en este caso, el cd ni va a bootear). Por eso, dependiendo cuál o cuáles sean los archivos defectuosos, el live puede funcionar pero no instalarse o instalarse en algunas máquinas y fallar en otras (es raro pero me ha pasado: puede q el archivo defectuoso sea un driver q sólo se usa en determinada máquina)...

Saludos

---

### Post by anagramagia on 2009-05-04
¡Hola Juanman!
Finalmente usé la opción instalar kubuntu con wubi y no hubo fallos, pero debido a que no tengo internet se hace muy cuesta arriba ir consiguiendo los paquetes que voy necesitando o queriendo probar, así que por el momento sigo con Ubuntu 8.04 y Gnome.
Me había gustado Mint ya que venía con bastante soft extra. 

Hice el chequeo de sda8 y no salió ningún error.

Y saliendo del tema ubuntu pero siguiendo con la pc que se apaga, me pasa algo así en win ¡cuando entro en "modo seguro"!, todavía no encontré el motivo, estoy investigándolo en google.

> Yo ahora tengo el kubuntu 9.04 de 64b en cd q andabas buscando en flisol (no pude conseguir el dvd aún). Si querés te hago una copia y lo pasás a buscar cuando vengas a capital... El sábado 16 de mayo, de 15 a 18hs, se va a hacer un "Bazaar de Soluciones"
en FM La Tribu; si vas, te lo puedo dar ahí. Y si no avisame por MP cuando vengas y coordinamos, que todavía te debo un cd con kde4 q ande...
Estaría buenísimo. Puede ser que me de una vuelta el 16/5 por el Bazaar de soluciones. Te confirmo más sobre la fecha.

> Otro tema, te había comentado una página para descargar paquetes con sus dependencias, sin la necesidad de armar un script de descarga... La dirección es [http://webuspc.appspot.com/](http://webuspc.appspot.com/)
También hay una versión más actualizada y con más opciones, pero hay q instalar el programa en la pc [http://code.google.com/p/uspc/](http://code.google.com/p/uspc/)

No tenía idea, le voy a dar un vistazo, gracias.
Saludos.

---

### Post by anagramagia on 2009-05-14
Quizá sea algo de hardware, llamé al servicio técnico y me dijeron que podía ser o la fuente o la memoria... Hoy les llevé la pc y mañana veré qué pasa.

---

### Post by anagramagia on 2009-05-15
Había un problema con la fuente y hubo que cambiarla. Aún no volví a probar la instalación de kubuntu 8.10, en cuanto pueda hacerlo comento el resultado, que espero sea positivo.
Saludos.

---

### Post by anagramagia on 2009-05-16
¡Ya instalé Kubuntu 8.10! Era la fuente nomás.
Saludos.

---

