---
title: "Me presento (con un problemón)"
date: 2008-09-30
forum: Hardware
---

### Post by andresjb on 2008-09-30
Hola gente!
Me llamo Andrés y me acabo de registrar al foro. Hace un par de días me decidí completamente a dejar Windows por que me hartó... :mad:
Lo único que me detenía a cambiarme a Ubuntu eran los juegos, pero ví todas las alternativas que hay y YA me cambié Ubuntu, pero... acá viene el problema... :(

Primero les describo mi PC y después les cuento cuál es el problema: Athlon XP 2000+ (1.6 GHZ), 512MB de RAM (en dos módulos), GeForce FX5200, un disco de 40 GB con Windows XP (en NTFS), otro disco de 80GB con una partición NTFS para datos y el resto (37GB aproximadamente) sin formato. De esa manera estaba la maquina antes de instalar Ubuntu.

Me bajé (de la página oficial) y me grabé la imagen del Ubuntu 8.04.1.
Mi problema es que el instalador se me trabó varias veces (pero al fin lo pude instalar bien), y cuando entro en Ubuntu después de un rato se traba completamente y no responde ni el mouse, ni el teclado y se queda la imagen congelada. Ese rato puede ser 30 segundos, 1 minuto, 3 minutos, pero no más de eso. A veces se me traba después de salir de la pantalla de login sin siquiera poder mostrar el escritorio... :(

Lo intenté instalar más o menos 5 o 6 veces y siempre se me trababa el instalador en partes diferentes y lo único que podía hacer era resetear. Después de varios intentos lo pude instalar bien sin ningún problema extra.
Ahora cada vez que entro a Ubuntu se me traba tarde o temprano, no importa lo que haga. Se me traba sin permitirme hacer nada de nada, o a veces puedo abrir de todo al mismo tiempo y no pasa nada, pero después de un corto ratito se me traba.

Ya le pasé el Memtest que viene en el CD y me da perfecto, comprobé si el CD estaba bien y no hay ningún problema. Cuando inicia Ubuntu no bajo ninguna actualización. Probé sacando la placa de video (la GeForce) y activando la que tengo onboard y me sigue haciendo lo mismo.
Formateé el disco de nuevo y lo pude volver a instalar y probé actualizando los drivers de la Geforce originales y sigue el mismo problema.

Ya no se me ocurre que más probar, busqué con google todo el día y de las 1001 maneras posibles que se me ocurrieron, probé todo lo que decían pero no pude arreglarlo.

Perdonen si soy pesado con éstas consultas, pero estoy desesperado... Por favor si me pueden ayudar se lo voy a agradecer eternamente.
Como es la primera vez que utilizo Ubuntu no se casi nada, así que tengan en cuenta eso... :D

Desde ya muchísimas gracias por cualquier ayuda que me puedan dar.

---

### Post by Mauro22 on 2008-09-30
Hola!!


Podes intentar desinstalar el powernowd que a mi (tambien AMD) me lo colgaba...


Vas a Aplicaciones -> Accesorios -> Terminal y pones:

sudo apt-get remove powernowd

Das enter, pones tu contraseña y listo. Fiajte si con eso se va... 

Cuando se cuelga, tambien lo hace el teclado??

Si se te cuelga otra vez, hace control + alt + F1, si se pasa a modo texto, lo que se te cuelga es el modo grafico y no la PC...



Comenta cualquier avance que tengas... Suerte!

---

### Post by andresjb on 2008-09-30
Gracias por responder Mauro!

Ahí probé lo que me dijiste pero hubo complicaciones.

Pasó ésto:
Reinicié, entré en Ubuntu y se me quedo trabado en la pantalla de carga (no se movía la barra de progreso). Después reseteé y volví a arrancar. Llegué a escribir mi contraseña y tocar enter, después de eso me volvió a pasar lo que me pasó antes, se me quedo trabado con la pantalla del color marrón clarito y la flechita del mouse nada más.

Volví a resetear. Inicié de nuevo y se me volvió a trabar en la pantalla de carga, pero ésta vez toqué ctrl+alt+f1 y empezé a ver mensajes de todo tipo. Lo que pude anotar fué ésto:
ata2.01: revalidation failed (errno=-5)
ata1.00: revalidation failed (errno=-5)
buffer I/O error on device..................
EXT3-fs error (device sdb2): ext3_find_entry..........

Esos mensajes eran más largos pero es lo que pude anotar. Al parecer por los mensajes el problema está en el sistema de archivos.

Después de ésto la volví a resetear y pude entrar. Fuí lo más rápido que pude, abrí la terminal, escribí lo que me dijiste, cuando me pide si quiero continuar le digo que sí y me pone "Leyendo de la base de datos" y se traba. La volví a resetear, hice lo mismo y se me volvió a trabar en la misma parte. Cada vez que se me trabó dentro de Ubuntu no podía hacer ctrl+alt+f1.

Si el problema es el sistema de archivos me desconcierta porque apenas instalado ya me hace éstos problemas.

Bueno, muchísimas gracias por la ayuda Mauro! Voy a seguir buscando en Google a ver que puedo encontrar.

Saludos

---

### Post by WanderingKnight on 2008-09-30
> 
ata2.01: revalidation failed (errno=-5)
ata1.00: revalidation failed (errno=-5)
buffer I/O error on device..................

Eso es un error de I/O al disco, y más que error de soft parece de hard... (o sea, en mi vida he escuchado que un filesystem falle de esta forma, y menos ext3).

Siempre instalaste Ubuntu en el disco nuevo? Tenés experiencia previa con ese disco?

PD: Es SATA o IDE? [Acá](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635) parece haber un problema muy similar al tuyo, pero es particular de un modelo de laptops Dell (Inspiron 530). Lo que sugieren ahí para ver si se arregla es agregar

```
irqpoll all_generic_ide
```

a la línea de GRUB que llama al kernel (apretá E, agregá eso, y después apretá B para bootear).

---

### Post by Mauro22 on 2008-09-30
Por lo que pones ahi, parece un error de disco o de formato...


1) El live cd te corre bien?

2) Con que formato creaste las particiones? ext2, etx3, etc

3) Al parecer lo tenes instalado en sdb2 (en español, disco dos, particion 2), hiciste (o viste) alguna vez que se haga un chkdisk ?? Podes hacerlo desde el livecd con el comando: sudo fsck sdb2 (pero espera confirmacion de alguien mas porque no estoy seguro si esto es correcto)

4) Si entras en ""recovery mode"" y luego elegis la opcion "root promt" y en la consola pones startx, hace lo mismo??




Saludos!

---

### Post by andresjb on 2008-09-30
Volví :-)

El disco donde instalé Ubuntu es un disco IDE nuevo comprado hace menos de un año (por febrero más o menos). Desde que lo compré lo tuve en NTFS cómo partición lógica para guardar archivos para Windows. Antes de instalar Ubuntu utilizé el Partition Magic 8 desde Windows, redimensioné la partición a la mitad del disco y dejé la otra mitad sin formato que es donde tengo instalado Ubuntu ahora. El formato dejé que se lo dé el mismo instalador de Ubuntu que lo hizo en ext3.
Probé lo de "irqpoll all_generic_ide" y me tira un mensaje:
kernel panic - not syncing: attempted to kill the idle task!
y se queda ahí.

También probé otra opción que encontré que es agregarle a la misma línea del kernel noapic y acpi=off pero se me trabó cuando estaba reproduciendo el sonido de inicio después del login.

Lo del chkdsk no lo se hacer, pero me voy a fijar cómo se hace.
También voy a probar si el live cd anda bien.

Y por último, entré en recovery mode, en root prompt, escribí startx y anduvo lo más bien. Estuve probandola por 10 minutos más o menos y no se trabó (estaba en inglés). Abrí un montón de aplicaciones, abrí un video, activé los efectos gráficos en las ventanas, puse 4 escritorios virtuales y anduvo lo más bien. Pero venía bien hasta que quise salir... fuí a system->quit y no hacía nada pero el mouse y el teclado respondían lo más bien. Pude tocar ctrl+alt+f1 y abrió la terminal, toque ctrl+alt+backspace y cambió entre las ventanas y la terminal, pero no se apagó y otra vez tuve que resetear...

Muchas gracias, ahora voy a seguir probando más, apenas pruebe les cuento.

Saludos.

---

### Post by feche_mza on 2008-09-30
> **andresjb said:**
> 

Volví a resetear. Inicié de nuevo y se me volvió a trabar en la pantalla de carga, pero ésta vez toqué ctrl+alt+f1 y empezé a ver mensajes de todo tipo. Lo que pude anotar fué ésto:
ata2.01: revalidation failed (errno=-5)
ata1.00: revalidation failed (errno=-5)
buffer I/O error on device..................
EXT3-fs error (device sdb2): ext3_find_entry..........

Esos mensajes eran más largos pero es lo que pude anotar. Al parecer por los mensajes el problema está en el sistema de archivos.Si el problema es el sistema de archivos me desconcierta porque apenas instalado ya me hace éstos problemas.

***de que forma lo instalaste, las particiones las editaste manualmente o usaste la totalidad del disco?, si lo hiciste manualmente para dejar XP, puede que te ayas olvidado de dejar un espacio del disco para la memoria de intercambio, para eso tenes que crear otra partición con formato swap,todas las distribuciones de Linux  necesitan una partición de este tipo para cargar los programas y no saturar la memoria RAM, y tenes que darle un tamaño de mas o menos el doble de la RAM que tengas ponele vos que tenes 512 tenes que darle mas o menos 1 GB, si tuvieras un giga tenes que darle dos y así y así , la falta de esta partición puede ser el origen de los problemas esos, y al no poder leer bien el disco te puede generar los cuelgues que mencionás  ***

---

### Post by andresjb on 2008-09-30
> **feche_mza said:**
> ***de que forma lo instalaste, las particiones las editaste manualmente o usaste la totalidad del disco?, si lo hiciste manualmente para dejar XP, puede que te ayas olvidado de dejar un espacio del disco para la memoria de intercambio, para eso tenes que crear otra partición con formato swap,todas las distribuciones de Linux  necesitan una partición de este tipo para cargar los programas y no saturar la memoria RAM, y tenes que darle un tamaño de mas o menos el doble de la RAM que tengas ponele vos que tenes 512 tenes que darle mas o menos 1 GB, si tuvieras un giga tenes que darle dos y así y así , la falta de esta partición puede ser el origen de los problemas esos, y al no poder leer bien el disco te puede generar los cuelgues que mencionás  ***

Acá te dejo la imágen del partition magic de como tengo el disco:
[IMG]http://i471.photobucket.com/albums/rr76/andresjb/partmagic.jpg[/IMG]

La swap está creada y tiene un poco más del doble que la memoria RAM, pero hay algo que me llama la atención ahora... que el Partition magic me marca la particion que está en ext3 como si estuviera llena... y no tiene que estarlo porque lo único que hice fuí instalar Ubuntu.
Como dije antes, el disco antes estaba como una única partición NTFS lógica y la redimensioné para que sea la mitad del disco una partición NTFS lógica y la otra mitad sin asignar para que Ubuntu la formatee solo. Ubuntu creó la swap y la ext3 solo.

Gracias por la ayuda. Voy a probar el live cd y vuelvo. :D




EDITO:
Estoy con el live cd y me anda bien, le probé un montón de cosas, abrí de todo y anda de diez. El problema seguramente debe estar con el disco...

---

### Post by faktorqm on 2008-10-01
hola, yo tuve muchos problemas con el partition magic, por que aparentemente hace lo que quiere con la tabla de particiones, incluso formatié un disco con una sola particion sólo para ntfs y el xp me tiraba pantalla azul con el ntfs.sys, asi que imaginate!
La solucion que implemente yo, es agarar el hiren's boot cd, ponerle el acronis disk director, hacé las particiones con ese programa, que es una masa y anda mil veces mejor que el partition magic. Reinicias y reinstala todo, y ya no deberias tener problemas.
Si seguis teniendo problemas, lo mejor es hacer back-up de tus cosas, volar todas las particiones con el acronis, y armar de vuelta todas las particiones con sus sistemas de archivos. Cualquier cosa postea. salu2!

---

### Post by andresjb on 2008-10-01
Gracias faktorqm por la respuesta.

Ya estoy tomando en consideración conseguirme una grabadora de DVD o un disco para hacer una copia de mis carpetas y arrancar desde cero. Hoy volví a formatear la partición, probé otras cosas, lo reinstalé sin problemas pero cuando inicié se me trabó al ratito.
Ah, me olvidaba... también se me trabó una vez en la pantalla de carga del instalador, no me sale una.

Bueno, voy a seguir viendo que puedo hacer porque quiero usar Ubuntu en ves de uindous.
Me tengo que ir a la facultad (clases de cobol :'(), saludos!

---

### Post by faktorqm on 2008-10-01
Ok, mas o menos segui un esquema parecido a este para rehacer las particiones:

primera particion - ext 3 - 15 gb (si no instalas juegos 10gb) - ubuntu /
segunda particion - ext 3 - tus datos (64 gb aprox) - ubuntu /home
tercera particion - swap - (aprox el doble de tu memoria ram) - intercambio ubuntu

en todos los casos, deben ser primarias las particiones, y la primera tener la marca de booteo, las demas no. Luego, para acceder a tus datos personales desde windows, podes instalar el driver ext3 y te lee la particion del linux como f: por ejemplo. ([http://www.fs-driver.org/](http://www.fs-driver.org/))
Salu2!

---

### Post by andresjb on 2008-10-01
Gracias otra vez por la respuesta!
Estoy siendo re pesado... jaja.

Capaz que ya sé cual es el problema. El partition magic me marca la swap como una partición lógica y vos me decís que tiene que ser primaria.
Mañana al mediodía intento cambiarla y veo si anda.

Saludos.

---

### Post by Mauro22 on 2008-10-01
Con swap o sin swap deberia arrancar igual y con 512mb de ram al principio no deberias tener problema.


Para mi es otra cosa...

---

### Post by faktorqm on 2008-10-01
No, no importa si es primaria o extendida, es otro el problema. salu2!

---

### Post by andresjb on 2008-10-02
Acá estoy de nuevo... me van a bannear el usuario por hincha... jaja

Buscando por Google encontré otra persona que tenía un problema parecido al mío y que lo solucionó llevando la swap al principio del disco.
¿Puede ser que tenga problemas porque la swap no esté al principio del disco? Me suena muy extraño, pero les pregunto a ustedes que saben más.

Saludos.

---

### Post by faktorqm on 2008-10-02
No, no tiene nada que ver. son inventos de gente que poco sabe computacion/informatica, ni siquiera de sistemas operativos. 
El problema es la tabla de particiones, o sea el lugar donde dice que particion esta en que lugar. si seguis con dudas leete algun wiki o wikipedia la parte de particiones, sistemas de archivos, mbr y demases y vas a ver que nada que ver si pones swap al final o al principio o al medio. salu2!

---

### Post by WanderingKnight on 2008-10-04
Lo único que importa para bootear es que en el MBR esté el bootloader, y el MBR es el primer sector del disco que ni siquiera es "tocable" mediante métodos normales de particionamiento. Después, mientras el bootloader esté apuntando a las particiones correctas, podés tenerlas en el orden que se te cante.

---

### Post by ADICTOALMAXIMO on 2009-03-31
Y com salio

---

