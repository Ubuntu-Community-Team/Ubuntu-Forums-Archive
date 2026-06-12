---
title: "Ampliar la particion de kubuntu"
date: 2010-04-12
forum: Hardware
---

### Post by giov on 2010-04-12
Sres.

Volviendo luego de un largo paseo por win 7 obligado al necesitar autocad en una version x para trabajo en la u he vuelto esta vez instalado kubuntu karmic ya que encontre a medusa4 un software cad que esta rebuenisimo.

Pero a lo que vengo, nuevamente a solicitar vuestra ayuda, instale con 3 particiones swap y 2 ext4, la particion donde instale ubuntu me quedo chica por lo que necesito ampliarla, pense en reinstalar pero no tengo como respaldar mis datos tampoco quiero perder lo que ya tengo armado.

Intente con gparted pero la particion de kubuntu ya esta bloqueada por lo que pedi ayuda en kubuntu-es.org, pero en mi empresa esta bloqueado ahora no puedo navegar en ese sitio.
ello me dieron esta estas observaciones, que no comprendo mucho ya que busque lo que me indicaron pero encontre solocasos particulares que no comprendo.

>  No puedes redimensionar las particiones si están montadas, en este caso tienes que hacerlo desde un livecd. 

> Si no tienes ningún LiveCD puedes usar "GParted LiveCD". Si ya Tienes sin Arranca LiveCD CON EL e instala Sólo Paquete El gparted. Si ya tienes un LiveCD arranca con él e instala sólo el paquete gparted 

> ojo con redimensionar particiones. Que tendras fstab El revisar Y El grub. Tendrás que revisar el fstab y el grub. Busca en El Foro Algún hilo Que contenga Las Tres Palabras: redimensionar fstab grub Busca en el foro algún hilo que contenga las tres palabras: redimensionar grub fstab

Que es el fstab (pregunta aparte de la solicitud de ayuda)

Porfavor si me pudieran guiar a lograr aumentar o eliminar la segunda particion que ya no voy a utilizar les agradeceria.

Saludos

---

### Post by asterix77 on 2010-04-12
Primero que nada, deberias entregar más detalles de tu disco duro. Para ello detalla lo que aparece con el comando

#sudo fdisk -l

Otra cosa, no entiendo porqué tienes 3 particiones swap, si con una te basta.

Con respecto a fstab:

[http://es.wikipedia.org/wiki/Fstab](http://es.wikipedia.org/wiki/Fstab)

[U][http://wiki.archlinux.org/index.php/Fstab_%28Espa%C3%B1ol%29](http://wiki.archlinux.org/index.php/Fstab_%28Espa%C3%B1ol%29)

[/U] 
Saludos

---

### Post by giov on 2010-04-12
Esto dice,
Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x647fd7e4

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1         124      995998+  82  Linux swap / Solaris
/dev/sda2             125        9729    77152162+   5  Extendida
/dev/sda5             125        6082    47857603+  83  Linux
/dev/sda6            6083        9729    29294496   83  Linux

Disco /dev/sdb: 998 MB, 998768640 bytes
32 cabezas, 63 sectores/pista, 967 cilindros
Unidades = cilindros de 2016 * 512 = 1032192 bytes
Identificador de disco: 0x00000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1         967      974670+   6  FAT16

Disco /dev/sdc: 4043 MB, 4043284480 bytes
255 cabezas, 63 sectores/pista, 491 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x04dd5721

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   *           1         492     3948488+   c  W95 FAT32 (LBA)
La partición 1 tiene distintos finales físicos/lógicos:
     físicos=(490, 254, 63) lógicos=(491, 144, 53)

No  no son 3 swap si no que 1 swap y 2 ext4

Gracias,

---

### Post by asterix77 on 2010-04-13
Una cosa me olvidé de comentar, con desmontar una unidad no vas a borrar los datos, solo si la formateas.

Lo que pides creo que no se puede hacer, creo entender que lo que quieres hacer es fusionar dos de tus particiones, pero sin perder los datos en la partición añadida.

Con Gparted lo que si puedes hacer es aumentar el tamaño de tu partición con ubuntu a costa de "espacio libre que tengas en otra partición" (siempre y cuando sean del mismo disco duro). Quizás de esta forma puedas agregar un espacio necesario para traspasar la información de la otra partición, para luego formatearla y terminar de agregarla a la de ubuntu.

Corre el siguiente comando para ver el espacio disponible en tus discos

#df -h


Saludos

---

### Post by giov on 2010-04-13
S.ficheros            Tamaño Usado  Disp Uso% Montado en

/dev/sda5               45G    38G   5,1G   89% 
/
udev                 497M   288K   497M   1% 
/dev
none              497M    12K   497M   1% 
/dev/shm
none          497M    80K   497M   1% 
/var/run
none          497M      0   497M   0% 
/var/lock
none         497M      0   497M   0% 
/lib/init/rw

/dev/sda6              28G  233M   26G   1% /usr/local


quiero quitarle espacio a sda6 para aumentar a sda5.

Graciasss

---

### Post by Carlos C on 2010-04-13
+1 a lo dicho por asterix77. Puedes aumentar una partición a costa de otra que tengas en el mismo disco.

Me da la impresión de que lo que citas es una traducción de google de algo en inglés, porque hay cosas que no se entienden bien. Sí se entiende lo obvio: que tienes que desmontar las particiones que vas a modificar. Como en este caso entiendo que deseas modificar tu partición "/", necesitas partir desde un cd o un pendrive para que esa partición no se monte. Puedes usar el LiveCd de Ubuntu que trae Gparted (al menos en karmic viene con Gparted). Tambien puedes usar el LiveCd de Gparted que puedes descargar desde su sitio oficial o instalar ubuntu en un pendrive con gparted y partir desde ahí.

Saludos.

---

### Post by giov on 2010-04-13
Ya tengo el kubuntu live voy a iniciar con el pero una vez en el debo iniciar gparted y traabjar con el.

Estas son las respuestas que me dieron en kubuntu-es
> Si no tienes ningún LiveCD puedes usar "GParted LiveCD". Si ya tienes un LiveCD arranca con él e instala sólo el paquete gparted.


> ojo con redimensionar particiones. Tendrás que revisar el fstab y el grub. Busca en el foro algún hilo que contenga las tres palabras: redimensionar grub fstab
Hice esto pero solo encontre casos particulares que no creo que hayan sido algo estandar para estas situaciones.

> Es cierto, por un momento olvidé que al redimensionar particiones cambia el UUID de las mismas. Gracias shaola.

Graciasss..

---

### Post by asterix77 on 2010-04-13
En sda5 te quedan 5,1 Gigas de espacio disponible, mientras que en sda6 te quedan 26 Gigas de 28 (tan solo has ocupado 233 Megas de esa partición)

Consultas :

¿porqué en sda6 tienes montado /usr/local ?¿al instalar ubuntu lo montastes en esa partición y no en sda5?

¿no tienes /usr/local en tu directorio principal, vale decir / en sda5?.


Aumentar la partición sda5 es sencillo.

a) Si es que ya posees /usr/local/ en sda5 solo tienes que usar un live cd que posea gparted, desmontar con gparted ambas particiones, redimensionar, y aplicar los cambios.

b) Si es que no posees /usr/local/ en sda5, copiaría todo lo que esté en sda6 a sda5 en el directorio / de forma que te quede un /usr/local (igual al que tenías en sda6, pero ahora en sda5), y luego continuaría con el live cd de la misma forma comentado arriba.



De todos modos, tal vez para futuras instalaciones, te recomiendo dejar una partición solo para tu /home/usuario, de esta forma al querer actualizar o instalar una distro linux, no se borrarían tus archivos.


Saludos y espero que se entienda y que que sirva

---

### Post by giov on 2010-04-14
Estimado

gracias por la explicación, esta tarde decidí reinstalar kubuntu dejando todo en una sola partición desconocia lo del home por lo que no lo hice de esa forma, e hice todo esto pensando que falta poco para que liberen el 10.04  y recomenzar con el con una instalacion limpia.-

agradesco la ayuda que siempre han estado dispuestos a brindar.

---

### Post by asterix77 on 2010-04-14
Creo que para fines de este mes liberan la nueva versión que será LTS.

Bueno creo que al principio a todos nos pasa lo mismo, yo estuve con la misma disyuntiva.

Lo más recomendable es dejar una partición swap (2 Gigas app), una para Ubuntu (15 ó 20 gigas o más si tienes un disco duro grande), y otra para tu /home/usuario

Todo esto si es que no vas a dejar otro S.O.

Saludos

---

### Post by giov on 2010-04-17
Bueno mi disco es de 80g entonces que configuracion me recomiendan, por otro lado 2 de swap no es mucho? 
hasta el momento no pretendo cambiar de so. Tengo todo lo que necesito aqui.

SLDS

---

### Post by asterix77 on 2010-04-17
Por lo general, se recomienda el doble de memoria en la swap; pero 2 gigas a mi parecer está bien. En mi caso tengo un pc con 80 gigas que lo dejé de la siguiente forma: (mi pc tiene 2 gigas de memoria)

Swap-------> 2 Gigas
Directorio Raíz("/")------> 20 Gigas (es aquí donde se instala ubuntu, pero sin el "home"
/home/usuario--------> El resto en Gigas

Obviamente esto puede variar un poco, por ejemplo si vas a instalar mucho software, dejas más espacio en /

Pero esto ya se sale del tema, que era como ampliar una partición, por lo que si quieres más info, debieras abrir otro post.


Saludos

---

