---
title: "[SOLVED] Instalacion de Ubuntu en PC con win xp"
date: 2007-11-22
forum: Hardware
---

### Post by BiTFx on 2007-11-22
Hola, estuve leyendo los post al respecto, y quería preguntar por mi caso particular:
 
**Mi PC**: Placa Madre M2NPV-VM, Video NVIDIA GeForce 6150 (on board), Procesador AMD64 Athlon X2 3600+, **1 Gb** de Ram, Disco Rígido de** 250 Gb** Sata 2 (particionado en 2).
 
El disco está particionado en 2:
**Primera particion** (acá esta Win XP): espacio asignado **20 Gb **(libre 11.4 Gb).
 
**Segunda particion** (acá están mis cosas, mis documentos, etc): espacio asignado **212 Gb** (libre 3.34 Gb) --> Estoy en proceso de liberar bastante espacio --> backup en dvd's.
 
No puedo de utilizar Windows repentinamente, debido a que solo tengo 1 pc en casa y otra en el trabajo, y debo utilizar mis aplicaciones todos los días, y hasta que le agarre la mano a Ubuntu, no puedo dejar de lado lo otro.
 
Quiero instalar Ubuntu y dejar Funcionando Win XP, pero me confunde lo de las particiones, por un lado dice que necesito 3, y que a una debo asignarle el doble de memoria RAM (tengo 1 Gb), por otro leí que Ubuntu crea todo automáticamente en el espacio libre, y necesito su consejo en esto, gracias.
 
Nota: la primera partición, por motivos de backup con Norton Ghost, trataría de no tocarla.

---

### Post by luisfcup on 2007-11-22
Here are two good tutorial to get you started.

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
[http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon]("http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon")

Look in the Ubuntu community documents, you will probably find everything you need there.

I also have dual boot, with WinXP in the first partition (NTFS), the second partition is FAT32, that I use for storage, and the last partition for Ubuntu. I don't know if this is the best option but works fine for me.

You can leave the Windows partition alone, and take care of cleaning the second one. When you finish backup, you start Ubuntu installation and it will ask you for the installation partition, at this point you can resize the second partition to put Ubuntu and leave another one for storage.

The second partition you heard about was the swap partition, its similar to the pagefile in windows (but stored in a separate partition with 2xRAM), but I think that  the installation will take care of creating it as well.

Sorry for the answer in English but I am Portuguese and i haven't written in Spanish a long time now.

---

### Post by sajnox on 2007-11-22
No te compliques demasiado la vida, por la maquina que tenes podes correr tranquilamente Ubuntu 7.10 (es importante que sea 7.10 y no 7.04 por el tema de la compatibilidad con NTFS) bahhh igual en 7.04 lo podes hacer igual pero tenes alguna que otra vueltita mas (nada serio)

Obvio que lo mejor es tener la maquina con dos discos, uno para los SO y otro para datos (pero obviamente no siempre se puede).

Dejate unos 10gb libres para ubuntu y en el proceso de instalacion tenes la opcion de que tamaño va a usar el sistema para instalar Ubuntu (no te vuelvas loco con el tema de la particion para el Swap, deja que el sistema se encargue). 

Conoce el sistema de a poco y familiarizate, despues esas cosas las podes modificar y arreglar para que todo quede a tu gusto.

Lo queres hacer aun mas facil!! (no es la ideal pero si la mas facil) usa WUBI [http://www.wubi-installer.org/](http://www.wubi-installer.org/) , hace poco lo probe con una notebook toshiba y anduvo diez puntos (no es ideal por que para el disco toma un archivo en formato NTFS y lo trabaja desde ahi.

Insisto, hacete amigo del sistema fijate que opciones tiene, si te gusta en serio y despues las cosas se dan solas.

Saludos

---

### Post by BiTFx on 2007-11-22
Gracias por la información.
 
**Sajnox** te agradezco la ayuda y los consejos, pero me quedé con una duda, cuando me dices que me familiarice con el sistema ¿te refieres a que lo haga desde un Live CD o que puedo instalarlo sin problemas a Ubuntu, dejando todo tal cual está en mi pc ahora?
 
Cuando me dices que me deje unos 10 gb libres, ¿te refieres a la segunda partición?, y en ese caso ¿la instalación de Ubuntu no me borraría nada, no?
 
Estuve mirando las guias que dejó **luisfcup** pero me gustaría algo mas dede la experiencia de ustedes, tengo información que no desearía dañar ni perder en la segnda partición y no puedo conseguir por ahora otro disco rígido, que sería lo ideal, así que si pueden darme más en detalle la forma de poder instalar Ubuntu junto con XP sin perder información de ninguna partición y mas o menos los pasos a seguir (automática o manual).
 
Desde ya agradecido, disculpen que pregunte tanto, y que no entienda algunas cosas que tal vez son muy simples u obvias, la verdad es que no quiero meter la pata, saludos.

---

### Post by pablo0469 on 2007-11-23
Me imagino que desde la particion con Windows SO podes defragmentar la otra con datos, no?

Si es asi, hace esto y fijate como queda el disco, y si en la cola no queda nada, hace tal cual te dijo Sanjox sin ningun temor, solo tenes que correr el boton de la barra hacia la derecha en la 1º opcion de instalacion.

Para familiarizarte con Ubuntu, obviamente es necesario instalarlo.

Saludos.

---

### Post by BiTFx on 2007-11-23
> **pablo0469 said:**
> Me imagino que desde la particion con Windows SO podes defragmentar la otra con datos, no?
 
Si es asi, hace esto y fijate como queda el disco, y si en la cola no queda nada, hace tal cual te dijo Sanjox sin ningun temor, solo tenes que correr el boton de la barra hacia la derecha en la 1º opcion de instalacion.
 
Para familiarizarte con Ubuntu, obviamente es necesario instalarlo.
 
Saludos.
 
Muchas gracias **pablo0469** esta noche dejo defragmentando mi disco o mejor aún, trataré de crear una tercer partición con alguna herramienta tipo Partition Magic para win, así no pierdo información y de una vez empiezo con Ubuntu.
 
Yo también pienso que para familiarizarme con Ubuntu debo tenerlo instalado, gracias por tu ayuda.
 
EDIT:
Me gustaría que me respondieran lo que pregunto más arriba sobre la instalación y requerimientos para desburrarme. Gracias

---

### Post by sajnox on 2007-11-23
> **BiTFx said:**
> Gracias por la información.
 
**Sajnox** te agradezco la ayuda y los consejos, pero me quedé con una duda, cuando me dices que me familiarice con el sistema ¿te refieres a que lo haga desde un Live CD o que puedo instalarlo sin problemas a Ubuntu, dejando todo tal cual está en mi pc ahora?

Me refiero a que lo instales y que lo uses, si nunca usaste Linux te pueden explicar un monton de cosas nuevas que en un primer momento marean y despues empiezan a decantar solas.
 
> Cuando me dices que me deje unos 10 gb libres, ¿te refieres a la segunda partición?, y en ese caso ¿la instalación de Ubuntu no me borraría nada, no?
 
Exactamente, te comento que si bien las particiones son un proceso confiable implica sus riesgos y siempre es ACONSEJABLE hacer un backup antes de particionar un disco. Para tu caso te diria lo siguiente 1) Backup y 2) Defragmentar 3) Deja el espacio libre y no hagas vos la particion, el proceso de instalacion lo hace en forma automatica, simplemente tenes que indicar cuanto espacion queres que use (para el proceso de instalacion te aconsejo que veas la guia ubuntu [www.guia-ubuntu.org](www.guia-ubuntu.org) )

> Estuve mirando las guias que dejó **luisfcup** pero me gustaría algo mas dede la experiencia de ustedes, tengo información que no desearía dañar ni perder en la segnda partición y no puedo conseguir por ahora otro disco rígido, que sería lo ideal, así que si pueden darme más en detalle la forma de poder instalar Ubuntu junto con XP sin perder información de ninguna partición y mas o menos los pasos a seguir (automática o manual).
 

Con lo que te indicamos anteriormente vas a poder acceder a tus archivos desde cualqueira de los dos sistemas operativos, y si haces el back (menos riesgos vas a tener, todas las guias de instalacion te sugieren que hagas un backup antes de proceder con la particion)

> Desde ya agradecido, disculpen que pregunte tanto, y que no entienda algunas cosas que tal vez son muy simples u obvias, la verdad es que no quiero meter la pata, saludos.

Nadie nace sabiendo, y la gente con ganas de aprender es mas que bienvenida.

Contamos como te esta yendo y cualquier duda la posteas

---

### Post by pablo0469 on 2007-11-23
esta noche dejo defragmentando mi disco o mejor aún, trataré de crear una tercer partición con alguna herramienta tipo Partition Magic para win, así no pierdo información y de una vez empiezo con Ubuntu.

No es necesario (ni tampoco aconsejable) que uses ese programa para crear la particion Ubuntu. Con el particionador (gparted) que trae el live-cd basta y sobra, y te permite en el momento determinar cuanto le vas a asignar, compredes?

Saludos, y cualquier cosa, postea.

---

### Post by pablo0469 on 2007-11-23
***"esta noche dejo defragmentando mi disco o mejor aún, trataré de crear una tercer partición con alguna herramienta tipo Partition Magic para win, así no pierdo información y de una vez empiezo con Ubuntu"***

No es necesario (ni tampoco aconsejable) que uses ese programa para crear la particion Ubuntu. Con el particionador (gparted) que trae el live-cd basta y sobra, y te permite en el momento determinar cuanto le vas a asignar, compredes?

Saludos, y cualquier cosa, postea

---

### Post by BiTFx on 2007-11-23
Ok, gracias por la ayuda, entonces:
 
**1º** - Libero espacio en el disco (en la segunda partición).
**2º** - Defragmento, asegurándome que al final del disco no queden partes de archivos.
**3º** - Instalo Ubuntu, indicándole que "haga todo" al final del disco y con el tamaño adecuado (¿10 Gb sería?).
 
Luego les cuento como me fue. Calquier cosa me corrigen estos pasos.
 
Un abrazo.

---

### Post by margori on 2007-11-23
Yo voy a tirar un pequeño tip:

Muchos programas no se llevan bien con las particiones ntfs. Por ejemplo, he tenido problemas con Wine para ejecutar programas en esa particion. Los copie a una particion Ext3 y anduvieron de lujo (Por ejemplo, ejecute con exito Stacraft Brood War y WarCraft 3) Tuve problemas con Azureus para utilizar la ntfs como destino de las bajadas, pero se colgaba.

Eso entre otras cosas. Pero extrañamente utilizando un pequeño programita ([http://www.fs-driver.org/](http://www.fs-driver.org/)) que me permite leer particiones ext3 en windows, nunca tuve problema en ese SO.

Asi que yo recomiendo que la particion mas grande o de trabajo este en ext3, ya que de esa manera se puedan usar sin problemas desde ambos SOs. Podria ser que esta particion este en el punto de montaje "/home".

Es mi humilde aporte, quisiera que me den su opinion, por favor.

---

### Post by pablo0469 on 2007-11-24
Exactamente, pero con un disco de 250, le daria un poco mas de 10 GB, quizas con eso no puedas probar algunas aplicaciones muy interesantes como el quemador de discos "Brasero", ya que no te va a quedar espacio en la carpeta Home.

Con 20-25 GB, andaria mejor la cosa.

Saludos.

---

### Post by BiTFx on 2007-11-25
**BUENAS NOTICIAS GENTE!!! ESTOY UTILIZANDO UBUNTU GRACIAS A USTEDES!!!**
 
Disculpen las mayúsculas, son las 05:00 de la mañana y estoy desde las 21 con Ubuntu, entre que traté de instalar, y aparecieron problemas, y tuve que hacer algunos pasos de puro intruso, pero al final quedó funcionando perfectamente mi Ubuntu, no quiero dar una opinión apresurada sobre este Sistema Operativo, pero se instaló rapidísimo, es muy muy intuitivo (para ser un usuario de windows), con respecto al manejo, es mas rápido, me pareció mas fácil a la hora de configurar la red y otras cosas, es como que tengo mas libertad para modificar a gusto...
 
**Estos son, a grandes rasgos, los pasos que seguí para llegar a este punto, aprovechando la ayuda de los que me aconsejaron en este foro, tal vez sean útiles para personas como yo, que solo utilizaron windows hasta ahora y que se han complicado al intentar hacer las particiones**:
 
 
 
(utilizando **windows):** Liberé 80 Gb en el disco **D** de mi PC, en el **C** tengo **Windows XP**.
 
(utilizando **windows):** Defragmenté 5 horas y más el disco **D**, y luego un **scandisk** a fondo (1 hora y media).
 
(arrancando con el CD/DVD de **Ubuntu):** Intenté instalar Ubuntu 7.10 versión 64 bits como 6 veces, y **NO** me aparecía la opción de instalar en el espacio libre del disco **D**, ya que me decía en la parte de Tamaño de Partición del disco **D** **"Unknow"** (como si el disco estuviera dañado), en cambio el disco** C** aparecía correctamente. 
 
[COLOR=darkred]**Nota:**[/COLOR] al abrir el instalador de **Ubuntu,** una vez cargado el Live CD, noté que no veía los botones **"siguiente",** **"atrás"** y **"cancelar",** y al no poder cambiar la resolución de pantalla a 1024 x 768, tuve que hacer lo siguiente: click derecho en el panel superior (la barrita larga que contiene Aplicaciones | Lugares | Sistema, etc) y hacer click en **"Propiedades",** se abre una ventanita y marcar la opción: "**Ocultar automáticamente**", hice lo mismo con la barra de abajo, luego, al ocultarse la barrita superior, subí mas arriba la ventana de Instalación, y al estar oculta también la barra inferior, se podían llegar a ver asomados los botones para poder moverme en la instalación, este sería el orden de los botones **[atras]** **[cancelar] [siguiente]**.
 
(arrancando con el CD/DVD de **Ubuntu):** Después de intentar instalar 6 veces Ubuntu, tanto de la ISO para DVD como la ISO para CD, pasé al siguiente paso.
 
(utilizando **windows):** Instalé Partition Magic 8.0 para crear una partición de 20 gb al final del disco D (que es de 212 Gb mas o menos) y le di el formato de Linux a esa partición de 20 Gb (ext3).
 
(utilizando **windows):** Le hice un **scandisk** (escaneo de disco para chequear errores por si había) al disco **D**, que ahora era más chico, todo salió bien, no hubo pérdida de información al utilizar Partition Magic.
 
(arrancando con el CD/DVD de **Ubuntu):** Intenté otra vez la intalación de **Ubuntu,** y al llegar a la parte de selección de partición, ahí estaba la partición de 20 Gb, pero no aparecía la opcion de que lo haga al final del espacio libre, etc etc, asi que decidí hacerlo **MANUAL,** tuve que eliminar la partición de 20 Gb (no debía tocar para nada las otras 2 particiones ya que en una tengo el Win Xp, y en la otra todas mis cosas), y crear en esos 20 Gb libres lo siguiente:
[LIST]
[*]1 partición de 1 Gb y que sea del tipo **swap** (y que comience desde el principio de espacio libre).
[*]1 partición de 10 Gb aprox. del tipo **ext3**, y **punto de montaje "/"** (sin comillas, y que comience desde el principio de espacio libre).
[*]1 partición con el resto de espacio, y creo que del tipo **vfat,** no me acuerdo, es que buscaba la forma de poder verla con Windows (pero no elegí ni ext2 ni ext3), tal vez ahí me equivoqué. Cuando arranque con windows de nuevo, me fijo, y el **punto de montaje "/home"** (sin comillas, y que comience desde el principio del espacio libre).[/LIST]Desde aquí todo siguó normal.
 
Luego de instalar todo (unos 10 minutos), me pidió reiniciar el equipo, sacar el DVD de la lectora para que no arranque desde ahí, y al hacerlo, ahí estaba **Ubuntu** y **Windows** para elegir, obviamente que saben que elegí.
 
Y acá estoy, ya instalé los drivers de la placa nvidia, venían en esta version de Ubuntu, pude configurar facilísimo speedy con un módem **Ethernet Huawei SmartAx MT880**, venía con el **openOffice** en español, asi que me abre los documentos de Microsoft Word, y creería que todo lo de Office (aun no pruebo todas las aplicaciones).
 
Ahora estoy probando todo lo que puedo, para acostumbrarme.
 
Para los nuevos e indecisos, no duden en probar, pueden tener los 2 sistemas andando a la perfección.
 
**Mis mas sinceros agradecimientos a todos los que me dieron una mano para dar el puntapié inicial.**
 
**EDIT:** Arranqué con windows ahora, y todo anda igual, no hubo problemas, solo que no veo la partición donde cree el /home en Ubuntu (aclaro que en Ubuntu veo todas las particiones, pero en Windows solo veo el C y D). Cuando la cree y seleccionaba Fat32 o Fat16 para la partición, Ubuntu no me dejó utilizarlas.
 
Saludos.

---

### Post by Mauro22 on 2007-11-25
> **BiTFx said:**
> 
 
**EDIT:** Arranqué con windows ahora, y todo anda igual, no hubo problemas, solo que no veo la partición donde cree el /home en Ubuntu (aclaro que en Ubuntu veo todas las particiones, pero en Windows solo veo el C y D). Cuando la cree y seleccionaba Fat32 o Fat16 para la partición, Ubuntu no me dejó utilizarlas.
 
Saludos.


Felicidades y bienvenido oficialmente a la comunidad :)

Eso que decis es normal, window$ tiene un ego muy grande y sólo acepta particiones fat y ntfs. Pero por suerte hay plugins para montar las particiones ext en window$.

Saludos!

---

### Post by sp33d3rs on 2009-04-26
> **BiTFx said:**
> Hola, estuve leyendo los post al respecto, y quería preguntar por mi caso particular:
 
**Mi PC**: Placa Madre M2NPV-VM, Video NVIDIA GeForce 6150 (on board), Procesador AMD64 Athlon X2 3600+, **1 Gb** de Ram, Disco Rígido de** 250 Gb** Sata 2 (particionado en 2).
 
El disco está particionado en 2:
**Primera particion** (acá esta Win XP): espacio asignado **20 Gb **(libre 11.4 Gb).
 
**Segunda particion** (acá están mis cosas, mis documentos, etc): espacio asignado **212 Gb** (libre 3.34 Gb) --> Estoy en proceso de liberar bastante espacio --> backup en dvd's.
 
No puedo de utilizar Windows repentinamente, debido a que solo tengo 1 pc en casa y otra en el trabajo, y debo utilizar mis aplicaciones todos los días, y hasta que le agarre la mano a Ubuntu, no puedo dejar de lado lo otro.
 
Quiero instalar Ubuntu y dejar Funcionando Win XP, pero me confunde lo de las particiones, por un lado dice que necesito 3, y que a una debo asignarle el doble de memoria RAM (tengo 1 Gb), por otro leí que Ubuntu crea todo automáticamente en el espacio libre, y necesito su consejo en esto, gracias.
 
Nota: la primera partición, por motivos de backup con Norton Ghost, trataría de no tocarla.

Che, tenes mi pc!, no me la querras formatear! :lolflag: jajaja

---

### Post by faktorqm on 2009-04-28
Los sistemas de archivos: fat32/16, ntfs, hpfs y todo aquel que provenga de microsoft, olvidate. Lo que yo tenia era, un windows en una particion de 5gb formateada como ntfs, y el driver ext3 para poder leer las demas particiones ext3. Redireccioné "mis documentos" a una carpeta en una particion ext3 y ya.
El resto tenia todo ext3 con ubuntu y demases particiones y desde ubuntu veia a la unica ntfs con el paquete ntfs-3g, creo que en jaunty ya viene por defecto.

Salu2!

---

