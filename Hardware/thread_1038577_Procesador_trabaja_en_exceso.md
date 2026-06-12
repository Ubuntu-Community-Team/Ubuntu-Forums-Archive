---
title: "Procesador trabaja en exceso"
date: 2009-01-12
forum: Hardware
---

### Post by Applelnx on 2009-01-12
Tengo el siguiente problema, cuando abro cualquier programa, por mas liviano que sea el trabajo del procesador se me dispara. Cuando reproduzco un dvd con vlc lo tengo al 60% y la imagen queda "freezada" por decirlo de alguna manera. Nunca me habia pasado y menos con el VLC. Incluso cuando abro el monitor del sistema el procesador empieza a funcionar abruptamente. La verdad que de computadoras no soy experto, asi que puede ser alguna idiotez mia que no me de cuenta. Si alguien me puede ayudar le agradezco. Saludos.

PD: dejo screens por si sirven de algo.

[[IMG]http://img211.imageshack.us/img211/3569/monitorij8.th.png[/IMG]](http://img211.imageshack.us/my.php?image=monitorij8.png)

[[IMG]http://img211.imageshack.us/img211/6798/procesos2rq3.th.png[/IMG]](http://img211.imageshack.us/my.php?image=procesos2rq3.png)

---

### Post by guillermolisi on 2009-01-13
> **Applelnx said:**
> Tengo el siguiente problema, cuando abro cualquier programa, por mas liviano que sea el trabajo del procesador se me dispara. Cuando reproduzco un dvd con vlc lo tengo al 60% y la imagen queda "freezada" por decirlo de alguna manera. Nunca me habia pasado y menos con el VLC. Incluso cuando abro el monitor del sistema el procesador empieza a funcionar abruptamente. La verdad que de computadoras no soy experto, asi que puede ser alguna idiotez mia que no me de cuenta. Si alguien me puede ayudar le agradezco. Saludos.

PD: dejo screens por si sirven de algo.

[[IMG]http://img211.imageshack.us/img211/3569/monitorij8.th.png[/IMG]]("http://img211.imageshack.us/my.php?image=monitorij8.png")

[[IMG]http://img211.imageshack.us/img211/6798/procesos2rq3.th.png[/IMG]]("http://img211.imageshack.us/my.php?image=procesos2rq3.png")
El ultimo grafico denota una alta carga del sistema, por encima de 1, que no se refleja en la lista de procesos (tal vez por la forma en que esta ordenada que oculta alguno que consume muchos recursos como CPU y/o disco y que componen los factores de carga del sistema).

Que procesador tenes ?

Version de Ubuntu ?

Esta actualizada con los ultimos parches ?

Que placa o placas de red estas usando (marca/modelo) ?

La primer tarea de la segunda pantalla consume mucha memoria RAM, que hace/que es ?

No se esta usando el swapfile asi que no es problema de poca RAM.

Hau cierta actividad de red, las placas de red son muy standard o poseen algun chipset con inteligencia como para descargar el trabajo de la CPU (las mas berretas son mas parecidas a un cable que a una interface. Le pasan todo el laburo a la CPU de la administracion de trafico de paquetes de red).

---

### Post by Applelnx on 2009-01-14
Procesador: Pentium4 524 (P) HT 3.06 GH

Version Ubuntu: 8.10

Todo actualizado

Placa de red: es una integrada, tengo una HP Pavilion, aca estan las especificaciones del producto [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00605009&lc=es&dlc=es&cc=ar&product=1840779&lang=es](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00605009&lc=es&dlc=es&cc=ar&product=1840779&lang=es)
Dice: Interfaz de red 10/100 Base-T integrada

La primer tarea de la segunda pantalla es el AMSN.

Y en cuanto a lo de la placa de red, no se, la verdad por ahora nunca me habia pasado que se freezara el vlc reproduciendo un dvd. El vlc es uno de los programas mas livianos y con menos requerimientos dentro de los reproductores.

---

### Post by guillermolisi on 2009-01-14
> **Applelnx said:**
> Procesador: Pentium4 524 (P) HT 3.06 GH

Version Ubuntu: 8.10

Todo actualizado

Placa de red: es una integrada, tengo una HP Pavilion, aca estan las especificaciones del producto [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00605009&lc=es&dlc=es&cc=ar&product=1840779&lang=es](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00605009&lc=es&dlc=es&cc=ar&product=1840779&lang=es)
Dice: Interfaz de red 10/100 Base-T integrada

La primer tarea de la segunda pantalla es el AMSN.

Y en cuanto a lo de la placa de red, no se, la verdad por ahora nunca me habia pasado que se freezara el vlc reproduciendo un dvd. El vlc es uno de los programas mas livianos y con menos requerimientos dentro de los reproductores.
Bueno, en general las placas de red integradas no son las mejores pero tampoco son tan malas como para producir el efecto que mencionas.

Pregunto algo que por obvio se me paso por alto. Cuando usaste el VLC que termino freezado, estabas reproducioendo un CD/DVD o un archivo en dico rigido ?

Si era un CD/DVD, podria ser que estuviera sucio, rayado o simplemente en esa unidad no se pueda leer bien y termina haciendo caer al VLC y este a la PC por exceso de consumo de CPU.

Probaste con otro disco a ver si volvia a pasar lo mismo ?

---

### Post by Applelnx on 2009-01-14
Bueno, reproduciendo un archivo desde el rigido no pasa eso. Solo con el DVD. Probe con otro para verificar y pasa lo mismo. Puede ser la compactera? :s

Pero tambien cuando se reproduce en la ventana pequeña se ve mucho mejor que cuando pongo pantalla completa, eso puede ser por el video? Es raro porque no me habia pasado nunca con el vlc.

Edit 2 minutos despues: sacandole todos los efectos visuales se ve perfecto, no se por que me consume tanto cuando pongo efectos medios.

---

### Post by guillermolisi on 2009-01-15
> **Applelnx said:**
> Bueno, reproduciendo un archivo desde el rigido no pasa eso. Solo con el DVD. Probe con otro para verificar y pasa lo mismo. Puede ser la compactera? :s

Pero tambien cuando se reproduce en la ventana pequeña se ve mucho mejor que cuando pongo pantalla completa, eso puede ser por el video? Es raro porque no me habia pasado nunca con el vlc.

Edit 2 minutos despues: sacandole todos los efectos visuales se ve perfecto, no se por que me consume tanto cuando pongo efectos medios.
Ahi ya cuenta la placa de video y sus drivers.

Si la unidad de CD/DVD esta muy usada y/o sucia es posible que tenga problemas de lectura y/o esta llegando al final de su ciclo de vida util.

Convengamos que una imagen con resolucion fija cuando la agrandas mucho se vera necesariamente pixelada a menos que el soporte grafico que estes usando se la banque decentemente.

---

