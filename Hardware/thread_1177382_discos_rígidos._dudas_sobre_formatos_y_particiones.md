---
title: "discos rígidos. dudas sobre formatos y particiones y errores de lectura"
date: 2009-06-03
forum: Hardware
---

### Post by granjero on 2009-06-03
buenas, tengo un par de dudas... 

la primera es que tengo un disco rígido de 80gb que mi idea es que funcione como backup.

lo formateé en ext3 y se lo puse a una máquina vieja que tengo (con ubuntu 9.04) conectada en red a mi maquina para ir backupeando todo...

ya le pase casi toda mi información importante y hoy cuando quise ver cuanto espacio tenía libre a ver si las películas entraban vi algo que me pareció raro **(imagen 1)** 

en propiedades del disco me dice "algunos contenidos son ilegibles"

quise correr el comando fsck pero no termino de entender como se usa...

ahora viene mi segunda pregunta y mi temor...

voy a actualizar mi computadora a ubuntu 9.04 ahora tengo ubuntu 8.04

y como cuando instale ubuntu no sabía que me iba a encantar hice un mamarracho de particiones...

el disco de 320gb lo partí como les muestro en la segunda imagen... (un asco) 

lo que quiero hacer ahora es estar seguro que el backup que hice en el disco de 80gb es seguro y completo... y no que cuando quiera recuperar datos me diga que tengo errores.

y luego rearmar el disco de 320gb de mi pc funcional con nuevas particiones para mi nuevo ubuntu.

mi idea es dejar la partición ntfs como está ya que la uso para jugar...

y luego que debería hacer? una partición extendida con el resto y dentro hacer
 
una de 30gb para /
una de 2gb para swap 
una de el resto para /home

o que recomiendan?

muchas gracias.

---

### Post by gmunioz on 2009-06-03
Hola gra...:

Dices: 

```
"...quise correr el comando fsck pero no termino de entender como se usa..."
```

Con man fsck tendrás una salida amplia, que se puede resumir en:

```
SYNOPSIS
       fsck [ -sAVRTMNP ] [ -C [ fd ] ] [ -t fstype ] [filesys ... ] [--] [ fs-specific-options ]

DESCRIPTION
       fsck  is  used  to check and optionally repair one or more Linux file systems.  filesys can be a device name (e.g.
       /dev/hdc1, /dev/sdb2), a mount  point  (e.g.   /,  /usr,  /home),  or  an  ext2  label  or  UUID  specifier  (e.g.
       UUID=8868abf6-88c5-4a83-98b8-bfc24057f7bd  or LABEL=root).  Normally, the fsck program will try to handle filesys&#8208;
       tems on different physical disk drives in parallel to reduce the total amount of time needed to check all  of  the
       filesystems.
```

Dices:

```
"...es estar seguro que el backup que hice en el disco de 80gb es seguro y completo...."


```

Eso lamentablemente solo tu puedes saberlo.

Dices:

```
"...y luego rearmar el disco.... con nuevas particiones ... que recomiendan?..."
```

Mi sugerencia es que instales Ubuntu en:

Una partición primaria, activa, sistema de archivos ext4, de unos 12 gigas, punto de montaje /

Una partición lógica, sistema de archivos intercambio, de 1 giga, montaje automatico intercambio, para swap

Una partición lógica, sistema de archivos ext4 de unos 6 gigas, punto de montaje /home.

Estas tres particiones a formatear con cada instalación de una nueva versión.

Una partición lógica, del resto del disco rígido disponible para Ubuntu, sistema de archivos reiserfs o ext3, punto de montaje /home/usuario/datos

Esta partición se mantiene sin formatear, con los datos a salvo, con cada instalación o reinstalación que se efectue. (La mia viene de Debian Sarge y ha pasado por todos los Ubuntu desde Dapper Drake sin ser afectada)

Saludos.

---

### Post by granjero on 2009-06-03
buenas, gracias por la respuesta. 
Con respecto al comando fsck ya le había echado una leída al manual pero no terminé de entenderlo...

cuando digo > estar seguro que el backup que hice en el disco de 80gb es seguro y completo quiero saber por qué en propiedades del disco dice que hay algunos contenidos son ilegibles... como se ve en la imagen que subi más abajo...

Con respecto a las particiones no me conviene hacer todo en ext3? esa ensalada me va a dar disgustos me parece...

salud!

---

### Post by gmunioz on 2009-06-04
Hola gra.....:

1- fsck, desmontas la partición y ejecutas:

sudo fsck /dev/sdxx

2- Particularmente, reformatearia el dispositivo y haría un nuevo

respaldo.

3- Usa el sistema de archivos que mas te agrade o convenga, mezclar

distintos sistemas de archivos propios de gnulinux no causa ningun

problema. Cada cual tiene sus indicaciones, sus ventajas y desventajas.

Saludos.

---

### Post by Tosh78 on 2009-06-04
Un comentario nada mas. A mi entender 12 gigas para / es mucho. Yo le asigne 8 y todavia tengo libres 3. Calculo que dependera de cuantas cosas instales.
Con respecto al sistema de archivos, yo uso siempre que puedo ext4 y funciona todo perfecto.

---

### Post by granjero on 2009-06-04
corri el comando fsck pero no entiendo la salida....


```
jm@pcvieja:~$ sudo fsck /dev/sdb1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sdb1: limpio, 28850/4890624 ficheros, 13061260/19537040 bloques (comprobación después de 4 montajes)

```

supuestamente estaría todo ok?

que quiere decir en las propiedades del disco que dice hay algunos contenidos son ilegibles??

gracias!

---

### Post by staar on 2009-06-04
si, está bien el sistema de archivos, eso de los contenidos ilegibles imagino que será algún tema de permisos (archivos a los que no podés acceder como usuario normal), nada grave...

saludos

---

### Post by granjero on 2009-06-04
será la carpeta lost & found? la única con permisos raros?

gracias por todo

---

### Post by staar on 2009-06-05
probablemente (casi seguro), carpeta con permisos raros si, pero que NO se toca, es parte del sistema de archivos...

saludos

---

### Post by biale on 2009-06-05
Añado tres pequeños detalles.

El primero es que observo que en el pantallazo aparece que tenes instalado gparted. El cual tiene una opción para verificar discos que se puedan desmontar y le añade al comando fsck un par de parámetros mas.

El segundo es el signo de admiración en la partición NTFS. En principio no señala cosas buenas, si no la puede montar es por algo, por ejemplo un mal cierre de la partición quedando indicada como dirty. Lo mejor sería correr el chkdsk en modo fuera de línea con el parámetro /F.

El tercero es que en el dimensionamiento del / hay que tener en cuenta al /tmp (temporarios). Y eso depende de las aplicaciones que se usen. Por ejemplo, para ripear un DVD hay que considerar 5 Gbites por encima del espacio estatico ocupado.

Un saludos a todos...

---

