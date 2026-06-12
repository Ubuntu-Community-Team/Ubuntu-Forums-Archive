---
title: "Problema con monitor sin señal"
date: 2010-05-07
forum: Hardware
---

### Post by santiago79 on 2010-05-07
Hola gente tengo un problema que no se por donde entrarle
la cosa es asi.
yo estaba usando ubuntu 9.10 bien hasta que mi disco murió y bue como quedaban pocos dias para que salga ubuntu 10 me decidi por probar otras distros, bueno arranque con debian leny y todo bien
quise instalar Fedora y en el momento que quería arrancar el live cd se queda sin señal el monitor bueno volví a Ubuntu hasta que salga la 10
cuando voy a instalar Ubuntu desde el menú del live cd pongo instalar y se queda sin señal el monitor y si quiero entrar al live cd también pasa lo mismo, yo en el laburo probe fedora con un monitor mas viejo que el mio y funciona bien, ahora estoy con un LCD de 19 blument y funciona
pero el lcd no es mio,
MI MONITOR ES UN SAMSUNG DE 17 PULGADAS Y FUNCIONA CORRECTAMENTE. LA PLACA DE VIDEO ES UNA NVIDIA FX 5200.
yo creo que debe ser algo en el kernel o no se.
alguien tiene una idea????

---

### Post by guillermolisi on 2010-05-07
Modelo del Samsung ?

Tampoco te permite ver las consolas (Ctrl+Alt+F1 por ejemplo) ?

---

### Post by santiago79 on 2010-05-07
> **guillermolisi said:**
> Modelo del Samsung ?

Tampoco te permite ver las consolas (Ctrl+Alt+F1 por ejemplo) ?

mira el modeo te lo debo estoy en el laburo y no lo tengo enfrente en unas horas llego a casa y te lo confirmo
y respondo tu pregunta no puedo  hacer nada
directamente cuando pongo instalar o probar carga un toque y se pone la pantalla en negro y una imagen que con esto HZ? (como cuando desconectas el cable pero en vez del dibujo del cable la HZ? )
es raro que esta versión no soporte mi monitor

---

### Post by santiago79 on 2010-05-08
Perdón por tardar el modelo es SYNCMASTER 793s
ahora esta en una pc que usa windows XP y funciona muy bien, vi que ayer me salto una actualización del Kernel voy a ver si con eso se soluciona

---

### Post by anarko on 2010-05-10
Es probable que este mandándole una frecuencia que el monitor no soporta. A eso se debe referir con el HZ ( Hertz ). O una resolución que no soporta el monitor. Hasta donde me acuerdo había una opción para levantar el live CD en 800x600@60Hz para este tipo de problemas.
Es por eso que con otros monitores si funciona y con el samsung no. Eso va en la configuración del Xorg.

Saludos.

---

### Post by Kalil94 on 2010-05-10
Hola, a mi me paso exactamente lo mismo... Nunca use Ubuntu, pedi el CD, y cuando me lo trajeron decidi probarlo y me parecio muy bueno, por lo tanto decidi cambiar a Windows XP e instalarlo desde hay, la instalacion todo perfecto, pero cuando reinicie y eleji Ubuntu me aparece lo mismo, que no hay señal y un mensaje que dice: "PC config display correct?" o algo asi :?
¿Hay alguna forma de cambiar la resolucion de Ubuntu desde Windows? En este momento estoy usando Windows XP...
Saludos ;)
PD: Si es desvirtuar el tema o algo diganme que lo borro, soy nuevo..

---

### Post by guillermolisi on 2010-05-10
> **Kalil94 said:**
> 
¿Hay alguna forma de cambiar la resolucion de Ubuntu desde Windows? En este momento estoy usando Windows XP...
Saludos ;)
PD: Si es desvirtuar el tema o algo diganme que lo borro, soy nuevo..
:D por suerte no, desde Win no podes configurar el video de Linux.

---

### Post by guillermolisi on 2010-05-10
> **santiago79 said:**
> Perdón por tardar el modelo es SYNCMASTER 793s
ahora esta en una pc que usa windows XP y funciona muy bien, vi que ayer me salto una actualización del Kernel voy a ver si con eso se soluciona
Y ? Se soluciono ?

Un paso que se puede intentar antes de comenzar a meter mano en archivos y otras yerbas es correr en consola/terminal lo siguiente ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Kalil94 on 2010-05-11
> **guillermolisi said:**
> :D por suerte no, desde Win no podes configurar el video de Linux.

Que mala suerte, en verdad quería tener Ubuntu :( 
Lo peor de todo es que no entiendo nada, cuando dice "Sin señal" apretó ctrl + alt + F1, me logeo pero de hay no se que poner.. intente unas cosas que encontré en la web que dice "root" creo que era pero dice algo como que hay que instalarlo o algo así, no entiendo nada :?
Bueno, creo que tal vez Ubuntu no es para mi :cry:

---

### Post by anarko on 2010-05-11
Cuando entras con ALT+F1 y te logueas hace o que dice guillermo
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

PD: Lamento contradecirte pero si se puede conf. el video de linux desde windows, con un ext3/4 rw, yo los use, no son seguros y no siempre andan pero ... poder es intentar.
Y hay que saber configurar el xorg.conf.

---

### Post by Kalil94 on 2010-05-11
> **anarko said:**
> Cuando entras con ALT+F1 y te logueas hace o que dice guillermo
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

PD: Lamento contradecirte pero si se puede conf. el video de linux desde windows, con un ext3/4 rw, yo los use, no son seguros y no siempre andan pero ... poder es intentar.
Y hay que saber configurar el xorg.conf.

Ok.. lo voy a intentar, la configuración del xorg.confg la tengo, espero que funcione y no me pida nada raro, yo solo quería instalar Ubuntu y usarlo, me gusto mucho :)

---

### Post by guillermolisi on 2010-05-11
> **anarko said:**
> Cuando entras con ALT+F1 y te logueas hace o que dice guillermo
```
sudo dpkg-reconfigure -phigh xserver-xorg
```PD: Lamento contradecirte pero si se puede conf. el video de linux desde windows, con un ext3/4 rw, yo los use, no son seguros y no siempre andan pero ... poder es intentar.
Y hay que saber configurar el xorg.conf.
Ok. siempre se aprende algo nuevo solo que esta alternativa me parece solo recomendable a usuarios con conocimientos promedio o avanzados. Delicada la cosa si se la encara asi.

---

### Post by anarko on 2010-05-11
Kalil fijate que cuando hagas el dpkg-reconfigure del Xorg te va a pedir la frecuencia horizontal y vertical del monitor eso ES LO MAS IMPORTANTE lo demas no es tan importante.Tenes que buscar los datos en el fabricante del monitor.

PD: Guillermo, 10 años arriba del pinguino no me vienen solos, ademas de ser un complicado como me dicen mis amigos y compañeros de laburo que siempre tengo una solucion al problema, pero siempre es la mas complicada. Si no es complicado no es divertido ;)

---

### Post by alfplayer on 2010-05-11
anarko: Se puede escribir en ext4 ? Por lo información que encuentro no se puede si ext4 tiene *extents*, que es lo predeterminado.

---

### Post by anarko on 2010-05-11
Porsupuesto que se puede escribir en ext4 ... sino como hace mi ubuntu? Y como el codigo fuente del ext4 es abierto nada me impide pensar que salgan aplicaciones para otros SO que puedan hacerlo.
Pero creo que estamos desvirtuando el tema origina no?

---

### Post by alfplayer on 2010-05-11
> **anarko said:**
> Porsupuesto que se puede escribir en ext4 ... sino como hace mi ubuntu? Y como el codigo fuente del ext4 es abierto nada me impide pensar que salgan aplicaciones para otros SO que puedan hacerlo.
Pero creo que estamos desvirtuando el tema origina no?

Hay una confusión. Me refería a la escritura de ext4 (con extents) desde windows:

> **anarko said:**
> PD: Lamento contradecirte pero si se puede conf. el video de linux desde windows, con un ext3/4 rw, yo los use, no son seguros y no siempre andan pero ... poder es intentar.
Y hay que saber configurar el xorg.conf.

---

### Post by Kalil94 on 2010-05-11
> **anarko said:**
> Kalil fijate que cuando hagas el dpkg-reconfigure del Xorg te va a pedir la frecuencia horizontal y vertical del monitor eso ES LO MAS IMPORTANTE lo demas no es tan importante.Tenes que buscar los datos en el fabricante del monitor.

PD: Guillermo, 10 años arriba del pinguino no me vienen solos, ademas de ser un complicado como me dicen mis amigos y compañeros de laburo que siempre tengo una solucion al problema, pero siempre es la mas complicada. Si no es complicado no es divertido ;)

Ok, pero no sirvió, me apareció como que era algo invalido, o más bien como que no existía o le estaba dando un mal uso, ¿Hay alguna otra manera? :?
PD: ¿Eso se ponia despues de logearme, en la consola verdad? Osea apretando ctrl + alt + F1.... ¿Tienes 10 años con Linux? Yo no tengo ni 1 dia, por eso no entiendo nada, maldito Windows ¬¬

---

### Post by anarko on 2010-05-11
Hace una cosa, una ves que te logueas en la consola escribi lo siguiente, y postea el resultado de ejecutar ese comando:
cat /etc/X11/xorg.conf

Por la info sacada de aca : [http://www.superwarehouse.com/Samsung_SyncMaster_793S-Black_17_CRT_Monitor/793S-BLACK/ps/422156](http://www.superwarehouse.com/Samsung_SyncMaster_793S-Black_17_CRT_Monitor/793S-BLACK/ps/422156)
El modeline que tenes que poner es el siguiente : Modeline "1280x1024@60" 114.98 1280 1312 1744 1776 1024 1045 1055 1076
Si te dice que no existe el archivo xorg.conf te ayudamos a crear uno default con las especificaciones de tu monitor para poder acceder al modo grafico y ahi si poder instalar los drivers de nvida.

---

### Post by Kalil94 on 2010-05-11
> **anarko said:**
> Hace una cosa, una ves que te logueas en la consola escribi lo siguiente, y postea el resultado de ejecutar ese comando:
cat /etc/X11/xorg.conf

Por la info sacada de aca : [http://www.superwarehouse.com/Samsung_SyncMaster_793S-Black_17_CRT_Monitor/793S-BLACK/ps/422156](http://www.superwarehouse.com/Samsung_SyncMaster_793S-Black_17_CRT_Monitor/793S-BLACK/ps/422156)
El modeline que tenes que poner es el siguiente : Modeline "1280x1024@60" 114.98 1280 1312 1744 1776 1024 1045 1055 1076
Si te dice que no existe el archivo xorg.conf te ayudamos a crear uno default con las especificaciones de tu monitor para poder acceder al modo grafico y ahi si poder instalar los drivers de nvida.
Sinceramente agradesco mucho la ayuda que me estan dando, bueno, les cuento que ayer cuando recibi el CD de ubuntu, lo instale "dentro de Windows" entonces cuando reinicie y eleji Ubuntu para terminar con la instalacion me aparecia el cartel del monitor sin señal, al rato lo reinstale y hay si, me dejo terminar la instalacion pero cuando reinicie y llego a la pantalla de login aparecio otra vez que el monitor no tenia señal, y, de buscar y buscar y no encontrar nada, lo desinstale, cosa que no tendria que haber echo porque ahora cuando lo instalo no me deja terminar con la instalacion, osea, cuando elijo Ubuntu y llega hasta donde, supuestamente, se tiene que ver el fondo naranja con el proceso de instalacion aparece el cartel de que no tiene señal, y bueno, mi pregunta es la siguiente, aunque la instalacion no alla terminado, ¿Puedo ejecutar el comando cat /etc/X11/xorg.conf igual? ¿O si o si necesito aver terminado la instalacion y estar logeado? (Pregunto porque, aunque no alla terminado, a la consola puedo ingresar igual)

---

### Post by santiago79 on 2010-05-11
Bueno gente perdón por la tardanza es que ando con mucho laburo,
bueno esto ya esta solucionado tengo 2 teorías
la primera con la actualización del kernel que alla normalizado el soporte con este monitor.
la segunda fue la de instalar todo el S.O e instalar el driver de Nvidia configurarlo como se debe
igual ahora con este monitor vi que ahora me salen 70 75 87 Hz que antes en ubuntu 9 no salían capas es una mejora del kernel.

bueno lo único que me tiene medio medio, es si un día tengo que por X motivo reinstalar el S.O no voy a poder si no me consigo otro monitor.
al que tiene el problema te recomiendo conseguirte un monitor prestado por unos días instalar bien el S.O instalarle el diver actualizar el kernel configurar al mínimo el rendimiento del monitor y ahí probar con tu monitor.
MUCHAS GRACIAS POR TODO.

---

