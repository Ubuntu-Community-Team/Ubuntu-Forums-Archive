---
title: "No bootea"
date: 2012-10-21
forum: Hardware
---

### Post by Vero1 on 2012-10-21
hola todos. Tengo un problema que no sé como resolver. Tras hacer fsck de una partición con problemas(raíz) lo hice con un LiveCD, al reiniciar me dice: mountall: error while loading shared libraries /lib/liply-boot-client.so 2: file too short. En una palabra. No bootea. Alguien puede ayudar?

Estoy escribiendo desde Win2.

Gracias de antemano.

saludos:(

---

### Post by guillermolisi on 2012-10-21
Vero

Resolviste el problema del disco rigido ?

Si el disco continua con problemas vas a tener un camino largo y sinuoso con tu instalacion.

Que opciones utilizaste cuando corriste FSCK ?
En que operaciones tuviste que intervenir durante su corrida ?

Suponiendo que el problema con este archivo se solucione, como sabes que no hay otros N archivos con problemas similares ?

Con esto estoy queriendo significar que me parece que estas intentando resucitar un file system en agonia y, salvo que podamos determinar que el disco esta estable, que los bloques defectuosos se han marcado adecuadamente, que la cantidad de bloques defectuosos no se ha incrementado, me parece mejor hacer una copia de resguardo de tu /home antes de seguir adelante.

---

### Post by Vero1 on 2012-10-22
Hola guillermolisi,

Gracias de nuevo por contestar.

La otra vez había testeado la superficie del disco y no indicaba problemas.
Pasé fsck porque me salía una indicación de problemas con el driver del disco que indicaba la partición /.
Por lo tanto decidí correr, desde LiveCD fsck -cfv de esa partición o sea sdb2(antes desmonté esa partición)
Salieron un montón de errores de diversos tipos y preguntaba cada vez si arreglaba, borraba,reescribía, etc., preguntando si? a lo que yo contestaba que si. Otras veces directamente ponía que si.
Durante el escaneo no toqué nada.
Cuando terminó, puso que iba a escanear de nuevo todo y lo hizo.
El informe que salió esta vez parecía que estaba todo ok, salvo que en un lugar donde en las demás particiones decía 0/0/0, decía 2/2/2. Creo que son los errores.
Cuando reinicié me salió pantalla negra con la inscripción que menciono en el post anterior.
Lo curioso es que puse un CD que tenía de Rescatux y ahí montó las particiones sin problemas.
Con el Live CD no se puede hacer nada con respecto a los shared libraries que faltan y que no permiten que se monten las particiones?
Ah, con respecto a los drivers del que habla, no habla del disco en general sino de particiones o bien / o tambien en otra ocasión de /temp.
Tambien hice fsck -cfv de sdb1(boot) y sdb3(home) que no tenían problemas.

Te agradezco mucho tu ayuda.

saludos

---

### Post by hictio on 2012-10-22
Vero1, mi consejo, no inviertas más tiempo en este disco.
Poné uno nuevo y continuá adelante con tu vida.

---

### Post by Vero1 on 2012-10-22
Hola hictio,

Lo que pasa es que no creo que sea el disco el problema, porque como le dije a guillermolisi, no presenta problemas en si.
Puede tener problemas si, la mother, pero en estos momentos no dispongo de dinero como para cambiarla.
Lo mas urgente para mi ahora, es que alguien me indique qué hacer para recuperar el booteo o sea como se pueden recuperar esas librerías compartidas que faltan.
Ese trabajo se lo debo a fsck...
Reitero la pregunta: con el Live CD se puede hacer algo?

saludos

p.d.
en estos momentos estoy escribiendo desde Hotmail, así que si envían respuestas a mi dirección de siempre, no lo podré ver.
Por ese motivo veo directamente el Foro.

---

### Post by guillermolisi on 2012-10-23
Vero

Si en algun momento fsck/badblocks encontraron sectores dañados en el disco, hay algo que no esta funcionando bien. Sea el disco, sea su controladora.

Si es esta ultima, con agregar una placa PCI SATA o IDE, segun sea la tecnologia del disco que estas usando, posiblemente no tengas que cambiar toda la motherboard.

Mas alla de todo esto, para copiar los archivos que te faltan hay que hacerlo desde un LiveCD/LiveUSB y utilizar chroot (con el user root, obviamente).

No es nada de otro mundo pero hay que estar tranquilo, ser metodico y (posiblemente si son muchos los archivos que falten) tener mucha paciencia (y el tiempo suficiente que demande la tarea). Ademas, no solo puede ser que este faltando algun que otro archivo (fisicamente hablando), tambien podes tener links rotos (que en definitiva se muestran como que falta el archivo, tambien).

Cuando copias los archivos hay que prestar especial cuidado a sus permisos, owner y group, ya que de ser incorrectos puede que no funcione bien cuando inicies con el sistema recuperado.

---

### Post by EnriqueK on 2012-10-23
Probá con arrancar usando el Super Grub2 Disk , si arranca, usá este comando
sudo grub-mkconfig && sudo grub-install /dev/sda && sudo update-grub
El Super Grub2 Disk pesa muy poco, de orden de 2 Mb , de todas maneras vale la pena gastarse un Cd por que es muy útil
[http://www.supergrubdisk.org/category/download/supergrub2diskdownload/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/)

---

### Post by Vero1 on 2012-10-23
Hola EnriqueK,

No es problema del Grub ya que la pantalla del Grub sale.
El problema está en que al querer arrancar el SO sale el siguiente error: 
mountall: error while loading shared libraries /lib/libphy-boot-client.so.2.

saludos

---

### Post by Vero1 on 2012-10-23
> **guillermolisi said:**
> Vero

Si en algun momento fsck/badblocks encontraron sectores dañados en el disco, hay algo que no esta funcionando bien. Sea el disco, sea su controladora.

Si es esta ultima, con agregar una placa PCI SATA o IDE, segun sea la tecnologia del disco que estas usando, posiblemente no tengas que cambiar toda la motherboard.

Mas alla de todo esto, para copiar los archivos que te faltan hay que hacerlo desde un LiveCD/LiveUSB y utilizar chroot (con el user root, obviamente).

No es nada de otro mundo pero hay que estar tranquilo, ser metodico y (posiblemente si son muchos los archivos que falten) tener mucha paciencia (y el tiempo suficiente que demande la tarea). Ademas, no solo puede ser que este faltando algun que otro archivo (fisicamente hablando), tambien podes tener links rotos (que en definitiva se muestran como que falta el archivo, tambien).

Cuando copias los archivos hay que prestar especial cuidado a sus permisos, owner y group, ya que de ser incorrectos puede que no funcione bien cuando inicies con el sistema recuperado.

Pero yo creía que las controladoras se podían actualizar si fallaban, inclusive estuve buscando las controladoras de mi disco que es Western Digital.
Ahora, con lo que me decís, quedo algo sorprendida.

saludos

---

### Post by guillermolisi on 2012-10-23
Desde hace un tiempo para aqui, las controladoras de discos rigidos vienen integradas en la motherboard. ATA, PATA, SATA e inclusive algunas SCSI con limitadas prestaciones (economicas).

Salvo que la motherboard de tu maquina sea bastante antigua, digamos anterior al 2002, no creo que puedas cambiarla sin cambiar la motherboard. Por eso lo que dije respecto que agregar una placa IDE/SATA (lo que corresponda a la tecnologia de los discos que estes usando).

Ojo que una cosa es el hardware controlador y otra, complementaria, es el driver (software que se complementa con el hardware para operar un periferico).

---

### Post by Vero1 on 2012-10-27
Hola a todos,

Es para comentarles que me he cansado de los problemas, así que opté por cambiar mi disco, cosa que ya hice ayer.

Esta vez es un Disco SATA2(IDE no se consigue) y con un adaptador Molex-SATA
se solucionó, ya que el mother tiene un enchufe para SATA,

Ya reinstalé el SO, que esta vez, fue muchísimo más rápido que las veces anteriores con el otro disco.

Tenían razón. Era el disco :)

Muchas gracias por la ayuda recibida y será hasta cualquier momento.

---

### Post by guillermolisi on 2012-10-27
Que lo disfrutes !!!

---

### Post by Vero1 on 2012-10-28
Gracias:):)

---

