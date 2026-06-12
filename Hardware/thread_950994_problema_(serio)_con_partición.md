---
title: "problema (serio) con partición"
date: 2008-10-17
forum: Hardware
---

### Post by benjamin_linux on 2008-10-17
Hola a todos!!

Copié unos archivos desde Ubuntu a la partición de Win, quise entrar ahí y me aparece un cartel azul diciéndome poco amablemente que no puedo hacerlo... y ahora tampoco puedo montar la partición desde Ubuntu.
Estaba trabajando normalmente, no tiene mucho sentido... Por lo que leí podría tratarse de falta de espacio. No sé si será eso, pero aunque lo fuera no tengo manera de acceder a la partición como para liberar un poco de megas.
No quiero tener que restaurar el sistema a la versión de fábrica del Vista (la única opción que me da el sistema) y tengo miedo, de hacerlo, que me joda en algo tanto la partición de Ubuntu como el Grub.

PLEASE HELP!
Y gracias :D

---

### Post by benjamin_linux on 2008-10-17
Añado un screenshot del mensaje de error que me da cuando intento montar la partición. Como verán, dice que no puede hacerlo porque está "en uso".

---

### Post by Hei Ku on 2008-10-17
En ese mismo cartel te dice que podes meter un comando para forzar el mount, agregando force al comando que usas habitualmente.

Como la montas generalmente?

---

### Post by benjamin_linux on 2008-10-17
Usualmente, haciendo doble click :P (en Lugares > Soporte de 31,5g). El tema es que me da una opción pero "at your own risk", onda no es muy tranquilizador eso, no quiero perder información ni joder (más) el disco, en lo posible.

Me estoy quedando ciego y no encuentro nada en Google, lo único que encontré es un "device is busy" con un USB, solucionado con el comando fuser, porque una terminal seguía abierta... pero acá reinicé la laptop varias veces, no puede ser un proceso abierto que mantenga ocupado al disco.

De última restauro el sistema en Win, eso no me repercute en nada el grub, particiones, etc?

---

### Post by Hei Ku on 2008-10-17
El formato NTFS tiene un indicador en la particion para cuando la particion esta en uso. Por alguna razon, ese indicador debe haber quedado puesto.
Lo que te recomendaría es que hagas un backup de la particion con dd, y despues pruebes de montarla.

---

### Post by benjamin_linux on 2008-10-17
**(Antes que nada, gracias por la ayuda)**

Eso me lleva a una duda en dos partes, cuál es la ubicación de mis particiones, la de U y la de W... porque en /boot/grub/menu.lst aparece:

> ## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d0c58492-db66-4fe7-a40d-78601d514617 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
boot

y 

> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

y en fstab:

> 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=d0c58492-db66-4fe7-a40d-78601d514617 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=386ac617-9149-4176-a38d-1ec299141285 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0

Esto, para hacer el backup con dd con mi pendrive, que no tengo ni un cd/dvd virgen y no puedo ni ir al quiosco.

---

### Post by EnriqueK on 2008-10-17
No se si entendí bien, pero me da la impresión de que has dejado hibernado a WVista, por eso te indica que la partición está en uso y no la puedes montar, de todas maneras si este no es el caso, ya sabes que si dejas hibernado a Windows, no puedes montar su partición cuando arranques con Linux.

---

### Post by benjamin_linux on 2008-10-17
La verdad que no sabía eso pero no, no quedó hibernando. Copié unos archivos desde Ubuntu a la partición de Win lo más bien, vi unos videos, estudié, todo perfecto. La reinicié para entrar a W y ahí me apareció un mensaje de error. Lo único que me deja hacer es o reiniciar para correr el restaurador de sistema o reiniciar para correr el restaurador de sistema... Entro a Ubuntu y tampoco puedo acceder desde acá, me da el mensaje de error que pegué más arriba, intenté desde el LiveCD y me dice lo mismo.

---

### Post by guisheca on 2008-10-18
El problema es que no se cerró bien la sesión de win, por eso te sa ese error de disco ocupado.
Antes de seguir te recomiendo encarecidamente que ya mismo te pongas a hacer un resguardo de tus datos por el método que sea, pero hacelo antes que cualquier cosa.
Lo siguiente que te recomiendo es que de ahora en mas no pongas nada de importancia en tus particiones NTFS, es el peor sistema de archivos jamás creado.
De ahí en mas bien bien que pasos seguir no se, es decir, cuales el camino mas eficiente para lograr lo que queres. A mi me pasó exactamente lo mismo que a vos una ves y por hacer las cosas a las apuradas perdí tres años de mi vida en fotografías digitales.
Saludos.

---

### Post by benjamin_linux on 2008-10-18
-Uffffffff-
Pero que resguarde qué información decís... ¿la de NTFS o la de ext3? Es decir... no tengo la más mínima idea de cómo acceder a la partición NTFS, ya estoy dando por perdida toda la informaión. Podría llegar a intentarlo por la fuerza como me recomiendan, pero si hay pocas posibilidades para eso vuelvo el sistema a la versión de fábrica, si total de los dos modos pierdo la información... Nada puede joderme a la ext3 y el grub, ¿no?

---

### Post by Hei Ku on 2008-10-18
Lo que te digo es que solo forzas una marca de la particion.
Abri la particion y proba antes de darla por perdida.

Hay una forma de hacer resguardo de la particion NTFS con el comando dd, pero no me acuerdo bien como es. De todas maneras, proba de abrirla y ya esta.

---

### Post by benjamin_linux on 2008-10-18
Disculpá la pregunta tonta, pero cómo abro la partición si me niega el acceso?

---

### Post by Hei Ku on 2008-10-18
probaste agregarle force en el momento de abrirla, como te dice el mensaje de error?

---

### Post by benjamin_linux on 2008-10-19
Le agregué force y me dice "failed to access mountpoint" (adjunto un screenshot del error completo"; entonces agregué la línea en fstab, como me recomendaba y ahora cuando intento montar me dice 
[mntent]: la línea 11 de /etc/fstab es incorrecta, mount: no se puede encontrar /media/disk en /etc/fstab o /etc/mtab

Los dos me dicen básicamente lo mismo, que no lo pueden encontrar en /media

---

### Post by Mauro22 on 2008-10-19
La carpeta /media/disk existe? Si en la consola pones cd /media/disk entra o te da error?

Si windows quedo inarrancable (?) pero con el atributo "en uso" marcado.. si no me equivoco con un chkdsk lo podes sacar. Para eso necesitas bajarte un livecd en base a windows como el MiniPe o el ShagOs... pero no se si tenes un 100% de probabilidad de "liberar" el disco (digo esto para que no te bajes el cd al cuete)


:)

---

### Post by benjamin_linux on 2008-10-19
Medio problema solucionado: no existía la carpeta /media/disk... pensé que la crearía automáticamente pero no, la creé de manera manual y ahora haciendo 

sudo mount -t ntfs-3g /dev/sda1 /media/disk -o force

puedo ver la partición. Ya recuperé toda la información importante. :D

El tema es que sigo si poder entrar a Win, decís que con uno de esos LiveCD podría solucionarlo? Y de lo contrario, de restaurar el Win a la versión de fábrica, me cambiaría en algo el Grub o las particiones, que es lo que más me importa?

---

### Post by Mauro22 on 2008-10-19
Si recuperaste la info podes:


* Poner el cd de win y formatear y volver a instalar (Perdes Grub y todo la info)
* Poner el cd de win y reparar la instalacion (Perdes Grub pero no la info)
* Si tenes tiempo (y ancho de banda y un cd virgen) probar lo del livecd...


PS: Si queres dale a la medallita de mi post, que me faltan 2 para las 50 :D

---

### Post by benjamin_linux on 2008-10-19
Tengo ancho de banda y tiempo y no quiero tener que reconfigurar grub ni nada, así que voy a probar con algún LiveCD de esos, me recomendás alguno en particular?

Jajaja yo estoy encaminado, en un tiempo voy a llegar a los 50 thanks... :P

---

### Post by Mauro22 on 2008-10-19
Mira, el que siempre uso es el minipe:

```

www.minipe.org

```

Para descomprimir el pass es:

```
thecavern
```

---

### Post by benjamin_linux on 2008-10-19
Ya lo puse a bajar, parece práctico :D

Igualmente, si con eso no funciona... sacaré el Vista y eventualmente pondré un XP, por las dudas, que tengo el Starter y no puedo abrir más de 3 aplicaciones a la vez y ya no lo aguanto más, entro y me pongo de mal humor.

Gracias!!

---

### Post by benjamin_linux on 2008-10-28
Una vez probado, me sigue pareciendo práctico pero no me solucionó nada, sigo sin poder entrar a Win. Así que voy a aprovechar y lo voy a sacar de la laptop, no voy a poner ni el XP. Entonces mi duda es... porque las veces que instalé Ubuntu fue siguiendo una guía para un dual-boot y no sé bien que hacer, porque en este momento tengo

ext3 > 60g
ntfs > 30g
sin asignar > 15g

y mi idea es dejar ext3 como está y juntar ntfs con el espacio sin asignar y hacer de eso una partición aparte para /home. Hay bastantes guías para hacerlo, pero como tengo este lío de particiones que quiero estabilizar, con gparted puedo hacerlo de una? o me recomiendan reinstalar ubuntu para eliminar el dual-boot? Es una pregunta tonta pero la verdad que no sé.

Como siempre, mil GRACIAS.

---

### Post by Mauro22 on 2008-10-28
Por lo que entiendo ahora tenes en una particion ubuntu y /home juntos, no?


Con el gparted podes eliminar la de ntfs y junto con "no asignado" formatear como ext3.


Hasta ahi vamos, ahora:

* Lo del dual boot -grub-, con un par de modificacion, lo dejas 10 puntos.

* El problema radica en que la parte /home ya esta dentro de la primer particion junto con el sistema. Existe una guia para "mover" el /home a otra...




Ahora, si fuera mi caso, borro todo (lease TODO) e instalo ubutnu de 0 con 3 particiones:

* /
* /home
* swap 

y Listo el pollo!!

---

### Post by benjamin_linux on 2008-10-29
Yo también prefiero borrar TODO y arrancar de 0 :D

Entonces cómo sería la configuración de las particiones, durante la instalación?

---

### Post by Mauro22 on 2008-10-29
Elegi particionado manual, no el guiado que no sirve :D


3 particiones:

1) Punto de montaje / 
-> Aca va el sistema operativo, los programas instalados y demases.
2) Punto de montaje /home
-> Esta particion son pura y exclusivamente tus datos y la configuracion de los programas.
3) Swap 
-> Se calcula memoria RAM x 2 (Ej. Si tenes 1024 mb (1gb) haces una particion de 2gb)

y Listo el llopo!

---

### Post by benjamin_linux on 2008-10-30
Me veía más complicada la determinación de particiones durante la instalación jaja.
Voy a ver si el finde, que tengo tiempo libre, mientras estudia mi novia, me pongo a hacerlo :D
Porque justo sale Intrepid y Hardy lo he tenido que reinstalar por estupideces que hago al *aprender, siempre me funcionó genial, pero medio que me dan ganas de ver II

Veré, veré
Graciasss

---

### Post by benjamin_linux on 2008-10-30
Ni quiero ser pesado jaja pero adjunto un screenshot del sistema de particiones, porque no me acordaba de un *pequeño detalle al que nunca le di bola, la laptop me vino con una partición "Compaq" donde había archivos de sistema y demás, como se ve en la captura.

Ya que voy a eliminar win completamente, puedo "juntar" esos 10g con los demás sin problema? O perdería algo del BIOS o sistema o lo que sea, nunca entré la verdad a ver qué había :P

---

### Post by Mauro22 on 2008-10-30
Supuestamente esa particion es para (junto con los cds de recuperacion) podeis dejar la PC tal cual te la vendieron.


En vez de formatear e instalar todo de cero (cosa que el usuario promedio no deberia tener que hacerlo), los cds descomprimen esa particion en otra.



En criollo, eso es una imagen del S.O. que te vino de fabrica. Claro esta, si todavia la tenes en garantia, te conviene dejarla. Aunque por 10GB, yo la dejaria. No vaya a ser cosa que en el dia de mañana la tenes que llevar al STA y no te den soporte porque no tenes el s.o. original de la pc....



A ver que te dicen los demas.

---

### Post by benjamin_linux on 2008-10-31
Supuse. Y todavía me quedan varios meses de garantía, así que la dejo como está. Ya descargué Intrepid así que este finde lo instalo, gracias por enésima vez :D

---

