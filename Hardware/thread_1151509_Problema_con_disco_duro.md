---
title: "Problema con disco duro"
date: 2009-05-07
forum: Hardware
---

### Post by cor_stellae on 2009-05-07
Hola chicos:

Soy yo de nuevo con preguntas y problemas en Ubuntu. Hoy formateé una partición de un disco duro de 250 GB. Las tres particiones que tenía estaban en NTSF, pero al ver las ventajas del sistema ext3, decidí pasarme a este otro formato. 

Abrí el gparted, seleccioné la partición y le di formato nuevo. Al abrir la partición, encontré una misteriosa carpeta titulada **lost+found**, bloqueada, que no me permite borrar ni leer. Por lo que indica el uso del disco, mide cerca de 5 GB.

Bueno, aún así, creyendo que es simplemente espacio muerto, traté de copiarle cosas a la partición, pero me indica que no puede copiar porque no tengo privilegios para copiar al disco.

Estoy segura de que esto es algo muy fácil de solucionar pero, como siempre, no sé cómo se hace. ¿Alguien puede darme una manita?

Un millón de gracias.

---

### Post by guillermolisi on 2009-05-07
> **cor_stellae said:**
> Hola chicos:

Soy yo de nuevo con preguntas y problemas en Ubuntu. Hoy formateé una partición de un disco duro de 250 GB. Las tres particiones que tenía estaban en NTSF, pero al ver las ventajas del sistema ext3, decidí pasarme a este otro formato. 

Abrí el gparted, seleccioné la partición y le di formato nuevo. Al abrir la partición, encontré una misteriosa carpeta titulada **lost+found**, bloqueada, que no me permite borrar ni leer. Por lo que indica el uso del disco, mide cerca de 5 GB.

Bueno, aún así, creyendo que es simplemente espacio muerto, traté de copiarle cosas a la partición, pero me indica que no puede copiar porque no tengo privilegios para copiar al disco.

Estoy segura de que esto es algo muy fácil de solucionar pero, como siempre, no sé cómo se hace. ¿Alguien puede darme una manita?

Un millón de gracias.
Vamos desde el principio, dale ?

Que sistema operativo tenes instalado en la maquina ? Ubuntu, Ubuntu mas Win ? Solo Win ? Ninguno ?

Luego, funciona la PC con lo que tengas como SO ?

El disco lo agregaste al que ya tenia o es el unico en la PC ?

Todo esto es para instalar Ubuntu ?

El directorio lost+found es parte del sistema de archivos ext3 y NO debe ser borrado.

---

### Post by cor_stellae on 2009-05-07
Bien, aquí van todos los detalles, pelos y señales:

Sistemas operativos: Ubuntu Jaunty Jakalope 9.0.4 y Windows XP. El Ubuntu es el sistema operativo principal. El Windows está relegado a una partición de 25 GB (NTFS) y su única función es permitirme correr el CS3 y otras aplicaciones que necesito en estos días porque no quiero usar un emulador.

Discos duros físicos: total, 3:
a. **Disco duro principal:** 
comparte Ubuntu y Windows. 
Tamaño: 160 GB. 
Cuatro particiones: 1, Ubuntu; 2, Windows, NTFS; 2, datos; 4, swap.

b.** Disco duro 2:** 
Tamaño 250 GB. 
Tres particiones: 1, 98 GB; [COLOR=Green]2,[/COLOR] [COLOR=Green]103 GB (la que en este momento tiene problemas)[/COLOR]; 3, 30 GB. 
Ya sé que no suman exactamente 250, pero creo que ese era el tamaño original del disco. 
Las tres particiones eran NTFS hasta el día de ayer, que la partición 2 fue formateada con GParted como ext3. El objetivo es que este HD tenga dos particiones ext3 (las dos grandes) y reservar la de 30 GB como NTSF para archivos de Windows, mientras me deshago definitivamente de ese engendro de sistema.

c. **Disco duro 3:** tamaño 160 GB. Una sola partición, formato actual NTFS. Voy a formatearla como ext3, una vez resuelto el problema con la otra partición.

En cuanto al tipo de error que produce al copiar, adjunto imagen para mostrarlo mejor.

Esta partición NO SERÁ utilizada para sistema operativo. Es únicamente una partición de datos. El asunto es que necesito estar segura de que voy a poder utilizarla para comenzar a organizar datos de los otros discos en ella e ir migrando todas las particiones de NTFS a ext3.

Esto ocurre porque ayer descubrí el agua caliente: ¡que ext3 no necesita defragmentación, como el NTFS! Y, visto ahora que sí me voy a quedar en Ubuntu y dejaré Windows atrás, quiero todos mis discos duros funcionando de la mejor manera posible.

Así pues, mis sospechas son las siguientes:
1. Estoy haciendo mal algo durante el proceso de formateo.
2. Necesito abrir alguna consola extraña con algún código curioso para darle privilegios al HD. Esto me parece, en cualquier caso, extraño y no creo que deba ocurrir.

Otros datos: usuarios, solo uno con todos los privilegios: yo.

Espero que esta información más detallada sirva. Gracias por aclararme lo de la carpeta, yo estaba haciendo lo posible por borrarla... je je je... afortunadamente, sin éxito.

---

### Post by staar on 2009-05-07
podrías postear la salida de poner en la Terminal ```
sudo fdisk -l
``` y el contenido de tu archivo /etc/fstab?

creo que montando la partición, con los permisos necesarios, al inicio (agregándola correctamente a fstab), tu problema estaría resuelto...

saludos

---

### Post by pablo.s on 2009-05-07
Creo que con el consejo que le dió
Guille (que no borrara la carpeta) ya
no hace falta mas. Comparativamente
5 GB en una partición de 250 GB no
son mucho espacio. Incluso cuando se
sabe que en el próximo fsck le va a
crear la carpeta... otra vez.

---

### Post by cor_stellae on 2009-05-07
ya puse sudo fdisk -l

y lo que me sale es la lista de discos y particiones que tengo. 

¿Cómo agrego correctamente un disco al fstab? Insisto... soy novata y no sé una palabra de programación... si no me dan el tutorial para bebés, con monitos y todo, me cuesta mucho... :(

---

### Post by cor_stellae on 2009-05-07
Bueno, con la referencia del fstab, googlée un rato y me econtré este tutorial:

[http://lamaquinadiferencial.wordpress.com/2008/11/05/como-montar-un-disco-duro-automaticamente-en-ubuntu-fstab/](http://lamaquinadiferencial.wordpress.com/2008/11/05/como-montar-un-disco-duro-automaticamente-en-ubuntu-fstab/)

Lo logré seguir hasta aquí:

Creamos la carpeta donde queremos montarlo:
 $ sudo mkdir /media/disco
 Y editamos fstab para agregar la línea de montaje:
 $ sudo vi /etc/fstab

Pero cuando puse la última línea, me lanzó un montón de información del fstab... aquí es donde no sé qué debo editar...

---

### Post by staar on 2009-05-07
primero, estas usando el editor de texto vi, que es medio (bastante) dificil de usar, mejor usa gedit, la linea quedaría así ```
sudo gedit /etc/fstab
``` y tendrías que agregarle una línea así ```
/dev/*tupartición*  /media/disco   ext3     defaults                                            0 0
``` lo que faltaría es identificar que nombre le da ubuntu a tu partición (del tipo /dev/sda1, /dev/sdb2, o similar, por eso te pedí que postearas sudo fdisk -l) corré ```
mount
```, te va a listar los filesystems montados, identificá el montado en /media/Orfeo, y ponelo en la línea de tu fstab...

saludos

---

### Post by cor_stellae on 2009-05-07
Ya lo hice y ahora estoy peor que antes. Cuando me voy al menú Lugares, me dice que no puede montar el volumen porque solo el usuario root puede hacerlo.

Después de lo que hice, mi fstab quedó así:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=44423bd8-5171-4c8f-8c7a-765e55e876c4 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=f657b4e3-ee14-43cc-be34-e63bcaf68917 /home           ext3    relatime        0       2
# swap was on /dev/sda3 during installation
UUID=6fcbec2a-5bc1-4674-91b6-9f5b8e76c36d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb3 /media/Orfeo ext3 defaults



¿Qué le debo cambiar?

---

### Post by cor_stellae on 2009-05-07
Ya intenté cambiar varias veces el fstab. La última vez quedó así:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=44423bd8-5171-4c8f-8c7a-765e55e876c4 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=f657b4e3-ee14-43cc-be34-e63bcaf68917 /home           ext3    relatime        0       2
# swap was on /dev/sda3 during installation
UUID=6fcbec2a-5bc1-4674-91b6-9f5b8e76c36d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#/dev/sdb3 
UUID=9807ba5c-8230-4a57-aae4-3699560f97a3 /media/disco ext 3 relatime,errors=remount-ro 0 1



Pero esta vez, el mensaje que me da cuando lo intento montar es el siguiente:

no se puede encontrar media/Orfeo en etc/ftab o etc/mtab


¿Qué estoy haciendo mal...??? ¡Socorro!!!!   :confused:

---

### Post by pablo.s on 2009-05-07
Puedes probar instalando un gestor
llamado pysdm:

**[COLOR=DarkGreen]sudo apt-get install pysdm[/COLOR]**

Desde ahi puedes hacer modificaciones
a fstab pero de una forma sencilla.

---

### Post by cor_stellae on 2009-05-07
Hola Pablo:

Esa aplicación está genial, asumiendo que es la que me aparece ahora en Sistema > Dispositivos de almacenamiento.

Ahora ya puedo ver a Orfeo nuevamente en mi escritorio, el problema es que, todavía, no me deja copiarle archivos. Por lo menos ya regresé a dónde empecé, ¿ahora cómo lo pongo a funcionar?

---

### Post by pablo.s on 2009-05-07
Fijate si tiene permisos de escritura
para todos los usuarios, aparte de los
permisos de root.

---

### Post by cor_stellae on 2009-05-07
Odio preguntar algo tan básico, pero ¿dónde se administran los permisos? ¿Cómo puedo ver si los tiene o no?

---

### Post by cor_stellae on 2009-05-07
En todo caso, cuando solicito "propiedades", en el Tab "permisos" lo que dice es que los permisos para el disco no se han podido determinar... Ese es el mismo problema que presenta desde ayer...

---

### Post by pablo.s on 2009-05-07
La aplicación la estás ejecutando
como root? De no ser asi...

---

### Post by cor_stellae on 2009-05-07
Por supuesto que no... solamente la pido en Sistema...
¿Si la corro como root la misma aplicación me permitiría cambiarle los permisos al disco? Eh... voy a googlear pero... ¿cómo se pedía como root?

---

### Post by pablo.s on 2009-05-07
**[COLOR=DarkGreen]sudo pysdm[/COLOR]**

Cuando administrás el sistema
(los que saben no me peguen por
definirlo asi) usás obligatoriamente
la cuenta de root. Los usuarios no
pueden hacer cambios importantes
del sistema, solo cambios de su
cuenta y a veces ni siquiera eso.

---

### Post by cor_stellae on 2009-05-07
Bien... avanzo un poco más... ya descubrí una ventana que aparece cuando se le pide Asistente. Por lo que veo, ahí se le ponen todos los privilegios que le corresponden al disco. Aquí mi duda es que no sé cuáles debo poner... ya intenté varias combinaciones, ninguna sirve. Ya logré abrir el programa como superusuario, tampoco vi ninguna diferencia.

---

### Post by pablo.s on 2009-05-07
Como superusuario le puedes dar
permisos de lectura y escritura a
los usuarios comunes. Como usuario
común no te permite hacer eso.

---

### Post by cor_stellae on 2009-05-07
De acuerdo, Pablo, pero sigo con el mismo problema. En tanto no vea una casilla que diga literalmente "Dar permisos de lectura y escritura a todos los usuarios", que no la hay, no veo cómo le configuro esos permisos. Veo muchas opciones, pero esa no la veo... Incluso revisé las otras particiones, y tienen marcadas opciones como "Solo lectura" y aun así se puede hacer de todo con ellas.

Por otro lado, ya que seguimos en esto, ¿por qué ocurrió esto cuando formateé? ¿No debería haber formateado y dejar el disco listo para usar? ¿Qué debía marcar en el gparted para lograr eso?

---

### Post by cor_stellae on 2009-05-07
Je je je je!!!! Por fin lo solucioné... seguí googleando y me encontré por ahí que lo que debía hacer era meterme con sudo nautilus y, ahí, darle los privilegios...

yupiiii!!!!! Sí, era tan fácil como creía que era!!!!! :guitar:

---

### Post by pablo.s on 2009-05-07
> **cor_stellae said:**
> Por otro lado, ya que seguimos en esto, ¿por qué ocurrió esto cuando formateé? ¿No debería haber formateado y dejar el disco listo para usar? ¿Qué debía marcar en el gparted para lograr eso?

Cuando formateas un disco, le cambias
información (datos de particiones, longitud
de particiones, tablas, puntos de montaje, etc)
y Gparted es un excelente programa, pero como
todo programa, hace solo lo que uno le dice
que haga. Si tu le dices que haga una partición,
lo hace. Por eso se llaman programas: siguen
una secuencia de comandos (ordenes) al pie
de la letra. El tema de los permisos se maneja
en los archivos fstab y mtab. En fstab está
descripto cada disco con cada partición, que
tipo de sistema de archivos tiene, donde se
debe "montar" (este termino viene de la acción
de tomar una cinta magnetica y montarla sobre
un carrete para ser leida; ya casi no se utilizan),
si se "monta" automaticamente y si los usuarios
tienen permisos para escribir y leer o solamente
para escribir.
GNU/Linux está creado para ser un sistema
multi usuario. Hete aqui el porqué muchas cosas
no se realizan automaticamente. Hay usuarios
que con un comando erroneo o mal utilizado
pueden tirar abajo un sistema, por ende el usuario
administrador (root) solo puede ejecutar comandos
de configuración globales.

---

### Post by cor_stellae on 2009-05-07
Pablo, muchas gracias por la explicación. Lo tendré presente. A pesar de que me gustan más los sistemas Mac que, en esas cosas, son realmente sencillos, me alegra saber que Ubuntu impedirá que usuarios imprudentes lo manden a volar. Hay por aquí cerca un usuario de mi computadora que tiene prohibido usarla porque cada vez que la toca algo pasa. Hace unos días se lo permití porque "era solo por un ratito para ver algo en internet". Una semana después yo estaba borrando todo mi disco duro para librarlo del peor virus que he visto jamás y fue cuando decidí pasarme a Ubuntu... así que, aunque sea incómodo, aplaudo la medida. 

Pues muchas gracias y este foro podemos darlo por fin como SOLUCIONADO!!!!!!

---

### Post by ADICTOALMAXIMO on 2009-05-07
Te felicito pibe

---

### Post by josecuervo86 on 2009-05-07
> **ADICTOALMAXIMO said:**
> Te felicito pibe

Piba en todo caso ;)

---

### Post by cor_stellae on 2009-05-07
Gracias, chicos. Algún día dejaré de hacerles estas preguntas tan básicas, pero por ahora sigo aprendiendo y todavía me quedan unos cuantos problemitas técnicos por resolver.

---

