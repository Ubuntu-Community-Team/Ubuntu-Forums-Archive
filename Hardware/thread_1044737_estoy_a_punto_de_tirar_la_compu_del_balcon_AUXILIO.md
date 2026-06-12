---
title: "estoy a punto de tirar la compu del balcon AUXILIO!!!!!!!!"
date: 2009-01-19
forum: Hardware
---

### Post by aleittte on 2009-01-19
hola como va una vez mas tengo un problema grande como una casa.... esta vez esta todo instalado todo funcionando.... la cosa es que no se por que no carga ninguna pantalla para logearse ( ni la grafica ni la otra ) y lo unico que tira es que no tengo no se que init que necesita para bootear.para colmo de males no se que le hice al cpu en si, que no bootea del cd directamente, sino que tenes que buscar la opcion para....
estoy que me quiero morir y matar y romper la pc en 250 pedazos ..
que hago por favor ayuda!!!!

---

### Post by Cristiandley on 2009-01-19
Espera, Tranquilizate. Primero que todo la calma.

1ro.- Explica bien tu problema.
Asi podemos ver bien que te sucede.

Decis que no podes ver "nada" ?
La PC arranca ?
Se salta el Login y arranca directamente o queda todo Oscuro en la pantalla ?

Saludos y Suerte

---

### Post by Thalskarth on 2009-01-19
> **aleittte said:**
> lo unico que tira es que no tengo no se que init que necesita para bootear

Podrías trascribirnos el mensaje que te sale, como para saber exactamente cual es el error?

---

### Post by aleittte on 2009-01-20
[FONT="Comic Sans MS"]dice lo siguiente 
starting up ...
carga 1 seg la barra de ubuntu, despues se va a negro y aparece lo siguiente:
starting up 
loading, please wait..
19+0 records in
19+0 records out
kinit: name-to-dev-t(dev/disk/by-uuid/1733a799-aa1b-4ae6-b92a-be3543d41eb5)=dev(8,5)
kinit: Triying to resume from /dev/disk/by-uuid/1733a799-aa1b-4ae6-b92a-be3543d41eb5
kinit:no resume image. doing normal boot
mount: mounting /dev/disk/by-uuid/7eb88fc2-279f-4f8a-8206-bb5f3388d2 on /root failed: invalid argument
mount: mountig /root/dev on/dev/.static/dev failed: no such file or directory
mount:mounting /sys on/root/sys failed: no such file or directory
mount:mountig /proc on/root/proc failed:no such file or directory
target filesystem doesn't have /sbin/init.
no init foun. try passing init=bootarg.
busybox v1.10.2(ubuntu1: 1.10.2-1ubuntu6)built-in shell(ash)

y de alli en mas nada mas ....
entonces que hago? 
gracias 
[/FONT]

---

### Post by Hei Ku on 2009-01-20
Pareciera no encontrar el disco.

Que pasa si tratas de bootear desde un LiveCD?

---

### Post by guillermolisi on 2009-01-20
Por las dudas, no habras dejado puesto un CD, un pendrive o un diskette que la maquina reconoce y usa para bootear antes de llegar al disco rigido ?

Me llaman la atencion estas lineas:
```
19+0 records in
19+0 records out
```
que son la clasica salida de la ejecucion del comando dd.

Que version de Ubuntu instalaste ?

---

### Post by aleittte on 2009-01-20
tengo instalado el 8.10 no hay ni hubo ningun pendrive, cd o lo que sea solo un corte de luz y varias reiniciadas

---

### Post by guillermolisi on 2009-01-20
> **aleittte said:**
> tengo instalado el 8.10 no hay ni hubo ningun pendrive, cd o lo que sea solo un corte de luz y varias reiniciadas

Entonces mi recomendacion pasa por correr un filesystem check al disco de la maquina (con man fsck en una consola tenes acceso al manual para saber como usarlo) si aun no fue hecho (ext3 lo corre automaticamente despues de cierta cantidad de veces que el filesystem se monta).

Esto lo podes hacer iniciando en modo de recuperacion (tenes que entrar al menu de Grub cuando encendes la maquina, presionando ESC) o iniciando con un Live-CD e intentando montar a mano el disco de la PC (esto ya es algo mas sofisticado).

Si esto no encuentra errores en su estructura y los repara, entonces algo se rompio en forma irremediable (salvo con una reinstalacion y/o cambio de hardware en caso que sea el disco, la fuente, mother, etc. lo que este dañado).

---

### Post by aleittte on 2009-01-21
me gustaria que me explicaras como montar a mano el disco ya que con el live cd no lo puedo abrir... lo reconoce pero dice que no lo puede montar, la otra cosa es como abrir una terminal para accesar al disco desde el live cd..
otra cosa cuando inicia ni siquiera puedo cargar el grub o sea tira todos los mismos carteles que te dije antes y no puedo llegar a hacer el fsck ni siquiera acceder a una consola... please help no quiero reinstalar por que pierdo mi vida!!!

---

### Post by zeroadrenaline on 2009-01-21
> **aleittte said:**
> me gustaria que me explicaras como montar a mano el disco ya que con el live cd no lo puedo abrir... lo reconoce pero dice que no lo puede montar, la otra cosa es como abrir una terminal para accesar al disco desde el live cd..
otra cosa cuando inicia ni siquiera puedo cargar el grub o sea tira todos los mismos carteles que te dije antes y no puedo llegar a hacer el fsck ni siquiera acceder a una consola... please help no quiero reinstalar por que pierdo mi vida!!!

Primero lo primero, en la desesperacion estas ecribiendo cosas que no tienen sentido.
El grub es un listadito de opciones que te aparecen antes de que la maquina empiece a tirar esa lista de cositas que pusiste arriba.
Si la listita te aparece, es porque GRUB ya paso de largo, fijate si cuando inicias la maquina, no te aparece un contador regresivo, que diga press ESC to see options o algo asi, hay una opcion para ocultar el menu del GRUB, que te hace eso.
Si podes ver las opciones de grub, es un buen comienzo, en vez de elejir la primera, que seria el systema completito hecho y derecho, metete como te dijeron antes en el rescue, que seria el segundo si no recuerdo mal, pasa que nunca lo nececite asique no se cual es jejejej.
Igual ahi en el listadito de cosas que pusiste te dice que pruebes desde el GRUB cambiar las opciones de inicio y agregues 
init=bootarg
Para esto, en el GRUB te paras sobre la opcion que queres, y apretas la letrita ¨e¨ (edit) te va a aparecer un menu, en el renglo donde aparece el kernel, y las opciones de booteo, proba de agregar esa linea que te recomienda, le das ¨b¨ (boot) y probas.
No se si funsione pero yo soy de los que piensan que si la computadora te esta diciendo algo, primero hacele caso a la compu, para ver si por casualidad tiene razon.
Un abrazo, y ojala soluciones.

---

### Post by zeroadrenaline on 2009-01-21
[http://kubuntuforums.net/forums/index.php?topic=13879](http://kubuntuforums.net/forums/index.php?topic=13879)

Esta en Ingles, pero se entinede clarisimo, fijate si eso te soluciona.

Si lo hace, buenisimo, respira tranquilo/a, y como recomendacion, en los titulos de tus Hilos, no pongas AUXILIO ME HUNDO EN UN MAR DE DESESPERACION!!!
ya que hay algunos lectores (no es mi caso) que saben mucho mucho, pero les jode mucho mucho que no les pongan detalles del problema en los titulos,es comprensible, uno entra en un hilo con titulo catastrofico esperando un problema catastrofico, y despues resulta que el usuario se ataca porque reinstalo XP y no sabe como reinstalar grub, cosa que se aprende a hacer en el kiosco de la esquina, y te perdes de que te ayuden.
Repito, espero que el link te ayude a solucionar.

---

### Post by guillermolisi on 2009-01-21
> **aleittte said:**
> me gustaria que me explicaras como montar a mano el disco ya que con el live cd no lo puedo abrir... lo reconoce pero dice que no lo puede montar, la otra cosa es como abrir una terminal para accesar al disco desde el live cd..
otra cosa cuando inicia ni siquiera puedo cargar el grub o sea tira todos los mismos carteles que te dije antes y no puedo llegar a hacer el fsck ni siquiera acceder a una consola... please help no quiero reinstalar por que pierdo mi vida!!!
Para montar el disco desde el Live-CD tenes que usar los comandos mount y chroot.
Luego, para recuperar/arreglar el grub, tenes que seguir alguna guia para tal tarea. En este foro hay varios threads que hablan del tema (como reparar Grub).

Cuando usas chroot accedes al disco como si fueras root, asi que no necesitas sudo ni su.

Algo importante: Si la estructura del filesystem del disco rigido no esta bien el comando mount te va a decir que no lo puede montar.

Si podes iniciar la maquina con el Live-CD, probaria de abrir una terminal/consola (puede ser desde Aplicaciones-Accesorios o pasandote a una mediante Ctrl+Alt+F1).

Una vez en la consola, proba lo siguiente y comenta que resultado te dio:
```
sudo fsck.ext3 /dev/sda1
```
esto es para la primera particion del primer disco rigido, considerando que es reconocido como SCSI (cosa que sucede generalmente con los SATAII) y que es un filesystem ext3.

Si al disco le creaste mas particiones, tendrias que repetir para para el resto de las mismas (si tenes una segunda particion, referencia a /dev/sda2 por ejemplo).

Si queres ver las particiones que tenes en el disco rigido, usando el Live-CD, podes aprovechar el comando fdisk (o el parted) desde consola:
```
sudo fdisk /dev/sda
```

---

