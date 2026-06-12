---
title: "[SOLUCIONADO] Ubuntu 9.04 - no inicia windows xp"
date: 2009-08-22
forum: Instalación y Actualización
---

### Post by Skuee on 2009-08-22
hola a todos, este es mi primer post en el foro de la comunidad.

hace pocos dias migré a ubuntu, me familiarize super bien con el SO, el único problema fue que despues de instalar ubuntu 9.04 no puedo entrar a windows xp, despues de elegir la opción se queda pegado en "starting up..." y no puedo nisikiera volver a instalarlo o repararlo. Podría borrarlo y ya, pero necesito hacer un backup de mis marcadores de Firefox y los correos de thunderbird.

en otro foro me sugirieron ver este articulo [http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB) pero aun no puedo solucionar el problema

aqui hay informacion sobre el disco donde estan instalados los SO
```


ubuntu@ubuntu:~$ sudo fdisk -l

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x00a200a2

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        6687    53713296    7  HPFS/NTFS
/dev/sda2            6688        9729    24434865    5  Extendida
/dev/sda5            6688        9243    20531038+  83  Linux
/dev/sda6            9244        9729     3903763+  82  Linux swap / Solaris


```

**sobre el articulo llegue solo hasta donde esta en negritas**:
```

Cambiando el origen de la carpeta raíz Cambiamos el origen de la carpeta raíz de nuestro sistema de archivos al directorio en el que hemos montado la partición de Ubuntu, para que al instalar GRUB interprete que la raíz del sistema está ahí. 

1. Antes que nada, crear un directorio y montar allí la partición de Ubuntu:  

  $ sudo mkdir /media/ubuntu
$ sudo mount /dev/hda1 /media/ubuntu
  2. Luego conectar el directorio dev del livecd con el de la partición Ubuntu:  

  **$ sudo mount --bind /dev /media/ubuntu/dev**


```

[B]tuve ke hacer unas modificaciones, cambiar hda1 por sda1
[/B]```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
[B]ubuntu@ubuntu:~$ sudo mount /dev/hda1 /media/ubuntu
mount: el dispositivo especial /dev/hda1 no existe
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/ubuntu[/B]
ubuntu@ubuntu:~$ sudo mount --bind /dev /media/ubuntu/dev
mount: el punto de montaje /media/ubuntu/dev no existe
ubuntu@ubuntu:~$ sudo mount --bind /dev /media/ubuntu/dev
mount: el punto de montaje /media/ubuntu/dev no existe
ubuntu@ubuntu:~$

```

y llegue hasta ahi, despues fui a /media con el navegador de archivos y estaba la carpeta disk y la carpeta ubuntu.
la disk tiene el ubuntu 9.04 que instale y /ubuntu tiene el wintendo
[]("http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB")

---

### Post by Carlos C on 2009-08-22
Hola. Si puedes escoger la opción de partir con windows entonces no es un problema del Grub. No es necesario que lo restaures. En general es necesario restaurar el GRUB cuando instalas windows después de haber instalado Ubuntu, no al revés. Creo que tu problema es otro ¿Cómo fue que instalaste Ubuntu? ¿Modificaste la partición de Windows para obtener el espacio que necesitabas? Porque creo que hubo un problema al redimensionar la partición ntfs. Lo mejor sería que montaras la partición en donde tienes Windows y recuperaras los archivos que necesitas. Para eso puedes mirar acá:

[http://pcarmona.wordpress.com/2009/04/12/montar-discos-de-windows-al-logearse-en-gnome/](http://pcarmona.wordpress.com/2009/04/12/montar-discos-de-windows-al-logearse-en-gnome/)

Saludos.

---

### Post by nopersona on 2009-08-22
Y desde Ubuntu puedes ingresar a las particiones de windous?

---

### Post by Skuee on 2009-08-22
acabo de llegar a mi casa...

> **nopersona said:**
> Y desde Ubuntu puedes ingresar a las particiones de windous?

si, si puedo

---

### Post by gmunioz on 2009-08-22
Hola sku.....:

1- El tutorial que sigues es para montar un sistema

GnuLinux inaccesible, no un sistema Microsoft.

2- Instala si no estuviesen instalados, ntfs-3g,

fuse-utils, ntfs-config, ntfsprogs, esto lo haces

desde synaptic Sistema - Administración - Gestor ...)

3- Luego mediante ntfs-config (Aplicaciones - Herramientas

de sistema - Herramienta de configuración NTFS) puedes

intentar montar la partición para acceder a tus archivos

4- Si la partición estuviera dañada o corrupta, puedes 

intentar repararla con las ntfsprogs, de ellas, ntfsfix

es la herramienta que verifica completamente un volumen 

y es capaz de hacer recuperaciones básicas de los mismos.

---

### Post by Skuee on 2009-08-22
> **Carlos C said:**
> Hola. Si puedes escoger la opción de partir con windows entonces no es un problema del Grub. No es necesario que lo restaures. En general es necesario restaurar el GRUB cuando instalas windows después de haber instalado Ubuntu, no al revés. Creo que tu problema es otro ¿Cómo fue que instalaste Ubuntu? ¿Modificaste la partición de Windows para obtener el espacio que necesitabas? Porque creo que hubo un problema al redimensionar la partición ntfs. Lo mejor sería que montaras la partición en donde tienes Windows y recuperaras los archivos que necesitas. Para eso puedes mirar acá:

[http://pcarmona.wordpress.com/2009/04/12/montar-discos-de-windows-al-logearse-en-gnome/](http://pcarmona.wordpress.com/2009/04/12/montar-discos-de-windows-al-logearse-en-gnome/)

Saludos.

modifique la particion, la achique y con ese espacio hice el swap y la partición con ext3.
explicame un poco lo de:
> Este tip usa el comando [**gnome-mount**]("http://linux.die.net/man/1/gnome-mount") para montar las particiones de Windows vía HAL, permitiendo montar con [FUSE]("http://es.wikipedia.org/wiki/FUSE_%28Linux%29") los discos para que el usuario pueda modificarlos a su gusto.

---

### Post by Skuee on 2009-08-23
y el arranque de windows estaba malisimo asi que saque los archivos donde supuestamente se guardan los archivos que necesito, ahora veo como ponerlos denuevo xD

gracias por la ayuda (:

---

### Post by Carlos C on 2009-08-23
El enlace que te sugerí te mostraba como montar una partición ntfs desde linux, automáticamente al iniciar el sistema (es una de las formas posibles). Sin embargo, si ya pudiste sacar los archivos que querías, ahora puedes intentar arreglar tu partición ntfs. Eso lo puedes hacer siguiendo los consejos de gmunioz (paso 4).

Saludos.

---

### Post by Patriciologico on 2009-08-31
En resumen, el problema de windows pudo haberse originado con la redimension de la particion (windows es delicadito) y por que Skuee, movio los archivos de arranque. Pero ya puede acceder y restaurar los archivos. Lo pondre como Solucionado (si es que otra intervencion atingente no dice lo contrario).

---

### Post by rcharles84 on 2012-03-05
lo que pasa es que recuperaste el grub con otra confuracion a mi me ha pasado instale windows y recupere el grub pero voila no respondia el windows solo mostraba ubuntu. solo es necesario actualizar el grub que tiene la configuracion anterior:
$ sudo update-grub2

con esta linea nada mas :)

---

