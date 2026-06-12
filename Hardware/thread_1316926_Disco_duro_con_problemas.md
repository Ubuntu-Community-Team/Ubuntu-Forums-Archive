---
title: "Disco duro con problemas"
date: 2009-11-06
forum: Hardware
---

### Post by Vero1 on 2009-11-06
Hola todos,
Tengo un problema serio. Se trata de un disco Maxtor de 40 Gb que aloja Windows y tengo otro disco de 80 Gb que aloja Ubuntu Karmic.

El problema es que Karmic me informa que el disco de 40 tiene muchos sectores erróneos(antes de hacer desfragmentación en ese disco, me decía que había 80 sectores dañados).

Ahora bien, en este disco de 80, donde tengo Karmic, tengo bastante lugar libre como para instalar Windows y eliminar el disco de 40, pero no sé cómo hacerlo.

Si hago df:
S.ficheros         Bloques de 1K   Usado    Dispon Uso% Montado en
/dev/sdb1             19228276   8274492   9977036  46% /
udev                    254428       260    254168   1% /dev
none                    254428       316    254112   1% /dev/shm
none                    254428       304    254124   1% /var/run
none                    254428         0    254428   0% /var/lock
none                    254428         0    254428   0% /lib/init/rw
/dev/sdb2             55748380   4374884  48541640   9% /home

Aparte, el Grub lo tendría que recuperar con el SuperGrubDisk o cómo sería porque ahora no hay problema por tener a Win en otro disco y estaba ya antes de instalar Ubuntu, pero si ahora paso win a este disco, la instalación sería posterior o me equivoco?

Qué me pueden aconsejar que haga?

Gracias de antemano y saludos):P

---

### Post by pablo.s on 2009-11-06
Primero tendrias que hacer un
gran, gran backup. Todo lo que
tengas en <Sistema Privativo de
marca registrada> y todo lo que 
tengas en Ubuntu.
Luego y para evitar miles de vueltas
te convendria formatear completamente
el disco de 80 GB, primero la particion
para <Sistema Privativo de marca 
registrada> y luego el resto para
Ubuntu.

Igualmente me gustaria leer algun
otro consejo, que seguro que hay 
alguno mejor.

Saludos.

---

### Post by Vero1 on 2009-11-06
Hola pablo s.

Primero, gracias por contestarme.

Me causó gracia la denominación que le das a Windows;)

Lo que no me causa gracia es pensar siquiera en hacer un gran gran backup y luego formatear. Si no hay otra solución, prefiero comprar otro disco.

Esperaré tambien a ver si hay algun arreglo menos traumático.

saludos):P

---

### Post by staar on 2009-11-06
podrías postear la salida de ```
sudo fdisk -l
```? así estaríamos más seguros de la distribución de particiones en tus discos...

lo que se me ocurre es, si hay espacio suficiente, que desde un livecd achiques la partición donde tengas instalado ubuntu, luego crees una partición NTFS en el espacio libre que te quede, instales Ventanas ahí, y luego recuperes el GRUB (ojo con esto, si instalaste karmic desde 0 tenés GRUB 2 y el SuperGrubDisk todavía no lo soporta, tenés que recuperarlo desde la consola del livecd de karmic, si en cambio actualizaste no hay problema con SGD, porque todavía tenés GRUB legacy)

saludos

---

### Post by Vero1 on 2009-11-06
Hola staar, gracias por contestar.

El comando que me dijiste, dá este resultado:

Disco /dev/sda: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x4f744f74

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        4811    38644326    7  HPFS/NTFS
/dev/sda2            4812        4998     1502077+   5  Extendida
/dev/sda5            4812        4998     1502046    7  HPFS/NTFS

Disco /dev/sdb: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x2b2e2b2d

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        2432    19535008+  83  Linux
/dev/sdb2            2433        9483    56637157+  83  Linux
/dev/sdb3            9484        9729     1975995   82  Linux swap / Solaris

Decís que con un liveCD achique la partición de Ubuntu, pero te comento  que yo hice upgrade por Internet, por lo tanto no tengo LiveCD de Karmic.
Me sirve el LiveCD de Jaunty por ejemplo?
Con ésto ya quedó claro que el Grub no cambió y debo tener Grub1.
Por si acaso, hay forma de comprobarlo o es seguro que con upgrade queda el Grub anterior?

Gracias de antemano por tu ayuda.

):P

---

### Post by staar on 2009-11-07
si actualizaste, es casi seguro que tenés GRUB Legacy, podés comprobarlo al prender la pc, si arriba dice GRUB 1.97, ese es GRUB 2, sino es el Legacy...

el LiveCD de Jaunty te sirve perfectamente, solo tenés que arrancar con ese, ir a Sistema > Administración > Editor de particiones y achicar la partición, te recomiendo que sea la sdb2, donde montás tu /home, porque es la más grande y la que tiene más espacio libre, y, en el espacio sin particionar que queda, crear una nueva y formatearla como NTFS, después instalás Ventanas ahí...

ahora que lo pienso, es probable que una vez que hayas recuperado el GRUB, cuando saques el disco que anda fallando, no puedas iniciar ninguno de los dos sistemas, porque el archivo /boot/grub/menu.lst va a quedar apuntando al disco incorrecto (el segundo, que va a pasar a ser primero y único), si te pasa esto, posteá la nueva salida de *sudo fdisk -l* y el contenido del menu.lst, y en un ratito desde el LiveCD lo arreglás...

saludos

---

### Post by Vero1 on 2009-11-08
Hola staar,

Imposible saber qué Grub tengo porque son fracciones de segundo y no logro ver. Hay alguna forma de saber cuál tengo?

En lo que respecta a tu párrafo "ahora que lo pienso, es probable que una vez que hayas recuperado el GRUB, cuando saques el disco que anda fallando, no puedas iniciar ninguno de los dos sistemas, porque el archivo /boot/grub/menu.lst va a quedar apuntando al disco incorrecto (el segundo, que va a pasar a ser primero y único), si te pasa esto, posteá la nueva salida de sudo fdisk -l y el contenido del menu.lst, y en un ratito desde el LiveCD lo arreglás..." digo lo siguiente:

Si antes de eliminar el disco que falla(que todavía no sé cómo hacer) arreglo el grub/boot/menu.lst? 
No sé si me explico.
Ahora el boot/grub/menu.lst dice así sobre la partición de win:

#title		Microsoft Windows XP Home Edition
#rootnoverify	(hd1,0)
#savedefault
#makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
#chainloader	+1


title Microsoft Windows XP Home Edition
root (hd0,0)
 savedefault
 makeactive
 chainloader +1

o sea hace mención a hd0,0 y Linux sería hd1, cuando haya instalado en hd1 windows, cómo va a saber Grub con cual empezar? o va a crear otro hd2 por ejemplo y el menu lst.va a tener que apuntar allí?

Me siento algo embarullada :-(

La cuestión es que despues de instalar win habrá que reiniciar y si no arreglo el menu.lst antes va a pasar lo que vos decís y entonces cómo hago para hacer fdisk -l y el menu.lst si no va a arrancar, con el LiveCD?

Perdoná tanta cosa pero en ésto no tengo experiencia.

Bueno, espero tus noticias.

):P

---

### Post by Vero1 on 2009-11-08
> **Vero1 said:**
> Hola staar,

Imposible saber qué Grub tengo porque son fracciones de segundo y no logro ver. Hay alguna forma de saber cuál tengo?

En lo que respecta a tu párrafo "ahora que lo pienso, es probable que una vez que hayas recuperado el GRUB, cuando saques el disco que anda fallando, no puedas iniciar ninguno de los dos sistemas, porque el archivo /boot/grub/menu.lst va a quedar apuntando al disco incorrecto (el segundo, que va a pasar a ser primero y único), si te pasa esto, posteá la nueva salida de sudo fdisk -l y el contenido del menu.lst, y en un ratito desde el LiveCD lo arreglás..." digo lo siguiente:

Si antes de eliminar el disco que falla(que todavía no sé cómo hacer) arreglo el grub/boot/menu.lst? 
No sé si me explico.
Ahora el boot/grub/menu.lst dice así sobre la partición de win:

#title		Microsoft Windows XP Home Edition
#rootnoverify	(hd1,0)
#savedefault
#makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
#chainloader	+1


title Microsoft Windows XP Home Edition
root (hd0,0)
 savedefault
 makeactive
 chainloader +1

o sea hace mención a hd0,0 y Linux sería hd1, cuando haya instalado en hd1 windows, cómo va a saber Grub con cual empezar? o va a crear otro hd2 por ejemplo y el menu lst.va a tener que apuntar allí?

Me siento algo embarullada :-(

La cuestión es que despues de instalar win habrá que reiniciar y si no arreglo el menu.lst antes va a pasar lo que vos decís y entonces cómo hago para hacer fdisk -l y el menu.lst si no va a arrancar, con el LiveCD?

Perdoná tanta cosa pero en ésto no tengo experiencia.

Bueno, espero tus noticias.

):P

es boot/grub/menu.lst

---

### Post by staar on 2009-11-08
si tenés el archivo menu.lst, tenés GRUB Legacy, porque en GRUB2 ese archivo es reemplazado por el grub.conf (más otros, pero no vienen al caso)


personalmente, haría lo que vos querés hacer en este orden:

1) primero sacaría el disco fallado (abrís la PC, y lo desenchufas/sacas)

2) inmediatamente después arrancaría con el LiveCD y crearía la partición para Ventanas...

3) desde el mismo LiveCD modificaría el menu.lst para que apunte a las particiones correctas, te explico como es esto, GRUB toma el número de los discos según sea el orden de inicio, que se determina desde el BIOS. actualmente vos tenés el disco de 40 como primero y el 80 como segundo, en el menu.lst la sintaxis indica que los discos y particiones se empiezan a contar partiendo desde el 0, por eso vos tenés el inicio de Ventanas en (hd0,0), primer disco, primera partición. al sacar el disco de 40, el de 80 pasa a ser el disco hd0, pero la partición para iniciar Ventanas va a ser incorrecta, porque la partición 0 va a ser donde ahora está el / de ubuntu, por eso tendrías que cambiar el (hd0,0) a (hd0,X) donde X es el número de la partición que creaste para Ventanas menos uno, supongo que va a quedar como sda4, por lo que sería (hd0,3), la parte del arranque de ubuntu no creo que haya que modificarla...

4) después instalaría Ventanas...

5) y por último recuperaría el GRUB con el SGD, y, si no se me escapó nada, tendrías que tener los dos sistemas andando...


una aclaración, la parte de lo que posteaste que tiene un # al comienzo de la línea, no se toma en cuenta, esta comentada, no hace falta que la modifiques...

saludos

---

### Post by Vero1 on 2009-11-08
staar, a lo mejor se te pasó mi pregunta.
No se puede deshabilitar el disco que falla desde Bios? No me atrevo a meter mano en la CPU porque ni siquiera sé cuál es el disco malo.

Y otra cosa. Si tengo algunos archivos que me interesa conservar de win, no puedo hacer otra cosa que un backup o hay alguna forma de guardar esos archivos en Ubuntu o sea importarlos?

gracias

---

### Post by staar on 2009-11-08
los archivos los podés guardar fácilmente en tu partición /home, en el menú Lugares te deben aparecer dos entradas llamadas "Soporte de xx GiB", no? esas son las particiones del disco con Ventanas, simplemente abrilas, navega hasta los archivos que querés salvar, y copialos a tu home...

no conozco forma de deshabilitar un disco duro desde el BIOS, pero por dentro la PC no muerde :-P, los discos duros tienen, por lo general, una etiqueta encima, en la que se especifican muchos datos del mismo, entre ellos la capacidad, podés identificarlos por eso, para deshabilitarlo simplemente podés desenchufar el cable que va hacia la fuente, generalmente es parecido a [este]("http://upload.wikimedia.org/wikipedia/commons/thumb/3/31/Molex_female_connector.jpg/800px-Molex_female_connector.jpg")...

saludos

---

### Post by Vero1 on 2009-11-08
Bueno staar, si la CPU no muerde;) entonces haré de tripas corazón y probaré desenchufar ese disco.

Tambien copiaré a mi home lo que me pueda interesar de lado Ventanas, antes.

No sé cuando haré todo este trabajo(cuanto antes mejor) pero a vos te agradezco mucho toda la ayuda y espero poder volver aquí para decirte que todo funcionó a las mil maravillas(ejem)

):P

---

### Post by Vero1 on 2009-11-27
Hola,

Por pura casualidad, googleando, me topé con gente que tiene tambien problemas con los discos, basándose en el informe que dá gdu-notification daemon, donde recomiendan confirmar esta información, pasándole al disco algunos programas que detectan anomalías.

Pues bien, he pasado dos de esos programas y ninguno de los dos informa de fallo alguno en el disco, es más, dice: disk health: exellent.

Por todo ésto me pregunto y les pregunto: Hasta qué punto es confiable gdu?

Karmic Koala tiene alguna herramienta que se pueda usar para confirmar o descartar problemas en el disco? Lo que informa gdu es que hay 80 sectores erróneos.

Agradeceré cualquier información al respecto.

saludos

---

### Post by guillermolisi on 2009-11-27
> Por todo ésto me pregunto y les pregunto: Hasta qué punto es confiable gdu?
Tanto como los que utilizaste como alternativa de analisis.

> Pues bien, he pasado dos de esos programas y ninguno de los dos informa de fallo alguno en el disco, es más, dice: disk health: exellent.
Y que programas son esos ? Recordas nombres, links en Internet, referencias a los comentarios que has leido como para saber algo mas al respecto ?

---

### Post by Mauro22 on 2009-11-27
Por lo que entiendo hay dos cosas:

1) Los discos que tienen capacidad S.M.A.R.T (La tecnología S.M.A.R.T. acrónimo de Self Monitoring Analysis and Reporting Technology consiste en la capacidad de detección de fallos del disco duro. La detección con anticipación de los fallos en la superficie permite al usuario el poder realizar una copia de su contenido, o reemplazar el disco, antes de que se produzca una pérdida de datos irrecuperable.), se diagnostican por si solo, los programas en este caso, actuan de "mensajero" y muestran esa informacion de una forma mas simple, atractiva, etc...

2) El otro tema es analisis de escritura/lectura... 


Si el programa X hace el 1r punto y da error, el programa no tiene la culpa, el que brinda la información es el disco y no el soft en si.

Hay que ver que tipo de informacion manejan los otros que te dieron bien.

---

### Post by guillermolisi on 2009-11-27
Una practica recomendada es instalar Smartmontools para monitorear el estado de los discos con capacidad S.M.A.R.T.

---

### Post by Vero1 on 2009-11-27
Hola Mauro y guillermolisi,

Los programas que he usado son:

HDD health v.3.3 - Beta

HDTune Pro v.3.50(trial)

Las direcciones son:

[www.panterasoft.com](www.panterasoft.com)
[www.hdtune.com](www.hdtune.com)

HDTune indica, segun lo que entiendo, que había 80 sectores dañados que fueron trasladados a otro sector, con lo cual la "salud" volvió a estar OK.

Ësto creo que no fue tomado en cuenta por gdu o algo parecido.

guillermolisi, probaré el programa que me indicas, si es que puedo.

Informaré del resultado.

Gracias.

---

### Post by guillermolisi on 2009-11-27
> **Vero1 said:**
> Hola Mauro y guillermolisi,

Los programas que he usado son:

HDD health v.3.3 - Beta

HDTune Pro v.3.50(trial)

Las direcciones son:

[www.panterasoft.com]("http://www.panterasoft.com")
[www.hdtune.com]("http://www.hdtune.com")

HDTune indica, segun lo que entiendo, que había 80 sectores dañados que fueron trasladados a otro sector, con lo cual la "salud" volvió a estar OK.

Ësto creo que no fue tomado en cuenta por gdu o algo parecido.

guillermolisi, probaré el programa que me indicas, si es que puedo.

Informaré del resultado.

Gracias.
Cada cierta cantidad de veces que se monta el sistema de archivos de un disco con Linux, corre un utilitario llamado "fsck" que revisa la integridad del file system y si detecta secores dañados los re-mapea utilizando espacio en una area reservada para este fin.

Esta tecnica preserva el espacio en disco pero impacta en el rendimiento haciendolo algo mas lento que si el disco estuviera realmente bueno (sin defectos).

Como los programas los hacen personas y estas desarrollan mensajes segun cierto paradigma respecto de un situacion, puede ocurrir que tal o cual utilitario te diga "Disco OK" porque no encontro **otros** sectores dañados (y los que se encontraron fueron correctamente "reubicados" con anterioridad).

Esta area reservada tiene una capacidad limitada. Si el disco se esta degradando llegara  aun punto en que no podra preservar mas la capacidad porque no tendra forma de "reubicar" el sector dañado.

El paquete de Smartmontools esta en los repositorios de Ubuntu y generalmente se lo usa desde la consola/terminal para tener informacion relacionada con los discos.

---

### Post by Vero1 on 2009-11-27
Bueno te diré que el disco del que estamos hablando es donde está Windows y parece que ese SO tambien hace el trabajo que dijiste o sea guarda un sector en el disco a efectos de poder hacer esos traslados.

He instalado smartmontools pero no corre desde Consola en ninguna forma.
Como no lo encontré en ningun lado lo busqué con el Buscador y me informó que está en User/share y allí está.Al hacerle click muestra smartd-runner pero tampoco funciona. Saca un cartelito que dice: command not found y si trato de correrlo directamente desde su ícono pregunta si lo quiero ejecutar en terminal, le digo que sí, pero se queda con el cursor titilando sin que pase nada.

Todo ésto lo estaba probando a ver si me salvaba de tener que tirar ese disco, pero si como parece, los sectores dañados pueden aumentar y yo tener mas problemas, pues optaré por sacar ese disco y hacer lo que generó el post original o sea hacer lugar para "ventanas" en mi otro disco y ya.

Gracias a Uds. otra vez. Lástima que de todas formas no pueda utilizar el smartmontools porque siempre puede ser util. Me llama la atención que diga que es un archivo de texto ejecutable, cuando miro en propiedades.
Dice que es "script en shell (application/x-shellscript)" y pregunta con qué programa lo quiero abrir, mencionando gedit o notepad o OO.

saludos.

---

### Post by guillermolisi on 2009-11-27
[Aqui hay un tutorial]("http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/") (en Ingles) que me parecio muy completo y didactico.

Ese comando corre en consola/terminal (primero abris la terminal o vas a una consola y luego lo ejecutas, no como decis lo estabas haciendo).

Fijate que podes hacer distintos tipos de test sobre el disco y, ademas, iniciar un demonio (un proceso que corre dando servicio) para generar estadisticas a partir de un monitoreo configurado previamente.

Si es demasido denso el tuto, avisa y trato de destacar los aspectos mas importantes para este caso.

---

### Post by Vero1 on 2009-11-27
guillermolisi,
no sé qué se entendió pero lo que hice fue abrir terminal y poner smartmontools con y sin sudo y nada. Despues fui a tty e hice lo mismo pero nada.

Bueno, ví el tuto e hice algunas pruebas de lo que habla. Te anexo el resultado de Terminal a ver qué opinás, aunque es un poco largo.

veronica@veronica-Karmic-Koala:~$  sudo smartctl -i /dev/sda1
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Maxtor DiamondMax Plus 8 family
Device Model:     Maxtor 6E040L0
Serial Number:    E1KM01ZE
Firmware Version: NAR61590
User Capacity:    41.110.142.976 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Fri Nov 27 18:10:43 2009 ART
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

veronica@veronica-Karmic-Koala:~$ sudo smartctl -d TYPE -i /dev/sda1
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=======> INVALID ARGUMENT TO -d: TYPE
=======> VALID ARGUMENTS ARE: ata, scsi, marvell, sat, 3ware,N, hpt,L/M/N cciss,N <=======

Use smartctl -h to get a usage summary

veronica@veronica-Karmic-Koala:~$ sudo smartctl -H /dev/sda1
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

veronica@veronica-Karmic-Koala:~$ sudo smartctl -c /dev/sda1
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
General SMART Values:

Bueno se ve que no se puede poner todo en un post. Intento completar con otro.

---

### Post by Vero1 on 2009-11-27
la parte que falta:

=== START OF READ SMART DATA SECTION ===
General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (1021) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  17) minutes.

veronica@veronica-Karmic-Koala:~$ sudo smartctl -t short /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Fri Nov 27 18:21:32 2009

Use smartctl -X to abort test.
veronica@veronica-Karmic-Koala:~$ sudo smartctl -l selftest /dev/sda1
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      7401         -
# 2  Short offline       Completed without error       00%      7285         -

veronica@veronica-Karmic-Koala:~$ 


gracias.

---

### Post by EnriqueK on 2009-11-27
Un DD de 40 G debe tener unos 6 años, por lo que en mi opinión ya es hora de cambiarlo, no lo pensaría dos veces mas sabiendo que la tendencia actual es la de fabricar solamente discos Sata, asi que te sugiero que  no pierdas tiempo en tratar de prolongar la vida a un DD que ya la tiene cumplida , no vaya a ser que no consigas DD IDE y no te quede otra que adquirir equipo completo.

---

### Post by Vero1 on 2009-11-28
Bueno a los que me puedan leer y que me ayudaron hasta ahora.

Acabo de desenchufar el disco fallado y bootea directamente con Ubuntu, pero...

Para hacer lugar a Win, inserté para bootear un CD de Jaunty y otro anterior, pero ambos llegan un punto con la barra y se quedan clavados, por lo que no puedo usar GParted para redimensionar la partición de mi home(que es la mas grande).

Intenté usar GParted desde Karmic, tratando de desmontar el disco, pero me contesta que no se puede porque está ocupado.

La verdad es que no sé cómo puedo hacer ahora.CD de Karmic no tengo porque hice upgrade por Internet.

Tal vez elijo mal la forma de instalar. 
Primero elegí no hacer cambios en el equipo pero pensé que sí tiene que hacer cambios con GParted, entonces elegí Instalar, pero tampoco funcionó.

Ojalá haya alguno de Uds. que me pueda sacar de este apuro.

Gracias por adelantado y saludos.

---

### Post by Mauro22 on 2009-11-28
Hola!!


Podrias probar, si podes, con un cd alternate, asi instalas sin cargar el LiveCD...


Otra cosa no se me ocurre.

---

### Post by Vero1 on 2009-11-28
Hola Mauro22,

Lamentablemente ninguno de mis CD(probé ya 3 y creo que Hardy es Alternate) funcionan.

Intrepid y Jaunty se cuelgan y Hardy empieza a instalar porque no tiene para probar como los otros.

La verdad es que ya no sé qué hacer. En ubuntu-es tampoco me pudieron ayudar.

El problema está en que no puedo desmontar la partición /home porque me sale un cartelito que dice que está "busy", pero no sé con que porque yo tengo todo cerrado cuando pruebo GParted.

En fin, seguiré esperando a ver si alguien me puede ayudar.

Gracias.

---

### Post by Vero1 on 2009-11-28
Hola EnriqueK,

Sí el disco debe tener mas años todavía de lo que decís. 
Esta mañana me atreví y lo desenchufé pero ahora surgió el problema que podés leer en mis posts.

Espero que alguien pueda darme la solución.

Saludos.

---

### Post by EnriqueK on 2009-11-28
Veo dos posibles soluciones.
1.- Para mi la mejor es que adquieras un DD nuevo y le hagas una clonación completa disco a disco del DD donde esta Xp, es posible que tengas suerte y todo que funcionando igual que antes, esta tarea la puedes encargar un servicio técnico si es que no te animas a hacerlo, es fácil usando un disco bootable del Acronis o el Hiren's Boot Cd.
2.- Se me ocurre que podrías instalar en otra partición algún otro Ubuntu, por ejemplo Jaunty , en posible que al crear el MBR te reconozca en el Grub la presencia de Karmic, de no ser así es cuestión de introducir manualmente los paránetros de la instalación de karmic en el Grub, tenderlas que averiguarlo , pero no creo que haya problemas.
No logro entender los motivos para sacar un distribución con Grub2 en fase beta y sin documentación suficiente y para reemplazar algo que funciona muy bien .

---

### Post by Vero1 on 2009-11-29
EnriqueK,

Agradezco tus sugerencias pero te digo lo siguiente:
Tengo el CD original de XP para reinstalar y tengo archivos y configuraciones guardadas en un pendrive.
Así que por este lado no tiene que haber problemas.

En cuanto a lo segundo, no puedo desmontar la unidad para redimensionar, por lo tanto no puedo instalar nada.

Desde hace 2 días estoy luchando con GParted LiveCD, pero tampoco me funciona en modo gráfico o sea llega a un punto donde se cuelga en una pantalla negra. Tampoco puedo usar los LiveCD (ya probé con 3) porque tambien se cuelgan.

Estoy pensando en si tiene algo que ver que desenchufé el disco donde está Windows(ese disco está fallado), pero no creo aunque me puedo equivocar.

La cuestión es que ya me estoy desesperando porque no logro saber qué hacer.

Gracias por tu interés y saludos.

---

### Post by EnriqueK on 2009-11-29
Lo de la clonación del DD lo decía por que de esta manera vas a reponer el MBR y así se copian todos los datos de arranque , incluyendo el de Ubuntu, tu problrma es precisamente ese.
Para usar el Gparted  las particiones a editar deben estar desmontadas, inclusive alguna de ellas es lógica , debes tener desmontada todas las lógicas e inclusive debes desactivar la Swap por que el Live CD hace uso de la misma, todo esto lo puedes hacer desde el Gparted y luego de esto ya podrás editar la tabla de particiones para crear una nueva y allí instalar otro Ubuntu.
Otra cosa, me olvidaba de mencionar de que cuando desconectaste el DD1 debes de poner el otro DD como Master, para hacer eso debes de desmontarlo y cambiar de posisción ina lengueta conectora en la posición de Master, seguramente actualmente se encuentra en Slave y es otro motivo para que no arranque.

---

### Post by Vero1 on 2009-12-02
Hola a todos,

Solo decirles que ya solucioné mi problema. Desenchufé el disco malo y con el GParted Live le hice lugar a Windows en mi disco bueno. Luego con el SuperGrubDisk recuperé el Grub.

No fue poco trabajo pero ya está todo en su lugar.

Agradezco vuestra ayuda.

Saludos:)

---

### Post by guillermolisi on 2009-12-02
> **Vero1 said:**
> Hola a todos,

Solo decirles que ya solucioné mi problema. Desenchufé el disco malo y con el GParted Live le hice lugar a Windows en mi disco bueno. Luego con el SuperGrubDisk recuperé el Grub.

No fue poco trabajo pero ya está todo en su lugar.

Agradezco vuestra ayuda.

Saludos:)
Felicitaciones !! :D

Muy buen trabajo !

---

### Post by Mauro22 on 2009-12-02
EDiT

---

### Post by Vero1 on 2009-12-03
guillermolisi, gracias ;)

Mauro22, lo tuyo no lo entiendo :-(


saludos

---

### Post by Mauro22 on 2009-12-03
> **Vero1 said:**
> Mauro22, lo tuyo no lo entiendo :-(

Habia puesto algo, pero nada que ver con este hilo... Entonces lo edité, y puse eso. 
:popcorn:

---

### Post by Vero1 on 2009-12-03
Mauro22,

Qué ganas de asustarme :p

---

