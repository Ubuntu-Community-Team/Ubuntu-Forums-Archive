---
title: "Problema grave al inicio"
date: 2009-09-23
forum: Hardware
---

### Post by ddz0703 on 2009-09-23
Bueno tube un reinicio accidental y cuando reinicio me aparecio esto

[IMG]http://www.uploadfilesystem.com/thumbs/09/09/24/tn_0zM61021.jpg[/IMG]


Este es el link de la imagen en tamaño real

[http://a.imagehost.org/dl/97bf5e1b9527c55292d9e607770e1b46/0709/Syd_0033.jpg](http://a.imagehost.org/dl/97bf5e1b9527c55292d9e607770e1b46/0709/Syd_0033.jpg)


La calidad de la imagen es mala, pero se puede leer, y es muy complicado para transcribirlo aca:(
Ayuda por favor, ahora estoy en el lado oscuro:(:(:(

---

### Post by josecuervo86 on 2009-09-23
El enlace no anda (en realidad anda, pero te aparece un cartel por el hotlinking). Si podes subila aca: [http://imagehost.org](http://imagehost.org)

---

### Post by Fak89 on 2009-09-23
> **josecuervo86 said:**
> El enlace no anda (en realidad anda, pero te aparece un cartel por el hotlinking). Si podes subila aca: [http://imagehost.org](http://imagehost.org)

Exactamente, subí la imagen nuevamente cuando puedas..

---

### Post by ddz0703 on 2009-09-23
Listo, ahi subi la imagen en [http://imagehost.org](http://imagehost.org), avisen si no funciona, es la primera vez que subo imagenes a internet, nunca lo hice, puse en google "servidores de imagenes" y la subi en la primera que salio

---

### Post by josecuervo86 on 2009-09-23
> **ddz0703 said:**
> Listo, ahi subi la imagen en [http://imagehost.org](http://imagehost.org), avisen si no funciona, es la primera vez que subo imagenes a internet, nunca lo hice, puse en google "servidores de imagenes" y la subi en la primera que salio

Claro, pero cuando la subis, te pasa un link a la imagen. Pasanos ese link

---

### Post by ddz0703 on 2009-09-23
creo que ya esta solucionada la imagen

---

### Post by Fak89 on 2009-09-23
Tenés idea que provoco el accidente?

---

### Post by josecuervo86 on 2009-09-23
> **ddz0703 said:**
> creo que ya esta solucionada la imagen

El link que pasaste es a la pagina para subir las fotos, pero no a la foto en si. Luego de subirla, la pagina te da un par de opciones para compartirla, elegí la ultima, que es link liso y llano a la imagen.

O yo entendi mal y ya se soluciono el asunto?

---

### Post by Fak89 on 2009-09-23
> **josecuervo86 said:**
> El link que pasaste es a la pagina para subir las fotos, pero no a la foto en si. Luego de subirla, la pagina te da un par de opciones para compartirla, elegí la ultima, que es link liso y llano a la imagen.

O yo entendi mal y ya se soluciono el asunto?

[http://a.imagehost.org/dl/97bf5e1b95...9/Syd_0033.jpg]("http://a.imagehost.org/dl/97bf5e1b9527c55292d9e607770e1b46/0709/Syd_0033.jpg")

---

### Post by ddz0703 on 2009-09-23
No recuerdo bien la tarea que estaba haciando, pero era algo inseguro, creo que estaba jugando con los valores del firefox, de todas maneras, no creo que sea el problema. De momento la pc se tildo completamente, asi como pasaba en windows 98 y tube reiniciar desde el boton de reinicio, cuando quize iniciar ubuntu, salio eso

---

### Post by emiliano_raso on 2009-09-25
Si bien no tenemos la imagen, mas o menos la disposicion de los caracteres me da a entender que se te rompió el GDM y ahi te aparece para loguearte por consola.

Subí bien la imagen. Aprovechá fotolog, facebook o alguna de esas cosas.

---

### Post by ddz0703 on 2009-09-29
[B] Hola muchachos, mi problema fue asi, tube un corte de energia repentino y cuando reinicie la maquina me aparecio esto:



boot from (hd0,0) ext4 27z2b832-938-4eb0-z069-71cdda3ffdfa
starting up...
loading, please wait...
19-0 records in    
19+0 record out
kinit: name_to_dv_t(/dev/disk/by-uuid/b84e8646-c04d-4d37-8db3-17901a56574d) = dev(8.5)
kinit: trying to resume from /dev/disk/by-uuid/b84e8646-c04d-4d37-8db3-17901a56574d
kinit: no resume image, doing normal boot...
mount: mounting /dev/disk/by-uuid27a2b832-928d-4eb0-a069-71cdda3ffdfa on /root
failed: invalid argument
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
target filesystem doesn`t have /sbin/init.
No init found. Try passin init = bootarg


BusyBox v1.10.2 (ubuntu 1:1.10.2-2ubuntu?) built-in shell (ash)
Enter "help" for a list of built-i commands.

(inittranfs)



Se habran dado cuenta de que tengo ubuntu 9.04, pero mi disco en realidad es sata y ahi dice "hd0"

Ayuda por favor, si monto el live no puedo acceder a la particion, me muestra un error, pero es solo en esa, en las demas particiones(ext y ntfs) puedo acceder tranquilamente.
No quiero formatear esa particion, esta mi vida ahi t.t
Gracias por la ayuda
[/B]

---

### Post by faktorqm on 2009-09-30
linux no suele colgarse como lo hacia el windows 98, deberias informarte mejor antes de decir cualquier cosa.

con el live cd booteado, abri una consola y pone

sudo fdisk -l

y te da un listado de todas las particiones de cada disco. Busca la que necesites vos y despues haces

sudo mkdir -p /media/temporal

sudo mount /dev/XXX /media/temporal

donde XXX tiene la forma, hd0, sd0, etc. Si eso no te anda, postea el error.

---

### Post by ddz0703 on 2009-09-30
Que queres que te diga?
Se tildo asi plenamente, apretaba la tecla tab y la luz del teclado no reaccionaba, y el mouse tampoco, se tildo, como win 98. Es linux, lo se, esta hecho con mas responsabilidad, pero no es perfecto, sabelo, y puede ser vulnerable como cualquier otra cosa.
Gracias por responder, ahora pruevo tu solucion

---

### Post by faktorqm on 2009-09-30
se te colgo el hardware, no el linux!!

---

### Post by emiliano_raso on 2009-10-01
> **ddz0703 said:**
> Que queres que te diga?
Se tildo asi plenamente, apretaba la tecla tab y la luz del teclado no reaccionaba, y el mouse tampoco, se tildo, como win 98. Es linux, lo se, esta hecho con mas responsabilidad, pero no es perfecto, sabelo, y puede ser vulnerable como cualquier otra cosa.
Gracias por responder, ahora pruevo tu solucion

Ah flaco... XD Sos un EPIC FAIL.
Creo que los limites de la tolerancia con los nuevos/ignorantes terminan cuando ofenden o cuando hablan si conocer de forma incorrecta.
Y vos ofendiste, hablaste de forma incorrecta, sos nuevo e ignorante.

Volvé a Windows si es Linux el problema. Al menos en Windows podes jugar mas jueguitos que en Linux.
Sabias que no podes jugar ningun jueguito en Linux? Ninguno.
Ademas no podes usar NINGUN programa de los que conoces.

Te aviso por las dudas.
Tal vez cuando te des cuenta que ejecutas un .exe y no funciona en Ubuntu te metes en un foro de NVIDIA y decis "Sus placas de video no funcionan! Ejecuté un .exe de un jueguito en Ubuntu y no anda!"

---

### Post by guillermolisi on 2009-10-01
> **emiliano_raso said:**
> Ah flaco... XD Sos un EPIC FAIL.
Creo que los limites de la tolerancia con los nuevos/ignorantes terminan cuando ofenden o cuando hablan si conocer de forma incorrecta.
Y vos ofendiste, hablaste de forma incorrecta, sos nuevo e ignorante.

Volvé a Windows si es Linux el problema. Al menos en Windows podes jugar mas jueguitos que en Linux.
Sabias que no podes jugar ningun jueguito en Linux? Ninguno.
Ademas no podes usar NINGUN programa de los que conoces.

Te aviso por las dudas.
Tal vez cuando te des cuenta que ejecutas un .exe y no funciona en Ubuntu te metes en un foro de NVIDIA y decis "Sus placas de video no funcionan! Ejecuté un .exe de un jueguito en Ubuntu y no anda!"
Tratemos de seguir focalizados en entender cual es el problema para encontrar la solucion.

Si alguien se equivoca al dar una opinion, pedirle sus fundamentos para poder indicarle cuales y por que estan errados. Es la mejor forma de aprendern y creo que todos estamos en esa postura: la de aprender sobre Ubuntu, la de aprender a aprender y en la de ayudar.

Si quien abrio el thread emite comentarios de corte flamewar, indicarselo amablemente muestra el camino correcto y le dice que el flame termina en un callejon sin salida.

Les recuerdo que el cumplimiento del CoC alncaza tanto a los que recien ingresan al foro como a los de mayor antigüedad.

Si alguien quiere saber de que se trata o repasar su letra, en los sticky threads de la seccion Normal Threads hay suficiente material al respecto.

Dicho esto, espero no tener que intervenir mas energicamente sobre este thread.

---

### Post by ddz0703 on 2009-10-01
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       En algunos casos se encuentra información en syslog, pruebe
   dmesg | tail   o algo parecido

ese es el error que me muestra cuando pruevo la solucion de facktorqm. Ahora voy a tratar de reinstalar  grub.
Todo bien gente, todo bien. Se enojan por que digo que linux se colgo, que queres que haga? Que queres que te diga? se colgo y se colgo, sera el soft, sera el hard, se colgo. Emilia razo me trata de ********, hace quince años que estoy todo el dia sentado frente a la pc, de los cuales esos 15 años, en 9 tenia una particion que tenia mi hermano, con red hat, cuando todavia red hat se llamaba red hat. pero hace nueve meses que decidi empezar a usar linux por cuenta mia. Y la eleccion fue ubuntu, por que TODOS hablan de lo grandioso que es ubuntu, cosa que no niego, se verdad, se la re banca, pero pero nadie nace sabiendo, y para ser usuario de GNULinux tenes que tener conocimientos avanzados, eso lo sabemos todos. Empeze con ubuntu, y estube tres meses, TRES MESES, para instalar la placa de video
Como haria yo que recien habia empezado que para instalarlo tenia que cerrar el xserver e instalarlo desde la terminal, por linea de comando
Chicos no se enojen por que sigo que sus amado linux se colgo, paso y paso, se colgo y me fastidio el arranque. Pregunto en los tan conocidos foros de ubuntu con los slogan de  "ubuntu, software libre, ubuntu para todos los seres humanos, ubuntu somos todos amigos" y me tratan de ********

---

### Post by guillermolisi on 2009-10-01
> **ddz0703 said:**
> mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       En algunos casos se encuentra información en syslog, pruebe
   dmesg | tail   o algo parecido

ese es el error que me muestra cuando pruevo la solucion de facktorqm. Ahora voy a tratar de reinstalar  grub.
Todo bien gente, todo bien. Se enojan por que digo que linux se colgo, que queres que haga? Que queres que te diga? se colgo y se colgo, sera el soft, sera el hard, se colgo. Emilia razo me trata de ********, hace quince años que estoy todo el dia sentado frente a la pc, de los cuales esos 15 años, en 9 tenia una particion que tenia mi hermano, con red hat, cuando todavia red hat se llamaba red hat. pero hace nueve meses que decidi empezar a usar linux por cuenta mia. Y la eleccion fue ubuntu, por que TODOS hablan de lo grandioso que es ubuntu, cosa que no niego, se verdad, se la re banca, pero pero nadie nace sabiendo, y para ser usuario de GNULinux tenes que tener conocimientos avanzados, eso lo sabemos todos. Empeze con ubuntu, y estube tres meses, TRES MESES, para instalar la placa de video
Como haria yo que recien habia empezado que para instalarlo tenia que cerrar el xserver e instalarlo desde la terminal, por linea de comando
Chicos no se enojen por que sigo que sus amado linux se colgo, paso y paso, se colgo y me fastidio el arranque. Pregunto en los tan conocidos foros de ubuntu con los slogan de  "ubuntu, software libre, ubuntu para todos los seres humanos, ubuntu somos todos amigos" y me tratan de ********
Esta bueno tu comentario despues del mio pidiendo que se focalicen en la solucion al problema para no desvirtuar el thread.

Sos el interesado en una solucion y continuas enganchado con el desvio.

Una mas y cierro el thread.

---

### Post by ddz0703 on 2009-10-01
reinstale grub desde un live pero no se soluciono, sigue mostrando las mismas lineas de errores

---

### Post by ddz0703 on 2009-10-01
Toy en el horno y voy a tener que optar por la mediocreo solucion de formatear y volver a instalar.

---

### Post by faktorqm on 2009-10-01
no, primero tenes que salvar los datos que tenias ahi.

te tiro un par que encontre en la web

[http://alt-tab.com.ar/recuperar-sectores-defectuosos/](http://alt-tab.com.ar/recuperar-sectores-defectuosos/)
[http://www.ubuntu-es.org/index.php?q=node/101705](http://www.ubuntu-es.org/index.php?q=node/101705)

salu2!

---

### Post by ddz0703 on 2009-10-01
Bueno muchachos ya se soluciono todo!!!
Fue de pura casualidad, justamente hoy dejo de funcionar mi lectora de dvd, toda la bronca. Entonces recien, hace unos 40 minutos, me baje el unetbooting y me baje la iso de ubuntu 9.04 pero de 64 bits, grave la iso en un pendrive y lo configure para el arranque, monte el live usb y abri el gparted, y puse "check" en la particion de mi ubuntu, ya lo habia hecho varias veces y no habia funcionado, pero con el live cd, no usb. y cargo un par de cositas y despues oh sorpresa, me dijo que no pudo terminar de solucionar todos los errores y que debia solucionar, antes me decia que por un error en la particion no podia ni acceder a ella.
Reinicio ubuntu y llego a la parte de la consola y no me aparecio lo mismo de antes, me decia que el sistema tenia errores y que tenia que tirar un fsck manual, lo hice y despues de varios Fix salio dijo que ya estaba todo cocinado y que reinicie, "reboot" y cuado quizo bootear por completo ubuntu me dijo que estaba dañado el entorno grafico, y no podia iniciar xserver, entonces desde la terminal instale mi placa de video otra vez y salio andando!!!!
Y ahora estoy aca con mi ubuntu con compiz y mis favoritos y todos mis historialess y archivos personales.
Lo unico que me habia hecho la ilucion de que instalaria la version de 64 bits para usar todo el micro XD
Gracias a todos los que respondieron y perdon por las discuciones.
Ya pueden cerrar el hilo

---

### Post by emiliano_raso on 2009-10-02
No me quedó muy claro al final si tenes el disco rigido hecho ****** o no xD

Como sea si podes aclaralo.


PD: Guille, marque como [SOLVED] nomas ^^

---

### Post by guillermolisi on 2009-10-02
Lo que estaba molestando era la unidad optica que no funcionaba bien.
El disco tenia que ser verificado con fsck dado que el sistema se cerro sin shutdown y asi recomponer la integridad del file system. Esto como producto del corte de energia repentino.

Segui con 32 bits que tambien vas a usar toda la capacidad del procesador y toda la memoria que tenga el sistema.

Lee sobre los sistema de 64 bits porque, como todo, tiene cosas buenas y otras no tanto, depende mucho de cada caso particular.

---

### Post by ddz0703 on 2009-10-02
Si, se que usar 64 o 32 tiene sus ventajas y desventajas, y si me informe, lo que averigue fue que ubuntu usa mucho mejor el 64 bits, no como en win que por mas que sea de 64 bits todas las aplicaciones deben ser de 64 bits para que tenga buen rendimiento.
Recupere el disco y anda bien, sigo con mi disco y mis particiones y mi ubuntu con los miles de paquetes que habia bajado. No perdi nada y salio andando bien.

---

### Post by Mauro22 on 2009-10-02
> **ddz0703 said:**
> 
Recupere el disco y anda bien, sigo con mi disco y mis particiones y mi ubuntu con los miles de paquetes que habia bajado. No perdi nada y salio andando bien.

Un buen susto para empezar a rezarle al Dios del Backup :lolflag:

Nadie esta exento de la mala suerte!

---

