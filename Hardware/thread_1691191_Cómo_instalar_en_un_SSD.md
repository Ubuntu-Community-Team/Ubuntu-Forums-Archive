---
title: "Cómo instalar en un SSD ?"
date: 2011-02-19
forum: Hardware
---

### Post by losoollenos on 2011-02-19
Hola cómo andan tod@s?, espero que muy bien......

La cuestión es que el instalador de Ubuntu 10.10 no me detecta el disco SSD. Primeramente conecto el ssd, arranco el sistema que tengo instalado en el disco tradicional y todo bien; creé las particiones sin ningun problema.
Pero a la hora de la instalación no se detecta este disco, habrá que cambiar la forma de instalación?.

Gracias por cualquier ayuda

Saludos

---

### Post by hictio on 2011-02-19
Qué hardware es? Yo instalé en una Thinkpad T410 (Lucid Lynx 32 bits) sin ningún problema en un SSD. Hice la instalación desde un pen drive USB, fue la instalación más rápida que vi en mi vida.

---

### Post by losoollenos on 2011-02-19
Es un OCZ agility 2 y también lo estoy intentando instalar desde el pendrive aunque con Maverick de 64 bits, el mismo sistema desde el que lo particioné normalmente.
Ya le instalé el seven y arranca en 12 segundos !!!!! muero por ver como arranca Ubuntu jejjej.

saludos

---

### Post by losoollenos on 2011-02-19
La puuucha..... acabo de probar el ssd en una pc con mother MSI P35 neo para Intel desde el pendrive y lo detecta.
Que cosa extraña que desde el sistema instalado en el otro disco se vea el ssd, pero no desde el pendrive de instalación. Ya revisé alguna actualización de bios para el mother Asus m4n68m-le (AMD) que uso pero estoy con la última.

Gracias y saludos

---

### Post by biale on 2011-02-21
Pegale un vistazo a 

[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567557&viewfull=1#post567557](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567557&viewfull=1#post567557)

donde dice 

"BIOS settings interact with the Desktop Management Interface or the DMI Pool. These can result in the SSD sometimes not being found."

Ya que estamos, tuviste en cuenta la "alineación" durante el particionado?

[http://www.ocztechnologyforum.com/forum/showthread.php?77769-A-Simple-How-To-on-Partitioning-and-Alignment-on-GNU-Linux-using-fdisk](http://www.ocztechnologyforum.com/forum/showthread.php?77769-A-Simple-How-To-on-Partitioning-and-Alignment-on-GNU-Linux-using-fdisk)

---

### Post by losoollenos on 2011-02-21
Gracias por la info !!!
Aunque no encontré lo que me sugerís.... igual mi inglés es muy básico.
Respecto del alineamiento leí por ahi que no era tan importante para usuarios domésticos, sí para servers, no se......
Y si la configuración del bios puede hacer que el ssd no sea detectado por qué en mi caso sí lo detecta cualquier windows....??, no pensé que iba a ser tan complicadito el tema jejje.

Saludos y muchas gracias

---

### Post by biale on 2011-02-21
Hay bastante para leer en el sitio de OCZ. Los links apunta alli, la informacion algo dispersa.

Muchas de las explicaciones del site estan dadas para Windows. Si siempre lo detectara de una, no las darían (WXP?). De todas formas es anecdótico, yo espero que los dos sist op tengan sus mañas.

Ellos sugieren que la alineación es importante, y también explican como hacerlo bajo linux...

Si tu ingles es básico te cuento que las explicaciones son un tanto confusas. Pareciera que sugieren emulación IDE (!?) A la larga la idea es jugar con esas cosas.

Y de ultima, copias datos (-axv) y MBR, arrancas como podes y montas via Fstab.

Tip: Me acabo de enterar que ellos sugieren no cargar mas del 80% de espacio del disco. Tenía idea, pero no lo tenía claro...

Contanos como te fué...

---

### Post by losoollenos on 2011-02-21
Mirá traje dos del mísmo ocz, a uno le instalé el seven en una pc con el MSI que dije más arriba; en la mía un xp ue y después un original, los dos sin problemas.

 Luego cargué el ubuntu en el disco tradicional e instalé el grub en el sda, que ahora corresponde al ssd y puedo elegir bien con cual so arrancar. En la otra máquina si podía instalar ubuntu en el ssd, pero no es mía jejj. Asi que el disco es detectado segun en que mother parece.......

Me mataste con: "Y de ultima, copias datos (-axv) y MBR, arrancas como podes y montas via Fstab.". Lo podré hacer ??? ni idea a que te referís......,por las dudas te recuerdo que desde el sistema instalado accedo sin problemas al ssd. 

De nuevo gracias por la info !!!!

Y si arranco la instalación desde el xp ??? nunca instalé de esa forma, podrá servir en este caso????

---

### Post by biale on 2011-02-21
Mas facil de lo que parece...

La idea es obtener (al menos) una partición gemela en el nuevo disco, identica a lo que ya tengo en el disco viejo y se que anda, pero con uuid distinto. Particiono y copio los contenidos de "/" (cp -axv...)
 
Ahora con algun arranque live toco la fstab para que "/" se tome de donde yo quiera, del disco nuevo, y se monte como tal.

Y si no anda, nuevo arranque live y vuelvo atras la fstab. 

Solo si quiero (y puedo) arrancar (boot) con el disco nuevo, tengo que instalar el grub en el MBR. Verifico que tome /boot de donde yo quiera. Y todo eso depende mucho del Bios.

Mas dificil es probarlo sin tocar nada, haciendo chroot 

Mi idea actual es comprar uno de esos discos y usarlo principalmente para la partición root.

---

### Post by ubuntu27 on 2011-02-22
Quiza te ayude esto:

[How to get your Realtek card reader working in Ubuntu]("http://www.omgubuntu.co.uk/2011/02/card-reader-not-working-hp-mini-ubuntu/")

---

### Post by losoollenos on 2011-02-23
Hola gracias por las ayudas.....el fin de semana vuelvo y veo como me sale jejjje, tendras alguna guia para hacer eso biale?

garcias y saludos

---

### Post by biale on 2011-02-26
No tengo una guia, pero igual se lo puede intentar por pasos.

¿PC o Notebook? Si es una PC lo primero sería conectar el disco al tercer port SATA, como si fuera un disco mas. Luego verificar que el Linux instalado lo detecte con gparted. Y también que ingresando al BIOS este lo detecte, aparecerá en los mensajes "post"...

---

### Post by losoollenos on 2011-02-26
Ya estoy en casa....
Es una pc, es detectado con gparted (que la verdad es que tarda bastante más de lo normal en hacer la lectura de discos, dicho sea de paso) por el ubuntu que tengo instalado y por el bios, sólo que está conectado al sata 1, lo cambio si o si?.

El ssd está en el sda y ubuntu en sdb1, La partición a dónde lo copiaría sería la sda2.

Te recuerdo que en forma live no tengo acceso al ssd.....

---

### Post by biale on 2011-02-26
Por ahora no hace falta cambiar nada.

El siguiente paso es definir y formatear la partición sda2. Por ahora en forma gráfica con gparted y sin tener en cuenta la alineación. Ext4 si ya lo estas usando. Ponele una etiqueta de volúmen bonita, por ejemplo "testsys" y copy-paste de la uuid que gparted le asigne para referencia posterior.

edito: se trata de gparted corriendo bajo ubuntu normal y no bajo cd live

El copiado debería se sencillo. Hay que montar la nueva partición en algun lado:

sudo mkdir /mnt/testsys
sudo mount /dev/sda2 /mnt/testsys

Verificar un poco:
# muestra lo que pensamos copiar
ls /   
# todavia muestra una particion vacia
ls /mnt/testsys

Copiamos: 
sudo cp -axv   /*  /mnt/sda2

Y si todo salio bien vas a tener en el disco SSD una partición gemela a la partición de sistema que actualmente estas usando. Pegale un vistazo con Nautilus: parece estar todo igual?

Cuanto tenes de RAM?

---

### Post by losoollenos on 2011-02-26
Empezó a copiar y se quedó, te copio las últimas líneas.

«/proc/asound/seq/drivers» -> «/mnt/testsys/proc/asound/seq/drivers»
«/proc/sysrq-trigger» -> «/mnt/testsys/proc/sysrq-trigger»
cp: leyendo «/proc/sysrq-trigger»: Error de entrada/salida
«/proc/partitions» -> «/mnt/testsys/proc/partitions»
«/proc/diskstats» -> «/mnt/testsys/proc/diskstats»
«/proc/crypto» -> «/mnt/testsys/proc/crypto»
«/proc/key-users» -> «/mnt/testsys/proc/key-users»
«/proc/version_signature» -> «/mnt/testsys/proc/version_signature»
«/proc/kpageflags» -> «/mnt/testsys/proc/kpageflags»
«/proc/kpagecount» -> «/mnt/testsys/proc/kpagecount»
«/proc/kmsg» -> «/mnt/testsys/proc/kmsg»


Si le ponía "sudo cp -axv /* /mnt/sda2" me tiraba "cp: el destino, «/mnt/sda2», no es un directorio", por eso reemplazé sda2 por testsys, no se si habré hecho macanas jej.

---

### Post by biale on 2011-02-26
Esta bien lo que hiciste, fui yo el que me equivoque.

sudo cp -axv /* /mnt/testsys

Hay buenas noticias, ese disco de una forma u otra va a funcionar.

El error fue durante la lectura:
cp: leyendo «/proc/sysrq-trigger»: Error de entrada/salida

Voy a suponer que lo tira porque sdb1 esta montado como / (y no porque el sector sea ilegible) Lo podes verificar con la utilidad de discos, que diga "el disco esta sano"

Necesitamos hacer la copia fuera de linea. Si el cd live insiste en no ver al disco SSD, buscamos otro cd utilitario. 

SystemRescueCD puede ser una opción solida. Habría que bajar la ISO, controlar md5 y quemar un cd.

Entretanto verificamos la alineacion. Postea la salida del comando

fdisk -luc /dev/sda

---

### Post by losoollenos on 2011-02-26
Esto:

ubuntu@ubuntu:~$ fdisk -luc /dev/sda
No se puede abrir /dev/sda
ubuntu@ubuntu:~$ sudo fdisk -luc /dev/sda
[sudo] password for ubuntu: 

Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros, 234441648 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x00091800

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048    20973567    10485760    7  HPFS/NTFS
/dev/sda2        20973568    41945087    10485760   83  Linux
/dev/sda3        41945088    46139391     2097152   82  Linux swap / Solaris
/dev/sda4        46139392   234440703    94150656    5  Extendida
/dev/sda5        46141440   109055999    31457280    7  HPFS/NTFS
/dev/sda6       109058048   130029567    10485760    7  HPFS/NTFS
/dev/sda7       130031616   151003135    10485760   83  Linux
/dev/sda8       151005184   234440703    41717760    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by biale on 2011-02-26
En ese momento sda era el disco SSD? Parece muy cargado para serlo. Y si así fuera la particion sda2 ya esta alineada OK a 512. Si no es el disco acordate que nos interesa el SSD:  sudo fdisk -luc

Si lo que aqui se ve como sda7 es arrancable y hay visión del ssd, el copiado se puede hacer desde alli. Aunque son muy parecidos, te pasaría los comandos.

---

### Post by losoollenos on 2011-02-26
Sisi, es el ssd. Le hago varias particiones porque todavía no me canso jeje de ir probando sistemas, programas, betas.....

Vos decís que copie a la sda7 en lugar de la sda2 ??, por ?, no está bien alineada la sda2 ??

---

### Post by biale on 2011-02-27
Por un momento pense que el SSD habia dejado de ser sda...

Ambas partiones, sda2 y sda7 estan alineadas. Un tema resuelto

Lo mejor es limpiar la partición sda2 para eliminar los restos de la copia fallida anterior. Para ello la volvemos a formatear con gparted. Anotamos la nueva uuid, y le reponemos una etiqueta de volumen "testsys"

Bajaste la ISO del "System Rescue CD" y grabaste el CD? Arrancamos (boot) la computadora desde la unidad de CD Rom. Luego de configuarar al teclado va a quedar un prompt de consola. Desde alli...

Atencion que aqui no hay sudo, siempre se actua como usuario root. Hay que verificar un poco mas. 

mkdir /mnt/sdb1
mkdir /mnt/sda2

mount /dev/sdb1 /mnt/sdb1
mount /dev/sda2 /mnt/sda2

# Verificamos que las particiones sean las correctas!
ls /mnt/sdb1	# Es la particion de Sistema? 
ls /mnt/sda2	# Esta particion esta vacia?

cp -axv   /mnt/sdb1/*     /mnt/sda2  > listado.txt

Cuando devuelve el prompt sabemos que termino la copia. Si hubo algun error aparecera en pantalla.

Salvamos el listado para mirarlo mejor despues:

cp listado.txt  /mnt/sda2

---

### Post by losoollenos on 2011-02-27
Parece que no permite escribir, tampoco me lo permitió con el listado.txt, pero aparecían las carpetas del sdb1 y al lado > "read-only file system" sucesivamente.

---

### Post by biale on 2011-02-27
Eso es algo muy raro. Por ejemplo, bajo SystemRescueCD, listado.txt se escribe en /root, dentro de un file system en RAM.

Pasame los datos de la distro que usaste y algun detalle mas...

---

### Post by losoollenos on 2011-02-27
Maverick 10.10 64 bits, y bajé la última de SystemRescueCD.

---

### Post by biale on 2011-02-27
Seria la 2.0.1 (SystemRescueCd-x86-2.0.1)

En la primer pantalla yo le paso las opciones "setkmap=es docache". Cuando termina de arrancar, el comando "startx" arranca a su vez la interfaz gráfica.

Vas a encontrar a gparted. Conviene verificar (verify) las dos particiones que estamos usando, sdb1 y sda2. En especial, sdb1 se puede verificar porque esta desmontada. Esperamos que no aparezca nada raro...

Siguiendo, los comandos de copiado también se pueden ejecutar dentro de la consola que aparece.

Y a la hora de copiar podemos prescindir del "> listado.txt". Quedaria:

cp -axv /mnt/sdb1/* /mnt/sda2

---

### Post by losoollenos on 2011-02-27
Es esa version si.

Ahora estoy con el live de systemrescue con grafica. Abro el Gparted para volver a formatear y no se ve el ssd. Parece que la unica forma de ver el disco es desde el sistema instalado jaj.

Estoy pensando en pasarme a un mother intel........

---

### Post by losoollenos on 2011-02-27
Una buena !!! sin el "> listado.txt" copio todo parece, aunque le tiré de nuevo,

root@sysresccd /root % ls /mnt/sda2                 
ls: reading directory /mnt/sda2: Input/output error

No se, acá sigo esperandote desde el live jajjaj

---

### Post by losoollenos on 2011-02-27
Reinicié para ver desde el sistema que estaba instalado la sda2, y como vi que estaban todos los archivos tiré un update-grub. Se agregó al menú de inicio, reinicié, y seleccioné para que que arranque desde la sda2 pero en realidad arrancó desde la sdb1.

Bueno, por lo menos aparece en el grub jejej, calculo que habrá que toquetear el fstab ahora no??

---

### Post by biale on 2011-02-27
"Exactamente!"

Los ideal sería arrancar una vez mas con SystemRescueCD y correr gparted (pervio startx)

Al verificar las partiones sda2 y sdb1 aparecen totales de control (guardarlos o anotar!) . Sería interesante que por lo menos el numero de "archivos regulares" equalicen. 

sdb1 necesita del system rescue CD pero sda2 puede ser analizado con gparted corriendo desde Ubuntu instalado

Sería interesante que postees (1) tu fstab actual y (2) un fdisk -l /dev/sdb 

No te preocupes por la mother, despues vamos a revisar los ajustes del BIOS...

Mañana por la tarde puedo seguir con este thread.

---

### Post by losoollenos on 2011-02-27
Ok buenísimo...

Te voy preguntando cómo veo los "archivos regulares" de la sda2 en el gparted, en la información de la partición habla de sector primero, segundo y totales, es alguno de esos?.

_El fstab:_

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1

_El fdisk -l /dev/sdb:_

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sdb 
[sudo] password for ubuntu: 

Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
135 cabezas, 14 sectores/pista, 1033611 cilindros
Unidades = cilindros de 1890 * 512 = 967680 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x0003bf75

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               2       11098    10485760   83  Linux
/dev/sdb2   *       11098     1033611   966275072    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

Gracias capo !!!

---

### Post by biale on 2011-02-28
Si arrancamos gparted y seleccionamos una particion que no este montada o se pueda desmontar, la pestaña "Particion/ Verificar" estara disponible.

Cuando haya terminado la verificacion incluso ofrece la posibilidad de guardar los detalles:

...
263115 regular files     >>> Aqui aparecen los archivos regulares.
43802 directories
60 character device files
26 block device files
0 fifos
661 links
42387 symbolic links (34539 fast symbolic links)
9 sockets
--------
350060 files
...

Antes de tocar la fstab conviene revisar un poco el BIOS. Como las mothers son distintas, vas a tener que ingresar al BIOS y "buscar".

En algun lugar van a aparecer (espero) las opciones generales de SATA y dentro de ellas algo que considere la interfase. Por ejemplo, en una mother HP que vi esta mañana decía:

SATA options/ SATA emulation...

Y habia tres posibilidades (1) AHCI (2) IDE (3) Raid

Al menos por ahora conviene la que yo escribi como segunda opción, la emulacion de dispositivos IDE.

Bajo Linux yo he arreglado algun comportamiento asi. Incluso lei que la gente de OCZ dice especificamente, que si en algun momento hay que actualizar el firmware del SSD, se necesita fijar "emulacion IDE". 

Armo una fstab y vuelvo...

---

### Post by losoollenos on 2011-02-28
Si anoche después de postear encontré la verificación pero no pude encontrar dónde se guardó ?¿ incluso recién cuando le di a guardar me dijo que ya existía el archivo y no lo puedo ver ni habilitando los archivos ocultos !!!

Por suerte lo pude guardar en otra carpeta (sda2)


GParted 0.6.2

Libparted 2.3
Verificar y reparar el sistema de archivos (ext4) en /dev/sda2  00:00:04    ( ÉXITO )
     	
calibrar /dev/sda2  00:00:02    ( ÉXITO )
     	
ruta: /dev/sda2
inicio: 20973568
fin: 41945087
tamaño: 20971520 (10.00 GiB)
comprobar errores en el sistema de archivos en /dev/sda2 y (si es posible) arreglarlos  00:00:02    ( ÉXITO )
     	
e2fsck -f -y -v /dev/sda2
     	
Paso 1: Verificando nodos-i, bloques y tamaños
Paso 2: Verificando la estructura de directorios
Paso 3: Revisando la conectividad de directorios
Paso 4: Revisando las cuentas de referencia
Paso 5: Revisando el resumen de información de grupos

154725 inodes used (23.61%)
13 non-contiguous files (0.0%)
20 non-contiguous directories (0.0%)
# de nodos-i con bloques ind/dind/tind: 0/0/0
Extent depth histogram: 125758/6
926518 blocks used (35.34%)
0 bad blocks
1 large file

102815 regular files
17204 directories
208 character device files
64 block device files
0 fifos
390 links
34423 symbolic links (28677 fast symbolic links)
2 sockets
--------
155106 files
e2fsck 1.41.12 (17-May-2010)
aumentar el tamaño del sistema de archivos hasta llenar la partición  00:00:00    ( ÉXITO )
     	
resize2fs /dev/sda2
     	
resize2fs 1.41.12 (17-May-2010)
El sistema de ficheros ya tiene 2621440 bloques. ¡No hay nada que hacer!

En un rato pongo el de sdb1.

---

### Post by biale on 2011-02-28
Como seguiremos usando el subsistema de arranque en sdb, la fstab que debemos modificar es la que se encuentra en el HDD (sdb1), con una precaución que vemos después.

sudo gedit /etc/fstab.NEW

Y añadir esto al archivo vacio:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>

  proc /proc proc nodev,noexec,nosuid 0 0

# /dev/sdb1 Ubuntu en HDD:
# /dev/sdb1   /   ext4  errors=remount-ro 0 1

# /dev/sda2 Ubuntu en SSD:
# UUID=[NUMS-AND-LETTERS]    /   ext4   discard,errors=remount-ro      0       1
  /dev/sda2                  /   ext4   discard,errors=remount-ro      0       1

```

Guardar los cambios y verificar que se hallan guardado

Fijate que hay dos modificaciones en lugar de una. Segun OCZ la funcionalidad de TRIM se habilita con el parámetro "discard"

Una precaución. Esta vez arrancamos con el SSD o no arrancamos con ninguno de los dos. O sea que hay que estar preparados para revertir los cambios via arranque live en caso de ser necesario. Peor aun, si aparece de vuelta un cartelito "read-only file system" la situación no sera agradable.

Lo mejor es hacer los cambios a traves de un arranque live, cualquiera que permita trabajar sobre sdb1. "Y si los pudimos hacer desde alli, seguramente los podremos deshacer". Puede hacerse por consola o en modo interactivo. Suponiendo que te decidas por el SystemRescueCD:

```

startx

mkdir /mnt/sdb1
mount /dev/sdb1 /mnt/sdb1
cd /mnt/sdb1/etc

cp  fstab fstab.OLD       # Salvar la fstab actual como OLD
cat fstab.OLD             # Lo hizo bien?
rm  fstab                 # Recien ahora borrarla
cp  fstab.NEW fstab       # Y reemplazar por una copia de la NEW
cat fstab                 # Lo hizo bien?

```

Ahora hay que cruzar los dedos y reinicializar la compu.

Si no funciono es facil volver atras:

```

startx

mkdir /mnt/sdb1
mount /dev/sdb1 /mnt/sdb1
cd /mnt/sdb1/etc

rm  fstab                 # Borrar fstab fallida
cp  fstab.OLD  fstab      # Activar una copia de la que anda
cat fstab                 # Lo hizo bien?

```

Si funciono bien tendremos que instalar un grub en el MBR del SSD...

---

### Post by losoollenos on 2011-02-28
Ahora reinicio y lo hago.

Pego la verificación desde Systemrescue del sdb1, sólo que ME OLVIDE e instalé unas cositas en este, digo por si interfiere en que equalicen:

GParted 0.8.0

Libparted 2.3
Check and repair file system (ext4) on /dev/sdb1  00:00:03    ( SUCCESS )
     	
calibrate /dev/sdb1  00:00:00    ( SUCCESS )
     	
path: /dev/sdb1
start: 2048
end: 20973567
size: 20971520 (10.00 GiB)
check file system on /dev/sdb1 for errors and (if possible) fix them  00:00:03    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sdb1
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

157587 inodes used (24.05%)
110 non-contiguous files (0.1%)
221 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 0/0/0
Extent depth histogram: 128534/68
1085013 blocks used (41.39%)
0 bad blocks
1 large file

105460 regular files
17397 directories
208 character device files
64 block device files
0 fifos
390 links
34446 symbolic links (28700 fast symbolic links)
3 sockets
--------
157968 files
e2fsck 1.41.12 (17-May-2010)
grow file system to fill the partition  00:00:00    ( SUCCESS )
     	
resize2fs /dev/sdb1
     	
resize2fs 1.41.12 (17-May-2010)
The filesystem is already 2621440 blocks long. Nothing to do!

---

### Post by losoollenos on 2011-02-28
Mirá, entré a la carpeta "etc" como administrador, renombré el fstab original a old y el que creaste lo dejé sin NEW, sólo fstab.

Me sigue arrancando desde el HDD (sdb1).

Por otro lado en el bios encontré, por lo menos hasta ahora (aunque miré bien,pero...):

IDE CONFIGURACION, dentro de éste se encuentra ON-BOARD IDE CONTROLLER que está ENABLED, y SERIAL ATA DEVICE también ENABLED (si deshabilitaba serial ata device no arrancaba ni desde el cd jej).

---

### Post by biale on 2011-02-28
Si, arranca desde sdb1 y a la velocidad usual, pero luego debería ya estar pasando a sda2. Deberian notarse las diferencias.

Podes verificar lo que esta montado con gparted. La partición queda con un candadito. Asi deberia parecer un candadito en sda2.

Lo que encontraste en el BIOS no es a lo que me refería. Habra algo mas?

Preparo la actualización del grub.

---

### Post by biale on 2011-02-28
La sintaxis que sigue sirve solo si sda2 esta montado como raiz (y no sdb1) 

Los podes verificar tambien haciendo un "sudo mount" y deberia aparecer algo asi como...

/dev/sda2 on / type ext4 ...

Para el MBR:

```

sudo grub-install /dev/sda

```

Y para actualizar grub.cfg

```

sudo update-grub

```

No te olvides de copiar la fstab que esta en sdb1 a sda2.

Reinicio, y por BIOS seleccionas al SSD para arrancar

---

### Post by losoollenos on 2011-02-28
Raro...

No puedo entrar a sda2 si uso el fstab que me pasaste, yo sólo le agregué la uuid que ya la revisé.

Habrá que comentar la línea?:

/dev/sda2    /   ext4   discard,errors=remount-ro      0       1

---

### Post by biale on 2011-02-28
Postea los resultados de "sudo mount" para ver que quedo montado...

y si queres ganar tiempo la fstab modificada.

Otro si (e importante) asegurate que a nivel del BIOS estemos arrancando explicitamente con el MBR del disco SDB. Te digo esto porque ahora recuerdo que hubo un intento de instalación de Ubuntu fallida.

---

### Post by losoollenos on 2011-02-28
Volví al fstab original ahora para poder entrar a la sda2.


ubuntu@ubuntu:~$ sudo mount
[sudo] password for ubuntu: 
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
ubuntu@ubuntu:~$ 

_fstab modificado:_

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>

  proc /proc proc nodev,noexec,nosuid 0 0

# /dev/sdb1 Ubuntu en HDD:
# /dev/sdb1   /   ext4  errors=remount-ro 0 1

# /dev/sda2 Ubuntu en SSD:
# UUID=6564e5c9-dc7b-4d05-972d-7c20e0de1795    /   ext4   discard,errors=remount-ro      0       1
  /dev/sda2                  /   ext4   discard,errors=remount-ro      0       1

Desde el bios estoy arrancando desde el SSD. El gparted me marca la sda1 como boot, y también la sdb2 !!!, está bien eso ???

---

### Post by biale on 2011-02-28
> Desde el bios estoy arrancando desde el SSD.

Arrancá desde HDD. La fstab modificada estaba alli.

La marca de boot no influye. Y a larga los dos discos van a quedar como arrancables

---

### Post by losoollenos on 2011-02-28
Acabo de probar eso, pero sigue arrancando desde el sdb1.

Pero es normal que con éste fstab no puedo no sólo entra a sda2, sino que no me aparece en la carpeta Equipo; si aparece cuando abro gparted.

---

### Post by biale on 2011-03-01
No te entendí bien. Supongamos que arranques desde HDD por Bios, desde alli a sdb1 y que este activa la fstab antigua, tal como hacias antes de instalar al SSD. 

Bajo esas condiciones, en la carpeta "equipo", aparece alguna referencia a sda2 (testsys)? Te permite con doble click ingresar a ella?

Haciendo "sudo lshw" aparece el SSD?

Si existe una "/mnt/carpeta-vacia" y esta vacia, podes montar la partición:
"sudo mount -t ext4 /dev/sda2 /mnt/carpeta-vacia" ?

La utilidad de discos (palimpsest) lo encuentra?

Fijate en los logs todo lo que referencie al SSD (dmesg)...

---

### Post by losoollenos on 2011-03-01
Es así: con el fstab original aparece la partición "testsys" en la carpeta Equipo y puedo ingresar perfectamente.
Con "sudo lshw" detecta al ssd como disk 0 (si mal no recuerdo) con todas sus particiones.
En /mnt/ tengo la carpeta testsys y puedo montar ahi la sda2 perfectamente.

Luego, con el fstab modificado, ya no aparece la partición "testsys" en la carpeta Equipo, pero se monta perfectamente en /mnt/testsys y se entra a cualquier archivo; sin embargo, sigue sin aparecer en Equipo.

La utilidad de disco lo encuentra, el que no encuentra nada del ssd soy yo con el comando dmesg jej.

---

### Post by biale on 2011-03-01
De acuerdo con lo que me decis Ubuntu reconoce bien y maneja bien al disco. Ahora que ya se que existe un MBR en el SSD, yo creo que si revisamos con cuidado toda la cadena de arranque sda, tiene que salir andando...

Lo primero es grub. Si booteas sobre el SSD, al aparecer las sentencias de arranque de grub, da la opción de abrir una consola de comandos. Aqui interesa la salida de un comando "set", postea aunque sea el valor de la variable "prefix".

---

### Post by losoollenos on 2011-03-01
Dió:

    prefix > (HD1,MSDOS1)/boot/grub

    root > HD1,MSDOS1

---

### Post by biale on 2011-03-01
Eso parece ser sdb1 (?). Vamos a adicionar una entrada al menu de grub para los dos discos. necesito que postees las salidas de:

(1) sudo ls -l /dev/disk/by-uuid

(2) Que edites tu "/boot/grub/grub.cfg" y me pases la primer entrada de menu que tengas (comienza con "menuentry" y termnina con "}"

(3) Igual a como hiciste con el comando "set" a nivel del grub, pero esta vez el comando es "ls (HD0,MSDOS2)/boot"  Solo necesito que me confirmes si la salida del comando muestra a los nucleos. En teclado ingles ( es 9, ) es 0 y "-" es /

---

### Post by losoollenos on 2011-03-01
_Bueno, sudo ls -l /dev/disk/by-uuid:_

ubuntu@ubuntu:~$ sudo ls -l /dev/disk/by-uuid
[sudo] password for ubuntu: 
total 0
lrwxrwxrwx 1 root root 10 2011-03-01 17:56 283041A930417F36 -> ../../sda5
lrwxrwxrwx 1 root root 10 2011-03-01 18:22 29CB1F5C359100BE -> ../../sda6
lrwxrwxrwx 1 root root 10 2011-03-01 18:22 2C4109236C0EE907 -> ../../sda8
lrwxrwxrwx 1 root root 10 2011-03-01 18:22 4aa32250-84b1-47a4-839c-becc1b4a04c6 -> ../../sda7
lrwxrwxrwx 1 root root 10 2011-03-01 18:22 6564e5c9-dc7b-4d05-972d-7c20e0de1795 -> ../../sda2
lrwxrwxrwx 1 root root 10 2011-03-01 18:22 6E5C55535C551765 -> ../../sda1
lrwxrwxrwx 1 root root 10 2011-03-01 17:56 AA6688A166886FBD -> ../../sdb2
lrwxrwxrwx 1 root root 10 2011-03-01 17:56 aeb338ce-be00-498b-a00b-45983435c48b -> ../../sdb1
lrwxrwxrwx 1 root root 10 2011-03-01 18:22 df0b47fa-55d6-4d68-9e63-1ee139fdb1b4 -> ../../sda3
ubuntu@ubuntu:~$ 

_Grub.cfg:_

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

_ls (HD0,MSDOS2)/boot_

Error: no such disk


Fijate si lo del grub.cfg es lo que me pediste.....

---

### Post by biale on 2011-03-01
Para el grub.cfg: no es esa parte. Ubica la primera ocurrencia del string "menuentry", vas a ver el mismo cartelito que aparece en pantalla al arrancar. Necesito esa linea y las que siguen hasta el paréntesis de cierre "}" O sino postealo todo...

Para el "no such disk". Un nuevo arranque y los resultados del comando "ls" a secas. Aunque sea un poco largo.

---

### Post by biale on 2011-03-01
Esta fstab va en sda2. Ojo: no sirve para sdb1

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>

  proc /proc proc nodev,noexec,nosuid 0 0

# /dev/sdb1 Ubuntu en HDD
# /dev/sdb1   /   ext4  errors=remount-ro 0 1

# /dev/sda2 Ubuntu en SSD
  UUID=6564e5c9-dc7b-4d05-972d-7c20e0de1795    /   ext4    discard,errors=remount-ro 	0       1
# /dev/sda2                                    /   ext4    discard,errors=remount-ro    0       1

```

---

### Post by losoollenos on 2011-03-01
_1) Copiado nuevo fstab en sda2._

_2) grub.cfg, por las dudas....:_

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set aeb338ce-be00-498b-a00b-45983435c48b
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=aeb338ce-be00-498b-a00b-45983435c48b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set aeb338ce-be00-498b-a00b-45983435c48b
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=aeb338ce-be00-498b-a00b-45983435c48b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set aeb338ce-be00-498b-a00b-45983435c48b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set aeb338ce-be00-498b-a00b-45983435c48b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6e5c55535c551765
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 6564e5c9-dc7b-4d05-972d-7c20e0de1795
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=aeb338ce-be00-498b-a00b-45983435c48b ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 6564e5c9-dc7b-4d05-972d-7c20e0de1795
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=aeb338ce-be00-498b-a00b-45983435c48b ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

_3) ls:_

(hd0) (hd0,msdos8) (hd0,msdos7).....hasta 1 (hd1) (hd1,msdos2) (hd1,msdos1).

Vamos bien ???

---

### Post by biale on 2011-03-01
Vamos mejor de lo que pensaba. Hoy corto mas temprano, mañana seguimos y quizas completamos.

Solo confirmame que las sentencias del grub las tomaste del Ubuntu HDD, sdb1 montado.

---

### Post by losoollenos on 2011-03-01
Sisi, es el grub del sistema instalado en sdb1; y desde el mismo lo estoy posteando.

Que descanses y muchas gracias !!!

---

### Post by biale on 2011-03-02
Ahora solucionamos una de las galletas. Edita con cuidado el archivo grub.cfg en sdb1 con estas modificaciones:

Donde dice:
```

menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda2)" {
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 6564e5c9-dc7b-4d05-972d-7c20e0de1795
linux /boot/vmlinuz-2.6.35-25-generic root=UUID=aeb338ce-be00-498b-a00b-45983435c48b ro quiet splash
initrd /boot/initrd.img-2.6.35-25-generic
}
```

Se cambia por:
```

# (hd0,msdos2) =  6564e5c9-dc7b-4d05-972d-7c20e0de1795
# (hd1,msdos1) =  aeb338ce-be00-498b-a00b-45983435c48b
# Cambio uuid y retiro "quiet splash"
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda2)" {
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 6564e5c9-dc7b-4d05-972d-7c20e0de1795
linux /boot/vmlinuz-2.6.35-25-generic root=UUID=6564e5c9-dc7b-4d05-972d-7c20e0de1795 ro
initrd /boot/initrd.img-2.6.35-25-generic
}
```

Luego de salvarlo, ademas usalo para reemplazar el que esta en sda2 para que queden los dos iguales. Guarda una copia aparte porque un update-grub lo va a modificar a su gusto sin previo aviso.

La linea de menu que usaremos para arrancar es:
```

Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda2)

```

Arranca (boot) desde el disco que quieras y fijate si tira algun error o se bloquea durante el arranque. Si no arranca desde un disco proba con el otro.

---

### Post by losoollenos on 2011-03-02
No arranca che....desde sda2 no arranca, muetra que fallan algunos comandos (entre los que se ve el del dispositivo) y después da una larga lista de errores repetidos y medio que se planta.

En el segundo intento no tiró tantos errores, muy lentamente llega a donde pone "login", y ya de ahi no pasa, indistintamente que el bios tenga al ssd o al hdd como prioritario.

---

### Post by biale on 2011-03-02
Eso justificaría las definiciones que escontramos en grub.cfg, tomo de donde pudo. Supongo que no tenes /home (etc) encriptado? Si fuera asi no lo soporta.

Ahora habria que mirar los logs que quedaron en el SSD, /var/log/messages y asi siguiendo. Donde aparece "failed command", "error", "warning"...

Acabo de leer que pueden producirse "bloqueos" debido a que el scheduler esta preparado para discos mas lentos. Pero eran optimizaciones sobre discos funcionando.

Alguna otra idea sería reemplazar en la fstab "discard" por "noatime". 

Mas concreto sería elevar la versión del nucleo: Natty viene dentro de solo dos meses. Y hay mas particiones en el SSD que pueden servir para probar con otras alternativas.

---

### Post by losoollenos on 2011-03-02
Con "noatime" no hay cambios.

En el archivo "messages" del ssd no hay nada, tampoco en el "messages 1". En los del hdd si pero es larguísimo, no se......

Ya intenté con la beta 2 de Natty, kernel 2.6.38, y no lo ve che.

Mil gracias loco !!!

---

### Post by losoollenos on 2011-03-03
En horas extras anoche instalé Maverick en el MSI que conté al principio sin problemas.

De cabeza dura también intenté arrancar con ese disco en mi pc y se bloqueó, claro que podría haber otras causas supongo, viniendo de una instalación en otro hardware, aunque todas las veces que hice cambios de hardware, Ubuntu pareció ni haberse enterado.

Que Ubuntu arranca en esa máquina en 7.7 segs !!! va a ser un motivo que no voy a poder resistir jejjee.....me voy a negociar con mis amigos de computación urgente !!!!

Igualmente podemos probar cualquier cosa por las dudas que puedan quedar.

Saludos y muchísimas gracias !!!!

---

### Post by biale on 2011-03-03
Lo que pudiera quedar es muy a titulo experimental. 

Si una curiosidad, pregunta/ fijate si por esas casualidades el BIOS de la máquina de tu amigo, en los ajustes de SATA tiene fijada la "emulacion a IDE" (en lugar de AHCI pleno).

---

### Post by losoollenos on 2011-03-03
Si, hay la opción en ese mother, donde seteas sata dice IDE entre paréntesis. En el mío las opciones de sata son Disabled-Enabled.

---

