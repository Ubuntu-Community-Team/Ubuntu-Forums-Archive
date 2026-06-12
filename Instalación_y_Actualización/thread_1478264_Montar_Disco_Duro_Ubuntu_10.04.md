---
title: "Montar Disco Duro Ubuntu 10.04"
date: 2010-05-09
forum: Instalación y Actualización
---

### Post by Meenn on 2010-05-09
hola que tal..

les cuento que tengo 3 discos duros uno de 80 GB (ocupo el S.O.) otro de 250 GB (de trabajos) y de 320 GB de (Trabajos y respaldo)

asi que el de 80 borre e instalo windows y linux sin problemas y siempre me reconose los demas discos duros cuando hacia eso asi que no tenia ningun problema...

pero ahora que instale este fin de semana la version ubuntu 10.04 solamente me reconosio el disco de 250GB sin problemas con archivos y todos.  y el disco duro de 320 GB nada de nada.. me sale este error al tratarlo de montarle


[[IMG]http://img714.imageshack.us/img714/6300/errordiscoduro.th.png[/IMG]]("http://img714.imageshack.us/i/errordiscoduro.png/")





me gustaria saber como podre areglar este problema  para tener acceso al disco duro..


si ocupo el ubuntu 10.04 como LIVE-CD puedo ver los discos duros sin problemas. solamente me pasa cuando instalo el S.O. ubuntu 10.04

anteriormente con ubuntu 9.10; 9.04; 8.10 me funsionaba sin problemas.


si me pueden ayudar para tener acceso al disco y OVIAMENTE SIN PERDER LA INFORMACION DE ALLI estare muy agradecido..

Saludos...

---

### Post by Grasber on 2010-05-09
No soy un experto, pero creo que estás tratando de montar la unidad que tiene instalado el Ubuntu. O sea, tratas de montar la unidad sobre la que estás trabajando...
Seguramente la configuracion de nombre de los dispositivos cambió..
usa GParted para ver qué unidades están presentes y ve que nombres tienen.
Sino empieza a probar con sda2, sdb1, sdb2,etc.

---

### Post by Meenn on 2010-05-09
> **Grasber said:**
> No soy un experto, pero creo que estás tratando de montar la unidad que tiene instalado el Ubuntu. O sea, tratas de montar la unidad sobre la que estás trabajando...
Seguramente la configuracion de nombre de los dispositivos cambió..
usa GParted para ver qué unidades están presentes y ve que nombres tienen.
Sino empieza a probar con sda2, sdb1, sdb2,etc.


okey, amigo mucha gracias, pero me gustaria como poder hacer eso montar la unidad de esa forma.

saludos

---

### Post by asterix77 on 2010-05-09
Ejecuta los siguientes comandos, y los pegas acá.
	 	 	 	/etc/fstab 

Puedes forzar el montado de una unidad ntfs de la siguiente forma

#   	 	 	 	 	 	 	sudo mount -t /dev/xxx /media/disk-1 ntfs-3g force 0 0 

donde xxx es según la partición que te aparezca con los comandos anteriores

Con respecto a gparted aún no he instalado Lucid, pero me imagino que al igual que las distribuciones anteriores, solo el live cd trae gparted. Si tienes acceso a internet tienes que instalarlo de la siguiente forma desde la terminal:

#sudo apt-get install gparted

Luego te vas a sistema------->Administración-------->Gparted

La interfáz gráfica es fácil e intuitiva.


Saludos

---

### Post by Carlos C on 2010-05-10
Creo que Meenn tiene razón y tienes un pequeño problema con las particiones. Por favor corre los siguientes comandos y nos das la salida:
```
sudo fdisk -l 
```
para ver tus particiones. También:
```
df -T
```
y así vemos donde están montadas y el tipo de partición que es cada una. Por último:
```
cat /etc/fstab
```
Creo que esto último era lo que quería sugerir asterix77.

Saludos.

---

### Post by asterix77 on 2010-05-10
Si Carlos era eso, pero ahora que veo el post, este era más largo. Creo que accidentalmente pasé a borrar algo.

De vez en cuando me sucede, no sé el motivo, pero a veces estoy escribiendo algo, y la barrita se me desplaza a otra posición.

saludos

---

