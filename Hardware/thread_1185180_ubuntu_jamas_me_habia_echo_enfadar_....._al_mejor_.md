---
title: "ubuntu jamas me habia echo enfadar ..... al mejor estilo vista"
date: 2009-06-12
forum: Hardware
---

### Post by negrotuxero on 2009-06-12
[LEFT][FONT=Comic Sans MS][COLOR=Black][SIZE=4]ayer volvia yo de una escurcion al medico cuando llego a casa i encuentro .........[/SIZE][/COLOR][/FONT][COLOR=Black]
[/COLOR] [FONT=Comic Sans MS][COLOR=Black][SIZE=4]charan charan el livecd de ubuntu 9.04 esperando enfrente a la puerta[/SIZE][/COLOR][/FONT][COLOR=Black]

[/COLOR]  [FONT=Comic Sans MS][COLOR=Black][SIZE=4]ahora bien luego de instalar me encuentro con los siguientes problemas :[/SIZE][/COLOR][/FONT][COLOR=Black]

[/COLOR]  [FONT=Comic Sans MS][COLOR=Black][SIZE=4]1º perdi doce gigas de disco duro que no se donde fueron a parar sep sep 12gb ni ubuntu ni windows los han visto por ahi dando vuelta[/SIZE][/COLOR][/FONT][COLOR=Black]
[/COLOR] [FONT=Comic Sans MS][COLOR=Black][SIZE=4]2º al activarse el salvapantallas o al querer cambiarlo se tilda!!!! se tilda toda la maquina al mejor estilo vista ni el puntero se mueve o queda o imagen estatica del salvapantallas en cuestion[/SIZE][/COLOR][/FONT][COLOR=Black]
[/COLOR] [FONT=Comic Sans MS][COLOR=Black][SIZE=4]3º la conexion es un asco, super lenta comparada con 8.04 ...[/SIZE][/COLOR][/FONT][COLOR=Black]


[/COLOR]   [FONT=Comic Sans MS][COLOR=Black][SIZE=4]destaco que tengo solo 2 particiones[/SIZE][/COLOR][/FONT][COLOR=Black]

[/COLOR]  [FONT=Comic Sans MS][COLOR=Black][SIZE=4]al hacer sudo fdisk -l[/SIZE][/COLOR][/FONT][COLOR=Black]


[/COLOR]   [FONT=Comic Sans MS][COLOR=Black][SIZE=4]salio lo siguiente:[/SIZE][/COLOR][/FONT][COLOR=Black]
[/COLOR] [FONT=Comic Sans MS][COLOR=Black][SIZE=4]Disco /dev/sda: 160.0 GB, 160041885696 bytes[/SIZE][/COLOR][/FONT][COLOR=Black]
[/COLOR] [FONT=Comic Sans MS][COLOR=Black][SIZE=4]255 cabezas, 63 sectores/pista, 19457 cilindros[/SIZE][/COLOR][/FONT][COLOR=Black]
[/COLOR] [FONT=Comic Sans MS][COLOR=Black][SIZE=4]Unidades = cilindros de 16065 * 512 = 8225280 bytes[/SIZE][/COLOR][/FONT][COLOR=Black]
[/COLOR] [FONT=Comic Sans MS][COLOR=Black][SIZE=4]Identificador de disco: 0x90e528c0[/SIZE][/COLOR][/FONT][COLOR=Black]

[/COLOR]  [FONT=Comic Sans MS][COLOR=Black][SIZE=4]Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       15886   127601664    7  HPFS/NTFS
/dev/sda2           15887       19457    28684057+   5  Extendida
/dev/sda5           15887       19457    28684026   83  Linux
[/SIZE][/COLOR][/FONT][COLOR=Black]

[/COLOR]  [FONT=Comic Sans MS][COLOR=Black][SIZE=4]nodeberian ser dos lineas no mas[/SIZE][/COLOR][/FONT][COLOR=Black]
[/COLOR] [FONT=Comic Sans MS][COLOR=Black][SIZE=4]de los 160 gb solo veo 148,6 se que una parte esta destinada a vista i no debo verla pero la otra que si veia con anterioridad???una cosa mas que indica el * en inicio??[/SIZE][/COLOR][/FONT][COLOR=Black]


[/COLOR]   [FONT=Comic Sans MS][COLOR=Black][SIZE=4]sepan disculpar mi ignorancia i las faltas de ortografia!!!!![/SIZE][/COLOR][/FONT][COLOR=Black]

[/COLOR]  [FONT=Comic Sans MS][COLOR=Black][SIZE=4]espero que no me asesinen por lo del "al mejor estilo vista"[/SIZE][/COLOR][/FONT][COLOR=Red]:popcorn:[/COLOR] 

cambio el color juaz...


no tengo swap...probe la conexion en vista y anda lo mas bien 
tengo una integrada de intel

me movieron el thread no lo encontraba XD

sep me dice que son 149 gb pero antes tenia 159 y piquito :s

GRACIAS POR CONTESTAR !!!
[/LEFT]

---

### Post by staar on 2009-06-12
por las faltas de ortografía te disculpo (i en vez de y :o) por la tipografia, no... chaboon, casi me sacas los ojos :-P

los doce gigas no los perdiste, en realidad los discos no tienen la capacidad total con la que se venden, es un 'truco' de los fabricantes para vender más, la capacidad real es menor (mi disco de 80 tiene en realidad 74, se hace más notorio a medida que el tamaño del disco aumenta), aparte de que los sistemas de archivos toman espacio por el solo hecho de existir...

el fdisk -l está bien, son tres líneas porque ubuntu necesita mínimo dos particiones, una para los archivos, y otra para la swap (memoria de intercambio), el * significa que la partición tiene el flag de boot, las particiones con un windos instalado siempre lo tienen (si no, el Ventanas no podría bootear)

lo del protector de pantallas, raro, que placa de video tenés? drivers?

lo de la conexión, no creo que se deba a la versión ubuntu, en teoría tendría que andar siempre igual, probaste en otro SO? tu proveedor no tendrá problemas?

saludos

---

### Post by Hei Ku on 2009-06-12
Si no tenes paciencia para resolver problemas y aprender, volve a lo conocido. Es una condicion indispensable.

Te pido por favor que no vuelvas a escribir en ese tamaño de letra y color. Molesta a la vista, y no es necesario.

---

### Post by pol666 on 2009-06-12
nunca vi un disco de 160gb, son todos de 149gb como vos decis, ubuntu te canta la posta.

---

### Post by santiagoward2000 on 2009-06-12
> **pol666 said:**
> nunca vi un disco de 160gb, son todos de 149gb como vos decis, ubuntu te canta la posta.

> Disk /dev/sda: **160.0 GB**, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1bdf1bde

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13587   109128700    7  HPFS/NTFS
/dev/sda2           13588       19457    47150775    5  Extended
/dev/sda5           13588       19211    45174748+  83  Linux
/dev/sda6           19212       19457     1975963+  82  Linux swap / Solaris


Mi disco no existe! :lolflag:

---

### Post by staar on 2009-06-12
a la cantidad de bytes, tenés que dividirla por 1024, tres veces (los fabricantes la dividen por 1000)
160041885696 bytes / 1024 = 156290904 KB
156290904 KB /1024 = 152627,8359375 MB
152627,8359375 MB /1024 = 149,05062103271484375 GB
;-)

saludos

---

### Post by guillermolisi on 2009-06-12
Creo que la confusion viene por el lado de como se expresa la medida.

Me parece que los fabricantes, al margen de expresiones "marketineras", expresan la capacidad en bruto del disco. Como la propia estructura que se necesita para administrar particiones, MBR, bad tracks mapping area, etc. usa espacio, resulta que la capacidad efectiva es menor a la declarada por el fabricante en el modelo/etiqueta del disco.

---

### Post by negrotuxero on 2009-06-12
> **staar said:**
> 

el fdisk -l está bien, son tres líneas porque ubuntu necesita mínimo dos particiones, una para los archivos, y otra para la swap (memoria de intercambio), el * significa que la partición tiene el flag de boot, las particiones con un windos instalado siempre lo tienen (si no, el ventanas no podría bootear)



osea que si quiero instalar el boot grafico tendria que instalarlo en sda 1 no???

---

### Post by staar on 2009-06-12
nop, si con boot gráfico te referís al grub con gfxboot, va en /dev/sda, sin número, que se interpreta como la MBR (Master Boot Record) del disco...

es simplemente imposible que antes tuvieras 159 GB en un disco de 160 GB, todos los discos de ese tamaño tienen 149 GB (aproximadamente) usables, te debés estar confundiendo...

veo también que no tenés swap, pero la partición de ubuntu es una logica, que siempre van dentro de una extendida, por eso ves dos particiones en el fdisk -l, la extendida no tiene capacidad de almacenar por si misma datos, almacena particiones lógicas...

la conexión, la verdad ni idea, en teoría tendría que andar igual, que conexión es?

y lo del video, lamentablemente los drivers de intel para jaunty no estan del todo pulidos, por algunos cambios que se están haciendo...

saludos

---

### Post by negrotuxero on 2009-06-12
> **staar said:**
> nop, si con boot gráfico te referís al grub con gfxboot, va en /dev/sda, sin número, que se interpreta como la MBR (Master Boot Record) del disco...

es simplemente imposible que antes tuvieras 159 GB en un disco de 160 GB, todos los discos de ese tamaño tienen 149 GB (aproximadamente) usables, te debés estar confundiendo...

veo también que no tenés swap, pero la partición de ubuntu es una logica, que siempre van dentro de una extendida, por eso ves dos particiones en el fdisk -l, la extendida no tiene capacidad de almacenar por si misma datos, almacena particiones lógicas...

la conexión, la verdad ni idea, en teoría tendría que andar igual, que conexión es?

y lo del video, lamentablemente los drivers de intel para jaunty no estan del todo pulidos, por algunos cambios que se están haciendo...

saludos


si a eso me referia a gfxboot...

la swap no me parecio necesesaria con 1001 mb de ram XD

en cuanto a los 149 pues la verdad no se .. cuando compre la pc decia master tantos gb disponibles de 159 :s pero da igual total aun queda espacio ..jaja

en cuanto a lo de extendida, pues sep tenias razon me di cuenta cuando instale e editor de particiones de gnome y ademas me figuran dos particiones mas de menos e 2 mb O_O sin asignar pero que se yo 


GRACIAS A TODOS X CONTESTAR DE BUENA GANA ...

---

