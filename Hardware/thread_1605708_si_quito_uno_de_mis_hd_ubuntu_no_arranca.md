---
title: "si quito uno de mis hd ubuntu no arranca"
date: 2010-10-25
forum: Hardware
---

### Post by pulsar4 on 2010-10-25
Hola A todos tengo un problema para mi muy gordo porque soy nuevo en esto.

Tengo ubuntu 10.04 lts y hasta la fecha todo bien dispongo de 4 discos duros y el problema viene cuando se me ha estropeado uno de ellos y lo he quitado y lo curioso es que cuando arranca el sistema me carga el grub se selecciona el kernel que tiene que cargar y ya no arranca se queda en negro la pantalla y ya esta y si le pongo el disco duro que le he quitado si arranca.

Esto porque ocurre y como puedo quitar ese disco duro y que me arranque el sistema ya que no tengo windows solo unbuntu.

Esperando su ayuda reciban un cordial saludo Juan Carlos.

---

### Post by sebikul on 2010-10-25
buenas, podrias por favor pegar el contenido del archivo "/etc/fstab" y la salida del comando "# sudo blkid". Tambien te pido si sabes el directorio  en donde esta montado el disco duro que queres remover

es un problema simple, pasame esos datos y te digo como resolverlo

---

### Post by hectorivand on 2010-10-25
> **pulsar4 said:**
> Hola A todos tengo un problema para mi muy gordo porque soy nuevo en esto.

Tengo ubuntu 10.04 lts y hasta la fecha todo bien dispongo de 4 discos duros y el problema viene cuando se me ha estropeado uno de ellos y lo he quitado y lo curioso es que cuando arranca el sistema me carga el grub se selecciona el kernel que tiene que cargar y ya no arranca se queda en negro la pantalla y ya esta y si le pongo el disco duro que le he quitado si arranca.

Esto porque ocurre y como puedo quitar ese disco duro y que me arranque el sistema ya que no tengo windows solo unbuntu.

Esperando su ayuda reciban un cordial saludo Juan Carlos.

Hola Pulsar, bienvenido. Tal vez es una pregunta muy obvia, pero... ¿En ese disco dañado tenías instalado Ubuntu?

Otra cosa que pudo haber pasado que en ese disco estaba el punto de montaje o "/" y al sacarlo no lo encuentra y no arranca. Se me ocurre que con actualizar el gestor de arranque (Grub) el problema podría solucionarse, pero como no lo tengo muy claro, esperemos que alguien más nos ilumine, a los dos, así de paso aprendo.

Saludos
Nacho

---

### Post by pulsar4 on 2010-10-26
el fstab es el siguiente:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda7 :
UUID=8b6635e1-8814-474f-b5ba-897560efd245	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdc5 :
UUID=54A4229C86A0E5E4	/media/150_GB	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sdd1 :
UUID=13B8ED0A39FB9DA9	/media/250GB	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda3 :
UUID=6F1DD5A4686C53D4	/media/780Gb	ntfs	defaults,nls=utf8,umask=0222,nosuid,nodev	0	0
#Entry for /dev/sdc1 :
UUID=152908A5FB414FA9	/media/Fotos_150G	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sdb1 :
UUID=13FF3D9A07BA1E39	/media/PELICULAS	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sdb2 :
UUID=44B8BEF5B8BEE498	/media/PROYECTOS	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda8 :
UUID=b7af31b5-8955-470a-99d0-b4ded5385039	none	swap	sw	0	0

---

### Post by pulsar4 on 2010-10-26
las particiones que me dan problemas son la de PELICULAS y la de PROYECTOS y cuando accedo a ellos no puedo ni copiar ni borrar ni nada de esas particiones lo de otro comando se queda esperando y no me da respuesta

---

### Post by sys.adm.og on 2010-10-26
> **pulsar4 said:**
> el fstab es el siguiente:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda7 :
UUID=8b6635e1-8814-474f-b5ba-897560efd245	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdc5 :
UUID=54A4229C86A0E5E4	/media/150_GB	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sdd1 :
UUID=13B8ED0A39FB9DA9	/media/250GB	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda3 :
UUID=6F1DD5A4686C53D4	/media/780Gb	ntfs	defaults,nls=utf8,umask=0222,nosuid,nodev	0	0
#Entry for /dev/sdc1 :
UUID=152908A5FB414FA9	/media/Fotos_150G	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sdb1 :
UUID=13FF3D9A07BA1E39	/media/PELICULAS	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sdb2 :
UUID=44B8BEF5B8BEE498	/media/PROYECTOS	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda8 :
UUID=b7af31b5-8955-470a-99d0-b4ded5385039	none	swap	sw	0	0

Para solucionarlos, abrí un terminal y escribí:

sudo gedit /etc/fstab

Nota: El archivo /etc/fstab indica qué discos y particiones auto-montar al iniciar el sistema y las configuraciones para dicho proceso.

Lo primero que tenés que hacer es detectar la línea en la que se establece el montado de la partición problemática. Podría ser, por ejemplo:

```
# /windows was on /dev/sda1 during installation

UUID=572C8DDF568B4261 /windows        ntfs    defaults,uid=1000,gid=1000,noatime 0 0
```

El UUID es el número único de identificación de cada partición. También podría decir algo como /dev/sda1 o parecido (indicando la ruta del dispositivo). Lo que sigue es la ruta donde montar esa partición. En este caso /windows. Lo demás, son los parámetros que indican el tipo de partición (ntfs, fat, ext3, etxt4, etc.) y los permisos (que determinan quién tiene acceso a esa partición y bajo qué condiciones -sólo lectura, lectura y escritura, etc.), entre otras cosas.

La solución consta simplemente en agregar a la línea de tu partición problemática la parte que dice uid=1000 y gui=1000. Esto lo que significa es que el Usuario (User ID = uid) 1000 y el grupo (Group ID = gid) 1000 serán los "dueños" de esa partición. El uid y gid 1000 generalmente corresponden al usuario principal de la máquina. Para ver tu uid y gid andá a Sistema > Administración > Usuarios y grupos. Luego hacé clic en el botón Gestionar grupos, buscá tu nombre de usuario y hacé clic en el botón Propiedades. Para hacerlo directo desde el terminal escribí:

id

También es importante que borres cualquier parámetro mask (umask, dmask, fmask) que tenga esa línea y reemplazarlo por defaults, a menos que sepas exactamente por qué querés dejarlo. Éstos parámetros afinan la política de permisos (quién puede ejecutar, leer, modificar o crear archivos) de esa partición.

En conclusión, si querés podés copiar-pegar todo lo que sigue a la palabra ntfs en el ejemplo anterior y copiarlo en tu /etc/fstab en el lugar correspondiente.

Casi lo olvide a modo de informacion:
umask=0222 para entender mejor esto lee sobre los permisos en la estructura de ficheros unix
[http://www.ant.org.ar/cursos/curso_intro/x1439.html](http://www.ant.org.ar/cursos/curso_intro/x1439.html)

---

### Post by sebikul on 2010-10-26
aca te dejo como adjunto el archivo para que puedas iniciar el sistema aun cuando esos discos no estan montados

para poder aplicarlo ejecuta en una terminal
```
#sudo gedit /etc/fstab
```

pega los contenidos del archivo adjunto y guarda los cambios

para montar los discos cuando esten montados ejecuta en una terminal
```
# sudo mount -a
```

cualquier problema que llegues a tener postealo aca para seguir el tema

Saludos

---

